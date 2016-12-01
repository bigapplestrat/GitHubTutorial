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

Well commented code can solve many issues, but tracking changes over time is a valuable tool that allows coders to see how a project has evolved without resorting to confusing schemes that force you to remember if `newproject-definitelythefinalversionimprettysure1.py` was the last one that you got working correctly or if that was number 2.

Problems of this sort only become more complex when working on teams of coders. With many chefs in many kitchens, it can be difficult to figure out why a large project is no longer working the way it should. Many changes to different parts of a codebase can add up over time, and often the left hand doesn't know what the right hand is doing.

Version control systems allow you the ability to track and manage changes to code over time. They give a picture of how code evolves, give projects control over how to accept or reject changes, and allow the ability to undo destructive changes and start from the last time everything was working correctly.

`git` is a specific variety of version control that provides a set of commands allowing versions of code to be incorporated into a history (repository) that tracks what changes have been made over time, as well as allow collaborative coding efforts. `git` shouldn't be confused with GitHub. [GitHub](http://www.github.com/) is a repository hosting service that can store your code histories and allow you to distribute them easily, but it is not the only hosting service. `git` repositories can also be hosted by other companies like [BitBucket](https://bitbucket.org/), or stored on a local machine on your own network.

## How do you start a git repository?

There are many graphical user interfaces for interacting with `git`, but intitially we are going to focus on the Unix commandline version. The command line tools are more consistent across platforms and are much more explicit about what they are doing. For our purposes today we will be using GitHub as the main repository host.

First you will need to set up a user account and password on GitHub. Once you have done so, click the `+` sign in the upper righthand corner of the page and choose to create a new repo. Call it `exampleRepo`.

Now that we have created the repo on the server, the next step is to find a place to work on your computer. Navigate to the directory you would like to store your git repositories. The new repo will be saved as a subdirectory of that folder. Create a folder named `exampleRepo` and then navigate to the new directory. Type the following:

```sh
echo "# exampleRepo" >> README.md
git init
git add README.md
git commit -m "first commit"
```

This block of code first creates a README file, giving us our first file to commit to our repository. We then run `git init` in order to create a file that tells git that the current directory is a repository. We then add the README.md file to the files we would like to track changes on using `git add`. Finally we make our first commit, and add our changes to the repo history. 

So far nothing has been added to the remote GitHub repo. All the changes still reside on your own computer. Next do the following:

```sh
git remote add origin https://github.com/YOURUSERNAME/exampleRepo.git
git push -u origin master
```

This tells git that we want to refer to this repository as 'origin' when we commit additional information. You can type `git remote -v` to see all the current remote repositories git has references to. The `git push` command sends your data off to GitHub. You should be prompted for your username and password. The master command tells git that you are pushing the master branch, which will make more sense later.

If you're not using GitHub as your hosting service, you would simply give a different remote alias specific to that site. The convention of where the username and repo details go might be slightly different, but the process should be the same.

If you open the repository on `github.com` you should now see that your README.md file has been added to the repository. 

Let's see what happens when you change something in a file. Open the README.md file in a text editor and replace its text with the following.

```markdown
# Some new text here

Spam and eggs.
```

Once we've saved that file we can perform a new commit.

```sh
git commit -m "made some changes"
```

The `-m` flag allows you to add comments that will be tracked with each new commit.

Let's see what has changed.

```sh
git diff
```

This command will show you which files are different and how they've changed since the last time you synced your repository. We can see that the initial line of text was deleted and that the new text was added below it.

```sh
git push -u origin master
```

We've now pushed the new version of the file to the repository. If you navigate to your GitHub repo, you should be able to click on the individual file, then click on history. From here you can view the individual changes that were made in this commit. Deleted code shows as red, and added code shows as green.

But shoot. Maybe looking at this new commit you really regret your choices. "Am I really the kind of guy who makes coding-related Monty Python references?" you may say to yourself. "No. We have to forget this ever happened."

To return to an earlier version of your code, we perform what's known as a `rollback`. This effectively returns the files that have been changed to their previous state. Type the following into the terminal:

