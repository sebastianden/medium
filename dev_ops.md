# How to DevOps

## Once upon a time...

... there was a smith who was a master at his craft. One day a great knight approached him and asked him to forge a sword more powerful than any sword in existence, to fight the dragon that had stolen his beloved princess. Just when the smith had finished his work the angry user, ... uhm I mean the dragon, attacked the village. In the chaos of the attack, the smith and the knight found each other on opposite sides of a tall fence. The smith cast the sword over to hand it to the knight. However, the smith, in his haste, hurled the sword over to the knight but forgot to share the chant to unlock its full potential.
Without the enchantment, the knight was overpowered, got eaten alive and the princess was never seen again.

Does this "fairy tale" sound oddly familiar to you? Do you identify with the knight or maybe the smith? Are "over-the-fence deliveries" a common thing in your team or organization?

<p align="center">
<img width=400 src="https://img.devrant.com/devrant/rant/r_2948651_xEiez.jpg"/>
</p>

The term DevOps is a combination of the words "Development" **and** "Operations". With an emphasis on the word "and" that's not even in the term. A development team is supposed to develop **and** take care of the product they are developing after its release. This makes sense since the developers are probably the ones who understand the technical intricacies of the solution the best. The term DevOps is also often used as a buzzword. Few people that are using the word know what it entails and even fewer are actually practicing it. The purpose of this article is to point you in the right direction. It will show you a list of things you should consider if you're working in a software engineering profession and want to excel at what you are doing or at least be part of the discussion. It will also provide you with some tangible advice on how to get started on your DevOps journey.

## Measure everything

In their book _"Accelerate: The Science of Lean Software and DevOps: Building and Scaling High Performing Technology Organizations"_ Nicole Forsgren PhD, Jez Humble and Gene Kim are using scientific approaches to identify the common characteristics of high-performing software development teams. They found that the most successful teams share several key traits:

- They deploy changes frequently, often multiple times per day.
- They have a short lead time for changes, meaning that new features or bug fixes are released to users quickly, often within an hour of being committed to the codebase..
- They are able to restore service quickly in the event of a problem, with downtime often being less than an hour.
- They have a low rate of change failure, with only 0-15% of changes resulting in errors or issues.

What is your deployment frequency? How often do new features released to production cause your application to fail? Simply saying "I don't know" is not enough. The initial step to becoming better at "doing DevOps" is to measure these metrics in the first place. We need to establish a baseline for them before we can talk about improving them.
Do other metrics make more sense in the context of your work or application? Then measure those, too!

## Decide on a branching strategy

