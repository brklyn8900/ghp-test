---
kip: 1
title: KIP Purpose and Guidelines
status: Living
type: Meta
author: Ron Hamenahem <ron@koinos.group>, et al.
created: 2021-05-05
---

## What is a KIP?

KIP stands for Koinos Improvement Proposal. An KIP is a design document providing information to the Koinos community, or describing a new feature for Koinos or its processes or environment. The KIP should provide a concise technical specification of the feature and a rationale for the feature. The KIP author is responsible for building consensus within the community and documenting dissenting opinions.

## KIP Rationale

We intend EIPs to be the primary mechanisms for proposing new features, for collecting community technical input on an issue, and for documenting the design decisions that have gone into Koinos. Because the EIPs are maintained as text files in a versioned repository, their revision history is the historical record of the feature proposal.

For Koinos implementers, EIPs are a convenient way to track the progress of their implementation. Ideally each implementation maintainer would list the EIPs that they have implemented. This will give end users a convenient way to know the current status of a given implementation or library.

## KIP Types

There are three types of KIP:

- A **Standards Track KIP** describes any change that affects most or all Koinos implementations, such as—a change to the network protocol, a change in block or transaction validity rules, proposed application standards/conventions, or any change or addition that affects the interoperability of applications using Koinos. Standards Track EIPs consist of three parts—a design document, an implementation, and (if warranted) an update to the [formal specification]. Furthermore, Standards Track EIPs can be broken down into the following categories:

  - **Core**: improvements requiring a consensus fork (e.g. [KIP-5](./kip-5.md), [KIP-101](./kip-101.md)), as well as changes that are not necessarily consensus critical but may be relevant to [“core dev” discussions](https://github.com/koinos/pm) (for example, [KIP-90], and the miner/node strategy changes 2, 3, and 4 of [KIP-86](./kip-86.md)).
  - **Networking**: includes improvements around [devp2p] ([KIP-8](./kip-8.md)) and [Light Koinos Subprotocol], as well as proposed improvements to network protocol specifications of [whisper] and [swarm].
  - **Interface**: includes improvements around client [API/RPC] specifications and standards, and also certain language-level standards like method names ([KIP-6](./kip-6.md)) and [contract ABIs]. The label “interface” aligns with the [interfaces repo] and discussion should primarily occur in that repository before an KIP is submitted to the EIPs repository.
  - **ERC**: application-level standards and conventions, including contract standards such as token standards ([ERC-20](./kip-20.md)), name registries ([ERC-137](./kip-137.md)), URI schemes, library/package formats, and wallet formats.

- A **Meta KIP** describes a process surrounding Koinos or proposes a change to (or an event in) a process. Process EIPs are like Standards Track EIPs but apply to areas other than the Koinos protocol itself. They may propose an implementation, but not to Koinos's codebase; they often require community consensus; unlike Informational EIPs, they are more than recommendations, and users are typically not free to ignore them. Examples include procedures, guidelines, changes to the decision-making process, and changes to the tools or environment used in Koinos development. Any meta-KIP is also considered a Process KIP.

- An **Informational KIP** describes an Koinos design issue, or provides general guidelines or information to the Koinos community, but does not propose a new feature. Informational EIPs do not necessarily represent Koinos community consensus or a recommendation, so users and implementers are free to ignore Informational EIPs or follow their advice.

It is highly recommended that a single KIP contain a single key proposal or new idea. The more focused the KIP, the more successful it tends to be. A change to one client doesn't require an KIP; a change that affects multiple clients, or defines a standard for multiple apps to use, does.

An KIP must meet certain minimum criteria. It must be a clear and complete description of the proposed enhancement. The enhancement must represent a net improvement. The proposed implementation, if applicable, must be solid and must not complicate the protocol unduly.

### Special requirements for Core EIPs

If a **Core** KIP mentions or proposes changes to the EVM (Koinos Virtual Machine), it should refer to the instructions by their mnemonics and define the opcodes of those mnemonics at least once. A preferred way is the following:

```
REVERT (0xfe)
```

## KIP Work Flow

### Shepherding an KIP

Parties involved in the process are you, the champion or _EIP author_, the [_EIP editors_](#kip-editors), and the [_Ethereum Core Developers_](https://github.com/koinos/pm).

Before you begin writing a formal KIP, you should vet your idea. Ask the Koinos community first if an idea is original to avoid wasting time on something that will be rejected based on prior research. It is thus recommended to open a discussion thread on [the Koinos Magicians forum] to do this, but you can also use [one of the Koinos Gitter chat rooms], [the Koinos subreddit] or [the Issues section of this repository].

Once the idea has been vetted, your next responsibility will be to present (by means of an KIP) the idea to the reviewers and all interested parties, invite editors, developers, and the community to give feedback on the aforementioned channels. You should try and gauge whether the interest in your KIP is commensurate with both the work involved in implementing it and how many parties will have to conform to it. For example, the work required for implementing a Core KIP will be much greater than for an ERC and the KIP will need sufficient interest from the Koinos client teams. Negative community feedback will be taken into consideration and may prevent your KIP from moving past the Draft stage.

### Core EIPs

For Core EIPs, given that they require client implementations to be considered **Final** (see "EIPs Process" below), you will need to either provide an implementation for clients or convince clients to implement your KIP.

The best way to get client implementers to review your KIP is to present it on an AllCoreDevs call. You can request to do so by posting a comment linking your KIP on an [AllCoreDevs agenda GitHub Issue].

The AllCoreDevs call serve as a way for client implementers to do three things. First, to discuss the technical merits of EIPs. Second, to gauge what other clients will be implementing. Third, to coordinate KIP implementation for network upgrades.

These calls generally result in a "rough consensus" around what EIPs should be implemented. This "rough consensus" rests on the assumptions that EIPs are not contentious enough to cause a network split and that they are technically sound.

:warning: The EIPs process and AllCoreDevs call were not designed to address contentious non-technical issues, but, due to the lack of other ways to address these, often end up entangled in them. This puts the burden on client implementers to try and gauge community sentiment, which hinders the technical coordination function of EIPs and AllCoreDevs calls. If you are shepherding an KIP, you can make the process of building community consensus easier by making sure that [the Koinos Magicians forum] thread for your KIP includes or links to as much of the community discussion as possible and that various stakeholders are well-represented.

_In short, your role as the champion is to write the KIP using the style and format described below, shepherd the discussions in the appropriate forums, and build community consensus around the idea._

### KIP Process

The following is the standardization process for all EIPs in all tracks:

![KIP Status Diagram](../assets/kip-1/KIP-process.png)

**Idea** - An idea that is pre-draft. This is not tracked within the KIP Repository.

**Draft** - The first formally tracked stage of an KIP in development. An KIP is merged by an KIP Editor into the KIP repository when properly formatted.

**Review** - An KIP Author marks an KIP as ready for and requesting Peer Review.

**Last Call** - This is the final review window for an KIP before moving to `FINAL`. An KIP editor will assign `Last Call` status and set a review end date (review-period-end), typically 14 days later.

If this period results in necessary normative changes it will revert the KIP to `REVIEW`.

**Final** - This KIP represents the final standard. A Final KIP exists in a state of finality and should only be updated to correct errata and add non-normative clarifications.

**Stagnant** - Any KIP in `DRAFT` or `REVIEW` if inactive for a period of 6 months or greater is moved to `STAGNANT`. An KIP may be resurrected from this state by Authors or KIP Editors through moving it back to `DRAFT`.

> _EIP Authors are notified of any algorithmic change to the status of their EIP_

**Withdrawn** - The KIP Author(s) have withdrawn the proposed KIP. This state has finality and can no longer be resurrected using this KIP number. If the idea is pursued at later date it is considered a new proposal.

**Living** - A special status for EIPs that are designed to be continually updated and not reach a state of finality. This includes most notably KIP-1. Any changes to these EIPs will move between `REVIEW` and `LIVING` states.

## What belongs in a successful KIP?

Each KIP should have the following parts:

- Preamble - RFC 822 style headers containing metadata about the KIP, including the KIP number, a short descriptive title (limited to a maximum of 44 characters), and the author details. See [below](./kip-1.md#kip-header-preamble) for details.
- Abstract - A short (~200 word) description of the technical issue being addressed.
- Motivation (\*optional) - A motivation section is critical for EIPs that want to change the Koinos protocol. It should clearly explain why the existing protocol specification is inadequate to address the problem that the KIP solves. KIP submissions without sufficient motivation may be rejected outright.
- Specification - The technical specification should describe the syntax and semantics of any new feature. The specification should be detailed enough to allow competing, interoperable implementations for any of the current Koinos platforms (cpp-koinos, go-koinos, parity, ethereumJ, ethereumjs-lib, [and others](https://github.com/koinos/wiki/wiki/Clients).
- Rationale - The rationale fleshes out the specification by describing what motivated the design and why particular design decisions were made. It should describe alternate designs that were considered and related work, e.g. how the feature is supported in other languages. The rationale may also provide evidence of consensus within the community, and should discuss important objections or concerns raised during discussion.
- Backwards Compatibility - All EIPs that introduce backwards incompatibilities must include a section describing these incompatibilities and their severity. The KIP must explain how the author proposes to deal with these incompatibilities. KIP submissions without a sufficient backwards compatibility treatise may be rejected outright.
- Test Cases - Test cases for an implementation are mandatory for EIPs that are affecting consensus changes. Tests should either be inlined in the KIP as data (such as input/expected output pairs, or included in `../assets/kip-###/<filename>`.
- Reference Implementation - An optional section that contains a reference/example implementation that people can use to assist in understanding or implementing this specification.
- Security Considerations - All EIPs must contain a section that discusses the security implications/considerations relevant to the proposed change. Include information that might be important for security discussions, surfaces risks and can be used throughout the life-cycle of the proposal. E.g. include security-relevant design decisions, concerns, important discussions, implementation-specific guidance and pitfalls, an outline of threats and risks and how they are being addressed. KIP submissions missing the "Security Considerations" section will be rejected. An KIP cannot proceed to status "Final" without a Security Considerations discussion deemed sufficient by the reviewers.
- Copyright Waiver - All EIPs must be in the public domain. See the bottom of this KIP for an example copyright waiver.

## KIP Formats and Templates

EIPs should be written in [markdown] format. There is a [template](https://github.com/koinos/EIPs/blob/master/kip-template.md) to follow.

## KIP Header Preamble

Each KIP must begin with an [RFC 822](https://www.ietf.org/rfc/rfc822.txt) style header preamble, preceded and followed by three hyphens (`---`). This header is also termed ["front matter" by Jekyll](https://jekyllrb.com/docs/front-matter/). The headers must appear in the following order. Headers marked with "\*" are optional and are described below. All other headers are required.

` kip:` _EIP number_ (this is determined by the KIP editor)

` title:` _EIP title_

` author:` _a list of the author's or authors' name(s) and/or username(s), or name(s) and email(s). Details are below._

` * discussions-to:` _a url pointing to the official discussion thread_

` status:` _Draft, Review, Last Call, Final, Stagnant, Withdrawn, Living_

`* review-period-end:` _date review period ends_

` type:` _Standards Track, Meta, or Informational_

` * category:` _Core, Networking, Interface, or ERC_ (fill out for Standards Track EIPs only)

` created:` _date created on_

` * updated:` _comma separated list of dates_

` * requires:` _EIP number(s)_

` * replaces:` _EIP number(s)_

` * superseded-by:` _EIP number(s)_

` * resolution:` _a url pointing to the resolution of this EIP_

Headers that permit lists must separate elements with commas.

Headers requiring dates will always do so in the format of ISO 8601 (yyyy-mm-dd).

#### `author` header

The `author` header lists the names, email addresses or usernames of the authors/owners of the KIP. Those who prefer anonymity may use a username only, or a first name and a username. The format of the `author` header value must be:

> Random J. User &lt;address@dom.ain&gt;

or

> Random J. User (@username)

if the email address or GitHub username is included, and

> Random J. User

if the email address is not given.

It is not possible to use both an email and a GitHub username at the same time. If important to include both, one could include their name twice, once with the GitHub username, and once with the email.

At least one author must use a GitHub username, in order to get notified on change requests and have the capability to approve or reject them.

#### `resolution` header

The `resolution` header is required for Standards Track EIPs only. It contains a URL that should point to an email message or other web resource where the pronouncement about the KIP is made.

#### `discussions-to` header

While an KIP is a draft, a `discussions-to` header will indicate the mailing list or URL where the KIP is being discussed. As mentioned above, examples for places to discuss your KIP include [Koinos topics on Gitter](https://gitter.im/koinos/topics), an issue in this repo or in a fork of this repo, [Koinos Magicians](https://koinos-magicians.org/) (this is suitable for EIPs that may be contentious or have a strong governance aspect), and [Reddit r/koinos](https://www.reddit.com/r/koinos/).

No `discussions-to` header is necessary if the KIP is being discussed privately with the author.

As a single exception, `discussions-to` cannot point to GitHub pull requests.

#### `type` header

The `type` header specifies the type of KIP: Standards Track, Meta, or Informational. If the track is Standards please include the subcategory (core, networking, interface, or ERC).

#### `category` header

The `category` header specifies the KIP's category. This is required for standards-track EIPs only.

#### `created` header

The `created` header records the date that the KIP was assigned a number. Both headers should be in yyyy-mm-dd format, e.g. 2001-08-14.

#### `updated` header

The `updated` header records the date(s) when the KIP was updated with "substantial" changes. This header is only valid for EIPs of Draft and Active status.

#### `requires` header

EIPs may have a `requires` header, indicating the KIP numbers that this KIP depends on.

#### `superseded-by` and `replaces` headers

EIPs may also have a `superseded-by` header indicating that an KIP has been rendered obsolete by a later document; the value is the number of the KIP that replaces the current document. The newer KIP must have a `replaces` header containing the number of the KIP that it rendered obsolete.

## Linking to other EIPs

References to other EIPs should follow the format `KIP-N` where `N` is the KIP number you are referring to. Each KIP that is referenced in an KIP **MUST** be accompanied by a relative markdown link the first time it is referenced, and **MAY** be accompanied by a link on subsequent references. The link **MUST** always be done via relative paths so that the links work in this GitHub repository, forks of this repository, the main EIPs site, mirrors of the main KIP site, etc. For example, you would link to this KIP with `[KIP-1](./kip-1.md)`.

## Auxiliary Files

Images, diagrams and auxiliary files should be included in a subdirectory of the `assets` folder for that KIP as follows: `assets/kip-N` (where **N** is to be replaced with the KIP number). When linking to an image in the KIP, use relative links such as `../assets/kip-1/image.png`.

## Transferring KIP Ownership

It occasionally becomes necessary to transfer ownership of EIPs to a new champion. In general, we'd like to retain the original author as a co-author of the transferred KIP, but that's really up to the original author. A good reason to transfer ownership is because the original author no longer has the time or interest in updating it or following through with the KIP process, or has fallen off the face of the 'net (i.e. is unreachable or isn't responding to email). A bad reason to transfer ownership is because you don't agree with the direction of the KIP. We try to build consensus around an KIP, but if that's not possible, you can always submit a competing KIP.

If you are interested in assuming ownership of an KIP, send a message asking to take over, addressed to both the original author and the KIP editor. If the original author doesn't respond to the email in a timely manner, the KIP editor will make a unilateral decision (it's not like such decisions can't be reversed :)).

## KIP Editors

The current KIP editors are

- Nick Johnson (@arachnid)
- Casey Detrio (@cdetrio)
- Hudson Jameson (@Souptacular)
- Vitalik Buterin (@vbuterin)
- Nick Savers (@nicksavers)
- Martin Becze (@wanderer)
- Greg Colvin (@gcolvin)
- Alex Beregszaszi (@axic)
- Micah Zoltu (@MicahZoltu)

## KIP Editor Responsibilities

For each new KIP that comes in, an editor does the following:

- Read the KIP to check if it is ready: sound and complete. The ideas must make technical sense, even if they don't seem likely to get to final status.
- The title should accurately describe the content.
- Check the KIP for language (spelling, grammar, sentence structure, etc.), markup (GitHub flavored Markdown), code style

If the KIP isn't ready, the editor will send it back to the author for revision, with specific instructions.

Once the KIP is ready for the repository, the KIP editor will:

- Assign an KIP number (generally the PR number or, if preferred by the author, the Issue # if there was discussion in the Issues section of this repository about this KIP)

- Merge the corresponding pull request

- Send a message back to the KIP author with the next step.

Many EIPs are written and maintained by developers with write access to the Koinos codebase. The KIP editors monitor KIP changes, and correct any structure, grammar, spelling, or markup mistakes we see.

The editors don't pass judgment on EIPs. We merely do the administrative & editorial part.

## Style Guide

When referring to an KIP by number, it should be written in the hyphenated form `KIP-X` where `X` is the KIP's assigned number.

## History

This document was derived heavily from [Bitcoin's BIP-0001] written by Amir Taaki which in turn was derived from [Python's PEP-0001]. In many places text was simply copied and modified. Although the PEP-0001 text was written by Barry Warsaw, Jeremy Hylton, and David Goodger, they are not responsible for its use in the Koinos Improvement Process, and should not be bothered with technical questions specific to Koinos or the KIP. Please direct all comments to the KIP editors.

### Bibliography

[devp2p]: https://github.com/koinos/wiki/wiki/%C3%90%CE%9EVp2p-Wire-Protocol
[light koinos subprotocol]: https://github.com/koinos/wiki/wiki/Light-client-protocol
[whisper]: https://github.com/koinos/go-koinos/wiki/Whisper-Overview
[swarm]: https://github.com/koinos/go-koinos/pull/2959
[api/rpc]: https://github.com/koinos/wiki/wiki/JSON-RPC
[contract abis]: https://github.com/koinos/wiki/wiki/Koinos-Contract-ABI
[interfaces repo]: https://github.com/koinos/interfaces
[the koinos subreddit]: https://www.reddit.com/r/koinos/
[one of the koinos gitter chat rooms]: https://gitter.im/koinos/
[pull request]: https://github.com/koinos/EIPs/pulls
[formal specification]: https://github.com/koinos/yellowpaper
[the issues section of this repository]: https://github.com/koinos/EIPs/issues
[markdown]: https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet
[bitcoin's bip-0001]: https://github.com/bitcoin/bips
[python's pep-0001]: https://www.python.org/dev/peps/
[the koinos magicians forum]: https://koinos-magicians.org/
[allcoredevs agenda github issue]: https://github.com/koinos/pm/issues

## Copyright

Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).
