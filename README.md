# Koinos Improvement Proposals (KIPs)

[![Gitter](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/ethereum/EIPs?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge)

Koinos Improvement Proposals (EIPs) describe standards for the Koinos platform, including core protocol specifications, client APIs, and contract standards.

**Before you initiate a pull request**, please read the [KIP-1](https://eips.koinos.io/KIPS/KIP-1) process document. Ideas should be thoroughly discussed prior to opening a pull request, such as on the [Koinos Magicians forums](https://ethereum-magicians.org) or in a GitHub issue in this repository.

This repository tracks the ongoing status of EIPs. It contains:

- [Draft](https://eips.koinos.io/all#draft) proposals which intend to complete the KIP review process.
- [Last Call](https://eips.koinos.io/all#last-call) for proposals that may become final (see also [RSS feed](https://eips.koinos.io/last-call.xml)).
- [Accepted](https://eips.koinos.io/all#accepted) proposals which are awaiting implementation or deployment by Koinos client developers.
- [Final](https://eips.koinos.io/all#final) and [Active](https://eips.koinos.io/all#active) proposals that are recorded.
- The [KIP process](./KIPS/KIP-1.md#KIP-work-flow) that governs the KIP repository.

Achieving "Final" status in this repository only represents that a proposal has been reviewed for technical accuracy. It is solely the responsibility of the reader to decide whether a proposal will be useful to them.

Browse all current and draft EIPs on [the official KIP site](https://eips.koinos.io/).

Once your first PR is merged, we have a bot that helps out by automatically merging PRs to draft EIPs. For this to work, it has to be able to tell that you own the draft being edited. Make sure that the 'author' line of your KIP contains either your GitHub username or your email address inside \<triangular brackets>. If you use your email address, that address must be the one publicly shown on [your GitHub profile](https://github.com/settings/profile).

## Project Goal

The Koinos Improvement Proposals repository exists as a place to share concrete proposals with potential users of the proposal and the Koinos community at large.

## Preferred Citation Format

The canonical URL for a KIP that has achieved draft status at any point is at https://eips.koinos.io/. For example, the canonical URL for KIP-1 is https://eips.koinos.io/KIPS/KIP-1.

Please consider anything which is not published on https://eips.koinos.io/ as a working paper.

And please consider anything published at https://eips.koinos.io/ with a status of "draft" as an incomplete draft.

# Validation

EIPs must pass some validation tests. The KIP repository ensures this by running tests using [html-proofer](https://rubygems.org/gems/html-proofer) and [eip_validator](https://rubygems.org/gems/eip_validator).

It is possible to run the KIP validator locally:

```sh
gem install eip_validator
eip_validator <INPUT_FILES>
```

# Local development

## Prerequisites

1. Open Terminal.

2. Check whether you have Ruby 2.1.0 or higher installed:

```sh
$ ruby --version
```

3. If you don't have Ruby installed, install Ruby 2.1.0 or higher.

4. Install Bundler:

```sh
$ gem install bundler
```

5. Install dependencies:

```sh
$ bundle install
```

## Build your local Jekyll site

1. Bundle assets and start the server:

```sh
$ bundle exec jekyll serve
```

2. Preview your local Jekyll site in your web browser at `http://localhost:4000`.

More information on Jekyll and GitHub pages [here](https://help.github.com/en/enterprise/2.14/user/articles/setting-up-your-github-pages-site-locally-with-jekyll).
