# GitHub Collaboration Guidelines: Managing `main`, `developer`, and `test` Branches

This document outlines a structured workflow for creating and managing a GitHub repository, collaborating in a team using multiple branches (`main`, `developer`, `test`), and setting up branch protection rules to control merging changes between branches.


---

## Table of Contents
- [Creating a New Repository](#creating-a-new-repository)
- [Setting Up Branches](#setting-up-branches)
- [Getting Started with Git](#getting-started-with-git)
- [Branching Workflow: `main`, `developer`, and `test` Branches](#branching-workflow-main-developer-and-test-branches)
- [Setting Up Branch Protection Rules](#setting-up-branch-protection-rules)
- [Making Changes to the Code](#making-changes-to-the-code)
- [Committing and Pushing Changes](#committing-and-pushing-changes)
- [Pull Requests and Merging Process](#pull-requests-and-merging-process)
- [Best Practices for Collaboration](#best-practices-for-collaboration)
- [Git Cheat Sheet](#git-cheat-sheet)
- [Inviting Collaborators](#inviting-collaborators)

---

## Creating a New Repository


### 1. Create a New Repository on GitHub
To create a new repository:
1. Go to [GitHub](https://github.com).
2. In the upper-right corner, click the **+** icon and select **New repository**.
3. Fill in the repository details:
   - **Repository name**: `your-repo-name`
   - **Description**: A brief description of your project.
   - **Public/Private**: Choose whether your repository is public or private.
   - **Initialize with README**: Check this if you want a README file created for you.
4. Click **Create repository**.


### 2. Clone the Repository Locally
After creating the repository, clone it to your local machine:

```bash
git clone https://github.com/your-username/your-repo-name.git
```

--------------------------------------------------------------




# Setting Up Branches

## In this workflow, we'll be using three main branches:

    main: The production branch where only tested and approved code is merged.
    developer: The branch where developers make and test initial changes.
    test: A branch where final testing happens before merging into main.


## 1. Creating Branches

To create the developer and test branches, use the following commands after cloning the repository:

``` git checkout -b developer
```
```
git push origin developer
```
```
git checkout -b test
```
```
git push origin test
 ```

----------------------------------------------------------

After pushing the branches to GitHub, the repository will have three active branches: main, developer, and test.

---------------------------------------------------------------------------


# Getting Started with Git

Checking Git Installation
Ensure Git is installed by checking the version:

```
git --version
```

If not installed, follow the instructions to install Git.

------------------------------------------------------------



# Branching Workflow: main, developer, and test Branches

## 1. Developer Branch:

Developers will work on the developer branch. This is the branch where new features or bug fixes are initially developed. When a feature is complete, the changes will be pushed to the developer branch and tested locally.

## 2. Test Branch:

Once changes in the developer branch are stable, they will be merged into the test branch for further testing (e.g., integration testing, QA testing). This branch serves as the final stage before moving changes to main.

## 3. Main Branch:

After successfully testing changes in the test branch, the code can be merged into the main branch. This process should involve a pull request (PR) and a review by an administrator before merging.


-------------------------------------------------------------------



# Setting Up Branch Protection Rules

## Protecting the main Branch
To ensure that no one can directly push to the main branch without approval:
   1. Go to Settings: Open your GitHub repository and click on the Settings tab.
   2. Branch Protection: Under the left-hand menu, select Branches.
   3. Add Rule: Click Add Rule under the Branch Protection Rules section.
   4. Configure Protection for main:
        Branch Name Pattern: main
        Require pull request reviews before merging.
        Require status checks to pass before merging.
        Restrict who can push to matching branches (Only allow administrators or specific roles).
   5. Approval Process: Enable Require pull request approvals and Dismiss stale pull request approvals.
   6. Include Administrators: Optionally, ensure that administrators also require PR reviews to merge code.
   7. Create Rule: Click Create to save the rule.

## Protecting the test Branch

Repeat the steps above for the test branch, ensuring that changes can only be merged into test from the developer branch and only after review.

----------------------------------------------------------------------



# Making Changes to the Code
1. Swith to the developer branch:
```
git  checkout developer
```
2. Make the necessary changes to the code in your local repository.
3. Stage the changes:
```
git add .
```
4. Commit the changes with a descriptive message:
```
git commit -m "Add feature XYZ"
```

---------------------------------------------------------------------



# Committing and Pushing Changes

1. After committing, push the changes to the developer branch on GitHub:
```
git push origin developer
```
--------------------------------------------------------------

# Pull Requests and Merging Process

## 1. From developer to test
1. After pushing your changes to developer, create a pull request to merge developer into test.
2. Go to Pull Requests on GitHub and click New pull request.
3. Choose developer as the base and test as the compare.
4. Add a meaningful title and description, and submit the PR.
5. The team can review and approve the PR before merging into test.

## 2.From test to main
1. After successfully testing the code in test, create a new pull request to merge test into main.
2. Similar to the previous step, go to Pull Requests, select main as the base and test as the compare.
3. Submit the PR for approval by the administrator. Only after their approval, the changes will be merged into main.

---------------------------------------------------------------



# Best Practices for Collaboration

1. Use Descriptive Commit Messages: Every commit should describe what has been changed.

2. Create Small, Focused Branches: Branches should be feature-specific or bug-fix-specific.

3. Always Pull Latest Changes: Before starting work, pull the latest changes from developer or test to avoid merge conflicts.
```
git  pull origin developer
```
4. Rebase Before Merging: To maintain a clean history, rebase your branch on top of the target branch before submitting a pull request.
```
git rebase origin/developer
```
5. Testing is Crucial: Always test changes in the test branch before merging to main.

---------------------------------------------------------------------------



# Git Cheat Sheet

## Command	Description

```git clone <repository-url>```	Clone the repository to your local machine.

```git checkout -b <branch-name>```	Create and switch to a new branch.

```git add .```	Stage all changes for commit.

```git commit -m "message"```	Commit the changes with a message.

```git push origin <branch-name>```	Push the changes to the specified branch on GitHub.

```git pull origin <branch-name>```	Pull the latest changes from the specified branch.

```git fetch origin``	Fetch updates from the remote repository.

```git merge origin/<branch-name>```	Merge the specified branch into the current branch.

```git rebase origin/<branch-name>```	Rebase the current branch on top of the specified branch.

```git status```	Check the status of your working directory.

```git log```	View the commit history.

```git reset --hard <commit-hash>```	Reset your working directory to a specific commit.

----------------------------------------------------------------



# Inviting Collaborators

## To work with others on your repository, you can invite them as collaborators:

1. Go to Your Repository: Open your GitHub repository.
2. Settings: Click on the Settings tab at the top of the page.
3. Manage Access: In the left sidebar, click on Manage access.
4. Invite Collaborators: Click on the Invite teams or people button.
5. Enter Username or Email: Type the GitHub username or email address of the person you want to invite.
6. Select Role: Choose the permission level for the collaborator (e.g., Write, Read).
7. Send Invitation: Click Add to send the invitation. The invited person will receive a notification and can accept the invitation.