You're not alone. At first glance this might sound like a good thing, however, everyone that has been working in a team of software developers, with multiple of them working on the same piece of code, knows that it comes with some drawbacks. Can you remember the time you had to resolve 20 merge conflicts because the new guy had pushed two weeks' worth of changes straight to main? (I hopefully don't have to tell you to use version control). Since the beginning of Git developers have devised hundreds of strategies for merging code changes. However, lately, there is a growing trend towards the most simple ones, so we'll start with those and move up in complexity:

- Trunk-based: The strategy is as easy as it gets. Everyone commits directly to the main branch (a.k.a. trunk). constantly. Team members integrate each other's changes without time-consuming merging processes. Conflicts are resolved fast and issues identified early. However, it requires a lot of discipline. Every team member needs to ensure that functionality is sufficiently tested. If you break main it is your responsibility to fix it - immediately. It might require some experience and seniority of the team members. It requires expertise in git and familiarity with feature flags.
- GitHub Flow/Feature Branches: In this strategy, team members create short-lived feature branches by branching out from main. The main branch should always be in a working state and changes are added by merging the feature branches (ideally after a peer review).
- GitFlow: This strategy utilizes multiple branches. New features are developed by branching out from a dev or develop branch. Once a feature is ready to be released, a release branch is created which in turn is merged into the main branch. Sounds complicated? It gets even better: If a bug is identified a hotfix branch is created containing the bugfix, which has to be merged into both, the develop branch and the main branch. It can be quite slow and tiresome to entangle this scheme of branches, however, this strategy allows for precise versioning and individual releases.

Now you might be asking: Which strategy should my team use? The answer is: It depends. If you believe your team has the necessary experience or if it doesn't matter that things are broken from time to time then maybe trunk-based development is for you. If you put a lot of value into quality but still want to integrate changes often and fast, go with feature branches. Try to avoid GitFlow if possible. There are other - even more complicated - branching strategies than GitFlow. The authors' advice: Don't!

## Establish and enforce best practices

Some people like single quotes, some people like double quotes. Some people end their lines with semicolons, others don't. And that's okay... until you find out that both types of people exist in your team. This makes code style inconsistent and the git history confusing since everything appears to be changed all the time. One way to address this issue is to agree on a set of standards within your team. Google is leading by example here by creating a [style guide](https://google.github.io/styleguide/) for nearly every programming language known and open-sourcing them. Try to create your own style guide. You can start by taking inspiration from others and add new rules over time.
It's good to have a set of rules or best practices clearly defined and written down, however, developers tend to forget these things if not reminded constantly. And because developers also tend to be smart people they long figured out how to automate most of this. You can have programs check your code for violations of standards and best practices (e.g. [pylint](https://pypi.org/project/pylint/)) and auto-format it to conform to a consistent style (e.g. [black](https://github.com/psf/black), [autopep8](https://pypi.org/project/autopep8/) for python or [prettier](https://prettier.io) for TypeScript and general web development).
Another way of enforcing best practices is during code reviews. Create a list of rules which both author and reviewer can tick off when they create or review a code change. Even better than that: Use pre-commit hooks. These are functions that automatically get triggered when e.g. `git commit` is run and can be used to execute checks against the files to be committed. This way you can detect failing tests and style violations (for example if Kyle is using tabs instead of space again) before code is even committed and pushed. Examples of pre-commit packages are [husky](https://typicode.github.io/husky/) and [pre-commit](https://pre-commit.com).

## Automate, automate, automate

You should strive to automate as much routine work as possible. Automate the build and deployment of your application as well as automate the provisioning of your infrastructure. What about testing? Automate that as well. DevOps is closely related to the practice of CI/CD (Continuous Integration, Continuous Delivery... or Deployment depending on who you ask). The idea of CI/CD is to have large parts of the release process of software automated away from the software developer so they can focus on developing and not installing the latest binaries on the server every time they want to release a new feature. Continuous Integration is the process of continuously integrating code changes into a shared repository. This process involves building and testing the code changes automatically as soon as they are committed to the shared repository. The main goal of CI is to catch bugs early in the development cycle, which can help reduce the cost of fixing bugs later on. Try and reduce the time the CI part takes as much as possible as it will be run every time you make a commit. And remember, you're supposed to make small changes often and commit them often.

If you go on from there and automatically deploy the built and tested code changes to a staging environment, where it can be tested more thoroughly before being released to production it's called Continuous Delivery. The main goal here is to ensure that the code changes are always in a releasable state, which can help reduce the time it takes to release new features or bug fixes.

Few teams manage to go even further and automatically deploy the built and tested code changes directly to production, reaching true Continuous Deployment. This process is only recommended for highly automated and well-tested applications, as any bugs introduced into production can have serious consequences.

## (TODO) Testing: Hope for the best, expect the worst

TDD, BDD
Integration Tests, E2E, Unit
Code coverage

High-performing teams test in production. And not just at deployment. They are running tests continuously to check the health of their application. Even more advanced organizations are taking it to the next level. Netflix infamously is letting loose "chaos monkeys" randomly terminating parts of their infrastructure in production to test the self-healing capabilities of their systems. This practice is also known as "chaos engineering".
If you're working in a regulated environment and this is not an option, at least be prepared: Define Recovery Point Objective(RPO) and Recovery Time Objective(RTO), Define a disaster recovery (DR) strategy. Organize game days where system failures are simulated and the team has to troubleshoot.

## Shift left on security, DevSecOps

The term "shifting left" translates to integrating something into the development process from the start (which would be located on the left side of any ugly roadmap PowerPoint slide of a product owner that behaves like a project manager). We have seen this with operations. Ideally, we want to tear down the fence and merge smith and knight into one single role. What is stopping us from doing that with other important software aspects? One often-forgotten topic is security. The authors have more than once seen fellow developers twitch when the word is even mentioned. That's because security is hard. It requires a deep understanding of the technologies used in your application and is thus often disregarded when developing under time pressure. This backfires by the time development of a new feature is nearly done and quality assurance is having a first look at the product. By then it is too late. Your 12 GB large docker images have 847 critical vulnerabilities and your python packages have dependencies that secretly make your compute resources mine Bitcoin. You are better than that. Tools exist to test your code for potential vulnerabilities early on in the development process. You can configure them to break your build pipeline if an issue with a too-high criticality is identified. Many of these tools are commercial and quite expensive. Nevertheless, if you are developing software in an enterprise setup you should seriously consider using a paid service. There are also free and open-source tools available that offer comparable feedback, such as e.g. [bandit](https://bandit.readthedocs.io/en/latest/) for Python code or [cfn-nag](https://github.com/stelligent/cfn_nag)/[cdk-nag](https://github.com/cdklabs/cdk-nag) for AWS Infrastructure-as-Code.

## It takes time

What works for other teams might not work for you.
Don't try to implement all suggestions at once. Try one of them and constantly evaluate. Does it make sense? Does it bring any value? If yes, good. If not, try something else. The authors of this article have backgrounds in various software engineering disciplines such as Data Engineering, Data Science and Cloud Development. However, we do not claim to have mastered DevOps, and neither do we claim that the above list is fully exhaustive and that by blindly following it you will become a great developer. It will take time, practice and a change in culture. The fact that developers will have to maintain a product for potentially a long time forces them to think about the quality of what they are building. It forces them to keep complexity low. If something looks too complicated, it probably is. Constantly question inefficient processes and reevaluate. There is no one correct way of doing DevOps, there is only your way.
