# The Art of Small Pull Requests - Part 1 Why?

## Why should I make my pull requests small?
Just like small change sets makes releasing features easier and less risky via continous deployment, writing small sets of changes in pull requests (PR) improves code quality, feedback, and understandability.  

Have you ever gotten a PR assigned to you where changes span a large number of files and are not logically related in any way?  These types of pull requests are really difficult to review and the code review fatigue that is associated with them usually results in one of two bad outcomes:

- **Review delay** - The PR is so large that it is daunting for the reviewer.  The reviewer wants to do a thorough job reviewing your code and providing feedback, but they know it will take them a long time to do the review.  Because of this they delay reviewing until they have more time.  This results in delay in feedback for you and causes delays in the entire development workflow of your team.
- **Rubber stamp** - Someone reviews your PR, but it's so large they decide to quickly glance over it and then approve or merge it.  This gives you a quick response on your pull request, but it doesn't give you the proper feedback.  Having someone review and provide feedback on your work is the main purpose of a pull request.  When review fatigue occurs and you don't get a thorough review, your code base, team and organization suffer.

```
If you care about the quality of your work and the product you're building for your customer then having a good review process that generates thoughtful comments and feedback is critical.  Using small, focused pull requests is critical to this process and creates a good invitation to your reviewer to provide quality feedback.
```
A pull request should have a singular focus.  That is it should do one thing and do it well.  This means building 

As we've discussed, small pull requests have the following advantages:

- Improved code quality
    Singular focus
    More disciplined and self-review
- Better feedback
- Shorter feedback cycle
- Understandability - 

It's usually possible to work in small pull requests, it just takes discipline.   

## Why is it so difficult?
Submitting small pull requests has so many benefits, why would we ever submit a large request?  The reason is that it usually takes more discipline and planning to create small pull requests. However, just like anything else you can turn this discipline into a habit where it becomes your natural tendency to create small well-defined pull requests.

### Trunk based development
    - Master branch has to always be deployable.
    - How to handle this:
        - Feature flags
        - Delay wiring up the class in the development process.

### Out of order
    - You need to build class A that depends on Class B, but it has not been created or will be created by another developer.

### Prototyping 
Sometimes you're trying to build something and you're not sure how it should work.  Maybe it needs to do something that hasn't been done before in your project.  Maybe you're new on the team and not that familiar with the project so you're still learning how to build features in it.  Whatever the reason, prototyping is often necessary.  After all software development is all about discovery.  Often to see if this prototype is going to work you have to build out a working model.  This usually means building a feature across layers of the application (database, domain, ui), requiring changes to relatively large number of files.  This type of protyping is normal and expected.  It's ok to build out the scaffolding for an entire feature and make sure what you're doing is going to work.  It's *not* ok to go back to a quickly built prototype, throw some tests on top of it, and submit a giant pull request.

If you are prototyping then you should do the minimum you possibly can to prove that the approach is going to work.  No tests should be written during this process because you're basically just experimenting.  I'm a big fan of TDD and I know many TDD purists may take issue with this, but creating tests at this point is too large of an investment in work that has a good chance of being thrown away.  

You shouldn't consider any of this work as complete or ready to be merged.   Once you have a prototype you think will work, you may want to create a (Work In Progress)[https://github.com/apps/wip] pull request so that other members of your team can provide feedback.  *Note*: A WIP pull request cannot and should not be merged.  It's just for review and feedback.

Once you have your prototype working and you and your team feel this is the right way to proceed, then you can start working on the feature in earnest.  The easiest way to start creating small pull requests is to start at the lowest level dependency (that is the dependency that has none of your other code depends on).  If this is a typical Ui->Domain->Database project, then this would probably be an artifacts in the data layer.  This is when you would start using TDD to build out the complete class.

Once this class and it's associated tests are complete you're ready to submit your first Pull Request to be considered for merging.  This is where Git's separation of the working and staging areas really helps you.  You can just stage and commit the class and test class you just worked on.  Once you've commited these changes you should verify that this change compiles, lints, passes all tests, and any other build pipeline checks you may have in place.  An easy way to do this is to use the git stash feature.  If the changes you want to submit for a pull request have been committed, then you can save you current work and clear it from the current working directory using (git stash)[https://git-scm.com/docs/git-stash].  Once you've stashed you only have the changes in your working directory that have been commited.  In this case that is the work on the lowest level class that you are planning to commit.  At this point you should run your entire build pipeline against this change locally to make sure it passes all of your coding, compilation,  linting, and testing standards.  Then you can push this branch and issue a PR for your class and it's associated test (assuming it passes everything on the build server).  

At this point you just need to rinse, wash, repeat this same set of steps at each layer as you make your way through your prototype.  You can create a new branch, pop the current stash, and begin working on the next class and its associated tests that are in your prototype.  

Here is a quick recap of these steps for working your way from a prototype to a set of well-coded small pull requests:

- 

## Conclusion
There really isn't much excuse for submitting large and difficult to review pull requests.   All the tools you need to break your work up so that it can be easily reviewed and understood are made available in git.  
