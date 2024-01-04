# Git Project

## How To Initialize a Git Repository

Before initializing a git repo you must have installed git in your computer. Follow these steps to initialize a git repo;

• Open a terminal on your computer,eg git bash.

• On your terminal create your working folder or directory eg devOps folder using this command " mkdir DevOps " .

• Change or move into your working directory or folder using this command " cd DevOps " .

• While you are inside the folder,run " git init " command.


![Alt text](<Screenshot 2024-01-01 at 01.28.02.png>)


## MAKING YOUR FIRST COMMIT.

We successfully created our working directory snd initialized it in a git repository in our last section. Now we will make our first commmit. But first lets understand wqhat commit is in git. Commit is more or less saving the change you made to your files. Changes can be adding, modifying or deleting files or text.

Now less make our first commit by following these steps:

• Inside your working directory create a file index.txt using this command "Touch index.txt"

• Write any sentence of your choice inside the text file. Afterwards save your changes.

• Add your changes to git staging area using this command " git add . "

• To commit your changes to git, run the command ' git commit -m "initial commit"

![Alt text](<Images/Screenshot 2024-01-04 at 13.20.36.png>)

The -m flag is used to provide a commit message. The commit messsage is a nice way to provide context about the commit. When writing a commit message, make it descriptive as possible. Let it explain why the commit was made.


## WORKING WITH BRANCHES

Git branch is an important tool for collaboration within remote teams(developers working from different location). They can make separate branches while working on same feature. And at the end of the day, converge their code to one branch.

## Make your first git Branch

To make a new branch run this command: 'git checkout -b

The -b flag helps you create and change into the new branch

Now lets make our first branch following these steps:

• Having made your first commit in the previous lesson

• Make a new branch by running this command ' git checkout -b my-new-branch


![Alt text](<Images/Screenshot 2024-01-04 at 17.00.42.png>)