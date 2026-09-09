---
title: "Identifiers and ActivityPub: Some Thoughts"
categories: 
  - blog
  - activitypub
  - content-addressing
  - design
  - user stories
type: "blog"  
layout: single
author_profile: true
read_time: true
comments: true
share: true
related: true
toc: true
description: "Unbundling the address, the identity, and the integrity of a Thing on the Web, for better ActivityPubs."
excerpt: "This essay sketches out the design space of extending ActivityPub into namespaces and identifier types beyond HTTPS URLs."
image: /assets/images/too_long.png
defaults:
  # _posts
  - scope:
      path: ""
    values:
---

## TLDR;

In its essence, ActivityPub is an HTTP data protocol, **not** a social-web protocol or a website-federation protocol, even if it tries to be useful to those higher-level usecases in its design.
As such, ActivityPub software can use whatever identifiers it likes, for all kinds of things, even addressing Activities and Actors, as long as the core HTTP semantics work.
ActivityPub identifiers need to be dereferenceable in _some_ cases, but just need to be globally unique in others, or dereferenceable by particular parties at particular times.
The identifiers used can rely on domain-based trust models to authenticate _some_ content, but for multi-domain, unknown-authority, and/or untrusted-domain user stories, other kinds of integrity guarantees and additional discovery and/or resolution mechanisms are quite valuable.
What's more, these additional capabilities can be integrated in ways that are backwards compatible and don't require specification changes, so this conversation is increasingly seeming urgent to unblock investment in other extensions and features.

> Unbundling identifiers' various functions in a decentralized data protocol (discovery, location, integrity, identity) is a necessary first step to reconsider entrenched habits and evaluate new designs, fitness for a given user story, and interoperability risks objectively. 

Identifier choice is, annoyingly, not a protocol question at all, but an interoperability and thus a profiling question.
Using HTTPS URLs exclusively is a choice an implementation can make, but one that limits interoperability and constrains what subset of the network they will see to those identifiers (a sharply-constraining profiling decision, as it were).
Implementations trying to achieve better data longevity and support happier, more portable users need to adapt new profiles of the protocol to do so, and new identifier types.
What follows walks the reader through various identifier options for various use-cases, with an eye to complexity and interoperability trade-offs primarily.
Backwards-compatibility is left as an exercise for the reader, to be addressed in more specific future essays and/or FEPs.

## Prelude: Protocols versus Platforms, Websites versus Information Flows

One of the most unnerving things about philosophy and law is that you can't escape either: try as you might to devote yourself to some "practical" field like software engineering, to focus on building things that help people, to try getting software in the hands of your community, and then BAM, you find yourself discussing the nature of information in legalistic ways with a bunch of standards sickos.
Standards is nothing if not purgatory for people who thought they could get real jobs far from philosophy and law.

Disappointing as this might be to many developers, the ActivityPub specification is **not** a recipe for building websites that talk to each other, which is what people think of when they hear "protocol".
ActivityPub is a philosophy of information flows that, perhaps, in a given decade, some websites using contemporary tools and modern economies of scale *might* be able to build a website around, if they're very lucky.
In fact, in the 7 years since it was ratified by the W3C, the tools and economies of scale that people use to build websites have changed a lot, and it's definitely urgent to write new profiles and forge interoperability between new implementations of that philosophy.

