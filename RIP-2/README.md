```
shortname: RIP-2
name: Consensus-Oriented Specification System
type: Meta
status: Draft
editor: Jürgen Eckel <juergen@riddleandcode.com>
contributors: JÜrgen Eckel <juergen@riddleandcode.com>
```

This document describes a consensus-oriented specification system (COSS) for building interoperable technical specifications. COSS is based on a lightweight editorial process that seeks to engage the widest possible range of interested parties and move rapidly to consensus through working code.

This specification is based on [unprotocols.org 2/COSS](https://rfc.unprotocols.org/2/) and on [EIP1 - EIP Purpose and Guidelines](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-1.md).

## Change Process
This document is governed by the [RIP-1 (C4)](../RIP-1/README.md).

## Language
The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED", "NOT RECOMMENDED", "MAY", and "OPTIONAL" in this document are to be interpreted as described in [BCP 14](https://tools.ietf.org/html/bcp14) \[[RFC2119](https://tools.ietf.org/html/rfc2119)\] \[[RFC8174](https://tools.ietf.org/html/rfc8174)\] when, and only when, they appear in all capitals, as shown here.

## Goals
The primary goal of COSS is to facilitate the process of writing, proving, and improving new technical specifications. A "technical specification" defines a protocol, a process, an API, a use of language, a methodology, or any other aspect of a technical environment that can usefully be documented for the purposes of technical or social interoperability.

A RDDL specification is called **R**DDL **I**improvment **P**roposal, **RIP** henceforth.

COSS is intended to above all be economical and rapid, so that it is useful to small teams with little time to spend on more formal processes.

Principles:

* We aim for rough consensus and running code.
* RIPs are small pieces, made by small teams.
* RIPs should have a clearly responsible editor.
* The process should be visible, objective, and accessible to anyone.
* The process should clearly separate experiments from solutions.
* The process should allow deprecation of old RIPs.

RIPs should take minutes to explain, hours to design, days to write, weeks to prove, months to become mature, and years to replace.

RIPs have no special status except that accorded by the community.

The author of the RIPs is responsible for building consensus within the community and documenting dissenting opinions.

## Architecture

### Types of RIP
There are three types of RIPs:
* A **Standard Track RIP** describes any change to network protocols, transaction validity rules, proposed application standards/conventions, or any change or addition that affects the interoperability of applications using RDDL products.
* An **Informational RIPs** describes a RDDL design issue, or provides general guidelines or information to the RDDL community, but does not propose a new feature. Informational RIPs do not necessarily represent RDDL community consensus or a recommendation, so users and implementers are free to ignore Informational RIPs or follow their advice.
* A **Meta RIP** describes a process surrounding RDDL or proposes a change to a process.

### RIP Format
A RIP is a set of Markdown documents (the main file SHOULD be called `README.md`), together with comments, attached files, and other resources. A RIP is identified by its number (e.g. this RIP is **RIP-2**). The number of the RIP is also the name of the directory where its files are stored.

Every RIP (including branches) carries a different number. New versions of the same RIP have new numbers.

### RIP template
Each RIP MUST customize and include this header:
````
```
shortname: [number/shortname]
name: [Full name of the RIP]
type: [standard | informational | meta ]
status: [raw | draft | stable | deprecated | retired | deleted]
editor: [Editor Name <email address>]
contributors: [Optional Contributor 1 <email address>, ..., Optional Contributor N <email address>]
```
````
_Note: the `number` is assigned after a RIP has been submitted._

Each RIP SHOULD include the following sections:

1. **Abstract**. The abstract is a short (~200 word) informal description of the technical issue being addressed.

1. **Motivation**. The motivation is a possibly long informal description of the issue being addressed. The motivation is critical for RIPs that want to change the RDDL protocol. It should clearly explain why the existing protocol is inadequate to address the problem that the RIP solves. RIP submissions without sufficient motivation may be rejected outright.

1. **Problem Breakdown** The detailed formal description of the problem in the form of the list of exact issues the solution has to address.

1. **Specification**: The technical specification should describe the syntax and semantics of any new feature. The specification must address the exact issues described in the solution breakdown and should describe how it addresses them. The specification should be detailed enough to allow competing, interoperable implementations. It MAY describe the impact on data models, API endpoints, security, performance, end users, deployment, documentation, and testing.

1. **Rationale**. The rationale fleshes out the specification by describing what motivated the design and why particular design decisions were made. It should describe alternate designs that were considered and related work, e.g. how the feature is supported in other languages. The rationale may also provide evidence of consensus within the community, and should discuss important objections or concerns raised during discussion.

1. **Backwards Compatibility**. All RIPs that introduce backwards incompatibilities must include a section describing these incompatibilities and their severity. The RIP must explain how the author proposes to deal with these incompatibilities. RIP submissions without a sufficient backwards compatibility treatise may be rejected outright.

1. **Implementation**. The implementations must be completed before any RIP is given status "stable", but it need not be completed before the RIP is accepted. While there is merit to the approach of reaching consensus on the RIP and rationale before writing code, the principle of "rough consensus and running code" is still useful when it comes to resolving many discussions of API details.

1. **Copyright Waiver**. Except for RIP-1 (C4) and RIP-2 (COSS), all RIPs MUST be released to the public domain. To do that, the following block of HTML SHOULD be used in the RIP's source Markdown file. ([HTML is valid Markdown](https://daringfireball.net/projects/markdown/syntax#html).)

```html
<p xmlns:dct="http://purl.org/dc/terms/">
  <a rel="license"
     href="http://creativecommons.org/publicdomain/zero/1.0/">
    <img src="http://i.creativecommons.org/p/zero/1.0/88x31.png" style="border-style: none;" alt="CC0" />
  </a>
  <br />
  To the extent possible under law, all contributors to this RIP
  have waived all copyright and related or neighboring rights to this RIP.
</p>
```

The first 4 sections above are based on the [Leslie Lamport's note about describing solutions](https://lamport.azurewebsites.net/pubs/state-the-problem.pdf).

## COSS Lifecycle
Every RIP has an independent lifecycle that documents clearly its current status.

A RIP has six possible states that reflect its maturity and contractual weight:

![Lifecycle diagram](lifecycle.png)

### Raw RIPs
All new RIPs are **raw** RIPs. Changes to raw RIPs can be unilateral and arbitrary. Those seeking to implement a raw RIP should ask for it to be made a draft RIP. Raw RIPs have no contractual weight.

### Draft RIPs
When raw RIPs can be demonstrated, they become **draft** RIPs. Changes to draft RIPs should be done in consultation with users. Draft RIPs are contracts between the editors and implementers.

### Stable RIPs
When draft RIPs are used by third parties, they become **stable** RIPs. Changes to stable RIPs should be restricted to cosmetic ones, errata and clarifications. Stable RIPs are contracts between editors, implementers, and end-users.

### Deprecated RIPs
When stable RIPs are replaced by newer draft RIPs, they become **deprecated** RIPs. Deprecated RIPs should not be changed except to indicate their replacements, if any. Deprecated RIPs are contracts between editors, implementers and end-users.

### Retired RIPs
When deprecated RIPs are no longer used in products, they become **retired** RIPs. Retired RIPs are part of the historical record. They should not be changed except to indicate their replacements, if any. Retired RIPs have no contractual weight.

### Deleted RIPs
Deleted RIPs are those that have not reached maturity (stable) and were discarded. They should not be used and are only kept for their historical
value. Only Raw and Draft RIPs can be deleted.

## Editorial control
A RIP MUST have a single responsible editor, the only person
who SHALL change the status of the RIP through the lifecycle stages.

A RIP MAY also have additional contributors who contribute changes to it. It is RECOMMENDED to use the [C4 process](../RIP0001/README.md) to maximize the scale and diversity of contributions.

The editor is responsible for accurately maintaining the state of RIPs and for handling all comments on the RIP.

## Branching and Merging
Any member of the domain MAY branch a RIP at any point. This is done by copying the existing text, and creating a new RIP with the same name and content, but a new number. The ability to branch a RIP is necessary in these circumstances:

* To change the responsible editor for a RIP, with or without the cooperation of the current responsible editor.
* To rejuvenate a RIP that is stable but needs functional changes. This is the proper way to make a new version of a RIP that is in stable or deprecated status.
* To resolve disputes between different technical opinions.

The responsible editor of a branched RIP is the person who makes the branch.

Branches, including added contributions, SHOULD be dedicated to the public domain using CC0 (just like the original RIP). This means that contributors are guaranteed the right to merge changes made in branches back into their original RIPs.

Technically speaking, a branch is a *different* RIP, even if it carries the same name. Branches have no special status except that accorded by the community.

## Conflict resolution
COSS resolves natural conflicts between teams and vendors by allowing anyone to define a new RIP. There is no editorial control process except that practised by the editor of a new RIP. The administrators of a domain (moderators) may choose to interfere in editorial conflicts, and may suspend or ban individuals for behaviour they consider inappropriate.

## Conventions
Where possible editors and contributors are encouraged to:

* Refer to and build on existing work when possible, especially IETF specifications.
* Contribute to existing RIPs rather than reinvent their own.
* Use collaborative branching and merging as a tool for experimentation.

## License
Copyright (c) 2008-16 Yurii Rashkovskii <yrashk@gmail.com>, Pieter Hintjens <ph@imatix.com>, André Rebentisch <andre@openstandards.de>, Alberto Barrionuevo <abarrio@opentia.es>, Chris Puttick <chris.puttick@thehumanjourney.net>
Copyright (c) 2023 RDDL Foundation

This RIP is free software; you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation; either version 3 of the License, or (at your option) any later version.

This RIP is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public License for more details.

You should have received a copy of the GNU General Public License along with this program; if not, see http://www.gnu.org/licenses.
