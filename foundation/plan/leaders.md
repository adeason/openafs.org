---
title: Project Leader Responsibilities
---

A project leader plan for OpenAFS
=================================

From the beginnging of the OpenAFS project, most of the resources used
to perform release engineering and management have been provided on an
ad-hoc basis. Now, as OpenAFS moves to formally organize, we outline
this plan for formalizing the project leader process.

Background
----------

For the purpose of this document, we assume project leaders are a group
of people who have access to commit changes to some or all of the
OpenAFS project source tree, and contributors are persons who provide or
are interested in providing such changes. A project leader may be a
contributor.

Implementation
--------------

This plan presupposes resources which do not exist today. Implementation
should be considered phased, which is to say, as resources to put the
plan into action become available the clauses here should be put into
effect. Conditions which are known to require additional resources are
marked with \*.

Responsibilities
----------------

### Code

1.  *Contributors*

    1.  must provide patches in context or unified format.
    2.  should provide against the current head of whichever tree the
        patch is for.
    3.  should provide a patch for both development and production trees
        where applicable.
    4.  should provide a unit test for any contribution.(\*)
    5.  should provide or update a functional test for any applicable
        contribution.(\*)
    6.  must provide necessary assertions that the contribution can be
        legally contributed by them and are provided under an acceptable
        license.
    7.  must provide documentation for submissions which add commands or
        functionality or change user-visible behavior, meeting current
        documentation standards.(\*)

2.  *Project Leaders*

    1.  may convene committees to delegate review and feedback to, but
        are ultimately responsible for enforcing project contribution
        standards.
    2.  should create and publish a checklist of required and desired
        steps for each variety of submission which is possible.
    3.  must create and publish standards for code and documentation
        contributions.(\*)
    4.  must provide review of any architecture proposals submitted.
    5.  must insure an issue in the issue tracker is opened for all
        submissions.(\*)
    6.  must copy all correspondence to the issue tracker.
    7.  must review all patches for compliance with OpenAFS code
        standards and provide feedback when standards are not met.
    8.  must review all patches for compliance with published protocol
        standards and provide feedback when standards are not met.
    9.  may arrange for orphaned contributions deemed of value to the
        community to be adopted or stewarded until they meet needed
        standards.
    10. for major architectural changes, must engage the community for
        guidance and the Advisory Council for a final decision on
        acceptance. A review of the proposed changes must be provided to
        the community and Advisory Council by the Project Leaders.
        (Standards-based changes must go through the protocol standards
        process rather than an internal process)
    11. must test submissions by compiling on all supported platforms
        before committing(\*).
    12. must apply all applicable unit tests before committing.(\*)
    13. must apply all applicable functional tests before
        committing.(\*)
    14. must require current documentation standards to be applied.(\*)
    15. must note information about the committed change to the issue
        tracker.
    16. must note which release(s) the change is targeted for to the
        issue tracker.
    17. must keep an updated list of which changes have been accepted
        but not released and when they are expected in releases.(\*)
    18. may keep a list of who has signed contributor agreements
        (possibly with issue tracker accounts for submitters) to
        simplify tracking of licensing of submissions.

Glossary
--------

1.  A major architectural change is defined as one that
    1.  requires additions, modifications, or deletion of communication
        protocols
    2.  is deemed by the project leaders or the community to result in
        some undue amount of risk
    3.  will require more than 40 hours to review and/or test

2.  An orphaned contribution is one for which
    1.  the contributor has not responded to project leader (or
        delegate) communications within six weeks.


