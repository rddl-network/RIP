```
shortname: REP-17
name: Fiat-Based Grant Program for RDDL Network
type: standard
status: draft
editor: Jürgen Eckel juergen@riddleandcode.com
contributors:
```

# Fiat-Based Grant Program for RDDL Network

## Abstract

This proposal outlines the creation of a grant program for the RDDL Network that utilizes on-chain governance for proposal approval but awards grants in fiat currency (EUR) instead of the DAO's native token. This proposal aims to expand the scope of our funding capabilities and attract a wider range of project proposals.

## Motivation

* **Limited Use Cases for Token Grants**  Many potential grant recipients may not have the immediate need or infrastructure to utilize our DAO's token. This limits the pool of qualified applicants.

* **Increased Accessibility** Offering fiat grants opens the door to a broader range of projects and individuals, including those unfamiliar with cryptocurrency or lacking the resources to manage tokens.
* **Strategic Partnerships** Fiat grants can foster collaboration with traditional institutions and organizations that may not be comfortable with cryptocurrencies.

## Proposed Structure

* **Grant Categories** Define clear categories for eligible grant proposals, aligning with the DAO's overall mission and goals.
* **Application Process** Establish an on-chain application system allowing potential recipients to submit proposals outlining project scope, budget breakdown (specifying fiat needs), timeline, and expected impact.
* **Review & Voting** Implement a multi-stage review process. Shortlisted proposals can be voted upon by token holders using the DAO's existing governance framework.
* **Compliance & KYC** Establish clear Know Your Customer (KYC) and Anti-Money Laundering (AML) procedures to ensure responsible fiat management.

## Benefits:

* **Wider Project Pool** Attract a broader range of impactful projects that align with the DAO's goals.
* **Increased Community Engagement** Encourage participation from non-crypto native individuals and organizations.
* **Strategic Partnerships** Foster collaborations with traditional institutions.
* **Enhanced Impact** Expand the DAO's reach and influence in the real world.

## Conclusion:

Implementing a fiat-based grant program represents a significant opportunity for RDDL Network to expand its reach, attract a wider range of impactful projects, and maximize its positive influence on the world. By leveraging on-chain governance for proposal selection while awarding grants in fiat, we can bridge the gap between the DAO ecosystem and traditional institutions.

## Specification

A proposal for a grant can be drafted by running the following cli command

```
planetmint-god tx gov draft-proposal
```
Selecting the proposal type ```text``` and follow the instructions to complete the proposal.

The proposal file comes with the following structure

```
{
 "metadata": "ipfs link or link to a REP at github e.g. https://raw.githubusercontent.com/rddl-network/REPs/main/rep17.md",
 "deposit": "10000stake",
 "title": "This is a proposal title",
 "summary": "This is the proposal summary"
}
```

The metadata of the grant proposal can be put to a ipfs document or a MD on this REPs repository.

```
{
 "title": "This is a samples proposal",
 "authors": [
  "Jürgen Eckel <juergen@rddl.io>"
 ],
 "summary": "This is the summary of the proposal",
 "details": "details",
 "proposal_forum_url": "please post a link to a topic from within the DAO proposal forum at https://discord.com/channels/1044693472390697011/1255140142444838912",
 "vote_option_context": "context"
}
```

The details should at least consist of the following details:

1. Cover Letter (Optional):

Briefly introduce yourself or your team.
Highlight the project's purpose and its alignment with the DAO's mission.
Mention the requested grant amount.

2. Executive Summary:

Provide a concise overview of the entire proposal.
Explain the problem you're addressing and your proposed solution.
Briefly outline your project goals, methods, and expected outcomes.

3. Project Description:

Elaborate on the problem your project addresses and its significance.
Define your project's goals and objectives in clear, measurable terms.
Describe your proposed approach and methodology for achieving the goals.
Explain the project timeline with key milestones.

4. Team & Expertise:

Introduce your team members and their relevant experience for this project.
Highlight any advisors or collaborators involved and their expertise.

5. Budget & Justification:

Detail the requested grant amount in fiat currency.
Provide a breakdown of how the funds will be used (e.g., personnel, materials, equipment).
Justify each expense category and explain its necessity for the project.

6. Evaluation & Metrics:

Describe how you will measure the success of your project.
Define key performance indicators (KPIs) aligned with your goals.
Explain how you will track progress and report results to the DAO.

7. Sustainability Plan (Optional):

If applicable, explain how the project will be sustained after the grant period.
Outline potential revenue streams or ongoing funding sources.

8. Conclusion:

Briefly summarize the key points of your proposal.
Reiterate the project's value proposition and its contribution to the DAO's goals.
Express your gratitude for the reviewers' time and consideration.

9. Appendix:

Include any supporting documents such as resumes, letters of recommendation, or detailed project plans.
Remember: