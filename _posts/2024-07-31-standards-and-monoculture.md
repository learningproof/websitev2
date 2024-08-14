---
title: "Standards and Monoculture: The Curious Case of Multiformats"
categories: 
  - blog
  - activitypub
  - journalism
type: "blog"  
layout: single
author_profile: true
read_time: true
comments: true
share: true
related: true
toc: true
description: "This article dissects how Multiformats fared at IETF so far and reformulates what a Multiformats working group at IETF should be good for, before defining a 'checklist' and next steps."
excerpt: "This article dissects how Multiformats fared at IETF so far and reformulates what a Multiformats working group at IETF should be good for, before defining a 'checklist' and next steps."
image: /assets/images/village_meme.jpeg
defaults:
  # _posts
  - scope:
      path: ""
    values:
---

## Abstract

A funny thing happened when I tried helping Manu Sporny and the current maintainers of Multiformats propose a Working Group at the Internet Engineering Task Force in the hopes of moving the registry to IANA governance:
Multiformats was publicly and loudly declared ["harmful"](https://mailarchive.ietf.org/arch/msg/multiformats/KqdFPgjbUcYhc4dHoWqQrUFGi08/) (a [long-standing IETF euphemism](https://en.wikipedia.org/wiki/Considered_harmful) for "net negative" or "bad at standardizing") by one of the most seasoned and respected IETF standards-bearers, and we got sent back to the proverbial drawing board.
This article will not seek to argue that Multiformats is benign or useful (Aaron Goldman already provided an excellent [point-by-point rebuttal](https://mailarchive.ietf.org/arch/msg/multiformats/w-etaODmYp82mfRa9FU7yo12ia0/) to which I could not add one useful iota).
Instead, it will first dissect what cultural and ideological assumptions underlie both sides of the argument-- and reformulate what a Multiformats working group at IETF should be good for, before defining a "checklist" and next steps.

If that sounds boring and navel-gazey to you, feel free to jump to the ["Coalition and Collusion"](#coalition-and-collusion) section for next-steps on rephrasing the ask, on a  sounder foundation for proving usefulness to various communities and translated into the specialized jargon and community norms of the IETF.

## Protocol, Optionality and Translation

The first two sentences of the first of the eight theses that Mike Jones nails to the door of Multiformats (ranked, one presumes, by relative harm) are, I think the ones I take the most issue with:

> Multiformats institutionalize the failure to make a choice, which is the opposite of what good standards do. Good standards make choices about representations of data structures resulting in interoperability, since every conforming implementation uses the same representation.

Despite multiple attempts in-person and on the official mailing list provided by IETF for discussing the proposal, most notably Aaron's listed above, Jones is still publicly crusading against the degree of "optionality" offered by Multiformats.
For example, in a recent appearance live on stage at EIC Berlin, a trade fair for middleware vendors in the OIDC ecosystem that his own standards created and continue to ["regulate"](https://www.mnot.net/blog/2023/11/01/regulators.html.brotli), Jones ranked various contemporary standards efforts on their approach to "optionality", as part of a broader thesis about [optionality in the standards-making process](https://self-issued.info/?p=2535).
With all the playful authority of a college professor, Jones gave Multiformats failing grades against the rubric of optionality:

![Mike Jones presenting the slide "Multiformats gets an F" at EIC Berlin](https://notes.learningproof.xyz/uploads/09517b5e-2723-48ff-9c50-8a3939c7689d.jpg)

Now, a big chunk of Jones' career in and outside of IETF has been spent triaging and reforming the [optionality problems](https://medium.com/@phosmet/forging-jwt-exploiting-the-none-algorithm-a37d670af54f) baked into the JWT stack upon which trillions and the security of today's web depends, so I can definitely sympathize with seeing optionality and interoperability as antonyms, or seeing too much optionality as a major failure mode against which infrastructural protocols must be protected.
Optionality upstream (at the protocol level) has, historically, proven to be very hard to correct after industry implements products, price points evolve into stable markets, and SLA contracts are signed.
Many of the decisions taken early in the JWT design process assumed different timelines and a less structural role for these protocols: who could have guessed just how much _commerce_ (and how much [ruthless market consolidation](https://digital-markets-act.ec.europa.eu/gatekeepers_en)) would occur downstream of these specs?

My problem is not with the argument against optionality in identity or security protocols, which I am woefully underqualified to argue with any career protocol engineer, much less against one with as much firsthand experience as Jones.
As Aaron Goldman eloquently [put it](https://mailarchive.ietf.org/arch/msg/multiformats/w-etaODmYp82mfRa9FU7yo12ia0/), Multiformats is not a protocol full of optionality, it is **decoupling mechanism** that lives on a different layer, enabling lossless translation _between_ the representational profiles of multiple protocols (wire formats, data systems) which [rightly] constrain optionality on _their own_ layer of a [messy, heterogenous, real-world] stack.
Multiformats has no intention to be (and realistically would be terrible at being) a "protocol" in the sense that OAuth is, or the JSON family of encodings and subprotocols stacked on top of it;
a better analogy would be JSON, or CBOR, or protobuf, a token system more than a protocol for tokens.
Furthermore, multiformats is not even meant to be a "good" token system that handles discreet pieces of sanitized and orderly data; it was designed to be a system for handling any data, messy, existing, realworld data in any format rather than a net-new allowlist of eligible formats meeting a criterion decided in advance and working together nicely.
Put bluntly, Multiformats is only useful in a world where monoculture has not yet been succesful in eradicating semantics from engineering.

Besides, "too much optionality in standards" is like "too much cowbell" or "the commodity theory of value", or any argument that hinges on "first principles": it is an unfalsifiable "best way of doing things" argument that I find orthogonal to what I consider the goal of "good standards," even if it is entirely defensible as a goal of good _protocol engineering_.
Namely, I think "good standards" are ones that build consensus and a stable common ground between market actors who already know they disagree and will continue to disagree on the best ways of doing things.
Me entering into a "best way of doing things" argument with Mike Jones wouldn't be bringing a knife to a gunfight, it would be bringing a slingshot to a nuclear war.
More importantly, it would be an argument orthogonal to Multiformats' actual goals.

My (personal and professional) problem is, firstly, with the presumption that Multiformats is an identity or a security standard in the first place.
That is entirely on me for drafting a proposal that enabled that misunderstanding, to be honest.
_Meas culpas_, dear reader.
Multiformats is anything but an identity protocol with strong security guarantees: it's optimized for exactly the opposite properties as OAuth or OIDC are fine-tuned to deliver.
It's a translation layer and an annotation protocol worth using in certain contexts to get data loyally in and out of tightly-specified systems like OIDC or wire formats with unique constraints and efficiencies.
In any case, I'll write a separate blog posts months or years down the line when I have a new draft proposal for review and I want to show my notes, hopefully on the basis of a crowdthinking process _this_ blog post invites you to contribute to.

My (political) problem, in the meantime, is with the phrase "what good standards do".

### What is a standard anyways?

Is interoperability (and economies of scale) the self-evident and only goal of "good standards"?
Can "standards" (or just "IETF standards", more pressingly for this case) usefully preserve or postpone consolidation and monoculture?
Here things get a little more "Meta," in the sense that many open source and decentralization communities use the word when designating a "Meta" category to their public "improvement process" and document-publishing systems.

Here I think there has been some soul-searching within IETF in recent years, trying to come to grips with the inevitable multi-stakeholder politics at play in any open decision-making process, regardless of whether they are deciding technical recommendations with global industrial consequences or budgeting for a social club.
Take, for instance, a recent "Informational" RFC (it would be called a "Meta" document in many younger processes like those of blockchain Improvement Proposals) authored by Mark Nottingham, another influential IETF thought leader with a long list of widely-structural Web standard RFCs to his name contemplates the limits of objectivity in standards. "mnot" writes:

> Successful specifications will provide some benefit to all the relevant parties because standards do not represent a zero-sum game.
([Src](https://datatracker.ietf.org/doc/rfc8890/))

Identity and security standards, within the scope of one or two Area Director's roles mediating between different working groups, could be expected to make painful zero-sum decisions from time to time, since the status of a consensual "recommendation" from IETF or W3C is meant to constitute some kind of coordination and prioritization across that bounded set of stakeholders.
But that is a narrow and rare case, which IETF is optimized to deliver on yet which applies most squarely to established core protocols of the internet which are already being contested between major swaths of the internet industry.
Most other standards, whether at IETF or W3C, represent decisions made by [consensus](https://www.mnot.net/blog/2024/05/24/consensus) among disparate stakeholders not already structured into working groups and area director "tracks".

### What kind of useful is multiformats, then?

Phrasing the value-proposition of Multiformats (without using ambiguous and contested words like "protocol" in a way that invites misapprehensions and category errors) is hard work, and like I said, ongoing work that needs to be crowd-sourced to be authentic and appropriate to a broad-based, [consensus-driven](https://www.mnot.net/blog/2024/05/24/consensus) organization.
More importantly at this stage is a similar, but upstream question:

> To whom is Multiformats helpful?

Protocol Labs underwrote a lot of multiformats work over time, for the simple reason that Multiformats proved very helpful to the elaboration of IPFS qua file system and toolchain, but also as ecosystem which made a place for everyone, even those who had no use for IPFS but found some marginal utility in sharing infrastructure or economies of scale with the IPFS world.
As the IPFS ecosystem transitions to more diverse governance and use-cases, however, different topologies have taken shape:
the once universal file system and components specific to the Amino Network (aka "the public DHT") are decoupled from different toolchains for different networks, and Multiformats is less the conformance tool for keeping all IPFS data "Amino-friendly" and more the [lingua franca](https://learningproof.xyz/of-grammatology-ipfs-as-language-family/) of dialects drifting apart in different climates.

Multiformats is a useful alternative to JSON because it is extremely efficient and optimized for "packing in" many different kinds of data (ASCII and text, sure, but also binary, quirky blockchain wire formats constrained by eccentric engineering choices, etc) into a dense and flexible binary format.
It inherits a lot of syntax and ergonomics from Protobuf, but without the mandated schema language (if anything, one way that IETF could benefit multiformats is bringing some experience to the process of hardening some schema options or interfaces for the BYO schema nature of IPLD...)
Its closest neighbor is most likely CBOR, but differs mainly in its generally looser syntax (most notably for its lack of a mandatory length prefix, but also for its composability and stream-optimizations).
Another key difference from CBOR is its larger and more heterogenous registry of supported codecs having, from the start, been governed and optimized for different use-cases and different priorities.

A common theme, as you can see from this high-level comparison, is that multiformats was designed from the beginning to be an open-world translation language optimizing for flexibility above efficiency, and trying to support a vast superset of data structures beyond those used internally by IPFS, and beyond today's known data generally speaking.
Whereas so much of IETF is about tradeoffs and optimizations for tightly-scoped problem spaces, Multiformats was always intended to be a global data translation layer, not the best possible data handler for any one kind of data.

### Diversity and Resilience

To summarize a bit, as Aaron so elegantly already did in the above-linked mailinglist tour-de-force, multiformats' superpower is _decoupling_ wire formats and contexts from data, allowing a global file system (or, if even that is too much overhead, a general-purpose data language, aware of its own multiformatedness) to superset all the more focused protocols and data languages hardened and matured at IETF.
That might seem like a fool's errand or, worse, naïve infrastructure more useful for phishing and piracy than for legitimate uses of the internet if you assume the best way of doing things at scale is always planned in advance (and at IETF, generally).

But if your takeaway from the last few years of global-scale outages and supply-chain meltdowns is that monoculture makes too many honeypots and attractive single points of failure, economies of scale might not always be an unalloyed good.
[Solarwinds](https://my.infotex.com/solarwinds-timeline/) may be the most dramatic software supply chain failure in recent memory, but fundamentally, no purely technological solution can help (despite many relevant building blocks moving through IETF at the moment!).
When any mission-critical piece of software is being updated on that many computers around the world at once, the stakes are too high and the temptation too great; it is a business problem and a governance problem how to _economize_ less, how to allow a more patchworked landscape made resilient by its diversity.
As SwiftOnSecurity wrote at the time, the [proper framing for cybersecurity](https://x.com/SwiftOnSecurity/status/1276347336067887105) isn't perfectionism (i.e., I can't afford to take a single hit, there are too many systems riding on me) but attrition (i.e., minimize the damage of any one hit and win the long game).

Two years on, it doesn't seem like the software industry has done much soul-searching about its teleological drive to always globalize and always economize, doubling down in the face of all risk.
Instead, we're right back to debating yet again if [global delivery of patches is even a viable premise](https://www.thestack.technology/crowdstrike-driver-outage-cause/) after another embarassing global meltdown that [grounded over 5000 flights](https://www.bbc.com/news/live/cnk4jdwp49et)
Scaling everything up as much as possible also scales up risks that undermine the alleged progress our technological society is making;
all the nation-state-level budgeting that cybersec at global scale requires just raises the stakes beyond what any number of individual meatbags with therapists and families can realistically deliver, because humans still fail and humans are still on both sides of the capture-the-flag game.
Having all the humans on the defensive side of the game work for only a handful of companies (even "indirectly") and defending one common technological edifice kind of defeats the point of having market capitalism, making for a fairly brittle and late-Soviet security model.
All technological systems turn into sociotechnical systems when money and human data start flowing through them, so in many ways the most effective way to decentralize away the next Cloudstrike or Solarwinds point of failure isn't cleaner layering or better technical standards at all... it's anti-trust enforcement and economic regulation to protect any single point of failure from being upstream of that much international business in the first place.

Perhaps the opposite of one-size-fits-all corporate monoculture hasn't yet found a universal _mot juste_, but we are currently living in a kind of bibliographical avalanche of internet architects begging for a more diverse and multivalent, decentered internet before we are left with a few website and a few [American] corporations policing world speech and information flows, to say nothing of capital flows.
Stretching back decades, both from [within IETF](https://www.ietf.org/archive/id/draft-nottingham-avoiding-internet-centralization-02.html) and from [core contributors to the internet we already have](https://mitpress.mit.edu/9780262547703/designing-an-internet/), there is an alarm people are raising over and over again about an over-consolidated, over-optimized, over-economized internet with a shrinking number of [control points](https://youtu.be/_uXL0MJiQXU?feature=shared&t=411) and a worrisome number of continent-crippling "single" points of failure.
Extending Leslie Daigle's metaphor of a ["climate change" event horizon for the internet](https://www.thinkingcat.com/wordpress/wp-content/uploads/2020/08/2019-InvariantsUpdated.pdf), Robin Berjon and Maria Farrell argued convincingly that the word we're all looking for is "[rewilding](https://www.noemamag.com/we-need-to-rewild-the-internet/)", and maybe they're onto something.

Coming back down a bit from such lofty, philosophical perspectives, we could simply point to recent history at IETF as increasingly the history of diversification, end-to-end criteria of value, and increasingly holistic thinking.
Many influential "informational" and process RFC in recent years have walked back some of the previous zeal for "one-layer-at-a-time" [protocol design](https://www.rfc-editor.org/rfc/rfc9170.html#name-good-protocol-design-is-not), hammering on excess faith in layering and thinking more historically and dialectically at the processes that ossify protocols and entrench ["middleboxes"](https://www.ietf.org/slides/slides-semiws-ossification-a-result-of-not-even-trying-00.pdf).
On the networking layer, this had led to more _adaptive_ and _emergent_ protocols like QUIC, which bucks the trend (and breaks many stereotypes about the "kind" or "style" of work done at IETF), even overtly and deliberately [resisting traditional versioning](https://www.rfc-editor.org/rfc/rfc9369.html#section-6) to prevent ossification as QUIC support moves into commodity hardware and low-level software.

This needs to be the tone set by the Working Group charter and initial documents, if the Working Group wants to roll with these dynamics and meta-minded currents in IETF design culture.

## Coalition and Collusion

So, the entirety of the above was a long-winded free-write workshopping a different approach to the _content_ of the working group charter and specifications, based on feedback I got from friends, strangers, working group chairs, and area directors.
If you're not involved at the _textual_ level in that editing process, you are probably quite safe _not caring_ or even _completely tuning out_ that aspect of the process.
Realistically, it only affects the non-normative and process sections of those texts which, to be honest, many downstream users will happily ignore or at most skim anyways.

But the same IETF elders and community managers also gave me some additional non-technological advice that was far more blunt and operational:

> Next time, bring a village.

IETF takes its neutrality quite seriously, even though most participants driving work items and taking on organizational roles are doing so representing a long-term employer as part of their career trajectories.
These professionals are managing ideas and technologies rather than products for their employers, and in many ways have graduated up to this more esoteric and fraught management role after proving themselves good at managing teams and products.
That might superficially or cynically seem to contradict how seriously they [can afford to] take neutrality, but that would be selling short the role of ethics in professional comraderie and norms:
it is exactly on the basis of a shared familiarity with and even temptation to partiality that colleagues build trust and "see something, say something" when the nearly-invisible lines are crossed.

This explains in large part the "affiliation politics" that make email signatures and offhand jokes about "dayjobs" so central to the life of a standards mailing list.
Without a long-term, public community organization behind the primary proposer of a new work item, there is a natural tendency to presume the worst, i.e. that some random learning-impervious consultant is just a proxy for some corporation big enough to pay such a consultant without taking credit and blame for the work item.

### Standards of Independence

Another natural skepticism I was told to go out of my way to forestall was the mythic "one company spec".
This term refers to an infrastructural building block that one company would stand to gain most from stabilizing, whether by capturing core value in an open ecosystem or by locking in economies of scale, etc etc.
"No company, no matter how large or small, is welcome to bring a one-company spec to IETF," one long-time IETF volunteer told me proudly at a new-attendee mixer, and interrupting a conversation about Google and W3C I was having with someone else in the process.
"No one volunteers to chair a working group here unless they've been doing this long enough to sniff a false community."

I teased him that collusion, like pornography, is hard to define but everyone knows it when they see it to change the mood a little.
But after a polite chuckle, he insisted that, no, really, it takes five minutes of googling to find out a company's cap table, and ten more to figure out their business model if you've been paying attention to the industry long enough.
Companies, he told me, are public commitments, and after a little workshopping, we talked through how non-profits, and even cooperatives and collectives, are still public commitments in ways that private contracts and grants and projects are not;
affiliations are the badges and uniforms that organize the game and save a lot of time whinging about conflicts of interest and ulterior motives.

Similarly, another career IETF engineer from the telecommunications industry told me that the use-cases documents that usually get edited by working groups before normative spec editing begins often takes years of work, or in the case of telcos, millions of dollars of research-department spend, validating market hypotheses and finding actors in markets that will be affected by a new invention or protocol.
He'd never had a organizational role, but he was quick to volunteer that if it was him, he would be more convinced by a coalition that involved very different _kinds_ of companies than a large number of similar companies, particularly involvement from a cloud or edge-compute or DevOps company that had thought through what a deployment at scale of a hardened data standard could mean at regional or global scale.
Downstream and upstream alignment matter more than coalitions of competitors, he told me, no matter how friendly or coop-itive.

### Competition and Protectionism

I asked many long-time IETF-watchers how important it is for there to be "multiple independent implementations" of a thing like Multiformats, and I was told that metric is often overextended to be a general rule of software's independence.
The re-implementability and maturity of multiple implementations matters more at higher levels, where a single implementation being first to market could tend towards a monopolistic or single-point-of-failure market outcome.
But this is somewhat off-topic for something so many layers lower down the stack, unlikely to be the "engine" or differentiator of a product or straightforwardly impactful in the market dynamics of internet infrastructure, even in cloud software or distributed computing contexts.
At this much lower level of complexity, Multiformats is more of a low-level competitor to (and distraction from) CBOR, Protobuf, named-information hash, dataURIs, and similar stable, mature standards.

Overlapping subsets of Multiformats functionalities having been implemented in many different programming languages and cloud environments, going all the way to production in a diverse set of product categories and form factors, is a great argument for its _maturity_ as a style of programming.
Diversity of implementation and context is very useful evidence that Multiformats are an organic aide to interoperability across disparate ecosystems, and this would be useful evidence towards a kind of meta-protocol diversity argument as outlined above.
However, this diversity is less helpful, maybe even at cross-purposes, on the topic of showing peaceful or constructive coexistence with the load-bearing data languages of IETF's "mainstream" (CBOR, JSON, Protobuf).

Here, the most useful narrative needs to be that there is a community of diverse and independent implementers using Multiformats _instead of the more mainstream choices_ for _equally diverse and independent_ reasons, which need to be captured in documents and submitted.
Requesting that Multiformats have a place at the table alongside more mainstream options requires documentation of what previously-undocumented (or at least underdocumented and underprioritized) use-cases are worse served by those mainstream options.
It also requires documenting the equivalences and translatabilities, since IETF blessing two alternative solutions to the same problem can create "translation burdens" for public, heterogenous systems.
This takes more than a few emails to the mailing list or light "community work":
this is "field research," in a sense, and best done in the context of community-building, ideally not under the banner of a single company or a company-centric ecosystem.

### Standardization as the Normalization of an Impersonal Passive Voice

That kind of research might sound like a lot of work and a precondition to further work, but it can easily be parallelized and crowdsourced given the right community support and feedback loops.
One great piece of feedback I got was normative specifications (whether independent-track or through a long-term working group) do not fall from heaven fully formed, but are the _end-result_ of a process that is often begun years earlier _within_ IETF, or more precisely, within IRTF.

Perhaps anyone reading this is familiar with the time-honored hack of referring to any specification as an "IETF specification" by writing it up in IETF format using the IETF tooling and linter, mailing it to a mailing list, and thus having it hosted on the IETF Datatracker at an "ietf.org" permalink.
Every Tom Dick and Harry with something to sell to engineers can register a burner email and sign up for an IETF mailing list, use this trick, and suddenly have an "IETF spec" to point to as the basis for whatever product or prototype they want to dress up in standardized threads.
The trained eye will click the IETF link, notice "internet draft" in the header, check the Datatracker frontmatter for approval status and disregard this as just some opinion on the internet, or more precisely, as what IETF terms an "internet draft".

![animated gif of the "that's your opinion, man" scene from The Big Lebowski, 1998](https://y.yarn.co/9212bb82-3c0d-4fa3-ae8a-a78ca74a9fe3_text.gif)

There are many shades of grey, though, between normative specifications that have gone through full review and received IETF recommendation status on the one hand, and some rando's "internet draft" on the other.
Less strenuous _technical_ review, which does not include asking the million dollar question, _would this be helpful or harmful if recommended by IETF and deployed at internet scale?_, is done by the IRTF, which is the "research" wing of IETF, mostly on use-case, requirements, and descriptive rather than prescriptive technical specifications.
These latter, "descriptive" RFCs are called "experimental RFCs", in the sense that they are for pre-standardization or "nightly"-grade technologies, not "stable" ones by IETF standards.

What is a "descriptive" technical specification, you might be asking?
A specification describing the consensus or harmonized techniques of a community of practice fit squarely in this category, which might be a pretty good fit for where Multiformats is today.
There is even a decentralization fanclub in the IRTF called the [Decentralized of the Internet Research Group](https://wiki.ietf.org/group/dinrg), which takes very seriously the documentation of organic and community experiments in decentralized technologies, decentralized registries, and data translation.

If some aspects of the Multiformats project are seen as relatively stable and unlikely to see major innovation or iteration, and particularly if they do not require the visibility and formalized management of an IANA registry, they could simply be documented as "experimental RFCs" to build up that documentation-base for the community of practice around Multiformats.
Since the [decision](https://github.com/multiformats/cid/pull/64) to make the _binary_ form of CIDs the normative and definitive form, and for multibase to be broken out as an optional "last-mile" app-level convenience, multiformats doesn't exactly _need_ multibase anymore.
(Minutae alert: it's also worth mentioning that despite the original design of the multicodecs table, multibase is no longer what IANA would consider a _subregistry_ of multicodecs; reserving a few values to preserve backwards compatibility would adequately protect the multibase projects from collisions if the authoritative multicodec registry moved into IANA and multibase stayed outside of it.)
This specific work process could happen independently and completely in parallel of the binary Multiformats specifications and the [fully-normative] Working Group charter, or be taken up first while more substantial community-building and governance is proposed to make the latter more convincing.

## This Is What Community Governance Looks Like

If all of the above sound like "too many options" and you were hoping for an update on what the one obvious path forward is, I have some bad news about community governance and open source.
Whichever of these options has the most community behind it are the options multiformats takes, and each moves as quickly as multiformats users helps it move.

The hackmd table formerly known as the IPFS Foundation is very much under construction right now, but one possible route forward is for that foundation to become a tent big enough for all the various use-cases and stakeholders downstream of Multiformats, in all its self-describing glory.
A Foundation (or, well, any other community organization that served as a lowercase-F foundation) that brought together stakeholders and research and early-stage market thinking about content-identifiers, multiformatted-data, and maybe even multiformatted data LINKED NATIVELY to more multiformatted data (!) could be an interesting venue for organic connections and collaborations to emerge from.
Such a community org would make a great foundation from which to grief IETF with all kinds of normative, non-normative, and descriptive documents that advance the diversity and resilience of multi-protocol software.

![butteryfly-questioning meme by DAyala that reads, "is a hackmd governance?"](/assets/images/ayala__is_hackmd_a_governance.png)

Or, conversely, the Multiformats working group might just... not make sense for IETF yet.
Community shouldn't be measured by organizations but by their organizing, as the union-builders say;
a community organization without a self-organizing community to fill it and make hard demands of it is just an empty vessel.

If you have opinions, the IETF already gave us a [mailing list](https://mailarchive.ietf.org/arch/browse/multiformats/) and it's still the best place to pose (open, archived) questions about any of the above.
