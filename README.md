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

There are many graphical user interfaces for interacting with 'git', but intitially we are going to focus on the Unix commandline version of 'git'. The command line tools are more consistent across platforms and are much more explicit about what they are doing. For our purposes today we will be using GitHub as the main repository host.

First you will need to set up a user account and password on GitHub. Once you have done so, click the '+' sign in the upper righthand corner of the page and choose to create a new repo. Call it 'exampleRepo'.

Now that we have created the repo on the server, the next step is to find a place to work on your computer. Navigate to the directory you would like to store your git repositories. The new repo will be saved as a subdirectory of that folder. Create a folder named exampleRepo and then navigate to the new directory. Type the following:

'echo "# exampleRepo" >> README.md
git init
git add README.md
git commit -m "first commit"'

This block of code first creates a readme file, giving us our first file to commit to our repository. We then run 'git init' in order to create a file that tells git that the current directory is a repository. We then add the README.md file to the files we would like to track changes on using 'git add'. Finally we make our first commit, and 

So far nothing has been added to the GitHub repo. All the changes still reside on your own computer. Next do the following:

'
git remote add origin https://github.com/YOURUSERNAME/exampleRepo.git
git push -u origin master
'

This tells git that we want to refer to this repository as 'origin' when we commit additional information. You can type 'git remote -v' to see all the current remote repositories git has references to. The 'git push' command sends your data off to GitHub. You should be prompted for your username and password. The master command tells git that you are pushing the master branch, which will make more sense later.

If you open the repository on 'github.com' you should now see that your README.md file has been added to the repository. 

Let's see what happens when you change something in a file. Open the README.md file in a text editor and replace its text with the following.

'#some new text here

Spam and eggs.
'

Once we've saved that file we can perform a new commit.

'git commit -m "made some changes"'

The -m flag allows you to add comments that will be tracked with each new commit.

Let's see what has changed.

'git diff'

This command will show you which files are different and how they've changed since the last time you synced your repository. We can see that the initial line of text was deleted and that the new text was added below it.

'git push -u origin master'

We've now pushed the new version of the file to the repository. If you navigate to your GitHub repo, you should be able to click on the individual file, then click on history. From here you can view the individual changes that were made in this commit. Deleted code shows as red, and added code shows as green.

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
