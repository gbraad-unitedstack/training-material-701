# Training 701

### Contributing
Gerard Braad

gerard@unitedstack.com


## Topics overview

  * Issue reporting
  * Asking questions
  * Email guidelines


## What can you do?
Contributing isn't about just code


## How to contribute

  * Become a tester
  * Write documentation
  * Build a community
  * Become a translator
  * Help with bug triaging
  * Suggest a feature
  * Help with design
  * Donate


## How to contribute

  * Code
  * ...
  * Code reviews


## Documentation
The first encounter with a project is either the documentation and/or website


## User / Tester
Look for the 'getting started' document and try to install/use the software


## Tester

  * Testing approach
    * ad-hoc
    * exploratory


## Tester

  * Report any issues you encounter
  * ...
  * Advanced testcases
    * hardware and software environments


## Verification
To verify something is not working correctly you need to look for
information.

  * Expected
  * Actual


## Issues
Reporting issues

  * Missing or incorrect documentation
  * Software not working as expected
    * behavior


## Who will read?

  * Can be people in different roles
    * users: operations, ...
    * engineers: developers
    * any person, or a combination of them
  * Community members who perform triage on defects
  * Developers who finally fix the defect
  * QA engineer(s) who needs to verify the fix


## Who will read?

  * Everybody who has the same problem and tries to understand whether
    * Your defect also describes their problem
    * Or whether your issue is one they like to vote for
      * could be a feature
  * UX team member evaluating a feature request
  * RelEng evaluating if the defect is important enough to be included
    in a maintenance update.


## Issue reporting

  * Reproducibility
  * Specific


## Issue reporting: template

  * Prerequisites
    * Versions used
      * Including components and/or dependencies
    * Settings
  * Steps to reproduce
  * Expected behavior
  * Actual behavior


## Issue reporting

  * Examples
    * :-) Good
    * :-( Bad


## Good reporting
Follow the guidelines

  * One problem - One issue
  * Provide a meaningful summary
  * Provide step-by-step descriptions
  * Provide sample material
  * Use Attachments where possible
  * Put all relevant information into the issue

[source](http://www.openoffice.org/qa/issue_handling/basic_rules.html)


## Good reporting
This means that you need to spend time on it. Preparation and effort
you spend on reporting, can help in pinpointing the actual problem.

More details:

  * How to Report Bugs Effectively  
    http://www.chiark.greenend.org.uk/~sgtatham/bugs.html


## Bug triaging
Assess quality of issue reports

  * incomplete
  * invalid
  * wont fix
  * duplicate


## Bug triaging
Deciding what bug should get fixed and when

  * priority


## Examples of bug tracking

  * Red Hat's Bugzilla  
    https://bugzilla.redhat.com/
  * Mozilla's Bugzilla  
    https://bugzilla.mozilla.org/
  * Launchpad  
    https://launchpad.net/


## Asking questions
When you ask a question, you are asking people to do you a favor.

People have no reason to help you


## Asking questions
... but in general hackers (aka programmers) will happily do so provided you:

  * show that you've done your homework
  * ask nicely
  * make it easy for them to understand what you need


## Before you ask
Try to find an answer

  * forum or mailinglists
  * Web (Google it)
  * read the manual
  * ...

[source](http://catb.org/~esr/faqs/smart-questions.html)


## Asking questions the smart way
Choose the place carefully

  * Ask OpenStack  
    https://ask.openstack.org/
  * Mailinglists  
    https://wiki.openstack.org/wiki/Mailing_Lists  
    https://lists.openstack.org/


## Asking questions the smart way

  * As part of an issue report

Try to avoid private discussions

  * IRC might be a better way


## How to ask
Similar to writing an issue report.

Be specific...

  * Use meaningful, specific subject headers
  * Make it easy to reply
  * Be precise
    * environment
  * Describe the problem's symptoms
  * Steps you performed
    * expectation


## Don't

  * Don't ask people to reply by private e-mail
  * Turn off HTML formatting !
  * Don't rush to claim that you have found a bug
  * Don't flag your question as “Urgent”
    * or describe “My company”

Email etiquettes will be discussed later in more detail.


## Do

  * Follow up with a brief note on the solution
  * Be courteous
    * “Please”
    * “Thanks for your attention”
  * Go for quality
    * avoid volume


## Email etiquettes

  * Don't send large attachements, such as screenshots
    * upload them to a remote service
    * prefer to use text format
  * Do not use HTML formatting
  * Allow for inline replying

More information:

  * Mailinglist etiquette  
    https://wiki.openstack.org/wiki/MailingListEtiquette


## Code reviews

  * examination of source code
  * to improve quality
    * overlooked problems
    * naming of variables

Reference:

  * Clean Code, Robert C. Martin
  * Agile practices


## Code reviews
a good way to get familiar to the code and project

All code is reviewed using Gerrit before merge

  * -2 / -1 / 0 / +1 / +2
  * Worflow
  * Merged


## Code contribution
Let's talk about code


## Well, source contributions

  * python
  * documentation
  * configuration

All is review as source contributions


## Contributions

  * When; roadmap or issue tracking
    * incremental

"Release Early, Release Often", this way you get feedback and
progress tracking is possible.


## OpenStack Blueprints
Blueprints are used to track the implementation of significant features

Current status is critical to the success of the release and the project
as a whole


## What you need to do

  * correctly working
    * Unit tests
  * coding style
    * PEP8
  * run unitests


## How to submit
You need to understand git and git-review

Will be discussed in a separate set of slides.

Reference:

  * http://docs.openstack.org/infra/manual/developers.html


## What will happen now
Your code is made public for review: http://review.openstack.org

  * unit tests run
    * indirect (gated)

Follow-up and be involved in the review process and make changes when necessary.
