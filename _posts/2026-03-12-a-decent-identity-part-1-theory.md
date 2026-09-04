---
title: "A Decent Identity Part 1: Theory"
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
description: "This essay outlines a set of capabilities and goals comprising decent social computing and then establishes a framework for assessing how well an ecosystem's identity system supports those goals and capabilities."
excerpt: "This essay outlines a set of capabilities and goals comprising decent social computing and then establishes a framework for assessing how well an ecosystem's identity system supports those goals and capabilities."
image: /assets/images/too_long.png
defaults:
  # _posts
  - scope:
      path: ""
    values:
---

## Context Window

Well, the "protocol wars" flared up again last month like a recurring case of shingles, and I was called upon to rehearse my fragmented critiques of what isn't credible about exiting from one PDS to another PDS already known to the Bluesky Public Benefit Corporation.
I refuse to participate directly in these protocol spats because every time I do, people misinterpret my motives or accuse me of favoritism, along predictably tribal lines (whichever tribe they're in is the one I'm accused of being unfair to).
Let me be clear: I want all "decentralized social protocols" and networks and implementation teams and workers to live up to their hype and stop allowing enclosure, control, and extraction in any protocol's name, even if that protocol is just trying to reach feature parity with another protocol.
This is not a "blog post," tho, so much as a problem statement and directional ideation exercise;
I do not claim to have some unique or special insight into how to fix any protocol or any of the tangle of business interests holding together its ecosystem, just opinions on various methods for modeling "identity" (and human behavior) in software.

At a high level, let's say the purpose of this treatise is to answer one question:

> What properties would an optimal "identity system" have to enable decentralized social computing ecosystems to flourish using it as infrastructure, i.e., what capabilities most maximize user agency and ecosystem resilience?

If you're the type to prefer actionable insights to treatises, you might want to skip ahead to [part 2](../2026-03-19-a-decent-identity-part-2-praxis/) where I propose specific short- and medium-term goals for achieving these properties in Atproto and ActivityPub.
If you're not, bear with me while I start at the very beginning, earlier perhaps than you might be used to technological essays beginning, "before the first principles" as it were.
Many of the terms used in that question above might sound obnoxiously undefinable, if you're a technologist or a journalist, hell, even if you're a regulator or community organizer specializing in user agency maximization and ecosystem health.
That sentence is honestly hard for even me to parse, and it could double as a summary of my entire career.
But you know what? I'm not sorry for that, your job is too easy (dangerously easy) if you can clock in every week and spend 40 hours advancing a definition of decentralization or social computing that's any simpler than the one proposed in this essay.
It's a collective failure of "the software industry" that all talk of decentralization fizzles out at disciplinary borders, specialized ontologies, and deceptive ownership shellgames (or "live laugh blockchain", as a friend once summarized the A16Z definition of [decentralization-as-financialization](https://a16zcrypto.com/posts/article/read-write-own-intro/)).

The scope of this treatise, however, is not "decentralization" of the software industry, for the simple reason that I think half the important work happening is neither industrial nor software.
I like to refer to this problem space not as "decentralized social media" or "next-generation social web" or any other O'Reilly-ready industry jargon, but the more unnervingly human nickname that [Christine Lemmer-Weber](https://dustycloud.org/) came up with on a planning call for an online conference on this very topic:

### "decent social"

