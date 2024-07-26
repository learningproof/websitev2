---
title: "ActivityPub and Newsrooms: Thinking Past Platforms"
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
description: "What should digital editors and news outlets know about the social media landscape post-Twitter?"
excerpt: "The technical and architectural tradeoffs along the spectrum from 'self-hosted' social to mega platforms, and the orthogonal question of AP as an open data language."
image: /assets/images/sous_les_pavés,_la_plage.jpeg
defaults:
  # _posts
  - scope:
      path: ""
    values:
---

## The Great Exodus That Wasn't

After Elon Musk raised profane amounts of capital to buy Twitter by appealing to [Saudi](https://www.aljazeera.com/news/2022/10/28/saudis-kingdom-holding-company-to-maintain-twitter-stake) and [Silicon Valley](https://www.techdirt.com/2022/10/05/elon-musks-texts-suggest-way-more-people-in-the-silicon-valley-elite-should-have-imposter-syndrome/) resentment of the current management of the world's first and last open newswire, digital editors and news outlet management worldwide were, understandably, _shook_.
The Wall Street Journal reported Ralph Ellison's rationale for investing a billion (give or take whatever Elon saw fit) as follows:
"It’s a real-time news service, and there’s nothing really like it,” he told me. “If you agree it’s important for a democracy, then I thought it was worth making an investment in it."
([Src](https://www.wsj.com/tech/elon-musk-twitter-x-takeover-walter-isaacson-5f553fa))
News outlets and individual byline-holders alike had evolved whole technological toolkits, middleware markets, and career trajectories around the Twitter platform over more than a decade before these sudden changes, and in large part it can be speculated that it was exactly this symbiosis between news and the Twitter platform that the bulk of Musk's financial backers wanted to disrupt and rebuild differently.

In the almost two years since, the Great Exodus many were expecting never quite happened: while Twitter's centrality to news is indisputably diminished, the landscape has gotten more and more fragmented rather than swinging markedly towards a new center of gravity.
Just as no "winner" has yet emerged, neither has a paradigm shift yet definitively occured towards decentralized and/or federated models, although both seem to be steadily gaining ground and on track to terraforming that landscape by the end of the decade.
Perhaps two years is an unrealistically short time to expect such results, and the balance of power between the Empires of Network Effects and Modes of Content Production should be studied on a more glacial and geopolitical time-scale.

In the meantime, however, news outlets need to be planning their next moves and the long-term direction they want to be headed, juggling engagement today against dependency tomorrow, and weighing a "more direct" relationship to readers that they own monetize directly against paying "the reach tax" to be visible where their readers are already looking.

> The purpose of this essay is to explain (hopefully not in too pedanty, eye-blurring detail) the technical and architectural tradeoffs in every option on the spectrum from "self-hosted" social to mega platforms, and hopefully to trouble that linear mental model a bit by introducing the open-data publication as orthogonal to more winner-take-all "attention economics".

We can start by looking at some interesting data from the American Press Institute, which shared with the [Online News Association in February 2023](https://journalists.org/resources/beyond-twitter-and-meta-whats-next-for-social-media/) the results of a survey they conducted while the topic was still front-of-mind for online editors everywhere:

![a pie chart from the American Press Institute's post-twitter migration survey, feb-2023, showing where news outlets are focusing their attention primarily as a portion of those deprioritizing twitter](/assets/images/american-press-institute--post-twitter-migration-survey--feb-2023.png)

For me, the main takeaway is not that for almost half of the parties surveyed, a Meta property (Instagram or Big Blue) was the next-best thing to Twitter and its closest replacement.
Nor was it surprising, at the time or in retrospect, that Mastadon [sic] hardly registers, given that news is a mass-market phenomenom driven by big numbers, big data, and advertising.

The main takeaway is that _until_ this crisis, Twitter was so useful for so many different kind of news outlets, each of which now splinters off into a different platform depending on what audience it primarily strives to cultivate.
Twitter could be the "public option" (outperforming and outrunning the more tailored "News" platform products that Apple and Google tried to make for penning news outlets into a closer feedback loop with advertising and discovery) exactly because it was both a "social media website" (in the sense of an account-based identity system) AND a kind of global data lake or information substrate, which Twitter's management leaned into for years before becoming a "democratized news wire".

## What We Lose When We Lose Twitter

Over the years that Twitter was ossifying into something like critical infrastructure for information distribution, it achieved a kind of invisibility and was taken for granted in ways that few commentators outside politics and news really recognized.
A "tweet" became a kind of low-level primitive for the web, so low-level that it can be hard to even remember this evolution or name the attention pathways and copycat UXs it created.
Tweets beat out "Facebook posts", "Reels", "Carousels", "tumblr threads," "[Medium] blog posts", "subreddits", and all the other atomic units of social media for mindshare exactly because it was easier to think of them as units of "content" divorced from their static, mostly unchanging presentation on the website.
Tweets were made for screengrabbing and linking-to, rather than for bringing you into a walled garden, much less an authenticated one.

![tumblr thread bemoaning the portion of internet usage devoted to cross-platform screengrabs](/assets/images/screengrab_internet.jpg)

In economic terms, I would argue that `twitter.com` (the website for reading, writing, updating and deleting tweets) was not even the most valuable asset bought by Musk, even if he's proven himself not to see it that way.
Instead, I would posit that the longevity and the data language of the huge corpus of tweets is both why Twitter was neutral enough to be plumbing for news, and what truly made it valuable (if difficult to monetize).
I believe Twitter was and still is a data and informational substrate in ways that no other "social media" has yet become in large part because it provided a "mode of publishing" that took root and became part of the furniture, eclipsing the mere internet "real estate" of `twitter.com` where people went for decades to do that kind of publishing.
Just as broadcast radio and television created the concept of the "soundbyte" which survives as a kind of UX primitive intuitive even for generations that need "broadcast" explained to them by a historian.
In this sense, we need to consider the difference between a tactical and a strategic "replacement for Twitter", in the sense that _tactically_ news outlets need to engage their readership today and build revenue around that relationship yesterday.

In the long term, however, news outlets _also_ need to make a strategic bet on "where" the most, best "tweet"-like things (at least in the eyes of their readership) will be ten years from now, what the "heir" to Twitter will be.
Or more precisely than "where", we might ask in what giant corpus and in what data model these gajillions of grains of content-sand will form giant dunes worth mining and sifting and navigating.
I think it is misleading to think in terms of "monthly active users" and growth charts-- these are the [metrics of commercial platforms and products](https://arxiv.org/html/2309.12613v2) ([alt link](https://www.researchgate.net/publication/381064386_Exploring_Platform_Migration_Patterns_between_Twitter_and_Mastodon_A_User_Behavior_Study)).
While "user metrics" and attention as conventionally measured are a crucial part of what drives and sustains engagement on the competing commercial platforms _generating_ their respective content data lakes, thinking about the long-term health of news (and of the internet itself) requires us to think past (and below) platforms, or at least to look orthogonally at their informational runoff, which in large enough quantities becomes its own center of gravity and takes on a life of its own.

## The Cowpath Beneath the Platform

In the vernacular of today's youths, who grew up swimming in the waters of commercial social media, Twitter is the lightest-weight, easiest-abandoned, most novice-friendly way of establishing a "presence online."
Twitter accounts can be earnest publishers, sincere consumers who want to respond in good faith on the threads of others, invisible lurkers who train an algorithm to surface the content they want to consume without a single tweet in years, or insincere trolls and spambots who are at cross-purposes with the OPs of every thread they post to; but in any of these cases, an account is a kind of micro-ledger of events published into an extremely public and searchable corpus.
To create a Twitter account is to hang a shingle, knowing that you will be easy for others to "find" only in proportion to how much engagement you garner from everyone else.
Twitter was engineered for decades to be coextensive with "the web" rather than to be a platform with a perimeter around it, giving some sense of semi-public obscurity or even private-mode occlusion, a feature which Meta properties made table-stakes for more properly "social" media over a decade ago.

By comparison, a typical [young] user today doesn't feel like they are signing up for a web presence directly on any social media website:

* creating a Reddit (or Lemmy) account feels like signing up for a debate club, or some kind of academic senate where the marketplace of ideas is tediusly voted up and down.
* creating an Instagram account feels like hiring a brand manager whose first piece of advice is to take out an ad in a fashion magazine
* creating a Facebook account feels like taking out a halfpage ad in a [Gannett-owned] smalltown local newspaper.
* creating a Tumblr account (in 2024) feels like getting a booth at an anarchist zine fest-- public, but not visible or mainstream in any sense.
* creating a Github account or a LinkedIn account feels like getting an Employer Identification Number from the IRS, or buying an Amazon Ring, the footage from which can be analyzed by any future employer and its various machine-learning products.

Partly my argument here is a bit of a sleight of hand, because the comparison of Twitter to "properly" social-media platforms is a bit of a category error, since Twitter is at least as much a publication platform as a "social" one.
In this sense, it could be argued that it actually outlived its real competition: Google Reader, user-friendly general-purpose RSS clients, and the mythic webring salad days of the pre-corporate web from which spawned the neologism of the "[we]blog" in the first place.
Squinting a little, we could call Twitter the freemium-model, lightweight, toy version of a more customizable "content management system" like WordPress, which is one of the oldest pillars of the modern web, [powering 40% of it and counting](https://wordpress.org/40-percent-of-web/).

![dashare.zone meme about bringing back RSS and blogs](/assets/images/dashare.zone--rss-and-blogs.png)

Here the most salient aspect of Twitter from the perspective of news is its "democratizing" horizontality, by which casual readers, loyal subscribers, individual by-line reporters, their reply-guys, desks or beats, and whole newspapers all stand on equal footing before the algorithm and moderation policies.
(Well, almost equal, modulo those pesky color-coded stars that have iterated so quickly as to lose all meaning since Musk started moving fast and breaking everything.)
This radical horizontality is a pretty hard illusion to pull off, of course.
The trick to pre-Musk Twitter was a massive and expensive armature of complementary sorting mechanisms:
algorithmic surfacing, search, moderation, and blocking/hiding unwanted or low-quality content creates a usable ocean of content to swim in for all user-classes, obfuscating the exceptions to its seeming horizontality and neutrality.
Making one giant comments section for everyone's micropublications definitely inherits the massively expensive liability of all social media, in that it is  made of humans, so if you want anyone to want to spend much time in your little corner of it, you'll have to hide a few of them.

Twitter could be thought of as the simplest-possible, most syndicatable, portable, dumbest-possible data model for publishing, and thus the hardest to kill, the cockroach of CMSs for powering a different 2-digit percentage of "the web" than WordPress manages (measured in individual humans rather than in domain names, that is.)

## Servers and Sources of Truth

Which brings us to another low-level building block of the web so basic as to be invisible to people who live and breathe it at least once in almost every waking hour of their day:
the ICANN worldview.
By this, I mean the almost universal impulse (up and down the spectrum from industry insiders to the most casual of web users) to think of each domain apex as a "real address" on the internet, and every other kind of actor or identity on the web as a mere tenant renting or otherwise borrowing "space on the web" from one.

This 1:1 mapping of "real addresses" to legal persons (and the occasional hobbyist nerd) is so foundational to the entire web (since at least the dawn of O'Reilly's "Web 2.0") it can be hard to even think outside of it.
In the meme above about an internet comprised entirely of screengrabs cross-posted between "four websites," we see how these platforms (and the "websites" mapping to them 1:1) jockey for a kind of mindshare olympics.
This axiomatic approach to web identity has been entrenched further and further in tandem with the dominant mode of web economics (governed by the extended metaphor of "properties" on a Monopoly board and users as tenants).

The economic model this identity paradigm creates is extremely winner-take-all, since how many humans visit or are familiar with a domain apex per month is a pretty good metric for how much mindshare it has in the human world in general.
This ICANN-refereed competition for eyeballs has reigned since Silicon Valley started pumping money into this kind of winner-take-all brand warfare decades ago, evolving hand-in-hand with a progressively more domain-bound security, privacy, and integrity model for the modern browser.
We could think of the "Web 2.0 cycle" (roughly mid 2000's to mid 2010's) as a protracted competition between "individual websites" struggling to own and build engagement on their small plot of land and megaplatforms housed under a single web domain which aggreggate and synthesize vast amounts of engagement into data-brokerage empires.
It feels like a cycle that came to a close because the latter won a pyrrhic victory, assuming such an outsized role in the economics of the web that the seemingly infinite growth slowed and the scale of its externalities and liabilities caught up to it.
What's more, these mega "websites" are increasingly beset by escalating anti-trust challenges and massive liabilities that their economies of scale increasingly struggle to outrun (not least of which are the political and ethical concerns around moderating all that enduser-generated content).

Coming back to news outlets, we could think of the debate over whether to be a website or an account on "someone else's website" has evolved and transformed so many times over the last 3 decades, and for a brief period the distinction seemed moot as even websites were fundamentally accounts in advertising empires anyways.
But the pendulum is swinging back a bit, as regulator dreams and enduser desires alike seem to be pointing towards more domain apexes and more local or bottoms-up control web-wide in the coming years.
Like any other attention business, news outlets nowadays juggle what portion of their budget and worker-hours to devote to each platform and what portion to spend on feedback loops and monetize systems they can more directly control.
And this calculus is changing fast, for a number of reasons.

Fundamentally, the platforms are retreating from an earlier position of self-centering, pushing various liabilities (from censorship to moderation to misinformation to AI-generated spam) back onto "local jurisdictions" and property management companies and individual owners of managed properties.
As "artificial" "intelligence" floods any less-than-perfectly bot-proofed and sybil-proofed mass communications channel with noxious chum and vapid arguments between formalism-spewing summary-bots, the economies of scale whereby a billion humans can share one "website" with 2 billion, rather than 2 thousand, bots breaks down completely.
Our introductory deal is over, and suddenly, no one wants to be in the "source of truth" domain apex business.

![tweet showcasing a particularly noxious piece of generative AI chum-art, namely a cute east asian baby in a police uniform clutching a gilded crucifix waste-high in flood waters](/assets/images/top-shelf-generative-ai-chum.jpg)

In a way, Twitter was the last platform of its size that could credibly claim to be neutral enough _not_ to feel like "someone else's website," a for-profit global mega-platform that didn't feel like one until its hostile take-over under new management.
But now the music has stopped and we have to wonder: which elements of that now historically-impossible bundle matter most?
Pick carefully, especially if you're bringing home any or all of the "social" functions previously hosted in the communications chicken farms of yesterday.

## Each Server a Variously-Unbundled Microduchy

In the American Press Institute poll above, many news outlets described their journey to build close-knit communities on "their own servers."
The presentation limited itself to only the two most popular forms that self-serving took in 2023: Discord servers and Mastodon servers.

![screengrab from API slide describing discord and mastodon server-selection friction for user engagement](/assets/images/american-press-institute--discord-and-mastodon--feb-2023.png)

I will leave Discord aside for the rest of my argument because I feel strongly that a different, more show-stopping category error pushes them (and Slack) squarely out of scope.
Not only are their data formats proprietary and their code closed-source, but furthermore their commercialization strategy increasingly evinces symptoms of the same [shareholder-value-driven enshittification vectors](https://blog.erlend.sh/communal-bonfires) slashing and burning Reddit and Slack.
More importantly, unlike their "open-core" competitor Discourse, each server in Discord or Slack is not _public_ in the literal sense of published to the open, unauthenticated internet, nor _public_ in the data-engineering sense of publishing in an easy-consumable, standardized, public data language.

Mastodon, on the other hand, is something like a reluctant platform, or a "locked-open platform" in the most generous of readings, in that it has exactly the opposite characteristics:
the data language in which each Mastodon server encodes all its human activities and publication events is basically ActivityPub, a 5-year-old standard designed in the open at the worldwide consortium, even if Mastodon is a bit of a dialect of that standard with some quirks that take a little translation to overcome when merging it into datasets of more conformant ActivityPub records.
Furthermore, the default (and most robust) configuration of Mastodon is for Twitter-like publication readable by unauthenticated users.
This makes sense considering that Mastodon's initial mission, before its data language was even standardized by "averaging" it with two other locked-open social projects to create ActivityPub, was to clone Twitter after Twitter closed off its API and "locked down" its servers to only be accessible from twitter's own website and mobile clients.

You could say Mastodon rewound history to the point at which Twitter started consolidating power in its website and instead chose to consolidate power at the "Subreddit level", splintering the network into thousands of servers that each design and enforce (and shoulder hte liabilities of) their own trust and safety systems.
They also opt into and out of federation with other servers in a completely patchwork and often gossip-based or probabilistic method, as researching those thousands of yes/no decisions and maintaining them over time would be an infinite resource quagmire.
Bundling so much of the human and social (and compliance) dimensions of "running a website" at the level of the server leads to an odd kinds of subsidiarity politics, and makes the major bottleneck to reach an impossible to control or predict compliance with the speech policies and etiquettes of thousands of house parties.
All the credit imaginable for the work of groups like [iftas.org](https://iftas.org) for trying to establish more scalable norms, but it's slow work retrofitting standards and norms onto the deliberately heterogeneous patchwork of today's Mastodon fediverse.

There is another major difference between Mastodon and Twitter, however, and this is painfully apparent in the world of news professionals that have honed their craft to optimize algorithmically-boosted reach:
Mastodon does not have an algorithm, or a particularly useful "global" search (across all Mastodon servers, or even across all servers connected to a given server directly or indirectly).
Global reach and global search were specifically **not** design goals of Mastodon; being searchable requires a double opt-in (by server management AND by each user), and the Mastodon developer community has been hostile even to "aftermarket" application of algorithmic feed-sorting to the Mastodon server stack.
So while algorithms and more powerful global search over a substrate of ActivityPub data from many Mastodon and non-Mastodon servers is entirely _possible_ using non-Mastodon ActivityPub software... that hypothetical software isn't really available in production today on any server that a newsroom could just install and host at its own `social.` subdomain.

## Sidebar: The Alternate Fediverse of BlueSky

Contrast all of the above with BlueSky, which is [so far] [pre-enshittification](https://doctorow.medium.com/https-pluralistic-net-2024-04-04-teach-me-how-to-shruggie-kagi-caaa88c221f2) and at least in the medium-term credibly friendly towards federated services and forks of its server code.
It has even promised to federate using its [own federation protocol](https://bsky.social/about/blog/5-5-2023-federation-architecture) that [deliberately reinvents much of ActivityPub](https://atproto.com/guides/faq#why-not-use-activitypub), making it a kind of alternate-fediverse on simplified rails it doesn't yet share with anyone.
This "federation" is in its early days and thus almost as hypothetical as a Fediverse-wide global search or reach guarantees enforceable enough for news outlet usage.
While 2024 has seen considerable growth in alternate _clients_ (with some innovation at the "AppView" level!), BlueSky's identity servers and relay servers are still effectively the only members of their federation.
A space _has_ at least been deliberately and publicly carved out for future alternate AppViews and independent Relay firehoses, although the economics of how long they take to develop remain to be seen.
Until newsrooms can self-host "ATProtocol"-powered `social.` websites that they fully control and federate to the bsky network, their options are still basically to have an account in the bsky network with credible promises of future portability, or stand up a Mastodon, or use some other kind of ActivityPub software to manage its content, and the users it hosts.
It's worth noting that self-hosted or Discord-hosted but self-managed "social servers" enable configurable special privileges for the "internal users" it hosts, a promising prospect for the cultivation of loyal subscribers and "powerusers" driving monetization.

In many ways BlueSky today feels (to a non-journalistic user) like the closest replication of pre-platform, pre-open-API Twitter.
It even has a UX and a userbase that both feel like Twitter's did _before_ it become a general-purpose information pipeline far-reaching enough and useful enough to double as a newswire and free `academia.edu`.
Honestly, newsrooms could be forgiven for "waiting and seeing" how things develop differently the second time around, with a novel and minimalist federation protocol and open-graph data language:
it genuinely could turn out to be the best of all worlds, or the best rearrangement of the elements that Twitter evolved (largely on accident) in a different sequence.
But tactically, anyone migrating from Twitter to BlueSky in 2024 feels like they are accepting a major loss in reach, almost as major as moving to a self-hosted Mastodon, so it really is a choice between two different orders of operations, two different reshufflings of the Twitter playbook being run again in a new landscape.

## Having Your Picks and Shovels and Eating Them, Too

There's even more rabbitholes to go down, for the news outlet manager looking to really exhaust this open wound of a research question.
There's an entire garden of forking techdebts that we call the Fediverse, which are variously accessible to the user of Mastodon (or Threads), and variously functional.

Today's Fediverse is a vast, unfinished Linux of networks that mostly interoperate and mostly "work" in the way that Linux distributions "work", i.e. not at all, at least by the standards of the mainstream consumer used to what Apple and Amazon call "just working".
Mastodon (the platform) is actually very distinct from ActivityPub (the data language), which means that while users of one Mastodon server can "follow" and interact with users on any other Mastodon-compatible server, they can also follow (with variously degraded service and a subset of supported features working as expected) RSS-like content streams from elsewhere in the ActivityPub universe.

In the "full Mastodon API support" category we find Zuckerberg's newest property, [Threads.net](https://threads.net).
Its top-level domain (`.net`) is a subtle nod to the humbler, more utility-like aspirations of Meta's "public option" and, realistically, the most viable Twitter replacement in 2024, at least from the perspective of news outlets looking for maximum reach, minimum risk, and a realistic chance of a "self-hosting option" that can be smoothing upgraded to and downgraded back from.
(I think that if the American Press Institute ran the same survey today, Threads would take a 2-digit percentage of the pie chart, but that's just my ignorant and tendentious speculation.)
Threads may not be as wild or organic as BlueSky, or as addictive or libidinal as Instagram, but that's OK, it's not trying to be;

I suspect it's not even trying to be _profitable_, really, or glamorous, or addictive, or innovative in the conventional sense, except insofar as driving hard into the center of the chessboard and being a no-frills loss-leader public option innovates by stretching the definition of social media.
It may not be immediately obvious what's so innovative about this, but one [intriguing reading of this business-model innovation](https://www.fromjason.xyz/p/notebook/copy-acquire-kill-how-meta-could-pull-off-the-most-extraordinary-pivot-in-tech-history/) posits that as federating with Threads becomes more and more valuable and attractive to the scrappy, bootstrapped, self-hosted servers of the grassroots Fediverse, Threads, Meta, or some cottage industry paying Meta for the privilege could turn around and sell moderation and compliance with Threads' high standards as a commodity per-user or per-post service.

Coming back to the forward-looking newsroom manager, I would argue that Threads deserves a second look NOT because of its size, its reach, its capitalization, or its market share but its ambitious gambit to reinvent the game and strike a new admixture of silo and open platform.
Threads is running a different race than it appears to be:
it is trying to beat BlueSky and Mastodon and LinkedIn not to profitability or to critical mass or even to centrality, but to _utility_, or to put a finer point on it, beat them at becoming _an informational utility_, infrastructure as invisible as golden-age Twitter was and Instagram and Big Blug both failed to be for all their overt `.com` producty-ness.
A huge part of this is that unlike Mastodon, it brings world-class global indexing and search and algorithm expertise that it is transfering over to a broader, federated data plane of Threads + Mastodon + GoToSocial (an independent re-implementation of the Mastodon-API), and hopefully soon many more ActivityPub flavors further from the Mastodon API center of power.
Embracing federation this openly means taking the hit of enforcing its quality, brand safety, moderation, and compliance norms on content generated by users it doesn't even serve at the point of federation firehose, which (in business terms) is kind of wildly innovative and novel for a company not known for adopting open standards, open networks, and even a [theoretically portable](https://codeberg.org/fediverse/fep/src/commit/997bc7ee1a31c279f3de8bd7dee4a21c3909ab4b/fep/7952/fep-7952.md), open social graph.
(Or perhaps armchair pundits like myself give Meta so little credit on the open standards front only because Facebook never publicly commented on its earlier attempt to corral friendly competitors to [embrace an earlier version of the ActivityPub federation standard in 2008-2009](https://archive.org/details/26-10-00_-_15th_anniversary_of_web_3.0_social.qt) before walking away from the idea.)

One particularly user-hostile feature of the Fediverse's radically decentralized, data-first federation to date is that on the level of end-user experience, users have no guarantee when they see a link on their "home server" pointing to, say, `unfamiliar.social` or `@someguy@bumblefudge.com` whether it will be a Mastodon link, a non-Mastodon ActivityPub link, or a third unknown thing.
To my knowledge no ActivityPub software to date has sorted the namespace of HTTPS URLs into degrees of AP parseability or conformance and surfaced that to the end-user as a different-colored link or other cue that any link might take them partly or fully out of the fediverse and onto the old silo-web.
Something I love about the Threads product is that it brings these kinds of user expectations to the forefront of discussion and makes them table-stakes of federation with the biggest body of users, incentivizing upgrades to the system and making a Meta-verse within the Fediverse (itself named satirically during the golden age of Zuckerberg's earlier rebrand).
To put it another way, Threads `.net` is emphatically trying to put the web back in Web

![screengrab of two bluesky early adopters discussing network effects and reach gains if bluesky federated to threads](/assets/images/underwood_and_niedermeyer_discuss_federating_bluesky_to_threads.png)

Newsrooms should consider Threads an interesting alternative to Bluesky, Instagram, or Mastodon, since it kind of straddles the line between Instagram and Mastodon.
What's more, it gives partial access to readers on both Instagram and Mastodon in different ways, and who knows, maybe some day it'll even partially have touchpoints or bridges with BlueSky as well, or some other networks?

## Oops I Forgot To Mention Another Big Chunk of the Fediverse

Earlier, I mentioned in passing a broader Fediverse that eschews or ignores the Mastodon API, with its sometimes tendentious interpretation of the ActivityPub data language that bends it to the needs of its inward-facing UX goals.
(In Mastodon's defense, it has naturally spent the last many years prioritizing the user experience of its loyal and loud users over an academic interoperability with a smaller userbase in the non-Mastodon fediverse, primarily comprised of its exiles and ex-users until Threads came along to legitimate many of its choices.)
Threads has, for the time being, something like 90% of the "active users" of the Fediverse, and before it joined, Mastodon-compatible servers had somewhere around 70 or 90%, but the remaining "rest of the Fediverse" is actually quite significant, growing rapidly and quite important to consider separately for many reasons.

One growing "neighborhood" of the Fediverse today is the so-called "Threadiverse" (no relationship to Threads!) which takes the basic shape of Reddit (link aggregation with upvote/downvote-sorted comments sections).
As Reddit has enshittified, [pivoting hard into stakeholder value at the expense of its previously autonomous communities](https://www.cjr.org/the_media_today/reddit_api_moderators.php) and [haggling hardballing with search engines for their valuable datasets](https://www.404media.co/google-is-the-only-search-engine-that-works-on-reddit-now-thanks-to-ai-deal/), a much larger exodus of users (particularly the most value-generating power-users, moderators, and daily posters) has created a massive population of exiles looking for their fix of a UX they were addicted to for years.
These exiles are increasingly finding homes, and many veteran subreddit moderators even pay out-of-pocket to stand up their own indie Reddit-clone servers... federated to those of other ex-moderators, a DIY replacement for a previously robust and deeply-entrenched community.
Like Mastodon, these clones trade independence and self-governance for the burden of self-hosting, plus a weaker form of "global" search, closer in essence to a search of "this server and the ones it swaps data with."
Also like Mastodon, these sites ([Lemmy](https://join-lemmy.org/), [kbin](https://www.reddit.com/r/KbinMigration/comments/14fm33o/recommended_kbin_instances_to_join/), and now [NodeBB](https://nodebb.org/showcase/development-communities-in-nodebb/)) enable patchworks of servers that run their own (customizable, often invite-only) user systems and moderation policies to cross-publish, cross-comment, and generally share data and users, owning their own infrastructure but still participating in a broader data lake of upvotes and downvotes and threads.
(A fun detail for the data nerds is that since servers and federations are fragile and sometimes fleeting, they've had to elaborate their own resilience mechanisms for displaying cross-server threads that survives server deaths and defederations, a fun distributed-systems UX problem to ponder!)

While the Fediverse heirs to Reddit might be less directly interesting to news outlets than other Fediverse form-factors and "neighborhoods", it is worth noting that unlike the original Reddit, there is a built-in upgrade path by which the Fediverse Reddit threads can be read, followed, and participated in _from_ a non-Threadiverse Fediverse application willing to do extra work displaying it properly and/or separately.
The neighborhoods can be as distinct or as merged as individual servers and clients choose to make them over time, because the underlying commonality of data records they generate and share makes the translation and interpretation issues relatively manageable.
You could think of Mastodon and Threads as distinct platforms joined at the hip, with slightly different features and governances, but almost completely interchangeable data flowing through the pipes; 
the same could could be said about Lemmy and kbin, and a little bit of fancy plumbing could federate the two federations since it's all ActivityPub data modulo their per-use-case extensions.
In this sense, while very few news outlets will be _standing up their own_ Lemmy instance any time soon, there is a very real sense in which case the health of Lemmy and kbin's community contributes to the health of Mastodon's and Threads' network effects as a kind of indirect ally and user-sharing agreement.

## Oops I Have Even More Fediverses To Explain

Even further afield, and probably much more relevant to news outlets thinking on a longer timeline, are three platform giants on the horizon, incrementally lumbering towards Fediverse interoperability as fast as you can expect three extremely complex codebases to move without breaking anything vital for their millions of users. 
These are:

1. [Discourse](https://discourse.org), the open-source, self-hostable, and enterprise-hostable forum software that powers a huge chunk of the subject-matter-specific Knowledge Bases of the world, is [quite far along in rolling out ActivityPub support](https://meta.discourse.org/t/activitypub-plugin/266794) for any Discourse user that wants it.(Fun fact, ActivityPub developers use an [ActivityPub-enabled Discourse server](https://socialhub.activitypub.rocks/) every day to debate protocol improvements and UX ideas, and some day [Ethereum developers](https://ethereum-magicians.org/) might as well.)
2. [Wordpress](https://wordpress.org/), the most widely used and load-bearing Content Management System in history, is rolling out support to make any WordPress "followable" from any ActivityPub client, and working out ways to even make ActivityPub-powered federated [comments sections](https://bora.uib.no/bora-xmlui/bitstream/handle/11250/3097698/drthesis_2023_knustad.pdf?sequence=2&isAllowed=y) for blog-style sites, one of the [original goals of the standard dating back to 2010](https://www.w3.org/2005/Incubator/federatedsocialweb/wiki/SWAT0).
3. Similarly open-source (or at least, Community-Edition, for the nitpickers) and self-hostable [Gitlab](), which has long beaten Microsoft-owned GitHub in just about every category except visibility, social-media-like network effects, and freetier subsidies, might finally see some progress on at least one of those categories by enabling [ActivityPub](https://docs.gitlab.com/ee/development/activitypub/), making repositories or packages followable actors for people that want to be notified about (and comment on) binary publication events. (Note that the even more indie option, [Forgejo](https://forgejo.org/) is also [working on ActivityPub support](https://codeberg.org/forgejo/forgejo#what-does-forgejo-offer), which of course opens up the possibility of a whole Gitiverse as well, or maybe Forgeiverse?)

## An Actual Everything App, or even an Embarassment of Everything Apps

One of the most esoteric aspects of ActivityPub as a data standard and minimalist messaging protocol that I have only hinted at until now is that ActivityPub isn't, at its lowest level, anything like a Social Media application or even a general-purpose language for building diverse social applications.
It's actually something far more generic: a messaging protocol somewhere between e-mail and RSS ([RDF Site Summary](https://www.oreilly.com/library/view/web-design-in/0596009879/ch07s08s02.html)), which despite a somewhat fumbled standardization history is still very load-bearing after all these decades since it's the basic mechanism by which podcasts publish new episodes and podcast readers can interchangeably subscribe to them.

This means that while Twitter-clone Fediverse and Reddit-clone Fediverse and Git-collaboration Fediverse and Wordpress Blogiverse can all support tailored apps, it's also technically imaginable that someone might just use a hypothetical "Threads suite" to access _all of the above_ without leaving their Instagram/Facebook account.
If that sounds too dystopian for you to stomach, think of how many email apps you can use for how many email accounts, and still have the basic concept of "emails" amassed in interoperable archive formats, but for... every other kind of social interaction and message and subscription and the like.

This radical commonality of underlying formats means that not just one Everything App but many Almost Everything apps will probably coexist for the foreseeable future.
The open-data substrate of ActivityPub data (or, for that matter, Lexicon data, the BlueSky equivalent) can be thought of as an Everything-layer for publication, and instead of a zero-sum game to control and monetize it, applications would have to compete on comparative utility to take any subset of that everything and any subset of the shared userbase;
business will continue as before and even adveritising, but at least the data and the attention-graph of each account (if not the social graph properly speaking) can stay locked open.
Or, hippie dream to end all hippie dreams, the pendulum could swing even a little bit in the other direction, and the web as we know it might just get a bit less consolidated, less corporate, and less advertising-driven.

![screengrab of james woglom teasing bluesky's founding engineer for an accidental elonism on bluesky](/assets/images/jwoglom.com__x,_the_everything_app.png)

It might be too big for one Everything App, too big for even a hundred Major Global Websites and App-store monopolies to extract even half the value of.
The arc of economic history might actually bend meaningfully towards decentralization, of the kind that actually benefits the information businesses.
The entire web might actually be a news wire, instead of a competition for attention-captivity ponzis.
In such an economy, information businesses can stick to their core competencies and worry less about this or that platform's algorithms and this or that platform's reach-buying economics.
They can just communicate more directly with their readers (did you notice how many news outlets were prioritizing SMS post-twitter in the API poll?), or more precisely, outlets and reporters can just deliver straight to the inbox of readers with complicated, robust combinations of clients and servers will be sorting, triaging, and managing that complex manifold inbox.
(In an alternate, better universe, our email inboxes might have been just as co-managed, instead of consolidating to a world with barely any competition for gmail and company-emails, but that's a subject for another, even longer essay perhaps.)

## The Beach Beneath the Pavement

In a way, the basic premise of Mastodon and Lemmy and other self-organizing, bottoms-up configurations of autonomous and omnipotent "servers" arrived almost 10 years too soon to be viable economically, and got mistaken for dead-ends due to just how inclement that climate was for them.
It sounded like a 1968 hippie fever-dream, in the cynical 2010s, to standardize _in advance_ a data language that would be the bedrock information-plumbing layer of multiple open platforms on which multiple future products would have to find their way to market, committed in advance to an open graph of public data in common.
In the golden age of platforms that were also websites, that were also data languages, that were also horders of closed social graphs, locking open and sharing even _one_ of those four layers was a hard sell and an uphill slog!
Decoupling all four to be independent layers of a stack that had to somehow cooperate to compete with the hyper-monetized Goliaths of the day was, even more than federating or sharing the "crude oil" of social data was unthinkable back then.

But now, as giant websites are incurring giant liabilities and disappointing their once delighted end-users and their general counsels alike, it's not looking so impossible to federate and share utility costs.
Calls to commoditize user-management and share infrastructure with grassroots, self-funded community infrastructure is coming from the most surprising corners of Silicon Valley these days, for the strangest of reasons (sadly none of which have to do with appeasing the FCC).
Even if advertising is still as oligopolous and mediated as ever, at least their _engagement operations_ are loosening their grip on the readers of media and gradually disintermediating themselves from the telemetry-obsessed, silo-filling marching orders that made them so unpopular with regulators for decades.
The Goliaths of yesteryear are suddenly all too eager to decenter themselves, if not completely disband the layers of their monopolies into distinct legal entities that orchestrate totally different platform economics where once they operated in lockstop.
The primitive accumulation and vertical monopoly phase is over, and this is great news for journalism and information businesses generally regardless of how uncertain the next ten years will be.

![Photo of Paris 1968 street scene with graffiti that reads, "Sous les pavés, la plage](/assets/images/sous_les_pavés,_la_plage.jpeg)

It's terrifying, at least tactically, to face a power vacuum, but it's also great news that a generational hegemony is just running out of steam and giving up.
A new age is dawning in which it will be increasingly less profitable (and bankable) to fence and horde network effects and information flows.
Say what you will about ActivityPub as a global data language, and I am the first to admit it is a wonky Frankenstein of a standard today, it is at least a workable Esperanto, and a lot easier to hold my nose and work with than a global [data] empire of [California accents](https://www.theguardian.com/books/2023/may/10/palo-alto-book-malcom-harris-interview) on which the sun never sets.
The W3C has certainly shipped worse.

I don't even worry about whether BlueSky will be more succesful sooner by federating those 4 layers in a different order, or by inventing its own streamlined data language, because either way the end result is immensely better than status quo, in that whichever federation protocol wins, [we win](https://berjon.com/user-agency/) as end-users.
Either way, the economics of information pipelines shift in a better direction, with more regulable and accountable utilities ("firehoses" and "clearinghouses" and "archival nodes") replacing today's vertically-consolidated Standard Oils of social data.
Everyone can only stand to benefit from that: today's vertical monopolies are holding our grandmothers' inboxes, our local newspapers' loyal readers, everyone student and voter's primary and secondary sources, and our baby pictures hostage.
However federation proceeds, it's a kind of de-growth and antitrust bonanza, loosening the strangehold hyper-consolidated advertising had up and down the value chain of information industries.

And I'm fucking pumped, dear reader, even if I'm a little scared I won't have a few American companies to blame for every outbreak of misinformation or every election obvious swung by some targeted filter-bubble ad-spend.
It's the only future in which I still want to have a computer or a smartphone, really.