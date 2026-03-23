---
title: "A Decent Identity Part 2: Praxis"
categories: 
  - blog
  - activitypub
  - atprotocol
  - governance
type: "blog"  
layout: single
author_profile: true
read_time: true
comments: true
share: true
related: true
toc: true
description: "This essay outlines a set of short- and medium-term goals for how activitypub and atproto could optimize their identity systems for user agency and good governance."
excerpt: "This essay outlines a set of short- and medium-term goals for how activitypub and atproto could optimize their identity systems for user agency and good governance."
image: /assets/images/too_long.png
defaults:
  # _posts
  - scope:
      path: ""
    values:
---

## Context Window

In the [previous, more philosophical essay](../a-decent-identity-part-1-theory/), I laid out a definition of success for decent social computing, then I worked backwards to define how an "identity system" for that definition of success would work:

> What properties would an optimal “identity system” have to enable decentralized social computing ecosystems to flourish using it as infrastructure, i.e., what capabilities most maximize user agency and ecosystem resilience?

After showing all my notes on what I meant by all those squishy terms and goals, I operationalized those properties and capabilities into a "rubric" for assessing how the identity layer undergirding a given social ecosystem can be assessed against the long-term goals.
In this piece, I will just try applying that rubric tactically to the short- and medium-term realities of two specific protocol communities: Atproto and ActivityPub.

### The Rubric