ActivityPub specifies a **data language** (not just a syntax or a data shape) for those information flows, and it goes way beyond "social media" to be more like a low-level infrastructure for social *computing* more generally, i.e. groupware and annotation and targeted delivery for arbitrary data, not just likes and follows.
It is a data protocol built on top of a social data model (ActivityStreams), and while the examples hint at use-cases at higher levels, it is a very low-level specification!
ActivityPub was never and can never become an [identity platform](https://learningproof.xyz/a-decent-identity-part-1-theory/), and it was meant to offer a way of sharing data not just across "websites" and communities but also across not-necessarily-interoperable identity platforms and heterogenous networks themselves.
Any attempt to make a subset or profile of ActivityPub that is coextensive with a given identity platform builds a walled garden _within_ ActivityPub's data plane and endangers everything outside of it, and can be considered an attempt to enclose the data commons if you really want to be dramatic about it. 
Luckily, identifiers can be used in many (counterintuitive) ways that cross-cut identity systems, security perimeters, and data retrieval systems.

By starting from the broadest approach to data and identifiers, I want to frame the question of identifier choices for ActivityPub in the context of interoperability beyond and "below" (in a layering sense) identity tooling and conventional thinking about websites.
As a developer of a federating website, how much additional work are you willing to do for data from outside your "backend" and its identity system to be trustworthy?
How can we minimize that work (and minimize the NxN interoperability costs of recommending or requiring other software to do work in turn),while maximizing the value and nover user-stories you bring to your users?
What hidden costs and complexities (and technical debts) get smuggled into ActivityPub software to allow in data from "outside" your perimeter?

Such low-level _data_ interoperability, particularly across heterogeneous paradigms of user consent, trust models, or security needs, requires a bit of unlearning and relativizing identity assumptions baked into the "mainstream" of modern computing, which sadly requires, in turn, a bit of philosophizing about the identity of data itself.
Thinking about data identity, server identity, and client/user identity as three orthogonal problems unlocks a lot of new capabilities for the software, though, so it's worth stripping the Fediverse "to the studs and doing it right," as we say in the house-flipping business when we need to upgrade a given architecture.

This essay will start by addressing how _data_ interoperability needs be as broad and identity-independent as possible (think of it as a cold plunge into icy philosophical waters to wake up your brain and open your mind to many counterintuitive possibilities!).
Then it will turn to the former: user-stories and use-cases that could shift the economies of scale and fundamental social contracts of today's ActivityPub social software, website-bound as it is in a [rapidly dying internet](https://www.wired.com/2010/08/ff-webrip/).
After that, I'll conclude with some remarks that, for better or for worse, will tie up these two philosophical quagmires with the third, implicit one: the governance and versioning of the protocol itself.
(If you're not a technical reader (or even if you are but distributed systems make your head hurt) you might want to skim until or skip ahead to the use-cases section.)

## Identifying Activities, Objects, and Attachments

### ActivityPub's Requirements

In today's web the way it's experienced by essentially 100% of non-developers, a "URL" and a "link" are interchangeable:
whether clicked or type, they take you to a "page," and pages live on "sites" (apex domains).
Normal humans might trust a given "site" more or less on the human/content level, but unless any scary popups about "credentials" ruins the party, they rarely worry they have an insecure connection to "the" server they're using to to interact with that "site," and they rarely think about what happens with that "site" dies or changes its mind about what pages to server.
Most normal humans do not use words like "dereference" or "authenticity" to describe the web, but to crisply define the problem space here, we need to.

At a high level, we could decompose the problem space of which identifiers we use by the categories of things to identify in ActivityPub: Actors, Activities, and Attachments.
Or, to be even more precise, we could decompose each of those three kinds of referents into which identifier functions we need in different parts of the protocol: to reference, to dereference, to guarantee identity, prove integrity, and/or to deduplicate referents already seen by other identifiers.
Which of these functions is needed in each user-story or protocol context shapes which identifiers are better or worse there; I will go in reverse order of complexity and difficulty.

### Unbundling the address, the identity, and the integrity of a Thing on the Web

[Sub-Resource Integrity][sri] is a great example of a technique by which modern web developers differentiate the _integrity_ and _identity_ functions of web-fetching from the _locator_ functions of a URL.
When an enduser's agent is loading a thumbnail or an image or a chunk of video from a server on another continent, that agent can wait for the bytes to arrive signed over by the domain it expects the bytes from... or, if it already has the _hash_ of those exact same bytes on hand, it can get them from a(ny) much closer source, hash them, compare to the hash provided, and be done before the first byte arrives from that faraway server.
Similarly, if that same enduser is on a website that loads many CSS style sheets and Javascript bundles to render each and every single page load, in common across many URLs on the same site or even across multiple sites, particularly if these are large style sheets and bundles, that enduser's agent might like to be able to cache these redundant downloads and skip those ten slow, heavy, expensive roundtrips per pageload.
In both of these cases, the bytes the agent gets to insert into a page from example.com do not need to come directly from example.com because it is faster, cheaper, and equally safe getting them elsewhere, if and only if the pages on domain X gave you the hash in addition to one or more locations where you could get the bytes.
Our modern Javascript-heavy web environment is really only economically possible (and the UX only tolerable) because of this standard for passing hashes around paired to URLs:
`example.com` in the examples above tells the enduser's agent that it can load each media chunk or page sub-resource from example.com/path/file OR ANYWHERE ELSE, confident that you have the right bytes if the provided hash function outputs the same provided hash output.

Subresource Integrity works because the link and the hash are provided from the same HTML tag, constrained to specific tags and patterns where it is safe to do so.
During the years of piecemeal support, as browsers introduced support and older browsers were gradually replaced, there was a simple fallback: non-supporting browsers simply got in the slow lane and waited for the bytes to be loaded from example.com and did nothing with the provided hashes.
Our approach in adding integrity- and/or identity-providing identifier schemes should follow this precedent, and be evaluated against it.

### Identifying Attachments

**Attachments**, which hang off of Activities like appendices and already links (often to other domains, often with low stakes for authenticity) 
deduplicating attachments, and tracking them independently from the Activities to which they're attached, is of utmost importance for modern table-stakes performance and economics (the modern web is only as performant and cheap as it thanks to Sub-Resource Integrity and Content Delivery Networks, after all), but also for Trust and Safety (detecting copy-pasta/inauthentic activity, detecting abuse, mitigating "toxic dump" attacks, etc.).
I gathered together many of these user-stories and use-cases in my 2024 [FEP-cd47], but abstracting a bit, attachments are already links most of the time, even when [uploaded atomically alongside an Activity][media-upload], so adding new identifiers here is a much simpler operation (at the data level) than one might expect.
Where the economics of deduplication really shine, however, is in massive _aggregate_: deduplicating uploads or downloads on a multi-user server is interesting, but hardly justifies the complexity, while deduplicating attachments across the entire data plane of `as:Public` content being piped through relays Fediverse-wide is a much more useful superpower, and only possible with some alignment between implementations about exactly how to deduplicate, which digests to use, which variant of a multi-variant file (like a thumbnailed and blurred image upload) to hash in the first place, how to canonicalize images and store metadata, etc.
Deduplication-aware _relays_ and _sharedOutboxes_ function, then, like nodes in a Content Delivery Network and greatly reduce chattiness of the protocol for servers, if and only if they are using the same deduplication tactics and configurations as most of the outbox servers themselves.

Why not just use [SRI] directly, you might be asking yourself?
Many recent implementations essentially do, but indirectly:
the Misskey/Firefish family, Pleroma, and Bonfire all support configurable "bucket storage" on arbitrary/external domains via commodity providers, itself a kind of "subresource integrity" feature under the hood.
But as mentioned above, aligning the exact details is needed for Fediverse-scale (and thus economically significant) benefits to accrue to servers, clients, and relays alike, so it is fundamentally a question of harmonizing implementations.
If you're already harmonizing, we can do better than proprietary S3-style identifier schemes to achieve common reliability and security.

#### Recommendations

Relay economics are inseparable from the feasibility and justification for exploring this use-case, so it can be difficult to make any concrete recommendations without some signalling of interest and requirements from server implementations _and relay implementations_.

That said, in my [prototyping exercise] I played around with the idea of URL rewrites, and "blob stores" being synced separately from streams of public Activities.
It is entirely feasible for clients to hash uploads client-side (before initiating a parallel [media-upload]), then include that hash in the uploaded Activity, giving the Server the chance to verify uploads before rewriting URLs, adding additional identifiers, and/or adding hash information to the attachment object.

Servers might even rewrite URLs to HTTPS URLs that contain the hash in them (a handy trick that solves backwards compatibility handily), just as today they write filenames and assign bucket-storage URLs to uploads for similar reasons.
Regardless of whether hashes are smuggled into outbox-server-assigned identifiers/URLs or not, relays that are hash-verification-aware could ALSO, in turn, assign additional identifiers or URLs _where they are confident they can do so safely_, i.e. where they have, in turn, verified the chain from client bytes to the bytes they are hosting/caching/serving.

It's also worth mentioning (for people that didn't click through the [FEP-cd47] link and read it carefully) that "media" (in the cultural sense) is never byte-stable, and that hashes of, say, film clips or entire pieces of art/media/etc rarely circulate in only one canonicalized version.
For this reason, an "advanced topics in content identification" footnote needs to be placed here about semantic-hashes, which are useful not for binary matching but for more probabilistic "nearest-neighbor search" in huge datasets, and operate not on a canonical _serialization_ of a file but instead on the perceptual _output_ per content-type.
Note that the main business-case for [ISCC] identifiers is for detecting infringement on moral rights, i.e. piracy, 

### Identifying Activities

For **Activities** (i.e. "content"), we might be tempted to apply the same logic as for Attachments, thinking of Activities as essentially static objects to be deduplicated once canonicalized, for any number of user stories (facilitating verifiability and discoverability after server death or migrations, for example).
This temptation is felt even more if we think of ActivityPub as a Publication protocol that produces published Activities at URLs, which, to be fair, is exactly what today's Mastodon-compatible Fediverse does, by using HTTPS URLs as primary identifier of each Activity.
There are real problems with that approach, however, because Activities have a life-cycle before and after first publication:

1. at least one copy existed on at least one client before being published, 
2. after being published, they might get republished elsewhere when their generating Actor moves,
3. even without migrating, a single Activity might co-exist on two different domains and still be valid (with the Actor blessing and verifying both),
4. they mutate in many ways, not just when edited by the original Actor,
5. even if never edited, they have multiple forms and variants: 
    1. a Actor-signed copy versus an unproofed copy to be sent under an HTTP Signature (see  the [C2S examples]() in the specification),
    2. a variant with `bcc` expressed and a copy with `bcc` values stripped for delivery,
    4. the copy with additional properties added by the server or with URLs rewritten by the server,
    5. the HTML version (which might vary per the authentication credentials of the caller) if it is hosted on a web-accessible outbox,
    6. etc etc.

A good identifier for Activities would "link together" (figuratively or literally) all of these versions, or at least link them "one way" (more on this below), identifying a logical continuity across locations and versions/variants.
However you might want them linked (not all AP software would have the same priorities!), allowing them to be linked across systems and locations is a pretty basic ask of the protocol which strives to work for distributed systems and graph queries, not just "websites".
Speaking of global graphs, keeping `id`s from colliding is difficult work, which is why outbox URLs make good collision-resistant `id`s.
(Everything looks like a nail when you're holding a domain apex's namespace!).
But using a(ny) URL on the outbox-server's domain as an identifier _exacerbates_ the lifecycle problem outlined above, and adds the additional problems of user migration (mentioned above), data/backend migration (i.e. a community switching from Bonfire to Mastodon and redirecting all its links), and server failure/"death".
Why aren't we just using UUIDs, or snowflakes, or [TIDs] exactly, and using properties like `url` or `alsoKnownAs` to point to fallible current-hosts, that might not last forever and might not be unique or authoritative?
Or more pointedly, is Mastodon conformant to the AP specification if it drops Activities that use UUIDs or other conflict-resistant URNs as their `id`s?

#### Recommendations

If we think of content-identifiers as a special case of UUIDs (or UUIDs with extra integrity properties), using a content identifier as an identifier (or as an additional/`alsoKnownAs` permalink) can be justified... if and only if a canonical version can be chosen to generate that single content identifier, and a "redirect table" or other such map of variants and alternate identifier can be managed centrally somewhere.
In such an approach, the software managing the Activity can work around the mutability of an object using the "microledger" pattern used in many decentralized or trustless contexts, e.g. hashing the "genesis state" of the object at inception using that content-identifier to link together later variants... and to anchor verifiable histories of mutable object.

I even experimented with two drastically different variants of this approach in a [prototyping exercise], and found that the privacy tradeoffs of content-identifiers are similar to the privacy tradeoffs of publishing signatures that verify against published keys, in that anyone with the pre-image can prove a publication event happened from witnesses, even if the original outbox server deletes the event or disappears.
To mitigate this, the pre-image of a content-identifier (like any nonrepudiable artefact) should be kept private and shared as selectively as possible;
in an ActivityPub context, this leads me to suggest content-addressing of Activities and direct signing of [equally difficult-to-canonicalize] Activities be entirely a **client-side** capability, as data portability is primarily a client-/user-initiated concern, and the client/user should probably be in the loop for (i.e. consenting meaningfully to) rare exceptions like whole-server migrations.

### Identifying Actors

**Actor objects** are, perhaps, the spiciest and gnarliest object in the protocol design space to identify, if we want their identity and integrity to OUTLIVE and/or be INDEPENDENT OF a given outbox server, which was debatably implied by the evocative phase "the actor's namespace" in the [identifiers section](https://www.w3.org/TR/activitypub/#obj-id) of the [ActivityPub] specification.
It is implied even more strongly by the original phrasing of that sentence, preserved in the [pre-consensus 2017 draft](https://www.w3.org/TR/2017/CR-activitypub-20170907/#obj-id): "the user's namespace".
How do users of websites (tenants, in the two-tier economy of the web, that do not control domain names) control a namespace, if (as mentioned above) domain names are usually used to partition the total namespace of possible URLs for guaranteeing uniqueness and/or communicating location and discoverability?

There are a couple different problems wound up in this one, which I left for last to build on the previous cases.
As above, any identifier and/or URL without the outbox server's domain in it loses the integrity and identity guarantees inherited from that domain, and Actor identifiers and URLs are no exception.
What complicates things is that this issue compounds when we unbundle the outbox server from the "identity provider," as it is called in OpenID Connect and the KYC industry generally.
Some combination of signatures and/or hash functions can provide integrity across the life of **Activities/Objects and Attachments**, but the _identity_ of the `Actor` that gets verified gets very hard to verify once we leave the "trust domain" of the outbox server (whether by migration, server death, technical failure, or server malice).
Actor identifiers and alternate identifiers found in Actor objects can be thought of as interdependent, because in some corner cases (like dead servers or migrations) you will need to verify them _both_ to trust the link between them bidirectionally, which may be needed, in turn to verify the _data_ originated by the Actor or its indirection/alias.
(This is compounded and even more true in the case of multi-protocol clients/users discussed below.)

Here, it is hard to exhaustively enumerate the architectural possibilities, or evaluate them fairly against each other, without considering _both_ the integrity and identity of _data_ from the integrity and identity of _Actors_ listed in them.
It helps to focus on an end-to-end user story to think through these dependencies, because whatever direction you run them in, they all have to verify for any of them to verify.
We have some clear, currently-impossible user stories like this in the ActivityPub context, which I wrote up in 2024 for the Portability Task Force as [FEP-73cd]:

1. How to recover social graph and publication history moving from server A to server B, if server A experiences a sudden and unexpected "server death" by force majeure or government/ICANN intervention?
2. How to execute an "adversarial migration", e.g. migrating an account from server A to server B or from B to A, where server A defederates from server B or otherwise refuses to accept its signatures and authority?

> The answer, in both cases, is of course server (or more likely serv**ice**) C.

Any way you slice it, you need a C for both these user-stories, whether that be operated inside the client, or in a witnessing service trusted (with or without cooperating and consent from A & B is an implementation detail).
I won't constrain or bias the problem space by throwing out solutions, but suffice it to say that, returning to identifiers, C necessitates some identifier that is neither assigned by nor relies on A or B for resolution.

An identifier independent from both outbox servers' domains and yet useful to both is, almost definitionally, a _decentralized_ identifier (even if it's not a conformant W3C Decentralized ID, i.e. a "[did]").
At the very least, such an identifier would need to be grounded in some neutral third authority, i.e. a live and long-lived third domain.
If not a third domain (who would run such a service? who would pay for the domain?), additional authority options that could provide integrity and/or identity of Actor Objects are basically limited to cryptographic guarantees provided by non-web protocols, i.e., an ICANN-independent state machine, distributed hash table, blockchain or directed acyclical graph.

As part of a larger grant-funded work to advance the state of ActivityPub implementations, Dmitri and I walked through the thought process of designing a simple third-domain system to have a baseline solution against which to compare more complex (or unpopular because unwebby) solutions to the same problem.
We published it in 2024 as [FEP-e3e9], and I stand behind it as a workable design, even if not one that a batteries-included adoption- or sustainability-model falls out of easily.
The biggest problem with that design is that as a percentage of ActivityPub users today or in any foreseeable future, a vanishingly small number would be motivated and skilled enough to spin up such a service on a simpleton domain on which they annual ICANN rent, _even if_ spinning up the service were a "one-click" VPS option (remember Digital Ocean droplets? and YuHost? that kind of thing).

In my [prototyping exercise] that I ran last month, I did a seemingly much more complex version of the same "permalink" architecture, but with a more automatable deployment structure and no ICANN rent to pay, namely based on "portable" did:[webvh] identifiers that can be spun up automatically at time of account creation and updated on the occasion of account migrations.
Whether or not the DID identifier is used as an Actor object's `id` or not, whether or not it's even included anywhere in the Actor object (in `alsoKnownAs`, or borrowing the DID vocabulary term `controller`, or in any other property or object) is kind of moot with `did:webvh`, because this particular DID method defines a bidirectional translation between DID identifiers and URLs so including it as a URL is just as valid as using the DID notation (again, this is [webvh]-specific).

Another interesting property of many DID methods, and [webvh] in particular, is [DID URLs], which are literally URNs that have the user-controlled identifier as authority, and redirect to current outbox as a second-step after first resolving said "authority" to the Actor Object (i.e. the DID document) to get the current outbox at which the rest of the URL can be resolved.
I will step over the rabbithole of how all this works in did:[webvh] specifically, but suffice it to say, there are many other DID methods or non-DID identifier/document publication mechanisms that could work as well, with a little glue and tooling and devops.

The important point (for architectural exploration) is that the handwavey "service C" I mentioned above can be primarily client-driven, or offered as a service by servers A and B as sidecars if they both supported this particular model of identity recovery/integrity.
It is possible today, anchored in normrefs, and not even particularly complex.
There are probably much more complex solutions worth comparing, or ones with different interop and UX tradeoffs that provide all the same integrity and identity properties, and many ways of remixing and combining them.

But at least one way of doing all of the above is already possible, and simple enough to be worth considering writing one or more _profiles_ around, for implementations interested in uniformly and securely enabling these user stories together.

## Coda: Other People's Protocols, Other People's Identifiers

The fourth use-case that [Evan mentioned wanting to discuss with the CG](https://lists.w3.org/Archives/Public/public-swicg/2026Sep/0008.html) (really more of a developer user-story) was that of a developer making a multi-protocol client and/or multi-protocol server.
If such a developer wanted to:

1. allows objects from other protocols to be attached to or embedded in Activities handled by her client/server,
2. use identifiers from another protocol in `alsoKnownAs`, `url`, `source`, and/or `id` properties of Activities, Objects, attachments, and/or Actor objects themselves
3. embed Activities or Objects into messages of other protocols, and/or 
4. create "polyglot" Activities that are comprehensible to both protocols,

All of these would be easier to achieve in the "dialect" or profile of ActivityPub sketched out at a high level by the preceding document than in today's fediverse profile of ActivityPub.

Of particular interest to my personal design explorations is how an ActivityPub client could share ephemeral, private, canonicalized, and/or content-addressed Activities with _other offline or non-web-based clients_.
This could be achieved using different protocols, or extensions to ActivityPub, or even via SoLiD or other RDF-based groupware to share Activities that have not been published on the web, might never be published on the web, and might not want that pre-publication collaboration being traceable or provable from what later makes its way into an AP outbox.

This broader space for experimentation both on and beyond the ActivityPub protocol is, I think, what the Social Web Incubator Community Group should be focusing on in 2027:
multiple profiles and extensions expanding _out_ from "websites", _out_ from all the existing and novel services beyond the outbox and webview, _out_ to meet the moment as the [dead internet] moves from theory to indisputable reality. 
In a world where web services get cheaper and cheaper, while moderation and cybersecurity get more and more expensive, we need to be thinking of social computing as both urgent [community work](https://www.wrecka.ge/against-the-dark-forest/) and also an immensely **valuable** counterweight to whatever else the internet is becoming.
There will always be other networks and other protocols, but ours gets more powerful the more flexible and adaptable we make it, which means not just picking up where client-to-server failed, but thinking wholistically about end-users as needing some "authority" of their own if they are ever to have agency.

## Appendix: Non-exhaustive Taxonomy of Potentially Relevant Identifier Schemes

Note: these are the variously content-addressing-based identifier schemes I'm most familiar with, from my time working for the IPFS Foundation and Decentralized Identity Foundation.
A more exhaustive list would take more time to prepare than this whole article took to write, and while I might have missed one or two good options for ActivityPub, I stand behind these as the bulk of a list of options worth considering.

|type|URI scheme|normref|pros|cons|
|---|---|---|---|---|
|ni://|yes, IANA-registered, simple /.well-known/ system|IETF [RFC 6920]|low complexity, zero-dep implementable|limited range of hash functions|
|ipfs://|yes, but very complex and likely needs to be profiled via regexp to reduce security surface for AP use cases|no hope of normref|"kitchen-sink", can handle many different use-cases and extensions, e.g. virtual file system, toxic/DMCA content blocklist built-in, etc.|quite complicated, requires separate DHT and/or trustful HTTPS routing to dereference, an additional chatty protocol to host, content-type must be passed out of band for type safety|
|magnet://|yes, stable and versioned|stable community spec and impls but no normref|less complicated, diverse implementations|requires separate DHT protocol to dereference and/or host, content-type much be passed out of band for type safety, no built-in affordances for tracking/blocklisting toxic or DMCA payloads|
|`digestMultibase`|no|stable, W3C normref|low complexity, zero-dep implementable; works more like SRI than rest of this list, i.e. provides a stable syntax for passing hash alongside URL as part of link object|limited range of hash functions|
|[hashlink]|yes|stable, but unlikely to get normative status|very simple syntax for expressing hash in query parameter of URLs|query parameters not ideal in every use-case, can get lost in transport, etc.|
|at://|current scheme is URL-spec non-conformant|iterating (slowly) in IETF|uses individual user's DIDs as "authority" component, for now at least|requires trustful and/or complex resolution (merkel tree walking), non-normative CBOR serialization, all events fully-public and non-repudiable|
|[DID URLs] (in general)|per-method|DID URL is ratified, DID Resolution (debatably on critical path) still unstable|portable|resolution, security all depend on the specific method used|
|DID URLs ([webvh])|yes, simple /.well-known/ translation|low complexity, zero-dep implementation|some complexity around witnessing to be 100% tamper-evident against malicious servers (requires something like soatak's key transparency system)|
|[UUIDv5]|no|IETF [RFC 9562]|takes a URL as input and turns it into an opaque UUID (but can be verified if you know the original URL)|not a *content*-identifier, just a one-way commitment to the URL itself|

## References

[didwebvh-ts]: https://github.com/decentralized-identity/didwebvh-ts
[caddy]: https://github.com/caddyserver/caddy
[dead internet]: https://en.wikipedia.org/wiki/Dead_Internet_theory
[DIDs]: https://w3c.github.io/did/
[DID URLs]: https://www.w3.org/TR/did/upcoming/#did-url-syntax
[UUIDv5]: https://www.rfc-editor.org/info/rfc9562/#section-5.5
[fedify]: https://github.com/fedify-dev/fedify
[FEP-cd47]: https://fediverse.codeberg.page/fep/fep/cd47/
[FEP-73cd]: https://fediverse.codeberg.page/fep/fep/73cd/
[FEP-e3e9]: https://fediverse.codeberg.page/fep/fep/e3e9/
[hashlink]: https://tools.ietf.org/html/draft-sporny-hashlink-05
[media-upload]: https://www.w3.org/TR/2017/CR-activitypub-20170907/#uploading-media
[nih uri]: https://datatracker.ietf.org/doc/html/rfc6920#section-3
[prototyping exercise]: https://codeberg.org/bumblefudge/cipub/
[RFC 6920]: https://datatracker.ietf.org/doc/html/rfc6920
[RFC 9562]: https://www.rfc-editor.org/info/rfc9562/#section-5.5
[sri]: https://www.w3.org/TR/sri-2/
[TIDs]: https://learningproof.github.io/tid-i-d/draft-goldman-tid.html
[vcdi]: https://www.w3.org/TR/vc-data-integrity/
[webvh]: https://didwebvh.info/