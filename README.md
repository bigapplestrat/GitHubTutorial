# GitHubTutorial

## Objectives

- Learn what `git` and version control are
- Learn basic `git` commands
- Play around with learned `git` commands
- Learn some `git` tips and tricks

## Outline

- [What is version control and git?](#what-is-version-control-and-git)
- [How do you start a git repository?](#how-do-you-start-a-git-repository)
- [How do you work on someone else's repository?](#how-do-you-work-on-someone-elses-repository)
  - [Make changes to someone else's repository](#make-changes-to-someone-elses-repository)
  - [Submit pull request to project repository](#submit-pull-request-to-project-repository)
- [Exercises/Playground Time](#exercisesplayground-time)
- [Git Tips and Tricks](#git-tips-and-tricks)
- [Resources](#resources)

## What is version control and git?

Writing code can be a messy process. When working on your code, you make many decisions over long periods of time. Files and lines of code are deleted and replaced, functions are changed, the structure of your programs are rewritten and refactored. All of these changes can have unintended consequences. Wouldn't it be great to undo them? Or just to remember why on earth you made that weird function in the first place? 

Well commented code can solve many issues, but tracking changes over time is a valuable tool that allows coders to see how a project has evolved without resorting to confusing schemes that force you to remember if 'newproject-definitelythefinalversionimprettysure1.py' was the last one that you got working correctly or if that was number 2.

Problems of this sort only become more complex when working on teams of coders. With many chefs in many kitchens, it can be difficult to figure out why a large project is no longer working the way it should. Many changes to different parts of a codebase can add up over time, and often the left hand doesn't know what the right hand is doing.

Version control systems allow you the ability to track and manage changes to code over time. They give a picture of how code evolves, give projects control over how to accept or reject changes, and allow the ability to undo destructive changes and start from the last time everything was working correctly.

'git' is a specific variety of version control that provides a set of commands allowing versions of code to be incorporated into a history (repository) that tracks what changes have been made over time, as well as allow collaborative coding efforts. 'git' shouldn't be confused with GitHub. GitHub is a repository hosting service that can store your code histories and allow you to distribute them easily, but it is not the only hosting service. 'git' repositories can also be hosted by other companies like BitBucket, or stored on a local machine on your own network.

## How do you start a git repository?

There are many graphical user interfaces for interacting with 'git', but intitially we are going to focus on the Unix commandline version of 'git'.

## How do you work on someone else's repository?

Find a repository to work on, such as this one.

```
https://github.com/bigapplestrat/GitHubTutorial
```

To contribute work on this repository, you'll first have to make a copy of the
repository by **forking** it.

### Make changes to someone else's repository

Branch and commit

### Submit pull request to project repository

## Exercises/Playground Time

- How do you create a new git repository?
- Create a file.
- How do you check the status of your git repository?
- What changes have been made to your repository?
- Stage your file.
- Check the status of your repository.

## Git Tips and Tricks

- `git stash`
- Creating git version controlled RStudio project

## Resources

- [Oh shit, git!](http://ohshitgit.com/)
- [Atlassian git Tutorials](https://www.atlassian.com/git/tutorials/)
- [Pro Git Book](https://git-scm.com/book/en/v2)
- [Ten Simple Rules for Taking Advantage of Git and GitHub](http://dx.doi.org/10.1371/journal.pcbi.1004947)
