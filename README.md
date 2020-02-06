# Process

## Agile Sprint-based delivery 

We are a Crown Commercial Services supplier and follow agile delivery approach outlined at
[https://www.gov.uk/service-manual/agile-delivery ](https://www.gov.uk/service-manual/agile-delivery)

## Innovation

Creating new Intellectal Property for our clients is important, and work to understand client's business vision, research competitors and market, analyse existing patents and academic publications.

# Development

## Sprints

One of our primary process goals is to make frequent, small releases of our working software. We do through frequent communication and weekly iterations on a product. A development sprint usually lasts two weeks.

## Error Tracking

We use error tracking software to capture exceptions in production.
 
We try to use tools that support all of the languages and platforms we use to build applications, and those which provide integrations that make it easy to stay on top of errors. Such as Sentry's Slack integration for real-time alerts and Jira integration so we can prioritize bugs in the same place as features.
 
## Acceptance Tests

Acceptance tests are jobs stories turned into code. This code is run against the application. When executed for the first time, the test will fail. The developer writes application code until the test passes.
 
When the test passes, the developer commits the code into version control.
 
The code is then run on the Continuous Integration server to make sure the acceptance test still passes in an environment that matches the production environment.
 
Meanwhile, the code is pushed to the staging environment and the developer and customer representative smoke test it in the browser.
 
When the acceptance test is green for the CI server and you and any other designers, developers, or clients are satisfied that the jobs story is complete on staging, the feature can be deployed to production at will. This can result in features being pushed to production very frequently, and therefore more value is being delivered to customers sooner.
 
## Code Reviews

Here's the flow:

- Create a local feature branch based off master.
- When feature is complete and tests pass, stage the changes.
- When you've staged the changes, commit them.
- Write a good commit message.
- Share your branch.
- Submit a GitHub pull request.
- Ask for a code review in Slack.
- A team member other than the author reviews the pull request. They follow Code Review guidelines to avoid miscommunication.
- They make comments and ask questions directly on lines of code in the GitHub web interface or in Slack.
- When satisfied, they approve or comment on the pull request that it's ready to merge.
- Rebase interactively. Squash commits like "Fix whitespace" into one or a small number of valuable commit(s). Edit commit messages to reveal intent.
- View a list of new commits. View changed files. Merge branch into master.
- Delete your remote feature branch.
- Delete your local feature branch.

Test-Driven Development moves code failure earlier in the development process. It's better to have a failing test on your development machine than in production. It also allows you to have tighter feedback cycles.
 
Code reviews that happen right before code goes into master offer similar benefits:
1. The whole team learns about new code as it is written.
2. Mistakes are caught earlier.
3. Coding standards are more likely to be established, discussed, and followed.
4. Feedback from this style of code review is far more likely to be applied.
5. No one forgets context ("Why did we write this?") since it's fresh in the author's mind.
 
## Continuous Integration
 
We have a test suite that each developer runs on their own machine.
When they commit their code to a shared version control repository, the tests are run again, "integrated" with code from other developers.
This helps ensure there's nothing specific to the developer's machine making the tests pass. The code in version control needs to run cleanly in production later so before the code is allowed to be deployed to production, it is run on a CI server or service.
 
When a build fails, we get alerts in Slack and via email. Click the alert and we see a backtrace that gives us a hint of how to "fix the build."
 
When we write the fix and commit to version control again, we'll get a "passing build" alert in Slack. Click the alert and we see the passing build.
 
Green is good.
 
A solid test suite is an absolute requirement for a web application. However, one major problem with test suites is that they get slow as they get large.
 
CI can ease the pain by distributing the test runs in parallel. 

## Refactoring

The third step of the "red, green, refactor" step is refactoring, the process of improving the design of existing code without altering its external behavior. It's a critical step in the process, but often overlooked.
 
## Style Guide

We write code in a consistent style that emphasizes cleanliness and team communication.
 
High level guidelines:
 
* Be consistent.
* Don't rewrite existing code to follow this guide.
* Don't violate a guideline without a good reason.
* A reason is good when you can convince a teammate.
* Create documentation and meaningful comments that explain what the code does.
* Build reusable components.

 
## Test-Driven Development (TDD)
 
Business benefits of TDD:
- Deliver more value, faster
- Always ship working software
- Adapt to change quickly

Code benefits of TDD:
- Readable specs and code
- Clean public interfaces
- Decoupled modules

Process benefits of TDD:
- Regression safety net
- Fearless refactoring
- Team trust

At a high level, how to test is very simple:
- Write test first.
- Red-Green-Refactor cycle.
- For more specifics, we recommend our Test-Driven Rails workshop. It goes into incredible detail about the TDD workflow specifically for Ruby on Rails developers.
 
## Version Control

We always use source code control. It's like a time machine. We can work in parallel universes of our source code, experimenting without fear of losing work, rolling back if something goes wrong.

We use GitHub for hosting our Git repositories.

## SSL Certificates

We want to ensure that our user's data is encrypted during transit and that the data they may provide is sent securely. The HTTPS-Only Standard provides a great, and much more detailed, description of the reasoning behind this.

 
## Transactional Email

We use SendGrid to have our application deliver email to users, known as transactional email.
 
Examples of transactional email are:
* Confirmations
* Follow ups after the first 3 days of use
* Free trial is expiring
* Message another user in the system

 
## Browser Testing and Support
 
We default to supporting the newest and the last previous two releases of popular browsers for desktop devices. 
 
Older versions are much harder, more time consuming and hence more expensive to design for, develop for and support.
 
In limited special cases, user demographics will dictate that supporting a less common or older version of a browser is required. Those special cases should be identified early on so we can plan for additional time and expense in order to support the version.
 
Browser support means that we make a site or web app usable. A usable site allows a user to achieve all necessary tasks. Support does not mean visual and behavioral parity across all browsers. While we may strive for this, it's not always possible to achieve the exact same user experience cross-browser.

# Operations

## Email

We use Gmail for our email.
 
## Calendar

We use Google Calendar for our calendars.
 
## Documents

We use Google Docs for our editable documents.
 
We prefer Google Docs because they are:
 
* Easily sharable by URL. Everyone has a browser, not everyone has Microsoft Office installed.
* Always up to date with the latest edits.
* Enable real-time collaboration, like group meeting notes.
* Autosaved to the cloud, so no worrying about backup.
* Are as easy to find as Googling something.
* Without document type versioning (e.g. xls vs. xlsx).
* Cheap.

These tools are not well-suited for large documents or complicated spreadsheets, but broadly these are not problems we have. We write code and are biased toward minimal documentation and against upfront specs so we rarely write long documents.
 
## Meetings

We aim to over-communicate with clients in-person and online. Every problem arises from poor communication.
 
When we need to meet for a discussion, we aim for 30 minutes spent in-person.
 
When working remotely, Google Meet are indispensable as the "next best thing". They are easy to set up, sharable by URL, and let us get a look at whoever we're talking to.

 
## Accounting

We use Xero.
 
## Performance Reviews
In order to continually improve ourselves and the company, all year round on every project we're on, we receive regular feedback from clients, managers, and teammates. We additionally have formal performance review four times a year.
 

The agenda for review meetings is roughly:
- Review the feedback from team members
- Our performance on recent consulting projects
- Our investment time contributions
- Our satisfaction with our work, projects, and the company
- Our questions about thoughtbot and our strategy
- Our areas of focus for the next quarter

# About Skein

We partner with organisations of all sizes to design, develop, and implement innovative digital tech for some of the worlds' biggest challenges, that included in the past solutions for providing housing, improving healthcare, fixing financial systems. 

We have worked with over a hundred of product teams all over the world, from individual founders who are self-funded, to large multi-national organizations. We have also created our own products and technologies.

This is **How We Work**. It details how we make successful tech products, and also how we run our company.

It is a living document that everyone at Skein can edit in a private GitHub repo.
- The results of the review are recorded and influence future compensation increases.
