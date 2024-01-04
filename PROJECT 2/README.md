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


## Listing your git Branches

Use the command below to list the branch on your local git repository

## 1. git branch


![Alt text](<Images/Screenshot 2024-01-04 at 17.08.53.png>)


## Change into an Old Branch

To change into an exiting or old branch use the command below:

## 2. git chackout <branch-name>


![Alt text](<Images/Screenshot 2024-01-04 at 17.25.32.png>)


## Merging a Branch into another Branch

Lets say we have A and B. And we want to add the content of branch B into A.

First we change into branch A and run the git command below:

## 3. git merge B


## Deleting a git branch

When new feature is added to an application, its often done in a feature branch. Usually this feature branch is deleted when the code must have tested and merged into a staging or dev environment depending on the branch strategy of the team. Git branch can be deleted with the command below:

## 4. git branch -d <branch_name>

This is by no means all that you can do with branches in git. To learn more types of the commands ' git branch --help ' on your terminal.


## COLLABORATION AND REMOTE REPOSITORIES

Lets take a moment to recap about what we have learnt so far. We learnt that git is a distributed version control system. That essentially solve the problem sharing source code and changes made to source code. We then learnt about some operation like initialing git repository in our local machine, creating commit,branches etc.
We also mention in passing that git is used for collaboration among remote teams(developers residing in different location). But come to think of it how can developer working remotely collaborate(making changes, adding,updating etc) on the same code base since we currently have our code in our local computer.

## Creating a Github Account

Step 1. Head over to join github.com

Step 2. Next enter your username, password,and email

Step 3. Next click on the verify buttom to very your identity

Step 4. Next click on the Create button to create your account

Step 5. An activation code will be sent to your email, enter the code in textboxes provided then click continue

Step 6. Select your preferences and click continue

Step 7. A list of github plans wikll be shown to you. Click continue for free


## Creating Your First Repository

Step 1. Click on the plus sign at the top right coner of your github account. A drop down menu will appear, select new repository

Step 2. Fill out tghe form by adding a unique repository name, description and ticking the box to add a Readme.md file

Step 3. Click the green button below to create your repository.


## Pushing Your Local Git Repository To Your Remote Github Repository.

Having created a github account and a github repository in earlier steps. Lets send a copy of our story to our repository in github.
We will achieve this by following the steps below:

• Add a remote repository to the local repository using the command below

## git remote add origin <link to your github repo>


![Alt text](<Images/Screenshot 2024-01-04 at 18.52.13.png>)

To get the remote link click on the green button code, copy the https link. A screenshot is shown below.

• After commiting your changes in your local repo. Your push the content to the remote repo using the command below:

## git push origin <branch name>


![Alt text](<Images/Screenshot 2024-01-04 at 19.02.26.png>)

The word origin refers to your remote repo link, it evaluate to the remote repo. It can be any word you choose.


## Cloning Remote Git Repository

The git clone command helps us make a copy of remote repository in our local machine. See it as a git tool for downloading remote repository into our local machine. The command is as follows:

## git clone <link to your remote repository>


![Alt text](<Images/Screenshot 2024-01-04 at 19.18.48.png>)


## BRANCH MANAGEMENT AND TAGGING

Introduction to Markdown Syntax 

Markdown syntax ia a lightweight markup language that is widely used for formatting plain text. It allows you to add formatting element to your text without using complex HTML or other formatting language. Markdown is commonly used for creating documents, README files, forum posts, and even web pages.

Here is the most commonly used markdown syntax elements:

### 1. Headings: To create heading, use the hash symbol at the beginning of the line. The number of hash symbol used indicate the level of the heading.

# Heading 1
## Heading 2
### Heading 3

### 2. Exphasis: asterisks or underscore is used to Emphasis text

* italic * or _ italic _

** bold ** or __ bold __

### 3. List: markdown has support for both ordered and unordered

unordered list example:

- Item 1
- Item 2
- Item 3

ordered list example:

1. First item
2. Second item
3. Third item


### 4. Links: To create a hyperlink, use square brackets for the link text followed by parentheses containing the URL. Example:

[visit darey.io](https://www.darey.io)

### 5. Images: To play an image, use an exclamation mark followed by square brackets for the alt text and parentheses containing the image URL.

![Alt Text](https://example.com/image.jpg)

### 6. Code: To display code or code snippets, use backticks (') to enclose the code.
example:

`console.log('Welcome to darey.io')`

Like i earlier mentioned these are the most commonly used markdown syntax elements. Tp learn more visit the link: markdown documentation

