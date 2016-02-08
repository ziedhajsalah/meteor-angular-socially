## How to edit this tutorial?

First, you need to understand how this tutorial works and the importance of the commits. 
This tutorial is based on [Meteor's tutorial tools](http://meteor-tutorial-tools.readthedocs.org/en/latest/) and use it's tools to create a simple diff-boxes for code changes accross the commit.

So the very first thing you need to know it that this specific tutorial is used in [Angular1 Meteor tutorials](http://www.angular-meteor.com/tutorials/socially/angular1/bootstrapping) and every diff box you see there is generated automatically from the commits in this repository.

So what is the flow?
- Create commits with specific format - the format in use in this repository and in Meteor tutorial tools is: 

  ````Step XX.XX: TEXT_TEXT_TEXT````

  (where XX.XX are numbers that relates to the step in the tutorial you write, and TEXT_TEXT_TEXT is the title of the generated diffbox you will get).

- Generate PATCH file, as described [here](http://meteor-tutorial-tools.readthedocs.org/en/latest/new-tutorial/), it's just running a simple `git` command that generates a file from all of you commits in the repository.

- Create a Meteor tutorial app and define the tutorial objects - also described [here](http://meteor-tutorial-tools.readthedocs.org/en/latest/new-tutorial/).

- Write your tutorial and use the `diffBox` helper to generate the actual HTML of the DiffBox.

**Note that commit without the speical format are also legal, but won't be available for creating diff-box!**

## How to add new steps to the tutorial?


## How to edit existing commits?

So this is there it becomes interesting - we want to keep the order of the commits as it should be in the tutorial.

Let's understand it with this order of commits:

````
Step 1.4: Create a new service
Step 1.3: Create a new view
Step 1.2: Create a new component
Step 1.1: Add the application dependencies
Step 1.0: Create new application
````

So now we created our tutorial, and we noticed that we have a bug in `Step 1.2` - our instinct is to go to the latest commit (most updated state of the repository) and add a new commit, and this will be the result:

````
Fix for step 1.2
Step 1.4: Create a new service
Step 1.3: Create a new view
Step 1.2: Create a new component
Step 1.1: Add the application dependencies
Step 1.0: Create new application
````

So now we have a commit on top of the rest of the commit and if we get the lastest repository commit - everything will work great and we will have the bug fixed we just applied.

This is good for regular applications or projects - but in case of a tutorial it isn't good at all - if we generate the diff box for the commit with `Step 1.2` we will see the code with the bug!

So as you might already understand - we need to edit the actual `Step 1.2` commit, without adding new commits!

In order to edit existing commits, we need to get the actual commit with the bug, edit it, keep the same commit message and the same commit id and then generate a new PATCH file.

This might sound complicated but it isn't, it just requires from you to know how to use some `git` commands and basic `vi` commands. I also recommend to use [SourceTree](https://www.sourcetreeapp.com/) - it's great Git GUI tool, but it is not enough and note that you **must** know how to use the command line git.


So let's edit the commit:

- Go the the project's repository after you clone it, make sure you all up-to-date (`git pull`) and make sure that you do not have any commits that you did not pushed, or any other uncomitted changes! (**This is VERY important**) 
- Find the commit id you want to edit, you can simply do it in SourceTree. For example, here:
![1](http://s10.postimg.org/qs4f1d2nd/image.png) 

- So in our case, we want to edit commit id `d002ba8`, so we need to go back in time and to set our local repository to that commit. This done by running the following command:

````
  git rebase -i d002ba8~1
````

- Now you will get the Interactive Rebase screen of git - you will see your commit in the first line:

![2](http://s8.postimg.org/sz0avbymt/Screen_Shot_2016_02_08_at_16_42_51.png) 


- Notice the `pick` near you commit? great! we want to edit that commit, so use your `vi` skills and change the word `pick` to `edit`, than exit and save your changes in `vi` (ESC, `:`, and then `wq!`).

- Great, now you in edit mode, and the repository is set to the commit you want to edit! ** so now make your changes to the file / files **

- Done with that file? Great. you now have two options: 

1. Keep the original commit and apply the changes to it, by running:
2. 
2. 
2. `

## Troubleshoot

#### How to create a new tutorial app?

Creating a new tutorial described [here](http://meteor-tutorial-tools.readthedocs.org/en/latest/new-tutorial/).
