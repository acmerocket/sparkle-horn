# sparkle-horn

Working title for a project to support community and social media in the Burlesque community, to support managing and owning our own data.

Currently, this project is in initial research stages.

## Basic Approach

I would suggest:
1. Identify features
2. Research and select an open source package.
3. Deploy and configure.
4. Invite a board/admin/moderator staff. Get that in place.
5. Make public announcements and handle invites (with help of new moderators).

## General Features

Forums are seen as vastly superior to most social media.

They can be a difficult moderate.

Primary goal is to have a forum where the regional burlesque community (as in performers, producers, and techs) can discuss the scene/post casting calls, etc. Something to take the place of the Facebook groups we're using for it now. 

Slow expansion.

Don't want to monetize it, and the only ads should be posts from members advertising their own burlesque-adjacent services.

UI that can be configured by the end user (colors, layout, etc.)

possibly DM functionality

Public sections, account holder only sections, and then members-only sections within the account holder sections. Like:
* A costuming section of the forum might be publicly viewable to someone searching the internet for how to make a boa.
* A "what are the photography norms in your city" thread would be viewable only to people logged in with an account.
* The local-specific casting call group would be viewable only to logged in members who have been specifically invited to join it.

I definitely think I want it to be invite-only with vetting as we get it off the ground, just to make sure the people joining are actual performers.

## Initial Research

This is an info dump of initial reseach into open source projects that could meet the requirements. 

Columns are project name, open source URL, primary programing language and stars (as estimate for community size)

- discourse, https://github.com/discourse/discourse, ruby, 43k stars
- answer, https://github.com/apache/answer, go, 13k stars
- talkyard, https://github.com/debiki/talkyard, typescript, 1.7k stars
- forum, https://github.com/forem/forem, ruby, 22.1k stars
- vanilla, https://github.com/vanilla/vanilla, php, 2.9k stars
- phpbb, https://github.com/phpbb/phpbb, php, 1.9k stars
- simple machines forum, https://github.com/SimpleMachines/SMF, php, 610 stars
- mybb, https://github.com/mybb/mybb, php, 1.1k
- flarum, https://github.com/flarum, php, 15.5k stars
- mastodon, https://github.com/mastodon/mastodon, ruby, 47.5k
- humhub, https://github.com/humhub/humhub, php, 6.4k
- dolphin, https://github.com/boonex/dolphin.pro, php, 148
- anahita, https://github.com/anahitasocial/anahita, php, 441
- minds, https://github.com/Minds, php, 200

Social media servers:
- https://pixelfed.org/
- https://joinpeertube.org/, (source?)
- https://join-lemmy.org, https://github.com/LemmyNet
- https://element.io/, https://github.com/element-hq
- https://getaether.net/, https://github.com/aethereans/aether-app (like slack/discord)
- https://diasporafoundation.org/, https://github.com/diaspora/


## Distributed Social Media

My "engineer sense" says some form of federation is the best approach for a long-term solution, but it adds another layer of complexity and research: Which underlying framework?

https://gitlab.com/bluesky-community1/decentralized-ecosystem#ecosystem-overview

There is no easy answer, and though ActivityPub is most widely deployed (and standardized), it is also the most limiting when it comes to identity and moderation in the distributed arena. (see https://atproto.com/guides/faq#why-not-use-activitypub). I'm using the above ecosystem overview doc to figure out which will be most applicable to our needs.


Architecture models:
- centralized: a main server that hosts all data. easy to find. easy to maintain. single point of failure
- distributed: regional servers, cross-region sync and backup
- federated: everyone runs their own server. you run your own or select one.

Deployment Options:
- self-hosted: techie volunteer has access to reliable hardware, network and power, and can host the services in a professional manner.
- cloud-hosted: volunteers run open source software in the cloud, and manage all data.
- hosted: A specific company manages the account and all the data.


## Identity

In most social media systems, identity is managed and owned by the "server". In centralized and distributed models, that is all encapsulated behind the "dot com". In a federated system, that ID is managed by your local federated server. Perhaps you run your own for just you. In the Mastodon network, it's easy to have multiple IDs, one from each server you log into. There's no easy or standard way to associate them.

The Decentralized Identifier (DID) spec (https://www.w3.org/TR/did-core/) attempts to decouple the host server from user/account ID by providing IDs and authorizition information together, apart from the host.
> DIDs are URIs that associate a DID subject with a DID document allowing trustable interactions associated with that subject.

For end-users, supporting DIDs will allow them server-independant identity. Not "Sparkle Horn on FB" or "Sparkle Horn on Twitter" or "Sparkle Horn at gmail", but "Sparkle Horn on any system that supports the distributed-ID specification." For server moderators, it also means being able to ban "Sparkle Horn on any system that supports the distributed-ID specification."

Noting that for this reason, basing a platform on the [AT protocol](https://atproto.com) is probably the most flexible and forward looking. This is the same protocol BlueSky uses, and will support direct interoperability.
