<template><div><h1 id="rust-rfcs-rfc-book-active-rfc-list" tabindex="-1"><a class="header-anchor" href="#rust-rfcs-rfc-book-active-rfc-list"><span>Rust RFCs - <a href="https://rust-lang.github.io/rfcs/" target="_blank" rel="noopener noreferrer">RFC Book<ExternalLinkIcon/></a> - <a href="https://rfcbot.rs/" target="_blank" rel="noopener noreferrer">Active RFC List<ExternalLinkIcon/></a></span></a></h1>
<p>The &quot;RFC&quot; (request for comments) process is intended to provide a consistent
and controlled path for changes to Rust (such as new features) so that all
stakeholders can be confident about the direction of the project.</p>
<p>Many changes, including bug fixes and documentation improvements can be
implemented and reviewed via the normal GitHub pull request workflow.</p>
<p>Some changes though are &quot;substantial&quot;, and we ask that these be put through a
bit of a design process and produce a consensus among the Rust community and
the <a href="https://www.rust-lang.org/team.html" target="_blank" rel="noopener noreferrer">sub-team<ExternalLinkIcon/></a>s.</p>
<h2 id="table-of-contents" tabindex="-1"><a class="header-anchor" href="#table-of-contents"><span>Table of Contents</span></a></h2>
<ul>
<li><a href="#rust-rfcs">Opening</a></li>
<li><a href="#table-of-contents">Table of Contents</a></li>
<li><a href="#when-you-need-to-follow-this-process">When you need to follow this process</a></li>
<li><a href="#sub-team-specific-guidelines">Sub-team specific guidelines</a></li>
<li><a href="#before-creating-an-rfc">Before creating an RFC</a></li>
<li><a href="#what-the-process-is">What the process is</a></li>
<li><a href="#the-rfc-life-cycle">The RFC life-cycle</a></li>
<li><a href="#reviewing-rfcs">Reviewing RFCs</a></li>
<li><a href="#implementing-an-rfc">Implementing an RFC</a></li>
<li><a href="#rfc-postponement">RFC Postponement</a></li>
<li><a href="#help-this-is-all-too-informal">Help this is all too informal!</a></li>
<li><a href="#license">License</a></li>
<li><a href="#contributions">Contributions</a></li>
</ul>
<h2 id="when-you-need-to-follow-this-process" tabindex="-1"><a class="header-anchor" href="#when-you-need-to-follow-this-process"><span>When you need to follow this process</span></a></h2>
<p>You need to follow this process if you intend to make &quot;substantial&quot; changes to
Rust, Cargo, Crates.io, or the RFC process itself. What constitutes a
&quot;substantial&quot; change is evolving based on community norms and varies depending
on what part of the ecosystem you are proposing to change, but may include the
following.</p>
<ul>
<li>Any semantic or syntactic change to the language that is not a bugfix.</li>
<li>Removing language features, including those that are feature-gated.</li>
<li>Changes to the interface between the compiler and libraries, including lang
items and intrinsics.</li>
<li>Additions to <code v-pre>std</code>.</li>
</ul>
<p>Some changes do not require an RFC:</p>
<ul>
<li>Rephrasing, reorganizing, refactoring, or otherwise &quot;changing shape does
not change meaning&quot;.</li>
<li>Additions that strictly improve objective, numerical quality criteria
(warning removal, speedup, better platform coverage, more parallelism, trap
more errors, etc.)</li>
<li>Additions only likely to be <em>noticed by</em> other developers-of-rust,
invisible to users-of-rust.</li>
</ul>
<p>If you submit a pull request to implement a new feature without going through
the RFC process, it may be closed with a polite request to submit an RFC first.</p>
<h3 id="sub-team-specific-guidelines" tabindex="-1"><a class="header-anchor" href="#sub-team-specific-guidelines"><span>Sub-team specific guidelines</span></a></h3>
<p>For more details on when an RFC is required for the following areas, please see
the Rust community's <a href="https://www.rust-lang.org/team.html" target="_blank" rel="noopener noreferrer">sub-team<ExternalLinkIcon/></a> specific guidelines for:</p>
<ul>
<li><RouteLink to="/lang_changes.html">language changes</RouteLink>,</li>
<li><RouteLink to="/libs_changes.html">library changes</RouteLink>,</li>
<li><RouteLink to="/compiler_changes.html">compiler changes</RouteLink>.</li>
</ul>
<h2 id="before-creating-an-rfc" tabindex="-1"><a class="header-anchor" href="#before-creating-an-rfc"><span>Before creating an RFC</span></a></h2>
<p>A hastily-proposed RFC can hurt its chances of acceptance. Low quality
proposals, proposals for previously-rejected features, or those that don't fit
into the near-term roadmap, may be quickly rejected, which can be demotivating
for the unprepared contributor. Laying some groundwork ahead of the RFC can
make the process smoother.</p>
<p>Although there is no single way to prepare for submitting an RFC, it is
generally a good idea to pursue feedback from other project developers
beforehand, to ascertain that the RFC may be desirable; having a consistent
impact on the project requires concerted effort toward consensus-building.</p>
<p>The most common preparations for writing and submitting an RFC include talking
the idea over on our <a href="https://rust-lang.zulipchat.com/" target="_blank" rel="noopener noreferrer">official Zulip server<ExternalLinkIcon/></a>, discussing the topic on our
<a href="https://internals.rust-lang.org/" target="_blank" rel="noopener noreferrer">developer discussion forum<ExternalLinkIcon/></a>, and occasionally posting &quot;pre-RFCs&quot; on the
developer forum. You may file issues on this repo for discussion, but these are
not actively looked at by the teams.</p>
<p>As a rule of thumb, receiving encouraging feedback from long-standing project
developers, and particularly members of the relevant <a href="https://www.rust-lang.org/team.html" target="_blank" rel="noopener noreferrer">sub-team<ExternalLinkIcon/></a> is a good
indication that the RFC is worth pursuing.</p>
<h2 id="what-the-process-is" tabindex="-1"><a class="header-anchor" href="#what-the-process-is"><span>What the process is</span></a></h2>
<p>In short, to get a major feature added to Rust, one must first get the RFC
merged into the RFC repository as a markdown file. At that point the RFC is
&quot;active&quot; and may be implemented with the goal of eventual inclusion into Rust.</p>
<ul>
<li>Fork the RFC repo <a href="https://github.com/rust-lang/rfcs" target="_blank" rel="noopener noreferrer">RFC repository<ExternalLinkIcon/></a></li>
<li>Copy <code v-pre>0000-template.md</code> to <code v-pre>text/0000-my-feature.md</code> (where &quot;my-feature&quot; is
descriptive). Don't assign an RFC number yet; This is going to be the PR
number and we'll rename the file accordingly if the RFC is accepted.</li>
<li>Fill in the RFC. Put care into the details: RFCs that do not present
convincing motivation, demonstrate lack of understanding of the design's
impact, or are disingenuous about the drawbacks or alternatives tend to
be poorly-received.</li>
<li>Submit a pull request. As a pull request the RFC will receive design
feedback from the larger community, and the author should be prepared to
revise it in response.</li>
<li>Now that your RFC has an open pull request, use the issue number of the PR
to rename the file: update your <code v-pre>0000-</code> prefix to that number. Also
update the &quot;RFC PR&quot; link at the top of the file.</li>
<li>Each pull request will be labeled with the most relevant <a href="https://www.rust-lang.org/team.html" target="_blank" rel="noopener noreferrer">sub-team<ExternalLinkIcon/></a>, which
will lead to its being triaged by that team in a future meeting and assigned
to a member of the subteam.</li>
<li>Build consensus and integrate feedback. RFCs that have broad support are
much more likely to make progress than those that don't receive any
comments. Feel free to reach out to the RFC assignee in particular to get
help identifying stakeholders and obstacles.</li>
<li>The sub-team will discuss the RFC pull request, as much as possible in the
comment thread of the pull request itself. Offline discussion will be
summarized on the pull request comment thread.</li>
<li>RFCs rarely go through this process unchanged, especially as alternatives
and drawbacks are shown. You can make edits, big and small, to the RFC to
clarify or change the design, but make changes as new commits to the pull
request, and leave a comment on the pull request explaining your changes.
Specifically, do not squash or rebase commits after they are visible on the
pull request.</li>
<li>At some point, a member of the subteam will propose a &quot;motion for final
comment period&quot; (FCP), along with a <em>disposition</em> for the RFC (merge, close,
or postpone).
<ul>
<li>This step is taken when enough of the tradeoffs have been discussed that
the subteam is in a position to make a decision. That does not require
consensus amongst all participants in the RFC thread (which is usually
impossible). However, the argument supporting the disposition on the RFC
needs to have already been clearly articulated, and there should not be a
strong consensus <em>against</em> that position outside of the subteam. Subteam
members use their best judgment in taking this step, and the FCP itself
ensures there is ample time and notification for stakeholders to push
back if it is made prematurely.</li>
<li>For RFCs with lengthy discussion, the motion to FCP is usually preceded by
a <em>summary comment</em> trying to lay out the current state of the discussion
and major tradeoffs/points of disagreement.</li>
<li>Before actually entering FCP, <em>all</em> members of the subteam must sign off;
this is often the point at which many subteam members first review the
RFC in full depth.</li>
</ul>
</li>
<li>The FCP lasts ten calendar days, so that it is open for at least 5 business
days. It is also advertised widely,
e.g. in <a href="https://this-week-in-rust.org/" target="_blank" rel="noopener noreferrer">This Week in Rust<ExternalLinkIcon/></a>. This way all
stakeholders have a chance to lodge any final objections before a decision
is reached.</li>
<li>In most cases, the FCP period is quiet, and the RFC is either merged or
closed. However, sometimes substantial new arguments or ideas are raised,
the FCP is canceled, and the RFC goes back into development mode.</li>
</ul>
<h2 id="the-rfc-life-cycle" tabindex="-1"><a class="header-anchor" href="#the-rfc-life-cycle"><span>The RFC life-cycle</span></a></h2>
<p>Once an RFC becomes &quot;active&quot; then authors may implement it and submit the
feature as a pull request to the Rust repo. Being &quot;active&quot; is not a rubber
stamp, and in particular still does not mean the feature will ultimately be
merged; it does mean that in principle all the major stakeholders have agreed
to the feature and are amenable to merging it.</p>
<p>Furthermore, the fact that a given RFC has been accepted and is &quot;active&quot;
implies nothing about what priority is assigned to its implementation, nor does
it imply anything about whether a Rust developer has been assigned the task of
implementing the feature. While it is not <em>necessary</em> that the author of the
RFC also write the implementation, it is by far the most effective way to see
an RFC through to completion: authors should not expect that other project
developers will take on responsibility for implementing their accepted feature.</p>
<p>Modifications to &quot;active&quot; RFCs can be done in follow-up pull requests. We
strive to write each RFC in a manner that it will reflect the final design of
the feature; but the nature of the process means that we cannot expect every
merged RFC to actually reflect what the end result will be at the time of the
next major release.</p>
<p>In general, once accepted, RFCs should not be substantially changed. Only very
minor changes should be submitted as amendments. More substantial changes
should be new RFCs, with a note added to the original RFC. Exactly what counts
as a &quot;very minor change&quot; is up to the sub-team to decide; check
<a href="#sub-team-specific-guidelines">Sub-team specific guidelines</a> for more details.</p>
<h2 id="reviewing-rfcs" tabindex="-1"><a class="header-anchor" href="#reviewing-rfcs"><span>Reviewing RFCs</span></a></h2>
<p>While the RFC pull request is up, the sub-team may schedule meetings with the
author and/or relevant stakeholders to discuss the issues in greater detail,
and in some cases the topic may be discussed at a sub-team meeting. In either
case a summary from the meeting will be posted back to the RFC pull request.</p>
<p>A sub-team makes final decisions about RFCs after the benefits and drawbacks
are well understood. These decisions can be made at any time, but the sub-team
will regularly issue decisions. When a decision is made, the RFC pull request
will either be merged or closed. In either case, if the reasoning is not clear
from the discussion in thread, the sub-team will add a comment describing the
rationale for the decision.</p>
<h2 id="implementing-an-rfc" tabindex="-1"><a class="header-anchor" href="#implementing-an-rfc"><span>Implementing an RFC</span></a></h2>
<p>Some accepted RFCs represent vital features that need to be implemented right
away. Other accepted RFCs can represent features that can wait until some
arbitrary developer feels like doing the work. Every accepted RFC has an
associated issue tracking its implementation in the Rust repository; thus that
associated issue can be assigned a priority via the triage process that the
team uses for all issues in the Rust repository.</p>
<p>The author of an RFC is not obligated to implement it. Of course, the RFC
author (like any other developer) is welcome to post an implementation for
review after the RFC has been accepted.</p>
<p>If you are interested in working on the implementation for an &quot;active&quot; RFC, but
cannot determine if someone else is already working on it, feel free to ask
(e.g. by leaving a comment on the associated issue).</p>
<h2 id="rfc-postponement" tabindex="-1"><a class="header-anchor" href="#rfc-postponement"><span>RFC Postponement</span></a></h2>
<p>Some RFC pull requests are tagged with the &quot;postponed&quot; label when they are
closed (as part of the rejection process). An RFC closed with &quot;postponed&quot; is
marked as such because we want neither to think about evaluating the proposal
nor about implementing the described feature until some time in the future, and
we believe that we can afford to wait until then to do so. Historically,
&quot;postponed&quot; was used to postpone features until after 1.0. Postponed pull
requests may be re-opened when the time is right. We don't have any formal
process for that, you should ask members of the relevant sub-team.</p>
<p>Usually an RFC pull request marked as &quot;postponed&quot; has already passed an
informal first round of evaluation, namely the round of &quot;do we think we would
ever possibly consider making this change, as outlined in the RFC pull request,
or some semi-obvious variation of it.&quot; (When the answer to the latter question
is &quot;no&quot;, then the appropriate response is to close the RFC, not postpone it.)</p>
<h3 id="help-this-is-all-too-informal" tabindex="-1"><a class="header-anchor" href="#help-this-is-all-too-informal"><span>Help this is all too informal!</span></a></h3>
<p>The process is intended to be as lightweight as reasonable for the present
circumstances. As usual, we are trying to let the process be driven by
consensus and community norms, not impose more structure than necessary.</p>
<h2 id="license" tabindex="-1"><a class="header-anchor" href="#license"><span>License</span></a></h2>
<p>This repository is currently in the process of being licensed under either of:</p>
<ul>
<li>Apache License, Version 2.0, (<a href="LICENSE-APACHE">LICENSE-APACHE</a> or https://www.apache.org/licenses/LICENSE-2.0)</li>
<li>MIT license (<a href="LICENSE-MIT">LICENSE-MIT</a> or https://opensource.org/licenses/MIT)</li>
</ul>
<p>at your option. Some parts of the repository are already licensed according to those terms. For more see <a href="https://github.com/rust-lang/rfcs/pull/2044" target="_blank" rel="noopener noreferrer">RFC 2044<ExternalLinkIcon/></a> and its <a href="https://github.com/rust-lang/rust/issues/43461" target="_blank" rel="noopener noreferrer">tracking issue<ExternalLinkIcon/></a>.</p>
<h3 id="contributions" tabindex="-1"><a class="header-anchor" href="#contributions"><span>Contributions</span></a></h3>
<p>Unless you explicitly state otherwise, any contribution intentionally submitted for inclusion in the work by you, as defined in the Apache-2.0 license, shall be dual licensed as above, without any additional terms or conditions.</p>
</div></template>