1. **Portability at multiple layers**, not just users credibly exiting apps or swapping out infrastructural dependencies within one otherwise-invariant platform:
    * A. *Apps and services* can also join or leave zero or more *platforms* (i.e., "userbases", moderation perimeters, literal or figurative jurisdictions) at any time and still use interoperable identifiers for their users
    * B. Apps can add or subtract *integrations and infrastructure* over time, without trapping users or impeding their own exitability.
    * C. Platforms can federate or defederate from one another at any time, fork or schism themselves, and enter or exit multiple protocols at any time
    * Jump to [Atproto](#portability-atprotocol) or [Activitypub](#portability-activitypub) diagnosis
2. **Transparent platform governance** (at least of the identity layer)
    * A. This includes *spam-protection* and *moderation*, but these two mechanisms have to be distinct (if not firewalled) to be credible
    * B. *Platforms and sub-platform networks* need distinct governance, even if the stakes are lower.
    * Jump to [Atproto](#protocol-governance-atprotocol) or [Activitypub](#protocol-governance-activitypub) diagnosis
3. **Transparent protocol governance**, ideally in public
    * A. SDOs are good but not the silver bullet people expect, in my extensive first-hand professional experience. Community venues can make up for less transparency with more accessibility and participation and less expensive divisions of labor.
    * Jump to [Atproto](#protocol-governance-atprotocol) or [Activitypub](#protocol-governance-activitypub) diagnosis
4. **Open-source and openly-governed APIs** break the architecture into layers that can be run by anyone, and ideally support competition at each layer.
    * A. Competition keeps margins low; ideally, no part of the architecture can get so expensive to run that it becomes a chokepoint/tollroad to the rest of the system
    * B. DIDs and PDSs in particular need to stay in the "commodity pricing" zone, which is one of the hardest things to ensure over time (see Bitcoin-based, or any mainnet-based DID methods priced out by their own upstream blockspace economics).
    * Jump to [Atproto](#scaling-mechanics-atprotocol) or [Activitypub](#scaling-mechanics-activitypub) diagnosis

## Diagnosis: ATProtocol

Fundamentally, the `atprotocol` as conceived, described, and to some degree already lived by its vibrant (if at times self-convinced) community of builders is indisputably a beautiful open developer protocol.
My experience with developer platforms in particular makes me a little to cynical to say we're there yet, or that such an outcome is destined or guaranteed, but it's certainly feasible that a "multiplatform" (in the international relations sense, of polycentric/multipolar equilibria) could form with the right tailwinds and investments.
I don't even think it would take too much luck, money, and regulatory tailwinds to evolve that open protocol out of what is today fundamentally an **open application platform** with credible intentions to open itself and hand off power incremental to external governance and institute various accountability mechanisms.
That is not status quo, however: viewed through the lens above, it is still shaped like a platform, running a fairly traditional trust & safety playbook over an identity system literally centralized in a single source-of-truth registry of all actors.

In its current cocoon-like structure, it is somewhat amorphous qua platform: it does not seem clear (to me or to anyone else) where it will extract its primary rents to repay its investors.
It could end up profitably functioning as any of the kinds of platforms hypothesized in [the previous piece](../a-decent-identity-part-1-theory/#quagmire-6-i-know-a-platform-when-i-see-it)!
The identity system, hard-coded and bound to a single registry (under TBD governance) in Switzerland, is a good metaphor for the current state:
**Groundwork** has been laid for more public governance that could go in a multi-platform and/or multistakeholder **direction**, but nothing very concrete has been committed to.
It crucially remains to be seen how antagonistic, how opinionated, or _how independent_ a significant ATP platform could be and still be invited to the table to govern the DID method/registry system.

The reason for this tension is that the protocol as specified can only allow one network (i.e., one *eventually-consistent event stream*) and one source-of-truth (i.e., one *universe of DIDs* contained in a unitary plc.directory).
The unitary `plc.directory` is a kind of brute-force consensus mechanism, more similar to ICANN than anyone seems to want to admit.
A persistent blurring of the line between DNS (all syntactically valid DIDs and DAG-CBOR data) and ICANN (the subset of that domain-universe rented and registered through ICANN-governed gTLDs) has created a paradigm where the needs of the bluesky platform have been made coextensive with the needs and architecture of the protocol that hopes to outlive the platform.
No "hard-fork" (to borrow a sociological term from the blockchain community) and no divergent usage of the code and data formats and historical DAG-state for a different universe of DIDs is specified;
trying any hijinx in that direction would almost certainly break compatibility and pollute the atmosphere with broken threads and confused deputies.
Even discussion of "alternate DID universes" seems to have no home in the community venue or the IETF mailing list!

At its lowest level, today's ATP identity system is pretty traditional and run like those of any centralized platform, even if the data model and the semantics of the DID method _imply_ it could be decentralized at a later time.
On top of this identity layer, all the other infrastructure is admirably thin-sliced into microservices, which allows self-hosters to mix-and-match how much of it they want or need to run to support off-protocol features or their particular definition of data sovereignty and independence.

### Portability: Atprotocol

*(Refresh your memory of section 1 in the [rubric](#the-rubric))*

User portability between PDSs (that are both known to plc.directory) is going great! Many other kinds of portability is still unspecified behavior, though: portability of off-protocol data or permissioned on-protocol data, some corner-cases around verifying signatures on keys rotated away, CDN/blob mechanics are a little glitchy across PDS migrations, how to handle historical DID docs and historical verification is a little underhardened, etc.

How *apps* secede from plc.directory and join some other universe of DIDs is undefined. How to migrate or tombstone or re-sign data across directory boundaries is also undefined.

The lexicon system is pretty good for this, modulo the interop issues created by unregistered lexicon use or lexicon usage that diverges from the published version (both failures which can be gracefully handled by defensively-designed apps).

This part ATP does pretty well; it's easy to "switch off" ATP since users "publish" to ATP "mainnet" by *leaving content in an outbox on a public endpoint*, which can just be shut off (without, for example, any other usage of that server's DIDs being interrupted-- DIDs keep DIDing if relays stop syncing them). No real blockers to entering or exiting communication via other protocols and networks seem to exist.

### Identity Governance: Atprotocol

*(Refresh your memory of section 2 in the [rubric](#the-rubric))*

The "Swiss entity" might help, or be mere kabuki/kayfabe; it all comes down to who has decision-power there, and what scope/powers they have over the system.

Spam-filtering is, as one might predict in a permissionless and unauthenticated PDS<>relay system, a major issue, with thousands of PDSs seemingly being stood up just to grief the plc.directory[^6] or waste its resources[^7]. Even in its current placeholder form, the spam filtering (excluding misbehaving PDSs from DID directory/ies) happens at a lower [content-agnostic] level than [lexicon-specific and semantic, i.e. platform-specific] moderation, but this has the side-effect of fusing together into one platform the spam-filtered universe of known PDSs (minus a PDS blocklist) and the universe of DIDs moderated to bsky.app's standards.
    
Platforms and networks are currently unnamed, invisible units of measure in ATProtocol; Rudy Fraser's insistence on referring to "our community" instead of using a technical boundary or abstraction (i.e. "our system, our network", etc) helpfully foregrounds this and forces this issue.

The main issue I see is that the "composable" moderation system as currently implemented confuses and obscures this issue and minimizes the need for moderation-boundaries to map to governance/branding/community boundaries. BlackSky's, EuroSky's, and NorthSky's attempts to build equal-but-independent (rather than merely additive) moderation loom on the horizon as negotiations without a clear venue or language.

BlackSky is pioneering/prototyping not just additive moderation but also overt _overriding_ of baseline moderation actions from the bluesky platform being pushed (unidirectionally) into their own. This could force some explicit rule-setting on what it means to ignore, e.g., a Bluesky-wide "ban" label, but there is a chicken-and-egg problem there, given that this hypothetical rule-setting currently has no natural home or venue (or authority).

### Protocol Governance: Atprotocol

*(Refresh your memory of section 3 in the [rubric](#the-rubric))*

Atproto's strategy for standardization at IETF is commendable in its scope and structure, in that it starts from the core data-publication protocol (the sync protocol used to build PDS contents into an event stream/"firehose" and from there a global archive/DAG), with the potential to standardize higher and lower layers over time. Handing over change control of an already-built, in-production system to IETF inherently risks breakage. This risk is usually managed at the working-group scope level, thus the protracted and ongoing scoping process debating "invariants" (assumptions about end-users and lower layers that a working group needs to just take as given, e.g., the stability, enumerability, and resolvability of identities and/or identifiers). The exact scope (and which "invariants" can be protected from redesign-by-committee) is still being negotiated at time of press, so it's necessarily a little TBD how the governance at IETF of the data protocol interacts with the lower-level identity primitives governed... somewhere else?

I would note here that my repeated calls on the mailing list for the invariants and identity assumptions to be made more explicit are, if anything, informed by my years of trying to debate data-sync and application-layer semantics in ActivityPub _without_ enough consensus on identity-layer assumptions. See the [corresponding section](#protocol-governance-activitypub) for context.

As mentioned above, the "moderation-layer" and platform dynamics at the identity layer are currently underspecified, almost unnamed and unrecognized, although I personally argue it would be a category error to try to govern any of these in any SDO (particularly at IETF!), and I would push back on any attempt to push those into scope at IETF. First steps would be to name the problems and get some kind of consensus in the developer community on what the governable questions even are; this will be a long process, and putting the cart before the jackass would be disastrous.

### Scaling Mechanics: Atprotocol

*(Refresh your memory of section 4 in the [rubric](#the-rubric))*

I added this category to the rubric of success less because there is any actionable thinking to be done today on any protocol, and more because I want to look smart years from now when this is the next Boss in the never-ending platform game that is protocol governance.
Atproto got off the ground with relatively good unit economics and economies of scale, constrained a little by the assumption that it would be years until >5% of PDSs would be paid for by anyone other the protocol's current loss-leading underwriter. Sadly, this 5% threshold still looking years off, but the basic cost structure still puts the vast majority of growing pains in moderation, the large-scale appview, and directory-wide cache/relaying infrastructure. This last one, though exponentially more expensive to operate on commodity cloud infrastructure as the network grows, is at least the easiest to share/fractionalize and govern anti-extractively (by, e.g., running it as a platform coöperative).

One minor qualm I will mention here is that per-user, user-managed rotation keys (whether [device-bound](https://bsky.app/profile/why.bsky.team/post/3mfhon6ss4k2g) or "paper keys" à la ethereum community) were defined in the initial protocol documents but left out of the initial reference implementation, and to date have only been added to un-maintained, [non-reference implementations](https://bsky.app/profile/angrydutchman.peedee.es/post/3lz5dp4vnbk27) of the PDS and identity tooling. Retrofitting these kinds of capabilities post-facto can be quite costly and disruptive, and may need to wait for a protocol upgrade/"major version."

I do wonder how permissioned and/or private data (or more complex key-sharing/-derivation mechanics) will become a cost center, although honestly I don't mind if PDSs have to charge (and compete on pricing and/or features) to allow a realistic number of private/permissioned-data apps to be used by each user.

## Diagnosis: ActivityPub

Where to begin assessing the Publication of Activities protocol in terms of its protocol-wide identity layer?
Honestly, it _effectively does not have one_, despite the best efforts of the protocol's authors to insinuate and assume every behavior and capability that they could not specify.
For better or for worse, [no consensus on identity was achieved](https://github.com/w3c/activitypub/issues/260#issuecomment-333551720) by the original working group that designed the protocol, and only somewhat cryptic assumptions about that [hopefully someday DID-based](https://gitlab.com/dustyweb/talks/-/blob/master/federation/rwot/even_more_distributed_activitypub.pdf) identity system were baked confusingly into the version of the specification that shipped[^10].
ActivityPub's identity model is actually very DID-like, and not by accident: the fundamental unit of identity for actors and services is a URI string (of which DIDs are just a fancy subset), which dereferences to a JSON-LD document containing some mandatory fields but which may also contain arbitrary additional fields and `@Context`s: i.e., a DID document.

But to speak of ActivityPub's identity layer in 2026 can be a little confusing without also addressing the identity platform Mastodon has extended by sheer market force onto all the non-Mastodon software of the fediverse.
This is vexing because Mastodon's identity platform is at best orthogonal to ActivityPub's model for identity, if not completely at cross-purposes with it, given that the latter specification assumes multiple platforms will arise and that authentication, authorization, and signing/verification mechanics will be profiled per platform.
Without limiting interoperability to such a profile, the client-side identity and signing powers assumed by the text of the client-to-server sub-protocol would hardly make much sense!
Insofar as a protocol can only be judged by [how it actually gets used](https://bsky.app/profile/blaine.bsky.social/post/3mf6bx7ymrc2q), the ActivityPub doesn't properly _have_ a client-to-server sub-protocol (although there is a [group at W3C](https://github.com/swicg/activitypub-api/) prototyping such a candidate sub-protocol and authorization profile in tandem), so I have to be careful not to overstate the completeness or even feasibility of an interoperable ActivityPub identity as distinct from Mastodon-API identity at time of press.

### Sidebar: the WebFinger issue

Even a casual reading of the AP spec will leave the Mastodon or user of Mastodon-compatible software (wordpress, ghost, peertube, pixelfed, nodeBB, etc) baffled;
"You mean that `@username@server.com` stuff isn't part of ActivityPub?!", I have many times been asked.
No, not at all, that email-like handle system was invented (ironically enough) by some [officious-sounding technologists](https://beyondtellerrand.com/events/dusseldorf-2013/speakers/blaine-cook) for... OpenID Connect, actually, and only adopted by Mastodon (well before ActivityPub was even a chartered work item) because it seemed state-of-the-art at the time, in the early days of federation before "Single Sign On" became synonymous with [Cambridge Analytica](https://www.amnesty.org/en/latest/news/2019/07/the-great-hack-facebook-cambridge-analytica/).
**WebFinger** documents are just **Mastodon identities** that Mastodon will attempt to discover via the apex domain found in your Actor's `id` field, and which it will [silently drop an actor](https://bsky.app/profile/pfrazee.com/post/3mgsy6uvzf22n) for not providing.
In Mastodon's implementation, an "off-protocol" handle (`@user@server.example`) has to be in the `alsoKnownAs` field of an Actor (i.e. DID) Document, AND the secondary document matching that handle has to be posted on an off-protocol live server endpoint, or else the otherwise-conformant ActivityPub actor is dropped.
This convention of handles (expressed in `alsoKnownAs`, just like ATP's handles) is mentioned nowhere in the ActivityPub specification and is, strictly speaking, an optional extension to it (or perhaps constitutes part of an "Authorization profile" of sorts, if you want to be generous, since dropped users cannot access "Authorized Fetch" or other semi-private data and side-effects).

> This effectively forces a whole side-protocol onto any ActivityPub server who wants its users to be visible to Mastodon users!

Luckily, adding this side-protocol to an ActivityPub implementation doesn't entail a huge lift compared to, say, HTTP Signatures, so it could  feasibly be deprecated, and in the process, the priority and "pecking order" of the two identity systems could be inverted gracefully:

1. Mastodon-style handles could be refactored as *one clearly-defined optional* `alsoKnownAs` handle type among many
2. expectations about how [optional handles get discovered](https://hedgedoc.socialweb.coop/s/LwyM-4-w5#), parsed and displayed could be harmonized, and
3. bonus feature, other easily-verifiable handle types like... idunno, [`_atproto` entries in DNS records](https://bsky.social/about/blog/4-28-2023-domain-handle-tutorial) could also be layered on using the same logic, to make things like bridgeyfed smoother and more [sovereignly integrated](https://fed.brid.gy/docs#mastodon-link-verification).

The WebFinger issue isn't a huge burden or an unfixable technological impasse, but it DOES serve as a crisp metaphor for how invisible identity systems are... and how powerful platforms can be.

### Platform Politics

Of course, if the whole ATProto thread through this article hinges on the often invisible ways in which platform economics contradict protocol rhetoric, _no one can accuse Mastodon of obfuscating its platform nature_.

If anything, Mastodon has always been quite open about its platform-like nature, carefully distinguishing between the "Mastodon-API fediverse" and the "broader ActivityPub community," not just [technologically](https://codeberg.org/fediverse-pl/maep/issues/1) but also in its communications, public appearances, and fundraising.
Mastodon has always had a distinct platform identity from the tribalism inherit in its earliest culture as a haven for Twitter-refuseniks to the structure of its codebase[^8]. 
One might argue that adopting post-facto ActivityPub's server-to-server federation model (i.e. message-routing "sync" protocol), its JSON-LD serialization, and its semantics didn't change that much of the nature of the platform and its priorities;
the non-Mastodon universe of ActivityPub applications did not grow as quickly, or entice Mastodon to have better support for, e.g., unknown Activities, JSON-LD extensions, etc.
Unlike BlueSky PBC, importantly, Mastodon GmbH have for years at a time publicly apologized for not having enough resources (particularly payroll) to adequate triage its insanely active github tracker, much less resources to make a substantial and multi-year commitment to interoperability and shared API design or portability mechanisms with the non-Mastodon ActivityPub community.
The GmbH can hardly be blamed for underprioritizing interoperability with moving targets in smaller communities, since there are zero platforms of comparable size (whether measured by servers or by monthly active users) on the Fediverse:
Pixelfed, PeerTube, Misskey, Friendica and Pleroma are probably the closest, although none of these has a comparably large *developer* community, comparable institutional userbase, or even much of a trunk/branch from which to coordinate better interoperability.

### Sidebar: Why doesn't ActivityPub have a DID method?

If ActivityPub Actor documents are basically already DID documents, why hasn't anyone proposed a *did:mastodon*, or a *did:ap*?
Well, a few people have proposed a method, most notably `@silverpill`, steward of the Fediverse Enhancement Proposal process and technical lead for the [mithra](https://codeberg.org/silverpill/mitra#readme) implementation, which also uses W3C Verifiable-Credential/Data-Integrity primitives for [per-Activity signing](https://codeberg.org/fediverse/fep/src/branch/main/fep/ae97/fep-ae97.md) and [client-side rather than PDS-side/server-side signing](https://codeberg.org/fediverse/fep/src/branch/main/fep/c390/fep-c390.md)).
The collective-action problem is severe, however, and even if there were ideological, economic, and architectural alignment among all major AP implementations, it would still be a nightmarish process to lay tracks (or in this case, Authorization profiles, Authentication guidelines, and user stories) in front of a moving train!

Any DID-based implementation that used [DID URLs](https://github.com/w3c/did-resolution/pull/260) or at:// URLs or some novel ap:// URLs or something blockchain-based like eth:// would immediately break interoperability with all of today's effectively [HTTPS-only](https://github.com/w3c/activitypub/issues/429#issuecomment-1994661937) Fediverse, partitioning the network severely.
Any change as breaking would have to be coordinated with others into some kind of ActivityPub "major version bump" with some serious motivation to upgrade, even assuming a chaotic upgrade full of broken threads and disjoint interactions could be avoided!
DID methods would have to be HTTP-based to be smoothly backwards-compatible with non-implementing AP software, i.e., a DID document would have to be dereferenceable from a stable long-lived URL, ideally one that can be derived from the DID programmatically. 
This would limit the set to known DID methods usable in this way to:

* [`did:web`](https://w3c-ccg.github.io/did-method-web/) (not very secure or even securable at scale)
* [`did:webvh`](https://identity.foundation/didwebvh/) which is basically did:plc but with deduplication/honesty policed by witnesses and caching done by relays/shared-directories explicitly put out of scope (PDSs must publish entire did histories, even for post-migration dids, at deterministic /well-known/ paths)
* [`did:webplus`](https://didwebplus.com/), a very similar design to webvh that has more of a witness- and directory-mini-protocol baked in (allowing DID updates to be pushed and/or pulled by relays and consumers)

Reasoning practically through the "upgrade path," the only way to motivate implementations to upgrade into some form of DID usage (regardless of which DID methods could and should be part of that usage) would be a backwards-compatible, probably "backend-only" usage of DIDs that do not affect federation and syndication of content at all.
I have [previously argued](https://lists.w3.org/Archives/Public/public-swicg/2023Jul/0057.html) for a brownfield approach where supporting one or more from a list of the DID methods that enable a given desired feature (like [account portability](https://codeberg.org/fediverse/fep/src/branch/main/fep/73cd/fep-73cd.md) across backends and data platforms, for example), without forcing all implementations to implement the same DID methods.
My colleague in the [socialweb.coop](https://socialweb.coop), [bengo](https://bengo.is/), has [argued even more explictly](https://lists.w3.org/Archives/Public/public-swicg/2025Sep/0071.html) that the ActivityPub identity system already supports many DID methods, and implementations should compete on features by supporting different ones.

> The best future for ActivityPub probably involves a lot of DIDs, including `did:plc` and `did:nostr`, I sincerely believe.
> "Sign in with Atproto" or "Sign in with Nostr" isn't just a positive-sum way of turning users of those protocols into users of ActivityPub servers, they're also just a way to detach apps from backend choices, and literally *learn from* the developers and users of other communities.

### Sidebar: What are the PDS-equivalent and the DASL-equivalent of ActivityPub?

Part of how ATProtocol has been so quick to onboard users and empower them to quickly build apps is that a high-level application developer has a long list of low-level functionalities and dependencies that they *barely have to think about*, and I don't just mean on the DID/identity layer:
the PDS "just works", signing each piece of content and handling publication/syndication to the network, encoding things very compactly in an [admittedly arcane and confusing dialect of CBOR](https://dasl.ing/drisl.html) which most application developers don't really need to know much about.
The equivalent wire serialization in ActivityPub, JSON-LD, is sadly almost every ActivityPub implementer's problem, and for many of them, the single most painful and frustrating aspect of the protocol[^9].
Per-Activity signing client-side is mentioned in the client-to-server section of the original specification, but this was until [quite recently](https://github.com/swicg/activitypub-api?tab=readme-ov-file#goals) done by only one known implementation (not counting Mastodon, which briefly adopted a form of it but ended up rolling back the feature).
After all, attaching a signature to each Activity seems like a lot of work to do if no other implementations are checking them or handling them any differently for being signed!
Note that interest in client-side signing is picking up now exactly to enable a PDS-like "oblivious server," which can host client-signed activities from services and applications not hosted on that server.
This kind of "BYO account (and oblivious storage)" user-story is increasingly being demanded by the community after years of opening a new account on each new service to take advantage of its particular features, cross-linking profiles, and other miscellaneous long-suffered frictions.

Of course, this is a simplification of the role of the PDS in Atproto, and it serves other functions as well.
For example, PDSs canonicalize and authenticate all their content before it gets published over the protocol;
the equivalent AP Server-to-Server authenticity mechanism, [HTTP Signatures](https://swicg.github.io/activitypub-http-signature/), was written into the original specification as a draft-RFC soft-requirement, which was soon thereafter deprecated and only a few years ago reached v1.0.
The joys of open standards!
Managing multiple (non-compatible) versions of this protocol was a major headache, and hopefully now that Mastodon has started its upgrade cycle and a few other major implementations have as well, v1.0 of HTTP Signatures can be used to authenticate server-to-server interactions for all implementations going forward with relatively less pain.

By canonicalizing not just protocol messages, but also basic account information, handle history, etc, the ATProtocol PDS makes portability between (non-blocklisted) PDSs relatively turnkey.
On the ActivityPub side, although the publishing canonicalization could be reused at rest... very few implementations do anything like that, tending to store all non-protocol information in proprietary formats at rest (and doing all authoring in proprietary forms as well).
With a grant from Germany's [Sovereign Tech Agency](https://sovereign.tech) (STA), the [socialweb.coop](https://socialweb.coop) designed and published as a series of [Fediverse Enhancement Proposals](https://codeberg.org/fediverse/fep/src/branch/main/fep/7952/fep-7952.md) to offer the ActivityPub equivalent of a ".CAR backup" (except, you know, a tarball of JSON-LD in folders for different purposes).
To date, there has been little interest in or implementation of these proposals, for any number of reasons, but mostly because painkillers are more urgent than vitamins.
It is, after all, a whole lot of work to retrofit onto existing systems.

> Atproto app developers don't know how good they have it! (except the ones that have also built an AP implementation from scratch)

### Portability: ActivityPub

*(Refresh your memory of section 1 in the [rubric](#the-rubric))*

Currently, none of this is looking great, and I'm not even sure what a realistic path to progress would look like.
The STA-sponsored work mentioned above on portability was meant to be a starting point for further dialogue and counterproposals, but even the very real competition from Atproto's portability mechanisms and guarantees wasn't enough to motivate painful cross-implementation co-design and refactoring work.
*It's really a vitamin and every AP implementation has plenty of urgent reasons to take painkillers or add userbase-boosting features!*

Incentivizing development towards portability goals, it would probably help to **decompose** them into manageable *building-blocks*:
e.g., one coalition of the willing needs to keep advancing and iterating on client-to-server, while another thinks about account recovery and portability, while another works on signing and integrity issues, before the three can be combined into a Voltron reasonably equivalent to ActivityPub's DID registry/PDS system.

In parallel, I find it kind of inevitable that someone will make an ActivityPub server that gives each user a "slot" in a forked PDS with, say, did:plc AND one other DID method support, to do "native" (on-PDS) ATProto things in addition to "native" AP things.
(And, who knows, maybe other DID-native things would fall out as a bonus!)
This will drive some healthy competition and "feature parity" with a dual-protocol server/client can be a very useful thing to have hovering over the community.

As longtime (and eternally-patient) ActivityPub sociologist and community-builder Arnold Schrijver put it, the "post-facto interoperability" paradigm (build first, translate/port later) is what has turned the ActivityPub community into a standoffish cluster of technocratic fiefdoms, and is a dead-end.
Schrijver recommends, for overcoming this, ["shared ownership"](https://coding.social/blog/shared-ownership/) of both code and protocol, and I think he's right.
Platforms are not inherently extractive or mercenary, of course-- [platform cooperatives](https://uwcc.wisc.edu/resources/platform-cooperatives/) exist, literally to overcome these kinds of collective-action problems.
In this, the next steps I propose for ActivityPub and for ATProtocol aren't even all that different, directionally?

### Identity Governance: ActivityPub

*(Refresh your memory of section 2 in the [rubric](#the-rubric))*

Sadly, this category is also not going well, despite the tireless efforts of many (but mostly [Emelia Smith](https://bsky.app/profile/thisismissem.social) and [Darius Kazemi](https://friend.camp/@darius)) to make the Trust and Safety Task Force of the Social Web Community Group a central repository for this collective feature backlog, compliance planning, and technical debts.
The work [Roost.tools](https://roost.tools) is doing to open-source reusable dashboards and plumbing for event-sourced (and variously-automatable) moderation pipelines is very promising, and probably needs to be adapted to the Mastodon codebase first before MAEPs can be written to figure out how to adapt it to other (adjacent/interoperable) ones.
More generally, though, the conversation about spam-protection and uniform/traceable/shared moderation records has to advance a lot, as the current paradigm in so much of the Fediverse seems to be a kind of emphatic yeoman insistence on manual processes and total liability for each server.
What's more, the all-or-nothing approach embodied by the [FediBlock](https://fediblock.neocities.org/) server naughty list is a temporary solution that has grown permanent, and does not scale or serve end-users well enough.

Ironically, there is another major force in the Fediverse standardizing on moderation, and that is Threads, which federates to large Mastodon API servers one by one, after assessing its moderation policies and history closely, to keep the Threads experience consistent across this additional foreign content flowing through its pipes and mixing into its users feeds.
It is tempting to see this moderation requirement buttressing as [a platform play unto itself](https://www.fromjason.xyz/p/notebook/copy-acquire-kill-how-meta-could-pull-off-the-most-extraordinary-pivot-in-tech-history/), selling to larger servers a turnkey, all-in-one, "pay per active user" solution to moderation, toxic content, and spam.
I suspect, however, that this would be less of a profit driver than a loss leader for Meta, for whom it would be orders of magnitude cheaper to just moderate internally ALL external content at scale than to bother certifying and trusting external moderators.
If anything, spending more money inefficiently trusting external moderation could cynically be judged as a relatively cheap way of buying an *anti-trust fig leaf*, with public displays of "decentralization" and "user choice" as a bonus!

Less nefariously, the Mastodon API Fediverse has been moving towards a kind of platform cooperative for general-purpose services in the [FASP](https://github.com/mastodon/fediverse_auxiliary_service_provider_specifications) system, although this is again not particularly integrated with the ActivityPub protocol and more like a platformization of the Mastodon API beyond the Mastodon codebase.
Information on the system is still a little scarce years after the NLNet grant that produced the specification above, but judging from [a presentation by one happy participant](https://fosdem.org/2026/schedule/event/M7DYRH-a-wild-fasp-appears/) in the invite-only beta release, it is going well and should be more widely enabled soon.
It would appear to have spam and moderation plug-ins, although it remains to be seen how this could converge with, say, Roost's model, or that of [IFTAS](https://iftas.org) or with non-Mastodon-API implementations.

### Protocol Governance: ActivityPub

*(Refresh your memory of section 3 in the [rubric](#the-rubric))*

The ActivityPub community has always had a fairly disjoint conversation about standardization and "protocol design", with a surprising number of implementations just categorically disinterested, hostile, or only interested in participating if they have a reasonable chance of dislodging JSON-LD from the protocol.
(I wish that last bit were a joke.)
This rocky history is why I lobbied over much of 2024 and 2025 for a kind of tiered system, where:

1. Anyone who implemented anything using or depending on ActivityPub can ship a mini-spec or even use-case documentation through the [Fediverse Enhancement Proposal](https://codeberg.org/fediverse/fep) process, a self-service community similar in shape to the [lexicon.community](https://github.com/lexicon-community) on github and/or the [atproto community Discourse](discourse.atprotocol.community).
2. Contributors to significant implementations (in production, with real users) with motivation to do so can harmonize, write officious-sounding reports and best-practice documentation, and define extensions or profiles that are more W3C-shaped and can be handed off as "input documents" (i.e. rough drafts) to normative work later on at W3C.
3. Normative changes are currently out of bounds for the Maintenance Working Group at W3C, but this can be rechartered later to include things that have demonstrated significant community support and implementer interest... via the non-normative work described above.

It is hardly the perfect system, but I have tried operating across all three "layers" of this system to direct effort away from written specifications as a means of _achieving_ implementer harmonization, and towards written specification as an _output_ of implementer harmonization.
(There is a rule of thumb in standards: *if there's disagreement at the point of writing down how you interoperate, you shouldn't be writing anything down yet.*)
As I mentioned above, "shared ownership" of APIs and interoperability surfaces make all the difference in reversing a tradition of muddled and standoffish "post-facto interoperability".
What inspires me most in today's ActivityPub community is the sense of shared experimentation and collaboration in the client-to-server space, largely driven by veterans hoping to avoid the fate of previous attempts to "interoperate in post".

One thing I have to point out, though, is that there is quite little coordination happening at the level of identity layers or identity building-blocks.
The closest we have is probably the conversation about OAuth, which is a building-block of a certain kind of platform-friendly identity which fits one profile of interoperability and cloud economics.
Conversations about capability certificates, serverless/local-first authorization, non-HTTPS systems, etc. are nowhere to be seen, and this makes me insistent that harmonizing around, say, one way of using OAuth that covers 90% of current usecases well enough to be specified should be defined as _one_ Authorization Profile, not _the_ Authorization Profile, even if it is the only 2026 profile.

### Scaling Mechanics: ActivityPub

*(Refresh your memory of section 1 in the [rubric](#the-rubric))*

This point here is almost entirely theoretical at present, because as I outlined above, there is no identity layer (commodity-priced or otherwise) in today's Fediverse.
I do think, however, that trying to support new use-cases (like cross-implementation end-to-end encryption, or oblivous-server C2S) will drive interest in something like a DID method (or some profile of multiple DID methods) and something like a PDS (or a shared API across more than one).

Today's major ActivityPub implementations and infrastructure aren't particularly cost-optimized to function as distributed systems or to operate complex NoDB-style queries over federated data... but they certainly could be.
That's kinda what JSON-LD is for, really: it's a profile of JSON made for distributed data and graph queries.

Similarly, ActivityPub as a push-based messaging protocol isn't particularly optimized for lightning-fast global publication;
it's more like email and more useful for granular authorization and collaboration than "global social".
Yet for reasons I've never understood, most of today's Fediverse uses ActivityPub to power usecases (or at least data models and UX paradigms) cribbed from the centralized global platforms, stored as plain-text on a server whose admins can see everything.
What results is a fig-leaf, polite-software model of privacy-by-obscurity or privacy-by-distributed-authentication that doesn't really hold up against motivated attackers or greedy search indexes.
To combine ActivityPub semantics and distribution mechanisms with end-to-end encryption or group-data (say, [using the new MLS standard for ratcheting group encryption](https://swicg.github.io/activitypub-e2ee/mls)) would live up to the architecture and the ambitions of the original protocol much better.
At that point, comparing ActivityPub's complexity and operating costs to something like Matrix or WeChat would make more sense than comparing it to today's BlueSky.

In this expanded scope of a future ActivityPub actually shooting for the stars and supporting use-cases for which it is uniquely suited, I think the cost-per-user of all this wacky JSON-LD and the complex federation protocols and heterogenous extensions *might actually make sense*?
It's possible, at least, if the parts that take do the heavy distributed lifting can be built as separately-maintained microservices and libraries that can be ergonomically consumed by more conventional apps. 

## Prognosis: ATProto

Coming back to ATProto, I want to emphasize the sheer size of the 9-digit elephant in this room:
we don't know how they're repaying their investors yet, and whichever kind of platform they decide to optimize for in a profitable way, it will open some doors to decentralization and sovereignty while closing others.
That sounds harsh but it isn't the fault of any individuals or collectives involved, it's just a harsh fact of late-stage capitalism.
Whether we want to be zen or anxious about that, the non-billionaires among us aren't in any position to do much besides monitor the situation and lobby for the opening of the doors that matter most to us, while we plan for others closing.

So, one possible future comes into focus if you squint and think of **atproto as a data platform** (a data platform I myself [gatekeep](https://dasl.ing/) to some small degree, full disclosure!).
In such a future, Bluesky the public benefit corporation is uniquely positioned to own the bespoke data plumbing and sui generis large-data/distributed-data systems that are expensive and finicky to run at scale;
they would maintain and best understand the tooling, the SDKs, the expertise, and  be/know the high end of the labor market for that data platform.
They would be uniquely positioned to sell/rent/manage/consult about running queries over all the history of the platform, or the universe of known PDSs, not that any of this sounds like a great business model in 2026.
Indulging my paranoid-hyperbole steelman of this nefarious data platform, then imagine the fully-decentralized, open, community-governed version of it (you probably can't unless you're one of the few thousand humans who work in big data ecosystems):
you have to imagine a bluesky-independent and community-participated governance mechanism for this low-level data infrastructure, to be able to in turn imagine BlueSky's open-core data business being succeptible to challengers and forks.
I pick this example first because it's the silliest:
for all the mean things I've said about American Venture Capital, I don't think you could raise as much as the PBC has to build... a weird hadoop/datadog/splunk competitor in 2026 based on a kooky CBOR dialect invented for canonicalizing IPLD DAGs.

But maybe starting with the low-stakes example makes clear what I'm driving at with platform governance and protocol governance being inherently at cross-purposes.
There are many adjacent possibilities:
for example, in a future where monthly active users hit, say, half a billion, BSPBC would be uniquely positioned to dominated the market for it if atproto-wide _search_.
(And 'search' isn't much more concrete than 'platform,' so for a vast enough universe of DIDs you could imagine many different kinds of search being profitable to corner: user-facing, B2B, branded or whitelabel, indexed archives sold off in curated subsets for LLM training data, etc).
Other than the aforementioned custom bare-metal aesthetic, there is perhaps not much of a moat in search, given the serialization and the design of the protocol, but who knows what will or won't be a moat as the LLM arms race distorts and terraforms so many of the economies upstream of things like clouds and platforms.

An even less far-fetched version of the platforms-versus-ecosystems argument emerges if you consider BlueSky as a **developer platform**, not unlike golden age open-API Twitter, or [app.net](https://www.fromjason.xyz/p/notebook/copy-acquire-kill-how-meta-could-pull-off-the-most-extraordinary-pivot-in-tech-history/), the developer-platform that drove Meta's astronomical growth and valuation as the world's most successful ever developer-platform play.
Bluesky's valuations and fundraising success so far could entirely be justified by a "devex play"-- if you don't believe me, do a little digging into the valuations and A-rounds of the companies sponsoring and speaking at [Local First Conf](https://www.localfirstconf.com/), an esoteric gathering of next-gen databases, Javascript frameworks, and other SDK-based devex plays that are all fully open-sourced and open-core.
Each of these companies is another bet, fundamentally, on how people will _want_ to design applications _tomorrow_, without "backends" and without vulnerability to clouds and other data platforms siphoning off their power and profits from below them in the stack.

Evaluated as a developer platform, today's "atproto" is honestly 10/10, no notes, truly bar-raising stuff:
it's very [well-documented](https://bsky.app/profile/alex.bsky.team), accessible, and abstracted into great open-source SDKs and building blocks and fork-friendly reference implementations.
The speed with which a team, a highly-skilled lone wolf, or even a clauded-up semi-technical can hit the ground running is staggering, a true triumph of developer relations (the dominant business strategy in web3/`dweb`, it needs to be stated somewhere).
This is often taken as an unalloyed good, because the ease of onboarding users and apps to today's open _platform_ **is** (or could be seen as) onboarding users and apps to the future ecosystem _outside_ the platform ("indiesky").
This cooperation just falls out of the box automatically from BSPBC investing in their own developer platform and referring to "the protocol as the product" so it's easy to assume this will continue on into the future.
It would be more strategic, however, to assume the opposite, that the easy present alignment of incentices will atrophy as indiesky finds its footing and investors start placing bets on... new platforms, perhaps even direct competitors, using the same protocol differently.

I would rather not get too deep into the ways in which BlueSky is likely to become a **payments platform**, because this paragraph is the most likely to see me testifying in court some day, but I have to address it.
For most of the community and current userbase of BlueSky, a payments platform might seem like the least nefarious door to close off to competition.
Maybe it's my background in fintech, but I find it far more palatable than paying their bills (and repaying their investors) by becoming, say, an **Advertising Platform**, a **Data Brokerage**, or some other kind of surveillance-business selling access to or authentication of users' [innermost thoughts, drives, attention and secrets](https://media.ccc.de/v/39c3-ai-agent-ai-spy).
The technologies needed to operate compliant, insurable, chargebackable payments are, like identity, something most app developers (and software developers generally) are happy to outsource to middleware or proprietary platforms and think about as little as possible, ideally not at all for years at a time.
Lots of critics think payments, like identity and compliance and insurance, are necessary evils that can only be run as platforms, ideally as cooperative or member-owned platforms, but Visa being a cooperative doesn't make the Visa/Mastercard duopoly any less nefarious or unpopular.
The protocol, in this analogy, is SWIFT, which supports multiple interoperable and coopetitive platforms on top (credit cards, GooglePay, ApplyPay, Stripe).
So if BlueSky starts doing payments, what happens when other appviews/communities/platforms[^5] want to start doing their own payments cross-interoperably? 
Does Atproto then have to become the SWIFT analogue, when multiple distinct platforms want to federate their payment protocols?
Does the board of `did:plc`'s Swiss Entity go for a walk across the valley and consult with the various SWIFT Swiss Entities about self-regulation?
Or does is the rest of Atproto fine with Bluesky keeping their payment platform co-extensive with the identity platform of the plc.directory, without meaningful competition and credible exit?
I am not presuming or hoping that it will get ugly, I mostly just want to point out _how_ ugly it could get, and how a payments platform basically _is_ an identity platform in both the technological and business-school senses of both terms, and how the non-BSPBC ecosystem and its protocol governance will have to grapple with that trillion-dollar business if it takes off.

Which shoe will drop?
Beats me, if I had raised that much money I wouldn't want some random blogger like me knowing either.
I think it's incredibly consequential for the future of the protocol and its identity system which kind of platform Bluesky becomes when it grows up, but the protocol (and its identity system) don't _need_ to wait for that to play out to start deciding what platforms it could live with and what they need to protect themselves from early.

Governance is actually as do-ocratic as open source in my experience (sometimes more so!).
To anyone anxious about these futures, I highly recommend just meddling and insinuating yourself into the various communities and foundations milling around trying to catch some money and turn it into IndieSky institutional power.
Already being there, known and working, will be a great advantage if those turn from sites of consultation to sites of negotiation and power over time.

## Prognosis: ActivityPub

The worst-case scenario is easy to table-top out: status quo, grumpy developers, no portability, no interoperability, ever-escalating compliance and spam-blocking and moderation costs per-user.
The bull case is a pretty wide-open field if significant progress can be made on all of above-detailed problems.

For the grumpy developers in particular, I think the breakthrough will be libraries that abstract (and take advantage of) the strengths and weaknesses of JSON-LD as a serialization... and everyone else being liberated from having to work too hard on this layer.
Promising work from [fedify](https://github.com/fedify-dev/fedify/discussions/580) (also supported by the STA!) could make (at least for the JS/TS ecosystem) JSON-LD less painful to use, making more powerful and ergonomic servers for various javascript runtimes (and, stretch goal, also for self-hosting platforms like Cloudron).
Similar tooling, [front-end frameworks](https://docs.nextgraph.org/en/reference/orm/), libraries, and per-language-family [frameworks](https://emissary.dev/) could form a patchwork of options that provide "pareto coverage," i.e. cover enough languages and architectures to provide some back bench of abstractions and building blocks for every motivated developer, at least in their second or third choice of major language. 
Developers thus served would be exponentially less overwhelmed by tasks like retrofitting client-to-server support onto their existing services or backends, wrangling with distributed-query, parsing lumpy or buggy JSON-LD from other implementations, or supporting account portability.
Similarly, the client-to-server experimentation happening now in the [W3C Social Web Community Group API Task Force](https://github.com/swicg/activitypub-api/?tab=readme-ov-file#user-facing-problem) could also produce some repeatable/generalizable gains, that similarly lower barriers and snowball into network effects.

That said, the amount of money going into ActivityPub is miniscule compared to the portion of BSPBC's warchest explicitly earmarked for furthering Atproto in ways that don't help their own platform.
The comparison is even more inequal if you also count the money spent on the platform with positive side-effects and network efforts for the "indie" players on the platform.
It is hard to say on what kind of timeline ActivityPub will advance, with or without new infusions of funding and institutional support.
In some sense, ActivityPub's challenges today are very similar to ActivityPub's challenges before Atproto was even launched, and next steps are more obvious and outlining as I've done above only because there have been years of trickle-funding to get us a little closer to a plan.

Real progress at scale, however, will probably require funding on another scale than has historically gone to ad hoc community investments.
Sharing costs to make more efficient and effective (cross-server, networked, auditable) moderation systems is a major piece of organizing that has to happen;
(All the horrible regulatory Torment Nexus forming around [age verification](https://www.theverge.com/policy/892075/age-verification-kansas-id-trans), real-name policies, and the imminent Show Me Your Papers internet might, one naïvely dreams, galvanize communities and make this feel more urgent than vitamin-taking.)
On the other side of that massive organizing process to add a moderation and resource-sharing layer to federation relationships, something like "network covenants" or platform constitutions can be worth the hassle to write.
Once you're already sharing liability, resources, and that much trust... co-funding development work, research, or feature development won't be as hard to fund or coordinate as in the "post-facto interoperability" days.

Most importantly, though, I think the future of ActivityPub depends on its level of ambition and its capacity to grow into new forms of coordination.
To be blunt, too many forks and not enough public accountability or joint planning doesn't really sound like the most appropriate way to write social software, and that's the FOSSy modality most of the Fediverse is stuck in, complete with martyrdom competitions and merge-request drama.
Hopefully sharing infrastructure will naturally tamp down on the FOSS ego problems, create cooperative platforms, and make it more obvious which codepaths benefit users at scale.

By level of 'ambition', I am refering to the [Scaling Mechanisms section above](#scaling-mechanisms-activitypub), which touched on the most ambitious possible next-steps:

1. end-to-end encrypted messaging and group data;
2. client-to-server with oblivious server and
3. diverse (and cryptographically-enabled) clients
4. with local-first support; 
5. being able to operate on (server-side) and display (cliend-side) heterogenous and distributed data.

If these 5 (admittedly massive) lifts can happen in parallel with distinct iteration cycles and user+institutional support, and be coordinated enough to combine when all five are ready like a Voltron-- that's a pretty wild system.
Keeping those 5 lifts roughtly on the same schedule and eventually-combinable is, realistically, at least one full-time job, and I have no idea who funds that kind of thing or how, but hey, it's possible.

And maybe all that is a little too "cathedral"/centrally-planned for a decentralized protocol.
Maybe the more realistic future is that it continues to be an unplanned mess of a bazaar, and still works out?
That wouldn't be so bad either.

## Endnotes

[^5]: Full disclosure, I have no insight into BSPBC's plans for payments, but I would like to take some small credit in having lightly advised and supported BlackSky Algorithms in their own community-based, transparent, and non-extractive payments project which [beat BlueSky to the punch by many months and counting](https://blackskyweb.xyz/anniversary/)).
[^6]: See [kuba's skeet](https://bsky.app/profile/mackuba.eu/post/3meoydfocsk2o) on the subject of "nonexistent trump PDSs".
[^7]: See [kuba's subskeet](https://bsky.app/profile/mackuba.eu/post/3llpnas3wt22x) about the plcfs attack.
[^8]: Mastodon was written in Ruby on Rails, the dominant developer platform of the early Y-Combinator/web2.0 app-building bonanza. Future historians will remark that "from hello world to IPO" was a little too on-the-nose to be believable as an encapsulation of the framework and its Zeitgeist. Ruby-on-rails was ruthlessly optimized for simplicity and modularity in those early days of cloud platforms, developer platforms, just ["platforms all the way down"](https://www.hellerhs.com/post/it-s-platforms-all-the-way-down): you did not need to know anything about clouds or distributed systems to quickly build something that would not have been possible 10 years prior, even with 10X the resources and 10 PhDs in distributed systems.
[^9]: I won't go into too much detail here, but it's worth mentioning that many, many implementers without prior JSON-LD or RDF experience have been gobsmacked by the difficulties of handling, parsing, and canonicalizing JSON-LD, particularly in languages without good JSON-LD tooling, which is to say, most languages. Many of the "protocol forks" have chosen to whittle down or completely abandon JSON-LD as the serialization of protocol messages, maintaining interoperability with the Mastodon API subset of the protocol by defaulting to (or translating to) a "plain-JSON" approach enabled by the [somewhat unpopular](https://tess.oconnor.cx/2023/09/polyglots-and-interoperability) "polyglot"/content-negotiation approach of the original specification. I don't personally share the anti-polyglot ideology, but I do worry that the ergonomics of a difficult serialization can lead to a developer-platform dynamic when the opacity or difficulty of a given serialization leads the bulk of developers to simply use provided tooling as a black-box and stay blissfully unaware of the distributed-systems hijinx happening inside that box; It would benefit the ActivityPub community immensely to have as ergonomic and powerful a blackbox as the suite of tools BSPBC has subsidized the rest of its community by opensourcing, documenting well, and maintaining!
[^10]: Note that the ActivityPub specification had to be ratified 3 years before [v1.0 of the DID spec](https://www.w3.org/TR/did-1.0/) was approved by W3C years later than expected, in 2022, over the objections of some browser vendors, i.e., W3C gold-star members.

## Acknowledgements

bengo, Aaron Goldman, Christine Lemmer-Weber, Chris Shank, Dmitri Zagudulin