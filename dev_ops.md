# How to DevOps
Author: Sebastian Dengler

Date: May 2023

## Once upon a time...

... there was a smith who was a master at his craft. One day a great knight approached him and  asked him to forge a sword more powerful that any sword in existence, to fight the dragon that had stolen his beloved princess. Just when the smith had finished his work the angry user, ... uhm I mean the dragon, attacked the village. In the chaos of the attack the smith and the knight found each other at the opposite sides of a tall fence. The smith cast the sword over to hand it to the knight. However, the smith had forgotten to tell the knight that he had to install all the necessary dependencies first, because the smith was really good at smithing but not so good at writing documentation. The knight got eaten alive and the princess was never seen again.

Does this "fairy tale" sound oddly familiar to you? Do you identify with the knight or maybe the smith? Are "other-the-fence-deliveries" a common thing in your team or organisation?

The term DevOps is a combination of the words "Development" __and__ "Operations". With an emphasis on the word "and" that's not even in the term. A development team is supposed to develop __and__ take care of the product they are developing after its release. Which makes sense, since the developers are probably the ones understanding the technical intricacies of the solution the best. The term DevOps is also often used as a buzz word. Few people that are using the word know what it entails and even less are actually practicing it. The purpose of this article is to point you into the right direction. It will show you a list of things you should consider if you're working in a software engineering profession and want to excel at what you are doing or at least be part of the discussion. It will also provide you with some tangible advice on how to get started on your DevOps journey.

## Measure everything

In their book _"Accelerate: The Science of Lean Software and DevOps: Building and Scaling High Performing Technology Organizations"_ Nicole Forsgren PhD, Jez Humble and Gene Kim are using scientific approaches to determine what high performing software development teams have in common. Their findings: The most successful teams have:

- A high deployment frequency. They release small changes frequently (multiple times a day) to production.
- A short change lead time. The time it takes from a code change to be committed until it is released to users (less than an hour).
- A low time to restore service (less than an hour).
- A low change failure rate (0-15 \%).

What is your deployment frequency? How often do new features released to production cause your application to fail? "I don't know" is the wrong answer. The initial step to become better at "doing DevOps" is to measure these metrics in the first place. We need to establish a baseline before we can talk about improving something.
Do other metrics make more sense in the context of your work or application? Then measure those, too!

## Decide on a branching strategy

You're not alone. At first glance this might sound like a good thing, however, everyone that has been working in a team of software developers, with multiple of them working on the same piece of code, knows that it comes with some drawbacks. Can you remember the time you had to resolve 20 merge conflicts because the new guy had pushed two weeks worth of changes straight to main? (I hopefully don't have to tell you to use version control.)

- Trunk based
- Github Flow
- GitFlow

## Establish and enforce best practices
PR review, Pre commit hooks, autoformatters

Style guide, rule book

## Automate, automate, automate

DevOps is closely related to the practice of CI/CD (Continuous Integration, Continuous Delivery ... or Deployment depending on who you ask). The idea of CI/CD is having large parts of the release process of software automated away from the software developer so he or she can focus on developing and not installing the latest binary on the server everytime they want to release a new feature. The idea of CI is that each commit instantly triggers an automated build pipeline

Automate the build of your application, automate the deployment of your application and automate the provisioning of your infrastructure. What about testing? Automate that as well.

Try and reduce the time the CI stage takes as much as possible as it will be run everytime you make a commit. And remember, you're supposed to make small changes often and commit them often.


## Shift left on security, DevSecOps
The term "shifting left" translates to integrating something into the development process from the start (which would be located on the left side of any ugly roadmap powerpoint slide of a product owner that behaves like a project manager). We have seen this with operations. Ideally we want to tear down the fence and merge smith and knight into one single role. What is stopping us from doing that with other important software aspects? One often forgotten topic is security. The authors have more than once seen fellow developers twitch when the word is even mentioned. That's because security is hard. It requires a deep understanding of the technologies used in your application and is thus often disregarded when developing under time pressure. This backfires by the time development is nearly done and the quality department is having a first look at the product. By then it is too late. Your 12 GB large docker images have 847 critical vulnerabilities and your the python packages have dependencies that secretly make your compute resources mine Bitcoin.

## Hope for the best, expect the worst
Testing in production, chaos engineering, game days
High performing teams test in production. And not just at deployment. They are running tests continuously to check the health of their application. Even more advanced organizations are taking it to the next level. Netflix infamously is letting loose "chaos monkeys" randomly terminating parts of their infrastructure in production to test the self healing capabilities of their systems.
At least be prepared: Define RPO and RTO, Define a disaster recovery strategy. Organize game days where system failures are simulated and the team has to troubleshoot.


## It takes time

What works for other teams might not work for you. Other things might work for your team but not anyone else.
Don't try to implement all suggestions at once. Try one of them and constantly evaluate. Does it make sense? Does it bring any value? If yes, good. If not, try something else. The authors of this article have backgrounds in various software engineering disciplines such as Data Engineering, Data Science and Cloud Development. However, we do not claim to have mastered DevOps, and neither do we claim that the above list is fully exhaustive and that by blindly following it you will become a great developer. It will take time, practice and a change in culture. The fact that developers will have to maintain a product for potentially a long time forces them to think about the quality of what they are building. It forces them to keep complexity low. If something looks too complicated, it probably is. Constantly question inefficient processes