Half the people that have contributed or are contributing substantially to the undoing of the Zuckosphere and the [extractive, addiction-powered antisocial web](https://bsky.app/profile/robin.berjon.com/post/3mg5tonsmxc2f) are not people who know or care what a decentralization is, they are just humans who want computer to be decent when they use computer to human with other humans.
"Decent" here means respectful, following the expected behaviors and separation of concerns that follow logically from a human using a computer to human with humans-- not CCing the NSA, for example, or fine-tuning an advertiser profile on the contents of direct messages.
That this process has gotten mixed up in "protocol wars" and platform economics and venture capital competitions is annoying because at least half the significant work on this topic is intentionally anti-commercial and non-extractive, or at least naïvely passive vis-à-vis extractive infrastructures that are so generalized as to be invisible.
(We could call this bucket "naïvely non-commercial" participants, and set expectations on their decency accordingly).
End-users, i.e. real people, just want to hang out online with their friends without some monopoly enshittifying their social graph or renting it back to them, simple as.
That some of this involves "protocols" that can be compared on the axis of "decentralization" is not just a distraction, but a technocratic anti-pattern that excludes from the conversation at least half of the people that should and need to be in it.

Pragmatically speaking, I hope this essay is useful for people that only care about one protocol and want to improve that one protocol's existing identity system.
At the same time, this isn't about you, partisans, I am trying to write something that could be directionally useful and immediately actionable for any ecosystem struggling to be born, be that ActivityPub, Nostr, some nomadic thingy I've never entirely understood, or any number of future protocols not yet defined or forked from today's.
(I will try to put any protocol-specific analysis into distinct, named section you can just jump over if you're too full of tribal hatred to learn from and empathize with others.)
I also want this essay to be useful for people who care about more than one protocol, or less than one protocol.
Or people who care about some other social computing paradigm that isn't yet or cannot be construed as a "protocol"-- even that framing is a concession to which ongoing discourses I am trying to intervene in.

### You are here

This document is, I hope, a thesis and the start of a broad conversation, and as such I expect to version it and revisit it over time, Borgesian navelgazer that I am: expect small changes and new memes forever.
In terms of future work or drastically new additions, I haven't included Nostr in my scope because I've simply not taken the time to really research and understand that third protocol, but I'd gladly take on a coauthor after v1 of this doc that can read me in and/or take on a financial sponsor to cover my outlay of research and writing time if that community doesn't have enough obnoxious opinions.

At a high-level, this is two-part treatise, each half of which has two major sections:

1. Terminology and Table-setting: this philosophical prelude is skimmable or even skippable if you just care about specific protocols, technological opinions, and next-steps.
2. Requirements for a Decent Identity: deriving from the theory a technological and governance rubric for various forms of user- and market-participant-empowerment against which any protocol ecosystem could be judged over time.

In the next installment, I will apply that rubric for assessing identity systems in detail to Atproto and ActivityPub:

3. Diagnoses: Measuring each protocol ecosystem against those requirements.
4. Prognosis: Forecasting and proposing medium-term priorities for each

## Definitional quagmires, or why no one lets me write "the Terminology section"

> What properties would an optimal "identity system" have to enable decentralized social computing ecosystems to flourish using it as infrastructure, i.e., what capabilities most maximize user agency and ecosystem resilience?

OK so having crystalized this^ as my goal, you're going to need some kind of working, local definitions of those weasely words, even if they are obviously hard words to define.
Through my veins flows the blood of a poet, and this broken brain was made for phenomenology more than epistemology, so I will admit upfront that all of these words suck and I shouldn't have chosen them.
But like democracy, each of these undefinable terms is less bad than any of the alternatives, so let me just flail around not defining them for a while, and filling in gaps in what I consider the pertinent backstories of how we got here.

### Quagmire 1: Social computing > Attention Media

> "Using these services began to feel like standing in front of a blaring loudspeaker, broadcasting fragments of conversations from all over the world directly in my face. [...] There was nothing social about them anymore. They had become *attention media*. "
> *--[Susam Pal, susam.net](https://susam.net/attention-media-vs-social-networks.html)*

One of the worst things we can do is reduce social computing to social "media," which I see as a kind of original sin committed at the very dawn of the internet industry.
Once the early web barons and commons-enclosors realized that our emergent online-first socialiability could be hijacked and hotrodded into a turtle-stack of advertising and surveillance monopolies, the game was already up.
We let "media companies" **privatize our digital sociability** simply because they were the first to invent a business model strong enough to distort and colonize the personal computer and personal connectivity, which took less than a decade.
I won't rehash the history of the "social-driven"/"Web 2.0" bonanza that warped and conquered the internet (there are plenty of great books on the subject[^1]) but suffice it to say, "Coke or Pepsi but Make It European" won't get us very far, and neither will thinking in terms of "websites" and "apps" instead of platforms, standards, infrastructure/dumb-pipes, and economies of scale.
Even thinking of "monthly active users" and "total addressable markets" are inheriting a lot of enclosure assumptions that are literally toxic to the online sociability we want and consider decent; data "ownership" suffers from the same inheritance.
Inheriting the framing of "social media," as much of the otherwise great social-computing work of 2000s/2010s did with its fixation on "walled gardens" and the capture of "social graphs", is a limiting anti-pattern, a "negative frame" as they are sometimes called in political theory.

If you're a glass half-empty person, you might accuse the original W3C "social web" working group of exactly that:
ActivityStreams started by distilling contemporary behaviors and UX expectations from that generation's ascendent extractive "social media" platform down to a core list of use-cases and an ontology, then imagining an end-to-end protocol for communicating these activities across a distributed system similar to email and/or RSS.
If you're a glass half-full person, they actually got pretty far engineering a train without tracks, as there was little precedent (much less normative reference) for how identifiers would work across this open-ended distributed system, how servers would ensure data integrity, how users could self-manage their accounts and even their authenticity-ensuring private keys, etc.
But one thing I love in the minutes of that working group is that, for all its faults, they were NOT trying to replace Twitter and Instagram-- they were trying to unlock some kind of social computing mechanism that would not, maybe even *could* not power any imaginable "media business."
The motley crew of shifty nomadic server-squatters, indie-web yeomen, and refugees from the commercial social web all had in common a pretty sincere and deep commitment to replacing "social media" with a web extended to be natively, invisibly, and inherently social.
Which is pretty beautiful, in a [time capsules are accidentally gallows humor](https://dustycloud.org/blog/a-letter-from-2016-to-2026/) kinda way.

But it's not enough to replace "social media" with "social web", in my humble opinion, because even "the web" (with its ossified HTTP semantics and public networks and server/client architectures) is a subset of what computing can be, and "the web" is itself just an economic relationship for networking computers to each other *advertisingly*.
The "local first" software movement[^2] (and the anti-client/server wing of the decentralized identity movement[^3]) are only two maybe-familiar-to-some-readers examples of why "the web" isn't pro-social and user-agentic enough to support all of our social computing.

If anything, all our computing could and should be *social* already, why would it be anything else?
In a Marxist sense, we're so deeply **`alienated` from the computer** because of the business models and geopolitics that determined the entire evolution of personal and infrastructural computers.
As a technology, they are deeply conditioned by the social relations reified in their Access Control Lists and the bureaucratic private-property regime inherent in the concurrency model of the "file system".
These malignant forces and rentier capitalist cancers invented first the enterprise mainframe for employees, and only derived the "personal" (i.e. consumer) computer from the "employee terminal" with some [union-busting, misdirected military R&D spend, regulatory arbitrage](https://popfeed.social/book/9780316592031), and a good deal of SBF-level [fraud and self-dealing](https://www.theguardian.com/business/2007/apr/25/3).

So, in the same sense that a cloud is just someone else's computer, so too is social computing just the computing you would already be doing if *someone hadn't already sold you a device under their own control* (that 99% of buyers barely understand) and if that someone weren't using it to *rent your own attention back to you*.
Maybe it sounds cliché or unthinkable with AI companies out here driving up the cost of all the components in your computer and renting your thoughts and languages back to you at low introductory rates, but it's just silicon.
We can void our warranties and recycle the parts into whatever configuration we want, without these demonic business models wielded by tyrants chanting "there is no alternative".

### Quagmire 2: User agency is a fancy name for restoring humans to their birthright (namely, the guillotine)

> "The distinction between programmer and user is reinforced and maintained by a tech industry that benefits from a population rendered computationally passive. If we accept and adopt the role of less agency, we then make it harder for ourselves to come into more agency."
> *--[Melanie Hoff](https://gist.github.com/melaniehoff/95ca90df7ca47761dc3d3d58fead22d4)*

A lot of the talk around agency and capabilities sounds intangible and slippery to technologists, for the simple reason that all philosophy and social science does.
Sorry, there's no engineering of the soul, just [religion](https://www.ncronline.org/vatican/pope-leo-tells-priests-not-use-ai-write-homilies-or-seek-likes-tiktok) and [philosophy](https://direct.mit.edu/posc/article/31/1/9/114165/Bruno-Latour-s-Science-Is-Politics-By-Other-Means), for now at least.
(We have yet to see what the [LLMs add to the liberal arts over time](https://www.wired.com/story/truth-terminal-goatse-crypto-millionaire/).)
There is no optimizing the pure function of free will or human self-expression, but what we CAN do is get the hell out of the way and let computer work for human instead of computer working for consumer/corporation/private-property-regime.
So much of the discourse of "user agency" to date has tried to spin a negative into a positive, making an *undoing* feel like a project of *making*.
In this sense, what I mean by optimizing for human agency is just freeing up as many possibilities for the computer-user and -toucher as possible, taking off the fetters of inertia and extraction and enclosure.
No need to get to specific or prescriptive here: anything that makes you less a passive "user" of the drug transnational pseudo-states are "pushing" is at least directionally helpful here.

"Ownership" is the mantra in so much of the hyperfinancialized world of "web3" and post-web software, but [ownership relations](https://popfeed.social/book/9780691189437) still make people fungible and lost in a network of value and debt where small players haven't got a chance.
Having "more" "money" doesn't particularly help you if everyone around you also has more, or if money gets harder to turn into the things and powers you want.
Ownership feels like a distraction to people who study power, because each wave of computing opens up new things that are scarce or powerful, which renders each previously-important ownable or powerful thing just a vestigial loss-leader for the new goldrush, a distraction from the new power struggle.

And real power, unlike ownership, is never individual and never neatly measurable in any kind of ledger, record system, or rulebook, not even law (which can only chase behind it regulating the residual institutions of the last power struggle). As Robin Berjon hints at near the [end of his popular essay on the subject of digital user agency](https://berjon.com/user-agency/#agency-is-collective), *individual* end-user agency is maximized when you network together the liberated people and let them compute *socially*.
It's one of those more-than-sum-of-its-parts type situations.
Or a `subsidiarity` situation, if you speak the dialect of the Europeans.
Or, in the dialect of the anarchosyndicalists: bottom-up power.

### Quagmire 3: identity systems are the invisible plumbing of object permanence

> "The purpose of a system is what it does"
> *--Stafford Beer, What is Cybernetics, 2001[^4]*

Of course, since we're talking power, it's time to get Foucauldian and drop all talk of formal or financial power, and get to the real-deal bedrock form of informational power.
In Judith Butler's reading of Freidrich Nietzche, she calls it "subjectification" and sketches out a Foucauldian meta-history of how that power was scaled up and bureaucratized by the nation-state to make invisible the boundary-drawing and ownership-regime-building.
The power to excommunicate, to deduplicate, to deny a fresh start or a false name are (along with violence) the core competencies of the State.
**Weaponized object-permanence**, you could call it: being able to track and predict the mapping of bodies to minds, to know even better than the minds in those bodies which body they've been in to date.
Naming power, the hardest problem in computer science (or any science), the part LLMs will always be bad at by definition.

Specialized technologists will tell you people too often say "identity" when they mean "identifier," since after all record systems (which most software is) need identifiers to link to one another, and establish that "object permanence" for the information they exist to manage across boundaries.
But this is an etymological nothingburger, like the classic Saussurean one at the origins of modern linguistics (and language-modeling, lol):
A signifier is only half of a signification relationship, and meaningless (or `insignificant`, even) without the signification.
Similarly, an identifier is just a simple record in a simple namespace presumed to be useful for tracking *a thing with an identity already agreed upon by all parties*.

Technosocial systems, where content and actors are tracked, use identifiers to keep straight who's on first, from which disparate outside systems hang their information, they can't stop themselves.
Mostly, depending on their business model, they need to track the specimens in the telemetry panopticon for that telemetry/ad-profile to be worth anything, and they need to track your attention to be able to sell it to other people, etc etc.
There are all kinds of identifiers used to make the data flowing off of every interaction with each [presumed] human usable and salable, and others for assigning a certainty score that each interactor is human, and others for assigning a certainty score for the likelihood of that human being unique and not an alt of other humans being tracked.

Legally, this of course maps to liabilities and actuarial logic about how likely each person is to blow up a world trade center, or participate in a class-action suit, or leak documents to journalists etc etc.
And in 2026 it's turtle-y systems all the way down, an interlocking microservices architecture of trackers, cookies, geolocation history, browsing history, profiles, and accounts that the right [well-capitalized buyer](https://popfeed.social/book/9780593443224) can [bulk-buy](https://www.aclu.org/news/privacy-technology/dhs-is-circumventing-constitution-by-buying-data-it-would-normally-need-a-warrant-to-access), query, merge and package up to, idunno, a [deportation effort](https://www.404media.co/here-is-the-user-guide-for-elite-the-tool-palantir-made-for-ice/) with a budget bigger than almost any military on earth.
In 2026, the potential damage caused by any "identity system" is hardly limited by what the system itself does or knows about each meatbag ensnared in its web; it needs also (realistically) be held responsible for what other identity systems it can be data-merged onto, what kinds of queries it powers and makes easier in combination with all other public data and purchasable data, two categories of which are almost coextensive with ALL DATA if you know too much.

Despite the lofty-sounding phrase, I am mostly defining "identity system" functionally, as all the interlocking processes that that rely on and are "downstream of" a namespace or a record system with humans as a record type or data subject.
Most people who build software don't think in those terms, as most work people get paid to do relies on rather than building identity systems;
there's an old saying in identity tech circles, that who wouldn't love to outsource these problems and never think about them again?
But I'm writing about them because they're my specialty so as long as you're paying attention to me you'll be thinking about them with me, sorry.

### Quagmire 4: decentralized identifiers are my favorite oxymoron

> "There is no point in claiming that the purpose of a system is to do what it constantly fails to do"
> *--Dark Stafford Beer, What is Cybernetics, 2001[^4]*

Decentralized identifiers are a funny kind of oxymoronic limit-case of identity systems-- they were invented ("made up"?) as a kind of thought-experiment by people who knew intimately the powerplays inherent in registries, namespaces, and naming power.
The process was kind of similar to (and contemporaneous with) that described above which gave us the "social web" as a goal, designed by the [International Web Designers' Guild](https://bsky.app/profile/blaine.bsky.social/post/3mf6bx7ymrc2q).
A group of identity specialists covered head to toe in registry-governance and namespace-design and low-level infrastructure battle scars got together and tried to imagine an export format that identity systems could use to interoperate better, and lock in their "users" less.
To make it harder for the next Google to emerge, basically.

"Credible exit" emerged years later from the woker/DWebbier end of the blockchain narrative mill, deeply tied up in financialization usages of the word "exit" in most early record.
A second meaning emerged over time, though, of exit as consumer protections in service relationships (phone number portability, for example), by which, yeah, "credible exit" was entirely the point, the primary goal of identity systems whose infrastructure was resistant to monopoly control or institutional/protocol ossification.
"Credible exit" has been more or less retconned as the primary goal of the DID design process that predates it as a stable term, but less widely-known are the contrasts between early DID thinking and contemporary OAuth, which was at that time forming into a middleware trade union (OIDF) and a foundational economic platform on which cloud companies could architect business models automatable and auditable at their lowest level.
Systems of record and economic models evolve in tandem and help one another become invisible;
this by-now-invisible norm-setting gets kind of esoteric for even fullstack engineers to see and reason about, as it's just the water the whole industry swims in!
Speaking in "use cases," however, we could refer to the working group's goals on this level as the cluster of "bring your own identifier" (BYOID) usecases: in them, a service provider does not need to "own" or lock-in network effects to take business from customers that bring their own (portable, exit-friendly, interoperable) long-lived identifier, reputation hooks that said service provider can use to query, e.g., public or commodity registries for basic trust-establishment inputs, and perhaps even a shared system for storage/cookies/public records.
(This last goal, not entirely consensual in the WG, was the driving vision of the founding of the [Decentralized Identity Foundation](https://identity.foundation), whose founding director worked for years to build ecosystems around a very PDS-like [semi-oblivious storage server](https://identity.foundation/decentralized-web-node)).

Another, even more esoteric dream (focused more at the OIDC layer and adtech and data brokerage than at OAuth and security guarantees) was the "BYOclaims" usecase.
I.e., "show me an authority I trust [claiming that](https://www.igalia.com/chats/vcs) you're old enough to be here so that I don't have to see, hold, or be responsible for the underlying proof".
In "web app" terms, users don't need to "create an account with" each app, even for apps that need to know some facts about you and judge coarsely your trust/credit-worthiness; neither do those users need to make themselves reachable by the app forever.
This dream took the form of a more user-first form of the Single-Sign-On paradigm where your home base advanced settings let you revoke permissions from apps still tracking or emailing you.
(That dream is still alive, largely on OAuth rails for now, in the form of the W3C [Federated Credential Management API](https://www.liquid.surf/fedcm).)

There were other goals and capabilities proposed as mandatory or good-to-have as well, which are to a wider audience quite hard to explain: permissionless query (for each DID's authoritative current document), self-authenticating data/records (insofar as key discovery is already solved), "commodity" (or near-zero) cost per record, scalability, and neutrality are the main ones.
Most of this didn't make it into the [dry, abstract specification](https://www.w3.org/TR/did-1.0/) that tells you what each DID system needs to *do*, exactly, but it's all there in the minutes of the design process and raucous mailing list, if you have a [few years](https://popfeed.social/book/9780197776698) to devote to the primary documents.

There were a few requirements that never quite achieved W3C **consensus** but definitely were a guiding motivation for a broad majority of the participant: "decentralization" in economic terms (capture-resistance, non-monopolizability), in the technological sense (no single points of failure), and in the ethical sense (non-coercive, transparent governance).
These almost-goals haunt the entire life of the working group, motivating many never satisfactorily-finished non-normative deliverables and [collectively-written rubrics](https://www.w3.org/TR/did-rubric/) and [statements of principles](https://blog.identity.foundation/the-did-dilemma--when-is-an-identifier--decentralized--/).
For the most part, the discussion of these forms of decentralization never quite got to fruition because they were not so much properties of the DID document or the DID identifier (i.e. the export format) as they were capabilities of the *identity system* that exported and interoperated with *other identity systems* by exporting these little record-keys called DIDs and their global documents.

Given that the overwhelming majority of participants had plenty of experience with both W3C and IETF, there was also an unspoken goal of circumventing "DNS".
(By "DNS", most of these folks actually meant the ICANN platform, i.e. the subset of the DNS cinematic universe that is governed by ICANN gTLD operating agreements and bylaws and censorship mechanisms; non-ICANN DNS is pretty inocuous and doesn't have nearly as much censorship surface).
Consensus was elusive here because saying that no domain names could be implicated in the resolving or publishing of DIDs felt odd, and consensus language never quite crystallized, even if `did:web` was generally agreed to be a placeholder or testing-tool rather than a production method, since

1. it adds no particular features or properties over DNS except simplified interoperability with other DID methods), and
2. hard-coding a domain name into a resolution specification would be so obviously centralized as to be pointless.

In some ways, the DID project feels failed or incomplete by its own definition of success.
In other ways, the DID project delivered something more interesting than what it promised: it memed into existence *decentralization* as a kind of *milennial cultural project* independent of blockchains and cryptocurrencies, even if all the goals mentioned above almost shake out of herding all the relevant cats onto a given blockchain.
(It's also worth mentioning, in the interest of historical materialist honesty, that many core contributors and prototyping efforts towards DID evolution were directly sponsored and underwritten by cryptocurrency foundations and whales.)
[Most of the core ideologues and architects of the concept of DIDs are still at it, iterating and refining their proposals](https://lists.w3.org/Archives/Public/public-credentials/2026Feb/0273.html) to this day, forking and reinventing and beefing like Linux distros or Linux Foundation projects.

To sum it up, individual DID methods should not be understood as `ARCHITECTURE.md` files that are written before identity systems are built that execute them as plans;
Similarly, DIDs in general, as a category, are useful but insufficient specification of the problem space for social (or any other form of) computing, much less a solution.
They are **export formats** that make *existing, functioning, load-bearing identity systems* more **federatable, exitable, forkable, salveage, reanimatable** in case of sudden- or heat-death.
They could, in the best of cases, turn identity systems into something more neutral and unownable: they can turn something as static as an identity platform's atomic structure (it's data model for identity, say, or it's lowest-level definition of a knowable actor) into something more open-ended and fluid, like a protocol that adapts that static thing to any outside context.

> It's not a great plan to draw the map before exploring the terroritory, but once you've got a bit of life stretched across a given territory, a map can really help you find new routes, new users, new use-cases, new lives.

### Quagmire 5: Ecosystems > Platforms > Markets > Networks

> "No Taylorist factory can sustain production without the unplanned improvisations of an experienced workforce. Planned Brasilia is, in a thousand ways, underwritten by unplanned Brasilia.""
> *-- James C. Scott, Seeing Like a State*

I want to really hammer on how different this "territory" is from the information, the "network effects," the social graph:
what I mean by territory is something lived and living, a chaotic writhing mass of  humans, at the very least an economy and ideally an ecology.
There is a temptation to see a technosocial thing as a deterministic technological container full of non-deterministic humans, but it's worse than that, it's a cyborg and a collective hallucination.
The system isn't just what it enables or what it tries to do, it's the whole thing, and that whole thing evolves over time as humans do and as capitalism does.

For this reason, the best "identity system" is one that is extensible, within reason, to repay the underwriting of Scott's unplanned Brasilia, to invest in future capabilities.
The best identity layer (and export format) for decent social computing isn't what cheaply scales or what locks in, forever, a baseline definition of service portability and data portability;
it has to balance these "keep it simple stupid" goals against extensibility and upgradability and graceful forkability.
It also has to balance supporting today's ecosystems with enabling tomorrow's ecosystems, even if those two are at crosspurposes.

Ecosystems are not rules, they are equilibria, and that is what drives any institution and social structure.
Laypersons think of legal and social structures as rigid, rule-driven things, but the rules are just containers for the all the chaos that specialists work tirelessly to hide from civilians.
This is especially true of technosocial things, the technical side of which is easier to talk about, grasp, map, and predict.
This is even more true of social computing, which strives (according to a deeply engrained habit in capitalist computing) to find reproducible, scalable routines and structures and make stable platforms of them.

But the more social the software is, the harder it is to platformize a scene or a site without turning it into a prison (or a [panopticon](https://en.wikipedia.org/wiki/Panopticon)).
That is why I propose that:

1. The *lowest* form of social computing is a **social "network,"** which occludes from its inmates the nature of the commerce powered by their exhaustive surveillance.
2. A little more *honest* is **a social market, a prediction market, a monetized attention arena,** or other form of dystopian late-capitalist **casino**, where at least some users win the jackpot and everyone knows they're an addict.
3. A **platform economy** (where buyers and sellers meet in a layered or multi-level marketing ecosystem) is in some ways a little closer to what a society might call `Law`, in that taking a percentage of all commerce and enforcing some rules of the road is at least a defensible, tolerable kind of carceral state with (ideally) some modicum of *accountability* in its administration.
4. None of the above are in God's image, though. We were not born for this endless slaughter and violence. Real social computing can never flourish within a closed perimeter or an extractive platform; if there is to be commerce on platforms, these platforms must be **connected** and there must be **exits, fast lanes and slows lanes**, outskirts and thoroughfares, some respite from the Dantesque [*threshing floor*](https://bsky.app/profile/scorpioheavy.bsky.social/post/3lrx5qd6tvk2x). There must be ecosystems that extend beyond any one platform, beyond the concept of a unitary platform, bound by a permeable membrane.

### Quagmire 6: I know a platform when I see it

> "Inappropriate concentration of power on the Internet has become a concerning phenomenon -- one that protocol design might have some influence upon."
> --mnot, [RFC8890](https://datatracker.ietf.org/doc/html/rfc8890)

If stackranking metaphors feels a little too abstract, I can try looping back and threading together all the aforementioned quagmires a bit:
they're all riddles about platform economics, which is what actually ate software and then the world.

People who've never studied economics may not think of platforms as [governance] failure modes or liability sinks, but "winner take all" is a real problem in human society anywhere outside of card game design.
People steeped in the software industry (I'm second-generation myself) can speak glibly about "infrastructure plays", "[picks and shovels](https://blog.shovel.company/)," and "built-in tollroads" but these are basically thin euphemisms for enclosure strategies and attempts at building a defensible monopoly, which are two of the easiest ways to raise venture capital.
Building a business that sells a product is like selling lemonade on the side of the road;
Owning a freeway or a clearinghouse (or a casino) is just printing money, taking a percentage of the total business with none of the risk.
If I seem disproportionately hostile to platform economics it's because I think they're incompatible with free markets, mostly because they enclose and limit and suck the life out of markets.
More importantly, though, they create [superhuman concentrations of power](https://archive.is/V01qz) which I think are probably incompatible with democracy.

Whether or not you share that ideological position, I think it is less controversial to say that platforms are the driving innovation of the "internet age" and, with an appropriately flexible and dynamic definition, most global names in software can be understood to operate platforms as a core function.
Platforms, in software, can refer to many things, and trying to abstract over all the variations[^5] might surface patterns and help dislodge oversimplifications and stereotypes about the platform dynamic:

- **Payments platforms** help merchants and buyers find each other to quickly establish a payment channel with various kinds of underwriting, insurance, and other services attached (and extract percentage-based rents).
- **Dating platforms** help pots find lids for, um, various human forms of human commerce or "traffic" as the Germans say. In olden time (and in the Indian subcontinent!), these were literal marriage-oriented brokerages, but nowadays we tend to also include many other forms of potlidding, particularly as the digitization of our lives makes possible [wholly new forms of potlidding](https://www.eurofound.europa.eu/en/surveys-and-data/platform-economy).
- **Search platforms** help searchers find content, with all the SEO and [poisoning hijinx](https://canadahealthwatch.ca/2026/03/09/tomorrows-ai-models-are-learning-from-todays-polluted-research) that entails, whether the mechanism be typing queries into webpages or chatting with your friendly anthropomorphic prison warden.
- **Data-sharing platforms** (aka trust frameworks or data brokerages) are a kind of search platform where the content being searched is high-certainty, sensitive, or consequential information about real natural or legal persons: marketplaces for intell (or *kompromat*, in the more sinister forms).
- **Commerce platforms**, whether irl bazaars or global online bazaar-ify type megaplatforms, rent booths and (in some cases) take a variable percentage depending on how much help you need getting customer money into vendor accounts/currencies/tax regimes.
- Hanging a shingle on **Publication platforms** is the career path refugees from a collapsing "media industry" are [increasingly taking](https://bsky.app/profile/jeffsharlet.bsky.social/post/3mfhkiviqzs25), at great peril to our [information ecosystem and democracies](https://localnewsinitiative.northwestern.edu/posts/2024/12/05/trump-wins-news-deserts-in-landslide/). Instead of *newspapers* we have *substacks*, instead of curated and ecosystem-bundling *record labels* we have *soundclouds*, instead of generalized and institutional *news sources* we have *link aggregators* and algorithms. I've written [elsewhere](https://learningproof.xyz/newsrooms-and-activitypub/) about this, there's whole [conferences about the problem](https://protocolsforpublishers.com/), but suffice it to say I'm personally more worried about it than climate change.
- **Developer platforms** help companies building products find the tools, languages, markets and ecosystems which will work best for maximizing shareholder value with those products.
- **Cloud platforms** help companies build, take, run, and deliver products to consumers, commoditizing and automating (and *surveilling* and *infering over*) as much of our digital lives as they can (by some estimates well over 90% of it and rising).

All of these are facilitations of commerce that at some tipping point become more profitable than the commerce itself.
In all platform dynamics, the golden rule is "network effects": the stability and profitability of a platform grows quadratically as it facilitates a bigger share of that kind of commerce.
The platitudinal way this is described is, ironically, as an identity system: the more buyers and sellers are "finding each other", the more "participants" are interchangeably bumbling about in the pinball or pachenko machine, the more "valuable" each participant is to the platform's operations, because it means more value can be skimmed off the frothy and combinatorial "top".
On some level, the most visible infrastructure of a platform is its identity system and the reputation system(s) hanging off of it:
Commerce lures buyers and sellers onto a platform (because it's the easiest way to find many pots for their lid), and almost imperceptibly, on their way in the door, they're tagged with an identity, a dance card, an eartag, a serial number which is the groundfloor of a multi-level economic system.
An identity system props up a platform economy and is its lowest level, its essential and often invisible plumbing: in this sense, *identity systems are the **bureaucracies** of platform economies*.

### Quagmire 7: Under the street, a protocol for humans

> We live under a capitalist mode of computing. The tools, languages, techniques, and assumptions of digital systems are structured by economic forces that shape not just what we can do, but what we can imagine doing. By separating production from use, producing inflexible software, and slicing up computing into siloed apps, your agency is held back by a tech industry that profits from a population rendered computationally passive.
> -- [Liberatory Computering](https://www.libcomp.org/)

If a structured, scalable "identity" is the atomic unit of a platform, then protocols are like the systems (wind, water, nitrogen-fixing) that enables an ecosystem for platforms to thrive in (and from).
In the best of cases, a protocol is a kind of law or force of nature, all of whose economic players and architectures can come and go, a [giant ship of Theseus](https://www.youtube.com/watch?v=Z04RGWgHzvU) describing not a group or a perimeter but a dynamic equilibrium.
While a platform benefits from being able to impose an optimally simple data model on each participant in its system, an ecosystem benefits from diversity, resilience, ungovernability and chaos... achieving dynamic equilibrium according to a few simple rules and negotiations.
That's what good protocols do, so understandably everyone who wants "engineer" written on their tombstone dreams of contributing to new ones forming on their watch.

Realistically, though, this technologists' dream is *partial*, because we're tinkering at the edges, focusing in on where technologists might accidentally, collectively engender a change to the system upstream of technology (human society) that allows some people to own silicon and force it to think, after iincentivizing other people to manufacture chips for them, etc.
Regulation matters as much protocol, or to put it another way, protocol is the technological equivalent of regulation, which exists not to siphon value or simplify the economy so much as protect it (often from itself, or from disastrious maldistributions between participants).
And here, by regulation, I'm not just referring to nation-state formal regulation, I'm also referring to emotional regulation, moral regulation, all kinds of counterveiling forces that keep the impulse to own and extract from rendering the earth uninhabitable sooner.
The most important parts of human society are meatbag protocols, after all;
in the best of cases, technological protocols inherit, extend, and are symbiotic with them.
The dream of [protocols transcending or obsoleting politics](https://scholarship.law.columbia.edu/cgi/viewcontent.cgi?article=1885&context=faculty_scholarship) are, to be frank, *anti-democratic fantasies of power* by people better at technology than politics, and should be dismissed as such.

It might seem a little self-defeating to plod through that many words about technosocial systems to ultimately arrive at "but all of this is downstream of politics".
This is not exactly my point: instead, think of this as the horizon of change circumscribing success in technosocial design, in my view.
We will have knocked it out of the park if a social computing protocol (or more likely, an interlocking patchwork of them) survives long enough to be obsoleted or drastically reworked by the social orders of our species evolving beyond those systems that funded and organized computing to date.
But that framing should help us order our concerns (and the layers of our stack), such that success means collective liberation and not private gains.

## Requirements for a Decent Social Computing Protocol

So after all that, maybe it's a little clearer what I mean by "identity system", "enable decentralized social computing ecosystems to flourish", "maximize user agency" and "ecosystem resilience".
We can get more concrete now and define specific capabilities of social computing that translate, at the lowest, atomic level, to a data model for identities and protocols for updating it, querying it, resolving state conflicts over it, etc.

Having studied the issue for a long time (and having previously received a grant to outline a similar [rubric for another form of social computing](https://learningproof.xyz/bags-of-URIs-all-the-way-down/)), I find a helpful way of organizing my thoughts is an evaluative "checklist".

1. **Portability at multiple layers**, not just users credibly exiting apps or swapping out infrastructural dependencies within one otherwise-invariant platform:
    A. *Apps and services* can also join or leave zero or more *platforms* (i.e., "userbases", moderation perimeters, literal or figurative jurisdictions) at any time and still use interoperable identifiers for their users
    B. Apps can add or subtract *integrations and infrastructure* over time, without trapping users or impeding their own exitability.
    C. Platforms can federate or defederate from one another at any time, fork or schism themselves, and enter or exit multiple protocols at any time
2. **Transparent platform governance** (at least of the identity layer)
    A. This includes *spam-protection* and *moderation*, but these two mechanisms have to be distinct (if not firewalled) to be credible
    B. *Platforms and sub-platform networks* need distinct governance, even if the stakes are lower.
3. **Transparent protocol governance**, ideally in public
    A. SDOs are good but not the silver bullet people expect, in my extensive first-hand professional experience. Community venues can make up for less transparency with more accessibility and participation and less expensive divisions of labor.
4. **Open-source and openly-governed APIs** break the architecture into layers that can be run by anyone, and ideally support competition at each layer.
    A. Competition keeps margins low; ideally, no part of the architecture can get so expensive to run that it becomes a chokepoint/tollroad to the rest of the system
    B. DIDs and PDSs in particular need to stay in the "commodity pricing" zone, which is one of the hardest things to ensure over time (see Bitcoin-based, or any mainnet-based DID methods priced out by their own upstream blockspace economics).

In the [next installment](../2026-03-19-a-decent-identity-part-2-praxis/), I'll apply this rubric in detail to Atproto and Activitypub and compare the two "report cards" to imagine productive collaborations and next steps worth investing in.

## Acknowledgements

Will be enumerated at the end of part 2.

## Endnotes

[^1]: [McNeil's Lurking](https://popfeed.social/book/9780374194338) is maybe my favorite but this essay is supposed to be about invisible economics so probably [Tim Wu's Attention Merchants](https://popfeed.social/book/9781524709242) would be more directly pertinent, or [Max Fisher's Chaos Machine](https://popfeed.social/book/9780316703314)
[^2]: See the reports from research agency [Ink & Switch](https://www.inkandswitch.com/), or the presentations from the Local First Conferences collected [on the Local First Conf youtube channel](https://www.youtube.com/@localfirstconf).
[^3]: See for a particularly succinct example chapter 1, "The end-to-end principle," in ["Design Principles for the ToIP Stack", 2021](https://trustoverip.org/wp-content/uploads/Design-Principles-for-the-ToIP-Stack-V1.0-2022-11-17.pdf)
[^4]: Delivered as an acceptance speech for an honorary degree at Universidad de Valladolid, Spain, 2001; [published](https://www.emerald.com/k/article-abstract/31/2/209/260241/What-is-cybernetics) in 2002.
[^5]: I didn't find it particularly useful for this essay, but people interested in a rough taxonomy of the software platform (beyond the simple binary of innovation platforms and transaction platforms, essentially hybridized out of usefulness by decades of antitrust underenforcement IMHO) are referred to chapter 3 of [The Business of Platforms: Strategy in the Age of Digital Competition, Innovation, and Power](https://popfeed.social/book/9780062973474) by Cusumano, Gawer, and Yoffie.