# LambdaClass Engineering Residency Self Learning Path

Welcome to the LambdaClass Engineering Residency Self Learning Path!.
It is similar to the original Self Learning Path but tailored to self-guided newcomers.

This guide consists of curated material to learn and put in practice.
There is written content, links to valuable online posts, selected book chapters, and projects with guidelines and tests.
To complete this self learning path and apply to the engineering residency, you must read the material from start to finish and develop the projects as you encounter them in their relevant sections.

The program is self-paced, but is designed to be doable in about a month of part-time dedication.
Once you have completed the program, you can let us know and we will schedule a few interviews to talk about your experience and go over your projects.

Completion of the program, that is, studying the material and completing the projects, enables you to interview with us but does not guarantee acceptance to the residency. 
Our goal when preparing this guide is to ensure that even if you are not accepted, you do take away what you learned as something valuable to your carreer as a software developer in these modern times.

---

## Table of Contents

- [LambdaClass Engineering Residency](#lambdaclass_engineering_residency)
  - [Table of Contents](#table-of-contents)
  - [Introduction](#introduction)
  - [Part I The Foundation](#part-i-the-foundation)
    - [Our Worldview and Company Culture](#our-worldview-and-company-culture)
      - [Attitude](#attitude)
      - [Ego, Learning to fail, and Your relationship with your own work](#ego-learning-to-fail-and-your-relationship-with-your-own-work)
      - [Principles for success and teamwork philosophy](#principles-for-success-and-teamwork-philosophy)
      - [Professionalism and Ethics](#professionalism-and-ethics)
    - [Practices at Lambda (for those that join the residency)](#practices-at-lambda-for-those-that-join-the-residency)
      - [Development processes and workflows](#development-processes-and-workflows)
      - [Design and coding standards](#design-and-coding-standards)
      - [Working on open-source projects](#working-on-open-source-projects)
      - [Learning Projects](#learning-projects)
    - [Technical Foundations](#technical-foundations)
      - [Development Environment](#development-environment)
        - [Homebrew](#homebrew)
        - [GNU tools](#gnu-tools)
        - [ASDF version manager](#asdf-version-manager)
        - [Code Editors and IDEs](#code-editors-and-ides)
      - [Software Engineering](#software-engineering)
        - [Complexity and KISS (Do The Simplest Thing That Could Possibly Work)](#complexity-and-kiss-do-the-simplest-thing-that-could-possibly-work)
      - [The Unix Philosophy](#the-unix-philosophy)
    - [Worse is Better](#worse-is-better)
      - [Linux](#linux)
        - [How to try some commands in MacOS with a VM](#how-to-try-some-commands-in-macos-with-a-vm)
      - [Networking and SSH](#networking-and-ssh)
      - [Version Control, Git, and Github](#version-control-git-and-github)
        - [Git](#git)
        - [GitHub and GitLab](#github-and-gitlab)
      - [Testing](#testing)
      - [Debugging, GDB, DTrace](#debugging-gdb-dtrace)
      - [Docker](#docker)
      - [Continuous Integration and GitHub Actions](#continuous-integration-and-github-actions)
      - [SQL and PostgreSQL](#sql-and-postgresql)
      - [Redis](#redis)
  - [Part II Specific Topics](#part-ii-specific-topics)
    - [Rust](#rust)
      - [Exercises](#exercises)
      - [Project - Rusty Merkle Tree](#project---rusty-merkle-tree)
      - [Project - Async Linkchecker](#project---async-linkchecker)
      - [Project - Rusty LC3](#project---rusty-lc3)
    - [Performance Engineering](#performance-engineering)
    - [Distributed Systems](#distributed-systems)
    - [The BEAM Ecosystem - Elixir](#the-beam-ecosystem---elixir)
      - [Phoenix](#phoenix)
      - [Project - Forth Interpreter](#project---forth-interpreter)
    - [General Cryptography](#general-cryptography)
    - [Blockchains](#blockchains)
    - [Bitcoin](#bitcoin)
    - [Ethereum](#ethereum)
      - [Introductory Material](#introductory-material)
      - [Ecosystem](#ecosystem)
      - [EVM](#evm)

---
## Introduction

> You can choose a life of ease and comfort or you can choose a life of service and adventure. When you're 90, which one of those things do you think you'll be more proud of? - Jeff Bezos

> My algorithm has always been: You put smart people together, you give them a lot of freedom, create an atmosphere where everyone talks to everyone else. They're not hiding in the corner with their own little thing. They talk to everybody else. And you provide the best infrastructure. The best computers and so on that people can work with and make everyone partners. - Jim Simons

> Top-down management leveraging command-and-control hierarchies are for the mahogany boardrooms of yesteryear. We are navigators, adventurers, and explorers of the future. We are married to the sea - Yearn's Blue Pill

> A boring codebase doesn't make a bored developer, on the contrary, it frees developers up to think about important stuff and deliver value to the business. Just as I want my language to be boring so I can focus on interesting stuff, I also want my tech stack to be boring - the interesting bits should be in the value added, not the stuff under that. - [HN](https://news.ycombinator.com/item?id=33215003)

Welcome! 

If you are reading this, you are probably giving your first -or second- steps on the long journey towards being a good developer, but first, try to be a good human being, and you will see how far that can get you.

This text is a guide intended to aid new hackers in their first steps on their journey to working on problems such as the ones LambdaClass focuses on. 
It will guide you in setting up expectations and working tools, and includes a whirlwind tour of the background knowledge necessary to work on the kinds of projects common at LambdaClass.
This comprises the first part of the path.

The second part is a repository of selected and categorized reference material, exercises, and projects for engineers at any stage.

---

## Part I The Foundation

### Our Worldview and Company Culture
Before tackling the technical challenges ahead of us, we realized that the most important things any institution aspiring to greatness must have are clear and shared values and principles. 
These characteristics, along with several others, define a company's culture.

In these pages, you will find these principles and values, which are expected of anyone who is part of this institution, whether they are a newcomer or a settled employee, an intern or a manager, and how to solve non-technical problems. 
LambdaClass is a company with high technical content, but this knowledge must be enhanced by cultural values that allow a fast identification of problems, as well as ways to solve them, based on different learnings and heuristics that many have experienced throughout this journey.

Since you are in a self-guided course, you may be tempted to skip or skim through these contents, but we strongly recommend that you do not do so. In fact, we recommend that you do not read all the culture sections at once, nor read each of them completely in the same day, but that you take the time to read and reflect on each text or video, especially thinking about the reason why we decided to ask you to review that content. During the interviews at the end of the residency, you will be asked questions related to them, not to check whether you have read them, but to see if you are a cultural fit with the company. In fact, if you join the residency, one of the aspects we will monitor is whether you are adapting to the company culture.

While this document aims to be useful, organized, and verified, it is important to note that knowledge and wisdom must be challenged, evaluated, and modified over time. 
The ideas in these pages are not set in stone but are constantly being assessed and seeking to be refuted or improved.

> c.f. [The Hacker Manifesto](http://phrack.org/issues/7/3.html). 

Many of the values we elaborate on stem from a central truth: our work only matters if it can be trusted.

We are part of a global effort to build open, secure, and equitable digital infrastructure—systems that may outlast us and serve people we'll never meet. That reach gives us both influence and responsibility: every decision we make must reflect precision, respect, and honesty.

We work on technologies that manage sensitive data, financial transactions, and trustless environments—tools that are redefining how information, value, and identity are handled worldwide. The choices we make ripple far beyond LambdaClass, directly affecting security, privacy, and access to information.

In the fields of blockchain, cryptography, and decentralized systems, maintaining trust is a foundational and non-negotiable principle. 
A single careless action can erode confidence not just in one project, but in the entire ecosystem that depends on it.

When we ask people to trust the systems we create, we are also asking them to trust us. 
That trust is earned only when every member of our team acts with integrity, safeguards information, and approaches their work with professionalism.

One of Lambda's core goals is the betterment of society via technology, and cryptography (and soon AI) are central to these goals.
- [Ergodic Group: Thesis](https://ergodicgroup.com/#thesis)
- [Ergodic Group: Theory](https://ergodicgroup.com/theory.html)
- [Lambda Crypto Doctrine](https://blog.lambdaclass.com/lambda-crypto-doctrine/)
- [Transforming the Future with Zero-Knowledge Proofs, Fully Homomorphic Encryption and new Distributed Systems algorithms](https://blog.lambdaclass.com/transforming-the-future-with-zero-knowledge-proofs-fully-homomorphic-encryption-and-new-distributed-systems-algorithms/)
- [Ethereum Series](https://federicocarrone.com/series/ethereum/)

#### Attitude
Attitude is how you feel, think, and what you believe regarding something; in other words, these things determine how you approach it.

Although the points we are going to discuss may seem obvious to someone with experience, most of the people who join us are trainees, meaning they have little or no experience in the development industry. 
Therefore, it becomes necessary to make these clarifications to ensure that everyone understands what we expect.

At Lambda, you'll be surrounded by highly skilled professionals. We focus on building a high-performance team, so everyone here excels at what they do. 
In fact, being exceptional is the standard, which creates a paradox—because in a sense, no one is truly exceptional. 
Achieving top grades and finishing your degree on time, being passionate about System Programming or Cryptography, or mastering coding skills may have brought you here, but they won’t suffice to ensure that you will continue to be a valuable team member. 
Everyone must continually prove they deserve to be part of this team.

Please don't interpret this point as an invitation to break rules, procedures, or timelines in the pursuit of excellence. 
While striving for exceptional performance is encouraged, it must be done within the boundaries of established guidelines. 
For example, completing the Learning Path in a week doesn't demonstrate mastery — it only shows that you rushed through the content without taking the time to truly absorb it. 
You won’t gain a deeper understanding by rushing through it. 
Additionally, we explicitly address the importance of ethical conduct, and cutting corners is never acceptable.

There are three key elements we want you to have present at every moment:
*Communication, Accountability, and Empathy*.
- **Communication** is a key aspect of every human relationship. If you can measure your words to give a positive, clear message, you can achieve anything in life through teamwork. Try labeling your emotions before communicating, since it is likely that people in front of you do not know what is going through your head. Also, be transparent but assertive if you disagree about something, as it will help your coworkers understand your point of view. Finally, try to avoid direct messages; working on channels allows more people to be in the loop, and better feedback can be given.
- **Accountability**. Everyone makes mistakes; learners do something about them. If you get something wrong, communicate poorly, or even feel overwhelmed about a situation, raise your hand and say it. A process likely failed, not you. Many people will be there to help you sort out the issue, and you will surely learn something along the way. If you keep quiet and don't say anything, you will regret it later when the truth bursts through another hole.
- About **empathy**, we are all human beings and have complex emotions; if you are feeling great, it doesn't mean your colleague isn't feeling like shit. Perhaps your coworkers don't feel comfortable talking about emotions, so go talk with them and help them. You can talk to them or their manager if you feel something is going on with them. There is a time when everybody feels weak and needs someone else for support. So be a hero, be empathic.

Also, remember our core principles are:
1. We hire fast, fire faster, promote the fastest. 
2. Adhere to the truth and be transparent
3. Do what is right for the product.

#### Ego, Learning to fail, and Your relationship with your own work
Those truly exceptional at Lambda are the least likely to believe they are. 
You may know how to code, but dealing with your own perception and emotions is a soft skill that appears more rarely in young developers. 
Trust is earned over time, skills are learned and perfected over time, outliers in one context may not be so in another, and being an excellent team member and understanding one’s role in an organization is more important than standing out.

Excellence is a habit, and no one is above making mistakes. 
These two facts together lead to an important conclusion: to be exceptional, it's crucial to learn from your mistakes. 
This starts with acknowledging them. 
Making mistakes isn’t the same as failing—pretending they didn’t happen is. 
Mistakes are an essential part of learning; you can’t grow without them. 
The next step is communicating them. 
Your work impacts others, so if you make a mistake, it’s important to acknowledge it. 
This not only makes it easier for others to help, but it also shows accountability.

On the other hand, self-doubt can also become unhelpful and crippling. 
We can guarantee that almost everyone at Lambda is constantly asking "how can I be better?" of themselves, but believing you don't belong will eventually lead to making it true.

As with most projects, making mistakes fast and loudly will make you learn faster; this is why you must work directly on a repository through Pull Requests rather than workshopping in a draft made elsewhere.
- **Avoid google docs**. Work directly with Git, it will help get more eyes on your work to get corrections earlier.
- **Default to git**. As said earlier, Git snapshots your work and makes it more accessible to the public; more eyes means more people eager to help you.
- **Avoid asking questions in private chats**: asking in the project channel is much better, as the question can be answered by anyone, more voices are heard, others with the same questions may also benefit from the answers, and finally, the discussion, if worthwhile, can be captured as documentation.

Much is said about the Dunning-Kruger Effect and Impostor Syndrome, but the important points can be boiled down to:
- Keep your ego in check
- Learn to fail, and learn from mistakes
- Learn from others and help others in need
- Listen to feedback and do not worry about evaluating your own performance

Some resources on this topic:
- [Dunning Kruger effect in Software development life cycle.(SDLC)](https://www.linkedin.com/pulse/dunning-kruger-effect-software-development-life-cyclesdlc-rauf-rahman/)
- [Software engineers suffer from Dunning-Kruger - do you too?](https://www.dateo-software.de/blog/dunning-kruger)
- [What Is Programmer Imposter Syndrome and How Can You Deal With It?](https://www.turing.com/blog/programmer-imposter-syndrome-tips)

Developing equanimity and focusing on the truth revealed by results is The Lambda Way.
You’ll come across more lessons on this throughout your learning path.

#### Principles for success and teamwork philosophy
We follow a code of conduct designed to ensure a safe team environment. 
Basically, treat everyone with respect.
- [Principles for success by Ray Dalio](https://www.youtube.com/embed/B9XGUpQZY38)
- [Charity Majors - The Sociotechnical Path to High-Performing Teams](https://www.youtube.com/watch?v=oV8VSBSBrr4)
- Chapter 1 of [Antifragile: Things That Gain from Disorder](https://www.amazon.com/Antifragile-Things-That-Disorder-Incerto/dp/0812979680)
- [Citogenesis in science and the importance of real problems](https://lemire.me/blog/2023/06/14/citogenesis-in-science-and-the-importance-of-real-problems/)
- Chapter 1 of [Data science in Julia for hackers](https://datasciencejuliahackers.com/)
- [The Biggest Mistake I See Engineers Make](https://web.archive.org/web/20220125174724/https://www.thezbook.com/the-biggest-mistake-i-see-engineers-make/)
- [The XY Problem](https://xyproblem.info/)
- [The Sunk Cost Fallacy](https://thedecisionlab.com/biases/the-sunk-cost-fallacy/)
- [The most important goal in designing software is understandability](https://ntietz.com/blog/the-most-important-goal-in-designing-software-is-understandability/)
- [How to Make Your Code Reviewer Fall in Love with You](https://mtlynch.io/code-review-love/)
- [How to Do Code Reviews Like a Human](https://mtlynch.io/human-code-reviews-1/)

#### Professionalism and Ethics
Just reading this subsection title, you can feel your eyes rolling back into your head. What does an attitude of "hack the planet" have to do with the words "professionalism" and "ethics"?

Well, the lone hacker may be romantic, but great things only come from working together. At Lambda, we foster a youthful, relaxed, and collaborative environment to make sure that we _can_ work together, and _because_ of this, professionalism and ethics are non-negotiable, whether you're 18 or 40. 

We'll elaborate, but a tl;dr boils down to:

- Work towards making your environment better than the way you found it. This ranges from cleaning tableware used at the office to helping others with your strengths.
- Deliver high-quality work and take ownership of responsibilities.
- Safeguard confidential information — never share or sell it to competitors. If you're unsure whether something can be disclosed, always check with your manager first.
- Respecting intellectual property, crediting others' contributions, and protecting confidential information—never sharing or selling it to competitors.
- Stealing, in any way, is explicitly forbidden and is grounds for immediate dismissal. This includes stealing software from other projects, open source or not, without attribution or credit.
- Times are changing fast, and we always encourage trying out new tools, but at Lambda, using code provided by AI or LLMs is strictly forbidden. You can still use LLMs for other purposes, but copilot-style integrations, which write code for you, are a net loss, as they are not accountable regarding where they get their inspiration from and do not understand code licensing issues.

As with all things, this is learned over time, with experience, and from others.
If you are ever in doubt, ask your managers, tech leads, and mentors.

So what _is_ professionalism?

Professional behavior is being considerate, formal, and focused. In other words, putting constraints on behavior to enable something else. What exactly?
A professional attitude makes you trustworthy and reliable. Clients and colleagues prefer to work with people who are polite and dependable.
When you are known as somebody reliable, you’re more likely to be given added responsibilities and opportunities, and can make faster progress in your career. 

Some of the most professional traits:

- Self-awareness of your behavior: The most important part of creating a professional reputation is showing that you behave well when at work. Every workplace has different rules, guidelines, and culture, and may be more or less relaxed, but some universally applicable tips are:
  - Be aware of others' personal boundaries.
  - Remain calm and unemotional. 
  - Be punctual when coming to work, arriving at meetings, or joining calls, to respect others' time. 
- Excellent communication: misunderstandings lead to lost productivity, so a professional always makes the effort to be understood.
- Honesty: Be open and honest, even during difficult conversations. Being able to confront people directly, rather than share your grievances about them with other people, is important in maintaining a professional attitude. 
- Integrity: Always tell the truth. Personal accountability is owning the outcomes of your decisions and is closely related to honesty and integrity. Although you should try to do your best, everyone makes mistakes. When you do, taking responsibility and offering ways to fix errors and prevent them in the future will help colleagues and supervisors maintain their trust in you. 
- Be respectful to others: treating others with respect and kindness is part of getting your ideas across, regardless of who you are interacting with. You don't have to like everyone, or be liked by everyone, but you do have to treat them well, no matter what their role is. Respecting others also includes supporting them when they need it and being generally helpful, since this furthers the group's goals, not individuals'. 
- Be a dependable team player: Come prepared and plan ahead. Build a reputation as someone who keeps their word and can be trusted to deliver on commitments and deadlines. Failing to follow through can have serious consequences for those who depend on your work. When things don’t go as planned, don’t make excuses—take responsibility, do your best to get tasks back on track, and communicate early if you need additional support or resources.
- Flexibility: Commitment to your role also means being adaptable when circumstances change. As projects move forward, plans, goals, and requirements may shift, and you are expected to maintain professionalism throughout. At times, this may require adjusting your schedule—such as staying late to ensure a task or deadline is met.
- Competency and a strong work ethic: Being highly skilled may be the first thing one thinks of in a professional. To be dependable, one first needs to be capable, so as not to leave others picking up the slack or doing more than their share of the work. Over time, keeping knowledge and skills up to date is also expected of a professional. No amount of highly specialized knowledge will compensate for this. Check your work for any errors before submitting it.

### Practices at Lambda (for those that join the residency)

#### Development processes and workflows
- There is a weekly call with every member of the team to set the most important goals of the week, as well as a daily call to focus on the problems of the daily tasks.
- When working on projects, the specific tasks to tackle are written in tickets on Github Projects. Some actual Lambda's projects are working on other project management software, but these are legacy.
- There are regular 1-on-1 meetings to check on your well-being and how you're feeling at Lambda. These are not instances where you receive feedback. Feedback at Lambda is an ongoing process; you'll be recognized for what you're doing remarkably well or corrected if you're making a mistake. The idea of the 1-on-1 meetings is explained in Chapter 1 of [The Manager's Path](https://www.amazon.com/Managers-Path-Leaders-Navigating-Growth/dp/1491973897/ref=sr_1_1?dchild=1&keywords=the+managers+path&qid=1625162711&s=books&sr=1-1)

#### Design and coding standards
- [The Basics](https://matklad.github.io/2024/03/22/basic-things.html)
- [make is the build tool](https://medium.com/@jlouis666/how-to-build-stable-systems-6fe9dcf32fc4).
- Postgresql is the default database.
- Write tests.
  - Favor integration tests over unit tests. A project's first tests should be end-to-end smoke and sanity tests, and only after that, if ever, should unit tests be written to test API's, system invariants, and help pinpoint bug causes and locations.
  - Do not write tests before you have solved the problem; you may waste time writing tests for the wrong implementation.
- Write for humans: coding for computers is easy, but writing code that is understandable by another person is an art.
- Code and document in English unless you have a very specific reason not to.
- Use meaningful, readable names for variables, functions, and files. Don't try to save characters.
- Documentation is a sign of the quality of an API. It's easier to write it when the design is right.
- [The less code you have the better. Deleted code is debugged code](https://suckless.org/philosophy/).
- Aim for simplicity, not performance. The latter is a by-product of the first.
- Only introduce optimizations if you have benchmarks that prove an improvement, and that the improvement is relevant in the context of the program.
- Only introduce optimizations if they represent a concrete gain (e.g., cost savings, improved user experience).
- Follow the [Zen of Python](https://www.python.org/dev/peps/pep-0020/), regardless of the language you are using at the moment. English also counts as a language.
- Don't introduce dependencies prematurely. You must evaluate your requirements, maintenance, and integration costs first.
- If you want to upgrade a dependency, test it first.
- Always lock your dependencies. Pin a specific version and a commit of a dependency, don't use the version at master.
- In general, avoid pinning the patch version of dependencies; more info [here](https://semver.org/).
- Use git and commit often, even in one-person projects.

#### Working on open-source projects
- Use MIT or Apache 2.0 license.
  - [Apache vs MIT](https://snyk.io/learn/apache-license/)
  - [How to make sense of the Apache 2 patent license](https://opensource.com/article/18/2/apache-2-patent-license)
- Fill the description field at the top of the repo page.
- Write a decent README.
- A good README starts with a succinct description (one or two sentences) and, whenever possible, a very short and illustrative example use. The rest of the details go after this header.
- Use continuous integration, most likely GitHub Actions.
- Make a good balance of features vs maintenance. Maintenance details usually matter more than adding a lot of features.

#### Learning Projects Guidelines

The learning path is not just a pile of material to read through, actually coding the projects is key to your learning process.
The only way to learn how to do this is via practice, and since small exercises can only exercise very specific things, there are a few larger projects throughout the learning path that newcomers are expected to complete. 
These projects are located in the respective section for their language.

The point of gaining knowledge is to be able to *do* more things and apply them in problem-solving.
If you do not actually do the practice, and either copy your work or rely on LLMs to generate the solution, you will gain nothing.
At the end of the residency, during interviews you may be questioned on decisions you made during the implementation process.

When the time comes to start one of the projects, please follow these steps:
- Create a new github repository under your personal account.
- Set up the project skeleton, which will vary depending on the language and tech stack used for the project. In all cases, the skeleton should include:
  - A `README.md`: Create some initial documentation that explains what the repository contains.
  - A `Makefile`: a Makefile with standard targets (`build`, `run`, `test`) will allow anyone, regardless of familiarity with the commands specific to your language, to run the project.
  - A code skeleton: even a "hello, world!" program will allow exercising the build, running, and testing targets.
  - CI: Part of learning a language or tool includes knowing how to automate the tasks of ensuring that a code change compiles and passes the tests. Since we host these learning projects on Github, the initial PR should include configuration for Github's Continuous Integration platform Actions to run after each change you commit to a PR.
  - Issues: Once you understand the project, create issues for the identifiable parts of the implementation solution. 
- Branches:
  - Immediately create a `dev` branch, in addition to the `main` one. Learning projects have two separate phases: the first is active development. During this phase, your PRs should branch from and merge into `dev`. Once your MVP has been achieved, and all the required base functionality is implemented, create another PR from `dev` into `main` with the entirety of the code developed during the first phase. This PR will be reviewed when you complete the Self Learning Path.
  - When tackling an issue, immediately create a branch for it, push it and open a PR in draft mode. Having an open PR that is not yet up to review is a good practice because it allows following the work, and provides a venue for discussion and comments even before a review takes place. 
  - At Lambda, repositories are automatically configured to delete branches once corresponding PRs are merged. Since learning projects are done under your user account, you must either configure this yourself or delete branches manually after merging. Allowing stale branches to accumulate is generally considered a bad practice. 
  - Another requirement is configuring branch protections for `main` and `dev` branches. Your CI must have jobs for ensuring that the code is formatted correctly according to the language's formatter, compiles, and passes tests. Each of these should be a separate job and required for merging a PR. 
- For a PR to be eligible for merging, it must at least:
  - Have a good description of its contained changes.
  - Compile, have no failing tests and pass all CI checks.

Usually, your PRs would be reviewed by your peers but since you are self-learning, you may exceptionally auto-merge your PRs. 
Why create PRs instead of pushing straight to main? Why simulate the development process?
Part of the reason is to teach what a normal flow looks like, although it feels like playing pretend with no friends. 
Another is giving reviewers enough information to go through your history.
The better your commit messages and PR descriptions, the better your project looks and the easier it is to evaluate!
The goal of doing all this for a learning project is to allow reviewers to skip the more basic corrections and address more meaningful corrections, and to make you familiar with the basic expectations and workflow of any project at LambdaClass. 

---

### Technical Foundations

#### Development Environment
We use a suite of tools to facilitate many tasks, as well as to enforce our security standards for all employees.

Before beginning with this Journey, if you're a macOS user, you may need some tools or utils for a better experience in your learning path, otherwise, you can skip this section.

##### Homebrew
[Homebrew](https://brew.sh/) is a package manager for macOS. It is a must on any developer machine.

##### GNU tools
Once you have installed Homebrew in your macOS system, you'll need to install some of the GNU tools/utilities for a better work experience. 
Just type in your shell the following command lines:
- [*coreutils*](https://www.gnu.org/software/coreutils/): `brew install coreutils`
- [*inetutils*](https://www.gnu.org/software/inetutils/): `brew install inetutils`

##### ASDF version manager
- [asdf](https://asdf-vm.com/guide/getting-started.html) is a version manager with the idea purpose of generating environmental variables to choose the specific version desired. Remember that to be able to use the environmental variables you need to set their path for the shell to check, you can see how to do it depending on how you installed asdf [here](https://asdf-vm.com/guide/getting-started.html#_3-install-asdf).

##### Code Editors and IDEs
**Do's and don'ts about the use of Vertical Whitespace**
- If you'd like to visualize more vertical whitespace than it's established in these Do's and don'ts configure your text editor to show more space.
- Most of these rules can be enforced automatically in your text editor, configure it to enforce them.
- Minimize the use of vertical whitespace.
- Do not end functions with blank lines.
- Do not start functions with blank lines.
- Do not use blank lines when you do not have to.
- Do not put more than one blank line between functions.
- Blank lines inside a chain of if-else blocks may well help readability.
- Blank lines at the beginning or end of a function very rarely help readability.
- Don't leave blank lines at the end of a file.
- Don't forget to put a *single* end of the line at the end of a file.

#### Software Engineering
- [Basic Things](https://matklad.github.io/2024/03/22/basic-things.html)

##### Complexity and KISS (Do The Simplest Thing That Could Possibly Work)
> "Always implement things when you actually need them, never when you just foresee that you need them" - Ron Jeffries

Strive for solving problems in the simplest way possible. To achieve this, you first need to figure out a handful of ways to confront the issue at hand, and only then pick the one you consider will work in the fewest, tiniest steps.
Afterwards, refactor. 
Tomorrow’s code may need to be more complex, so do everything in your power to facilitate tomorrow’s code as simple as possible.
Also, while you shouldn't be blind to the future, avoid investing time and effort into developing features that are not currently necessary and might be a waste.
- [Do The Simplest Thing That Could Possibly Work](https://www.artima.com/articles/the-simplest-thing-that-could-possibly-work)
- [YAGNI by Martin Fowler](https://martinfowler.com/bliki/Yagni.html)
- [The two root causes of software complexity](https://pressupinc.com/blog/2014/05/root-causes-software-complexity/)
- [Encapsulated vs systemic complexity in protocol design](https://vitalik.eth.limo/general/2022/02/28/complexity.html)
- [Practices of Reliable Software Design](https://entropicthoughts.com/practices-of-reliable-software-design)
- [Exit the Haunted Forest](https://increment.com/software-architecture/exit-the-haunted-forest/)
- [Constraints and guarantees](https://jfmengels.net/constraints-and-guarantees/)
- [Hyrum's Law](https://www.hyrumslaw.com/)
- [Cognitive Load is What Matters](https://minds.md/zakirullin/cognitive)
- [Software Design is Knowledge Building](https://olano.dev/blog/software-design-is-knowledge-building/)
- [Write Code that is easy to delete not easy to extend](https://programmingisterrible.com/post/139222674273/write-code-that-is-easy-to-delete-not-easy-to)
- [Negotiable Abstractions](https://ferd.ca/negotiable-abstractions.html)
- [How complex systems fail](https://www.adaptivecapacitylabs.com/HowComplexSystemsFail.pdf)

#### The Unix Philosophy
- [Unix Timeline](https://upload.wikimedia.org/wikipedia/commons/c/cd/Unix_timeline.en.svg)
- [Basics of the Unix Philosophy](http://www.catb.org/~esr/writings/taoup/html/ch01s06.html)
- [Modularity](http://www.catb.org/~esr/writings/taoup/html/modularitychapter.html) (Whole chapter)
- [Transparency](http://www.catb.org/~esr/writings/taoup/html/ch06s02.html)

### Worse is Better
- [Wikipedia: Worse is Better](https://en.wikipedia.org/wiki/Worse_is_better)
- [Worse is Better](https://www.dreamsongs.com/WorseIsBetter.html)
- [Worse is Better is Worse](https://www.dreamsongs.com/Files/worse-is-worse.pdf)
- [Is Worse Really Better?](https://www.dreamsongs.com/Files/IsWorseReallyBetter.pdf)
- [Worse is Better vs. Better is Better](https://andrumyers.wordpress.com/2014/09/20/worse-is-better-vs-better-is-better/)
- [What "Worse is Better vs The Right Thing" is really about](https://yosefk.com/blog/what-worse-is-better-vs-the-right-thing-is-really-about.html)
- [Worse is Better (is Worse (is Better))](https://olano.dev/blog/worse-is-better-is-worse-is-better)

**Some questions to guide your learning**
- How does complexity relate to modularity?
- Why is the text-stream interface important in the Unix Philosophy?
- Why should design for transparency encourage simple interfaces?
- How does robustness relate to transparency and simplicity?
- Even now with video processing, why output of programs should be terse?
- According to the Unix Philosophy, how noisy do errors have to be?
- How does the economy of programmer time relate to robustness?
- Why premature local optimization reduces overall performance?
- There is the approach of doing things in "one true way", how does it affect extensibility?

#### Linux
If you're a macOS user and you've already installed GNU-tools, there's no need to install Linux on a VM.
- [The Linux Command Line](https://nostarch.com/tlcl2)
  - Chapters [1-7], [9-10], 14, [16-17] Basic shell usage
- [Linux Basics for Hackers](https://nostarch.com/linuxbasicsforhackers)
  - Chapters [8-10] Bash scripting, Filesystems, and compression

##### How to try some commands in MacOS with a VM
1. There are some commands that don't work in MacOS. If you want to try them, you can use a VM to use Linux. For this, we can use [UTM](https://mac.getutm.app/). Follow the next steps [here](https://docs.getutm.app/guides/ubuntu/).
2. After the installation is complete, close the VM and press “Stop selected VM”.
3. Run the VM again.
4. Now you can use this VM to run the commands.

**Some questions to guide your learning**
- What do the following commands do?:
  - `ls -l /bin/usr > ls-output.txt 2>&1`
  - `ls /bin /usr/bin | sort | uniq | less`
  - `ls /bin /usr/bin | sort | uniq | grep zip`
- How does Linux determine how to interpret the format of a file?
- What does the `sda2` folder represent?
- What do `/root` and `/usr/bin` store?

#### Networking and SSH
- [How the Internet Really Works](https://www.amazon.com/Cats-Guide-Internet-Freedom/dp/1718500297)
  - Chapters [1-5] (RECOMMENDED)
- [Practical Packet Analysis with Wireshark](https://nostarch.com/packetanalysis3)
  - Chapters 1, [3-4], [7-10]
- [Burp](https://www.youtube.com/watch?v=G3hpAeoZ4ek)

**Some questions to guide your learning**
- How are data transmitted over the Internet?
- What functions do the layers of the OSI model perform?
- What is the difference between TCP and UDP?
- What does ARP mean?
- What range corresponds to private IP addresses?
- What does IPv6 propose to solve against IPv4?
- What does IPsec guarantee?
- What does DNS mean? How does it work?
- What is the difference between HTTPS and HTTP?
- What is the difference between asymmetric and symmetric cryptography?

#### Version Control, Git, and Github

##### Git
**No one** should merge his/her own PR without it being reviewed and approved by a co-worker and/or a client. However in this selfguided course you're going to do just that. Please realize that this is a special scenario, and usually you should never merge your own PRs without being reviewed by a peer.

*Note: commit and **push** every day. Don't expect something perfect, go for the concrete. In one way or another, you will likely have to iterate later about that work done. Also, since that work isn't only stored on your computer, it won't be lost.*

- [Introduction to GitHub](https://github.com/skills/introduction-to-github) (MUST)
- [Development workflows in GIT](https://docs.google.com/document/d/1k11yRykUpFjNEycxmjZbvg4piFqWAnjzujCmFXiK3ns/edit?usp=sharing)
- [The Git Parable](https://tom.preston-werner.com/2009/05/19/the-git-parable.html)
- Pages [10-50] of [Pro Git](https://git-scm.com/book/en/v2)
- [Learning Git Branching](https://learngitbranching.js.org/)
- [Git Exercises](https://jvns.ca/blog/2019/08/30/git-exercises--navigate-a-repository/)
- [How to write a Git Commit message](https://chris.beams.io/posts/git-commit/)
- [Merging vs Rebasing](https://www.atlassian.com/git/tutorials/merging-vs-rebasing)
- [Configure your end of line (EOL) management in your development environment](https://docs.github.com/en/get-started/getting-started-with-git/configuring-git-to-handle-line-endings)

**Note on Newlines at end of file**
It is considered good style - and sometimes a necessity - to always end files with a newline (see [here](https://stackoverflow.com/questions/729692/why-should-text-files-end-with-a-newline) and [here](https://gist.github.com/camh-/1bebfcff1b0f814e9b191edc60d5206b)).
Make sure your editor of choice is correctly configured to add them automatically.

**Some questions to guide your learning**
- Why is branching necessary?
- What is the difference between `merge` and `rebase`?
- What is a stash?
- What does `cherry-pick` do?
- What does `reflog` do?
- What does `git reset --hard HEAD` do?
- How to get back to a previous commit?
- How to do a pull request?
- Why are pull requests important?
- How to clone a repository using SSH?

##### GitHub and GitLab
Before you continue on your Git journey and learn how to use git together with GitHub, it is important to learn what an SSH Key (Secure Shell Key) is and how to generate one and add it to your GitHub account.
This key will allow you to connect and authenticate to remote servers and services using the SSH protocol. With it, you will be able to connect to GitHub without supplying your username and personal access token each time.
- [SSH Keys for GitHub](https://jdblischak.github.io/2014-09-18-chicago/novice/git/05-sshkeys.html)
- [Adding a new SSH key to your GitHub account](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account)
- [Authorizing an SSH key for use with SAML single sign-on](https://docs.github.com/en/enterprise-cloud@latest/authentication/authenticating-with-saml-single-sign-on/authorizing-an-ssh-key-for-use-with-saml-single-sign-on#)

Once you have an SSH key associated with your GitHub account, managing it will become a pain.
The most basic next step is learning that instead of entering your SSH passphrase every time you have to authenticate, you can tell your operating system's SSH Agent to remember it for you and provide it.

In addition, you can tell 1password to manage it as well: [instructions](https://developer.1password.com/docs/ssh/get-started/).

Once your system is configured to use the 1password SSH agent with your key, you can configure your local git client to use the SSH key to sign your commits, ensuring that your authorship of the code is verified.
You can find the instructions [here](https://developer.1password.com/docs/ssh/git-commit-signing/).

If you have existing commits that you need to push but have not been signed yet you can run the following command:
```
git rebase -i --exec "git commit --amend --no-edit -S" main
```

- Progress in any project must be pushed every day. This must be done within a branch of the master repository and a Pull Request (PR) must be opened for reviewing the code, previous to merging the branch to master.
- Doc files should always be added via pull request.
  - Be sure those files are written in Markdown. 
  - We always use [Mermaid](https://mermaid-js.github.io/mermaid/#/README) for flowcharts, sequence diagrams, graphs, etc.
- Never push to master directly, and only reviewers can merge branches to master.

#### Testing
- Test-driven Design
- Unit testing
- Integration testing
- Property-based testing
- Fuzzy Testing

#### Debugging, GDB, DTrace
- [The Debugging Mindset](https://queue.acm.org/detail.cfm?id=3068754) Understanding the psychology of learning strategies leads to effective problem-solving skills.
- [Give me 15 minutes and I'll change your view of Linux tracing](https://www.youtube.com/watch?v=GsMs3n8CB6g)
- [Introduction to gdb](https://youtu.be/xQ0ONbt-qPs)
- [Ptrace syscall example](https://www.linuxjournal.com/article/6100)
- [Using Dtrace on MacOS](https://poweruser.blog/using-dtrace-with-sip-enabled-3826a352e64b)
- [Tracing in Linux and macOS](https://web.archive.org/web/20220228193322/https://blog.xfbs.net/posts/tracing-linux-macos)
- [Ptrace](https://refspecs.linuxbase.org/LSB_5.0.0/LSB-Core-generic/LSB-Core-generic/baselib-ptrace-1.html)
- [Dtrace One Liners](https://www.brendangregg.com/dtrace.html#OneLiners)

#### Docker
- [Getting Started](https://www.youtube.com/watch?v=iqqDU2crIEQ)
- [Anti-Patterns When Building Docker Images](https://jpetazzo.github.io/2021/11/30/docker-build-container-images-antipatterns/)

**Some questions to guide your learning**
- In which scenarios would you use containers and in which you would prefer to use VMs?
- How do you retrieve and run the latest Ubuntu image?
- In a Dockerfile, what is the difference between `RUN` and `CMD`?
- Using port 8080, how do you run an image that exposes port 80?

#### Continuous Integration and GitHub Actions
- [About continuous integration](https://docs.github.com/en/actions/automating-builds-and-tests/about-continuous-integration)
- [Understanding GitHub Actions](https://docs.github.com/en/actions/learn-github-actions/understanding-github-actions)
- [Quickstart for GitHub Actions](https://docs.github.com/en/actions/quickstart)

#### SQL and PostgreSQL

- [SQL Bolt](https://sqlbolt.com/) (RECOMMENDED)
- [Mystery solver with SQL](https://mystery.knightlab.com/) (PRACTICE-RECOMMENDED)
- Chapters [10-11] from [SQL: Practical Guide for Developers](https://www.amazon.com/SQL-Practical-Guide-Developers-Guides/dp/0122205316)
- The introduction, chapter 2, and days 1 and 2 from chapter 8 of [Seven Databases in Seven Weeks](https://www.amazon.com/Seven-Databases-Weeks-Modern-Movement/dp/1934356921)

> Reference:
>- [SQL Cheatsheet](https://hackmd.io/POclvM30TbCT2IpB81a6bg)

**Some questions to guide your learning**
- How to use a wildcard as a character?
- What does `COALESCE` do?
- What does `LIKE 'S%'` do in a query?

#### Redis

- [Introduction to Redis performance](https://www.youtube.com/watch?v=-5RTyEim384)
- [An introduction to Redis data types and abstractions](https://redis.io/topics/data-types-intro)
- [Redis Transactions](https://redis.io/topics/transactions)
- [Redis Cheatsheet](https://cheatography.com/tasjaevan/cheat-sheets/redis/pdf/)

**Some questions to guide your learning**
- What is the difference between PostgreSQL and Redis?
- What type of databases are the following? PostgreSQL, Redis, MongoDB, MySQL, HBase, Neo4J, DynamoDB.
- What makes each database type unique?

---
## Part II Specific Topics

---
### Rust

There are now many books on Rust and specific topics within Rust but we consider the following to be of the highest quality/relevance, and required reading:
- [Comprehensive Rust](https://google.github.io/comprehensive-rust/) Days 1-4
- [The Rust Brown Book](https://rust-book.cs.brown.edu/) Chapters 1-19
- [Learning Rust: Mindsets and Expectations](https://ferrous-systems.com/blog/mindsets-and-expectations/)
- [A half-hour to learn Rust](https://fasterthanli.me/articles/a-half-hour-to-learn-rust) Basic syntax, very easy if you know C language
- [Three Kinds of Polymorphism in Rust](https://www.brandons.me/blog/polymorphism-in-rust)
- [Some mistakes Rust doesn't catch](https://fasterthanli.me/articles/some-mistakes-rust-doesnt-catch)
- [Learning Rust](https://learning-rust.github.io/) Example project
- [Guide on how to write documentation for a Rust crate](https://blog.guillaume-gomez.fr/articles/2020-03-12+Guide+on+how+to+write+documentation+for+a+Rust+crate)
- [2020 Rust Starter Kit](https://wiki.alopex.li/RustStarterKit2020)
- [Ferrous Systems' Elements of Rust](https://github.com/ferrous-systems/elements-of-rust)

The following resources are NOT required reading but may be useful during the development of your projects:
- [cheats.rs](https://cheats.rs/)
- [Rust by Example](https://doc.rust-lang.org/stable/rust-by-example/)
- [Rust Cookbook](https://rust-lang-nursery.github.io/rust-cookbook/)
- [Rust 101](https://www.ralfj.de/projects/rust-101/main.html)
- [Programming Rust 2nd Ed](https://www.oreilly.com/library/view/programming-rust-2nd/9781492052586/)
- [Rust for Rustaceans](https://nostarch.com/rust-rustaceans)

#### Exercises

The rustlings are a series of short exercises designed to give you a guided introduction to the language's features. 
Before starting the other projects in this course, complete the rustlings exercises.

- [Rustlings](https://github.com/rust-lang/rustlings). To enable *rust-analyzer* and its features (such as autocomplete and documentation), run this command in the rustlings directory: 
```bash
rustlings lsp
```

#### Project: Rusty Merkle Tree

See the [project description](projects/rust_merkle_tree.md).

#### Project: Async Linkchecker

See the [project description](projects/rust_linkchecker.md).

#### Project: Rusty LC3

See the [project description](projects/rust_lc3_vm.md).

---
### Performance Engineering

- [Moore's Law, Microprocessors, and First Principles](https://www.youtube.com/watch?v=Nb2tebYAaOA)
- [What Every Programmer Should Know about How CPUs Work • Matt Godbolt • GOTO 2024](https://youtu.be/-HNpim5x-IE?si=_T0lB-FoEEQipQZC)
- [Brendan Gregg: Flamegraphs](https://www.brendangregg.com/flamegraphs.html)
- [Datadog: Flamegraphs](https://www.datadoghq.com/knowledge-center/distributed-tracing/flame-graph/)
- [Profiling Rust programs the easy way](https://www.ntietz.com/blog/profiling-rust-programs-the-easy-way/)
- [Making slow Rust code fast](https://patrickfreed.github.io/rust/2021/10/15/making-slow-rust-code-fast.html)

---
### Distributed Systems

- The book [Designing Data-Intensive Applications](https://www.oreilly.com/library/view/designing-data-intensive-applications/9781491903063/) is an excellent introduction to many topics related to building scalable and fault-tolerant systems. It gives a decent map of the territory and jumping-off points for anyone beginning to understand how systems are architected to provide these characteristics, since it's packed with references for further reading. Read chapters 1, 2 and 8.
- [Notes on Distributed Systems for Young Bloods](https://www.somethingsimilar.com/2013/01/14/notes-on-distributed-systems-for-young-bloods/)
- [A Distributed Systems Reading List](https://ferd.ca/a-distributed-systems-reading-list.html)
- [Beating the CAP Theorem Checklist](https://ferd.ca/beating-the-cap-theorem-checklist.html)
- [The most important thing to understand about queues](https://blog.danslimmon.com/2016/08/26/the-most-important-thing-to-understand-about-queues/) 
- [Queues Don't Fix Overload](https://ferd.ca/queues-don-t-fix-overload.html)
- [Lessons Learned while Working on Large-Scale Server Software](https://ferd.ca/lessons-learned-while-working-on-large-scale-server-software.html)
- [Handling Overload](https://ferd.ca/handling-overload.html)
- [A Commentary on Defining Observability](https://ferd.ca/a-commentary-on-defining-observability.html)
- [Make your cluster SWIM](https://www.bartoszsypytkowski.com/make-your-cluster-swim/)
- [The State of State Based CRDTs](https://www.bartoszsypytkowski.com/the-state-of-a-state-based-crdts/)

---
### The BEAM Ecosystem: Elixir

In the beginning, the BEAM and Erlang were almost synonymous, there were no other languages that ran on the BEAM virtual machine and ERTS. 
In fact the core of the platform is the ERTS -- the Erlang Run Time System. 
In time, others have emerged such as LFE, Elixir, and Gleam. 
Today, the most common gateway into the ecosystem is learning how to be productive with Elixir, learning the serial (non-concurrent) and functional programming aspects first, and then the support for concurrency, the common concurrency and distribution patterns provided by the OTP. This is usually eventually complemented by learning Erlang to be able to understand and read code from common dependencies (e.g. Cowboy).
Lately, Gleam has also matured and is a very interesting possibility. 

- [Elixir Homepage](https://elixir-lang.org)
- [The Soul of Erlang and Elixir • Sasa Juric • GOTO 2019](https://www.youtube.com/watch?v=JvBT4XBdoUE)
- [When would you choose Erlang?](https://web.archive.org/web/20150810202529/http://blog.troutwine.us/2013/07/10/choose-erlang) Although Brian Troutwine talks about Erlang in this post, most of the content applies to Elixir as well.
- [The Zen of Erlang](https://ferd.ca/the-zen-of-erlang.html) Erlang base principles and good practices, these also apply to Elixir.
- Read the entire `Getting started` section starting at [the introduction](https://elixir-lang.org/getting-started/introduction.html)  EXCEPT:
  - "Module attributes"
  - "Protocols"
  - "Sigils"
  - "Writing documentation"
  - "Optional syntax cheatsheet"
  - "Erlang Libraries"

In addition, read:
- the documentation for Mix (https://hexdocs.pm/mix/Mix.html)
- the documentation for ExUnit (https://hexdocs.pm/ex_unit/ExUnit.html

#### Phoenix
- [Phoenix Official Guides](https://www.phoenixframework.org/)
  - Introduction (Except for _Community_)
  - Guides (Except for _Asset Management_)
  - Authentication
  - Testing (Except for _Testing Channels_)
- [Phoenix Chat Example](https://github.com/dwyl/phoenix-chat-example)

#### Project: Forth Interpreter

See the [project description](projects/elixir_forth.md).

---

### General Cryptography

- [crypto101](https://www.crypto101.io/) Crypto 101 is an introductory course on cryptography, freely available for programmers of all ages and skill levels.

---
### Blockchains

- [Introduction To Cryptocurrency](https://nakamoto.com/introduction-to-cryptocurrency/) A brief introduction to cryptography and P2P networking used in Bitcoin. Avoid The History of Bitcoin module. Also, if you already implemented the Rusty Merkle Tree you can skip the Merkle Trees lecture.
- [Electronification, Trading, and Crypto](https://blog.uniswap.org/electronification-trading-and-crypto) - Analysis of technology's impact on trading systems.
- [A Cambrian Explosion of Crypto Proofs](https://nakamoto.com/cambrian-explosion-of-crypto-proofs/) - Exploration of the surge in zero-knowledge proofs.
- [A Brief History of Money](https://nakamoto.com/a-brief-history-of-money/) - The background of money leading up to cryptocurrencies.
- [The Cypherpunks](https://nakamoto.com/the-cypherpunks/) - The role of software in privacy defense.
- [Hash Functions](https://nakamoto.com/hash-functions/) - Discussing this critical component of cryptocurrencies.
- [Merkle Trees](https://nakamoto.com/merkle-trees/) - Explanation of data representation in crypto.
- [Public-Key Cryptography](https://nakamoto.com/public-key-cryptography/) - The foundation of digital identities in the crypto world.

---
### Bitcoin

- [3blue1brown: But how does bitcoin actually work?](https://www.youtube.com/watch?v=bBC-nXj3Ng4)
- [Hashcash](https://nakamoto.com/hashcash/) Insights into Bitcoin's consensus mechanism.

---
### Ethereum

When onboarding to Ethereum-related projects it is important to get a general idea of the high-level components, how they relate, the general design tradeoffs involved, and finally a deeper understanding of some central components.
Understanding everything from the get-go is impossible. 
Read the `Introductory Material`, `Ecosystem`, and the `EVM` sections. 
The rest are for reference or reading at your own pace.

#### Introductory Material
- [Intro to Ethereum](https://ethereum.org/en/developers/docs/intro-to-ethereum/)
- [Ethereum in 30 minutes by Vitalik Buterin | Devcon SEA](https://www.youtube.com/watch?v=ei3tDRMjw6k)
- [Developer Docs Homepage](https://ethereum.org/en/developers/docs/)
  - [Accounts](https://ethereum.org/en/developers/docs/accounts/)
  - [Transactions](https://ethereum.org/en/developers/docs/transactions/)
  - [Blocks](https://ethereum.org/en/developers/docs/blocks/)
  - [EVM](https://ethereum.org/en/developers/docs/evm/)
  - [Gas](https://ethereum.org/en/developers/docs/gas/)
  - [Data Structures and Encoding](https://ethereum.org/en/developers/docs/data-structures-and-encoding/)
  - [Patricia Merkle Tree](https://ethereum.org/en/developers/docs/data-structures-and-encoding/patricia-merkle-trie/)
  - [Nodes and Clients](https://ethereum.org/en/developers/docs/nodes-and-clients/)
- [What happens when you send one DAI?](https://www.notonlyowner.com/learn/what-happens-when-you-send-one-dai) A look at the process of Ethereum transactions.
- [Research, Spec, Clients, & Nodes](https://youtu.be/vzgNqO_obH4)
- [The EVM](https://youtu.be/kCswGz9naZg)
- [Accounts, Private Keys, Wallets](https://youtu.be/A_c3bCkBtPA)
- Account Abstraction
  - [An ultimate guide to account abstraction](https://blog.getclave.io/p/ultimate-account-abstraction-guide)
  - [Part I: WTF is Account Abstraction](https://www.argent.xyz/blog/wtf-is-account-abstraction/)
  - [Part II: WTF is Account Abstraction](https://www.argent.xyz/blog/part-2-wtf-is-account-abstraction)
  - [Part III: WTF is Account Abstraction](https://www.argent.xyz/blog/part-3-wtf-is-account-abstraction)
- [Smart Contracts](https://youtu.be/PLgawr4pbqE)
- [Ethereum's Proof of Stake consensus explained](https://www.youtube.com/watch?v=5gfNUVmX3Es)
- [Understanding Rollups](https://vitalik.eth.limo/general/2021/01/05/rollup.html) - Vitalik Buterin's guide on rollups, a key scalability solution.
- [Roll-Ups](https://www.youtube.com/watch?v=7pWxCklcNsU)
- [ZK Roll-Ups](https://youtu.be/3C0g-60bAWc)

#### Ecosystem
- [Illuminating Ethereum's Order Flow Landscape | Flashbots Writings](https://writings.flashbots.net/illuminate-the-order-flow)
- [Ethereum is a Dark Forest](https://www.paradigm.xyz/2020/08/ethereum-is-a-dark-forest)
- [Keynote: Beam Chain by Justin Drake | Devcon SEA](https://youtu.be/lRqnFrqpq4k)

#### EVM
- [Ethereum White Paper](https://ethereum.org/en/whitepaper/) The white paper is a more high level, executive summary.
- [Ethereum Beige Paper](https://cryptopapers.info/assets/pdf/eth_beige.pdf) The beige paper is more technical but doesn't go into the deeper details.
- [EVM Handbook](https://www.notion.so/bb38e175cc404111a391907c4975426d?pvs=21)
- Parts I and II from: [Building an EVM from scratch](https://karmacoma.notion.site/Building-an-EVM-from-scratch-series-90ee3c827b314e0599e705a1152eecf9) 
- [A Playdate with the EVM](https://web.archive.org/web/20250126120648/https://femboy.capital/evm-pt1)
- [EVM Deep Dives](https://noxx.substack.com/p/evm-deep-dives-the-path-to-shadowy)