```sh
git log
```

The `git log` lists the commits you've made to the repository in the past by ID and gives you the comments you saved along with them. We want to go back to the good old days. Back when we just had a simple headline in our README file. Note the ID after the most recent commit, and enter it in the following command.

```sh 
git revert commitIdGoesHere

```

You should be prompted to enter a commit message to explain why you have such a terrible sense of humor. Submit and continue. If all has gone according to plan, inspecting the `README.md` file should show that it's been returned to its original state. Enter `git log` again and notice that you did not delete the previous commit. Instead we committed a new change which undoes what was typed in the previous changes. Your love of 1970s British comedy troupes remains in the official record, though the actual code in the current version shows no trace.

It is possible to totally delete the chain of records in a repository by using the `git reset` command, but this is a kind of nuclear option and is often heavily discouraged in group environments since it effectively destroys the commits that you are reverting past. For that reason we recommend using `git revert` whenever possible, since it maintains the overall project history and prevents loss of data. Go ahead and do the following to push your changes to GitHub.

```sh
git push -u master
```

There are a few tricks that can help make your time with git a little less painful. Git includes a number of configuration files. The one you'll probably be the most involved with is `.gitignore`. This file lives in your project's main directory and is a list of files that you would like to prevent from being synced along with the rest of your code. For example, if you have a terabyte of high resolution Nicolas Cage headshots in your directory it's probably a good idea not to send those to the Github servers. Try the following...

```sh
# Create a new file
ls > exampleFile.example

# Note the output here
git status

# Create your .gitignore file
touch .gitignore

# Add a new exclusion criteria to your .gitignore file
echo "*.example" >> .gitignore

# Ping git status again
git status

```

You should notice that once you create the `.gitignore` file, git begins ignoring any file ending with the .example file extension. This process works for any file type. The `.gitignore` file is like any other file, so we need to add it to our commit path and push it to the remote server in order to check it into the repository.

```sh
git add .gitignore
git push -u origin master
```

Your git repository will now exclude these filetypes until you modify the `gitignore` file to allow them through.

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

### GitHub GUI

There are a number of graphical interfaces for interacting with `git`. GitHub produces their own GUI which is available [as a download from their site.](https://desktop.github.com/) If the command line isn't for you, it offers a majority of the functionality of the command line interface and simplifies the process of commenting and tracking changes by providing a visual display.

### The README.md File

You may have noticed that we did a lot of playing with this file during the initial segment of the training. The `README.md` file is a markdown file that will automatically be displayed on your GitHub repository's page. You may have noticed that this very tutorial is written on a `README.md` file. Markdown is a [very flexible convention](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet#links) that allows you to make readable pages explaining the way that your code works in order to inform your users about how to use your programs.

- `git stash`
- Creating git version controlled RStudio project

### gitignore on specific directories

The `.gitignore` file works by affecting the directory it lives in and any subdirectories nested inside that directory. For this reason, your main `.gitignore` file should live in your root directory. However there might be cases where you wish to exclude a certain kind of files in one subdirectory or another. You can achieve this by creating a new `.gitignore` file in the subdirectory of interest. For example, if you have a `credentials` subdirectory with passwords and other credentials saved in plaintext form, but you wish to sync text files in other directories, you can create a new `.gitignore` in the `credentials` directory with the line `*.txt` inside of it. From this point on, `git` will sync text files from all other directories, but leave your dirty secrets alone as long as they're in the `credentials` directory.

You can also use `.gitignore` files if you wish to have a permanently empty directory - for example, if it's a place that users will be putting their own data. Simply initialize the `.gitignore` file in the directory you wish to remain empty and push the change. The directory should now be added like any other file despite being empty.

## Resources

- [Oh shit, git!](http://ohshitgit.com/)
- [Atlassian git Tutorials](https://www.atlassian.com/git/tutorials/)
- [Pro Git Book](https://git-scm.com/book/en/v2)
- [Ten Simple Rules for Taking Advantage of Git and GitHub](http://dx.doi.org/10.1371/journal.pcbi.1004947)
