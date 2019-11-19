
# About Skein

We partner with organizations of all sizes to design, develop, and grow innovative technology-based solutions for some of the worlds’ biggest challenges 

We have worked with hundreds of product teams all over the world, from individual founders who are self-funded, to large multi-national organizations. We have also created our own products and technologies to simplify your innovation process.

This is **How We Work**. It details how we make successful tech products, and also how we run our company.

It is a living document that everyone at Skein can edit in a private GitHub repo.


# Development

## Error Tracking

We use error tracking software to capture exceptions in production.
 
We try to use tools that support all of the languages and platforms we use to build applications, and those which provide integrations that make it easy to stay on top of errors. Such as Sentry's Slack integration for real-time alerts and Jira integration so we can prioritize bugs in the same place as features.
 
We like and use Sentry.
 
## Acceptance Tests

Acceptance tests are jobs stories turned into code. This code is run against the application. When executed for the first time, the test will fail. The developer writes application code until the test passes.
 
When the test passes, the developer commits the code into version control with a message such as:
 
>> Guest creates pledge
 
The code is then run on the Continuous Integration server to make sure the acceptance test still passes in an environment that matches the production environment.
 
Meanwhile, the code is pushed to the staging environment and the developer and customer representative smoke test it in the browser.
 
When the acceptance test is green for the CI server and you and any other designers, developers, or clients are satisfied that the jobs story is complete on staging, the feature can be deployed to production at will. This can result in features being pushed to production very frequently, and therefore more value is being delivered to customers sooner.
 
## Code Reviews

Here's the flow. Read our git protocol for the git commands.

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
 
When we write the fix and commit to version control again, we'll get a "passing build" alert in Slack and via email. Click the alert and we see the passing build.
 
Green is good.
 
A solid test suite is an absolute requirement for a web application. However, one major problem with test suites is that they get slow as they get large.
 
CI can ease the pain by distributing the test runs in parallel. We've had 45 minute test suites cut down to 2 minutes using this technique.
 
We've used CruiseControl, Integrity, Jenkins, and other CI libraries that we manage ourselves. This resulted in many hours of expensive attention.
 
Now, we use a combination of CircleCI and Travis CI (both for private repositories and open source) because of their great UIs, simple configuration and close integration with GitHub.
 
CI test runs are triggered when we push to Github and can be seen as part of the status checks of pull requests. We also use Hound to help us follow our style guide and keep review comments focused on improving the code quality.

## Pair Programming

Code that is written by two people who sit next to each other at the same computer is pair-programmed code. That code is considered high quality and should result in cost savings due to less maintenance.
 
In the long run, this style of development saves money because fewer bugs are written and therefore do not need to be fixed later.
 
An indication that pairing is beneficial and should be done more often is the following example:
 
When you are writing an important piece of code, don't you want another person to look it over before it goes into production?
 
While we don't pair program 100% of the time, we recognize the difficulty in acting as a team when we work at a distance from each other. There is no better collaboration between designers, developers, or between designers and developers than at the keyboard.

## Refactoring

The third step of the "red, green, refactor" step is refactoring, the process of improving the design of existing code without altering its external behavior. It's a critical step in the process, but often overlooked. We're so passionate about refactoring, we wrote an entire book on it, Ruby Science.
 
## Style Guide

We write code in a consistent style that emphasizes cleanliness and team communication.
 
High level guidelines:
 
- Be consistent.
- Don't rewrite existing code to follow this guide.
- Don't violate a guideline without a good reason.
- A reason is good when you can convince a teammate.
- Where we can, we set up Hound to help automate following the style guide during Code Review, which helps us stick to our high-level guidelines and keep our reviews focused on code legibility & quality.
 
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
 
Git is an open source source code control system written by Linus Torvalds. It's fast and great for working in branches.
 
We use GitHub for hosting our Git repositories.

## SSL Certificates

We want to ensure that our user's data is encrypted during transit and that the data they may provide is sent securely. The HTTPS-Only Standard provides a great, and much more detailed, description of the reasoning behind this.
 
This has become much easier with Let's Encrypt, which provides a free to use, automatic and secure certificate authority. It's integrated with Heroku, which allows us to use their Automated Certificate Management feature.
 
When we need wildcard certificates (e.g.: when we want to use the same certificate across www., staging., etc.), or those with advanced features, we use DNSimple.
 
## Transactional Email

We use SendGrid to have our application deliver email to users, known as transactional email.
 
Examples of transactional email are:
- Confirmations
- Follow ups after the first 3 days of use
- Free trial is expiring
- Message another user in the system
- We use SendGrid directly, not via the Heroku add-on, in order to avoid being lumped under the same IP group as others on Heroku (who might be misbehaving).
 
## Browser Testing and Support
 
We default to supporting the newest and the last previous two releases of popular browsers for desktop devices. 
 
Older versions are much harder, more time consuming and hence more expensive to design for, develop for and support.
 
In limited special cases, user demographics will dictate that supporting a less common or older version of a browser is required. Those special cases should be identified early on so we can plan for additional time and expense in order to support the version.
 
Browser support means that we make a site or web app usable. A usable site allows a user to achieve all necessary tasks. Support does not mean visual and behavioral parity across all browsers. While we may strive for this, it's not always possible to achieve the exact same user experience cross-browser.

# Process

We are a CCS supplier and follow agile delivery for tech innovation
https://www.gov.uk/service-manual/agile-delivery

## Agile Sprint-based delivery 

One of our primary process goals is to make frequent, small releases of our working software. We do through frequent communication and weekly iterations on a product.

## Discovery sprint

Finding ways to best resolve client challenges
Use cases
User personas
We use Figma to build flows and wireframes that will be used for screens

## How we work with Design

Fast prototyping - template. No design changes. Here that can be modified and used as a new website http://belmont.skein.co/
Proper design Sprint, based on Wireframes and user stories - pass over to partners (Rob etc)
While the latter approach is much more faster, but it can be used efficiently only in the case where colours, images and elements of the template are not changed, otherwise the overall look and feel will be negatively impacted; and if the template is kept as it is then obviously the unique aspect is lost. 

## Email

We use Gmail for our email.
 
## Calendar

We use Google Calendar for our calendars.
 
## Documents

We use Google Docs for our editable documents.
 
We prefer Google Docs because they are:
 
Easily sharable by URL. Everyone has a browser, not everyone has Microsoft Office installed.
Always up to date with the latest edits.
Enable real-time collaboration, like group meeting notes.
Autosaved to the cloud, so no worrying about backup.
Are as easy to find as Googling something.
Without document type versioning (e.g. xls vs. xlsx).
Cheap.
These tools are not well-suited for large documents or complicated spreadsheets, but broadly these are not problems we have. We write code and are biased toward minimal documentation and against upfront specs so we rarely write long documents.
 
We use Google Sheets for our company-wide budget and forecast. We also often use Google Sheets to collect or analyze other data. We can often create an initial version of something new there using IMPORTDATA and Heroku dataclips to avoid building a custom app.
 
## Meetings

We over-communicate with clients in-person and online to avoid having scheduled meetings. Every problem arises from poor communication.
 
When we need to meet for a discussion, we aim for 30 minutes spent in-person.
 
When working remotely, Google Meet are indispensable as the "next best thing". They are easy to set up, sharable by URL, and let us get a look at whoever we're talking to.
 
Screen-sharing is also very easy, when necessary. We have used Hangouts for client meetings, candidate interviews, and company meetings.
 
We use conference lines that are part of our VoIP system, provided by OnSip, for voice conferencing.
 
## Accounting

We use Xero.
 
Performance Reviews
In order to continually improve ourselves and the company, all year round on every project we're on, we receive regular feedback from clients, managers, and teammates. We additionally have formal performance review three times a year.
 
We use 15five to administer these reviews, which include a self-review, and feedback from both our manager and peers. The team feedback is shared with us before the review meeting.
 
The agenda for review meetings is roughly:
- Review the feedback from team members
- Our performance on recent consulting projects
- Our investment time contributions
- Our satisfaction with our work, projects, and the company
- Our questions about thoughtbot and our strategy
- Our areas of focus for the next quarter
- The results of the review are recorded and influence future compensation increases.

## Landin pages - questions to ask
 
Choice of CMS:
- Wordpress 
- Webflow

How much of edits for news/blog posts will you be making, that is how necessary a Content Management System is? We would ideally stick to a clean JavaScript implementation which will help the front-end to remain fast and SEO-friendly, as opposite to going with something like Wordpress which tend to create issues for page speed, which is in turn is a very important aspect these days for Google's Page Rank. For the platform front-end React looks like a perfect option (a Facebook-supported framework with huge community that provides a great Single Page Application implementation, and SEO-friendly among other advantages), so it would make sense to also use React for the front landing pages.

## How we work with data

User data protection
Secure servers and access
SSL 
Develop anonymisation

## Sprint proposal template
https://docs.google.com/document/d/1XevfXwI8wE-OdA0ehYJOw3n3irLYQ-xgcRtfKVDjqBA/edit?usp=sharing
User flow
Wireframes
Detailed estimate tasks a few hours each max
PM time
Team comm
Releases
Unit tests
