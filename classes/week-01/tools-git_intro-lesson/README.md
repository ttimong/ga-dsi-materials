---
Title: Intro to Git
Duration: "1:30"
Creator:
    Name: Dave Yerrington, Sam Stack
    City: SF, DC
---


# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Intro to Git


### LEARNING OBJECTIVES
*After this lesson, you will be able to:*
- Use and explain common Git commands, including `init`, `add`, `commit`, `push`, `pull`, and `clone`.
- Distinguish between local and remote repositories.
- Create, copy, and delete repositories locally or on GitHub.
- Clone remote repositories.
- Establish Secure Shell connections to remote repositories.

### STUDENT PRE-WORK
*Before this lesson, you should already be able to:*
- Show that you've completed [Code Academy: Learn Git](https://www.codecademy.com/learn/learn-git).
- Install [Homebrew](http://brew.sh/).
- Install Git (after installing Homebrew, type "brew install git").
- Set up a GitHub account.


### LESSON GUIDE
| TIMING  | TYPE  | TOPIC  |
|:-:|---|---|
| 20 min  | [Introduction](#introduction)   | Git vs. GitHub vs. GHE and Version Control  |
| 15 min  | [Git Basics](#git_basics)  | Let's 'Git' into it!  |
| 10 min  | [GitHub & GitHub Enterprise Accounts](#gh_ghe_accounts)  |  'Git' on GitHub and GitHub Enterprise:  |
| 15 min  | [Creating and Cloning Repos](#making_cloning)  | Making and Cloning Repositories  |
| 10 min  | [Pulling](#pulling)  | Create a Pull Request on GitHub  |
| 15 min  | [Secure Shell(SSH)](#ssh) | Create a SSH Connection  |
| 10 min  | [Independent Practice](#independent_practice)  
| 5 min  | [Conclusion](#conclusion)

---
<a id="introduction"></a>
## Git vs. GitHub and Version Control, an Introduction (20 min)


First things first — Git is not GitHub. This is a common mistake people make.


#### What is Git?

[Git](https://git-scm.com/) is:

- A program you run from the command line.
- A distributed version control system.

Programmers use Git so that they can keep a history of all changes made to their code. This means that they can roll back changes (or switch to older versions) as far back as when they started using Git in their project.

A code base in Git is referred to as a **repository**, or **repo**, for short.

Git was created by [Linus Torvalds](https://en.wikipedia.org/wiki/Linus_Torvalds), the principal developer of Linux.

#### What is GitHub?

[GitHub](https://github.com/) is:

- A hosting service for Git repositories.
- A web interface to explore Git repositories.
- A social network of programmers.

Some other points to note: 

- We all have individual GitHub accounts and store our code bases there.
- You can follow users and star your favorite projects.
- Developers can access code bases on other public accounts.
- GitHub uses Git.

#### What is GitHub Enterprise (GHE)?
[GitHub Enterprise](https://enterprise.github.com/home) Is:

- Professional application of GitHub
- All repository data is stored on private and/or local machines and networks.

Where GitHub is the _public_, 'Social Network' for programming and programmers, Github Enterprise is the _private_, professional application of GitHub.  Because, GitHub and GitHub Enterprise have a similar structure and are based off the `git` language, interacting with the two is is almost identical.  

**Additional information on [GitHub.com vs GitHub Enterprise](https://enterprise.github.com/downloads/en/comvsenterprise-082415.pdf)**

Over the course of this class we will be interacting with both GitHub and GitHub Enterprise(GHE).  You will set up a GHE account for sharing course materials and as a private repo for you to store your own works-in-progress.  

You will also setup a GitHub account as a location for you to host projects and work that you want to exhibit or share.  


#### Can you use Git without GitHub?

Think about this quote: “Git is software. GitHub is a company that happens to use Git software.” So yes, you can certainly use Git without GitHub!

Your local repository consists of three "trees" that are maintained by Git.

- **Working Directory**: holds the actual files.
- **Index**: acts as a staging area.
- **HEAD**: points to the last commit you've made.

![workflow](https://cloud.githubusercontent.com/assets/40461/8221736/f1f7e972-1559-11e5-9dcb-66b44139ee6f.png)

#### What about commands?

There are also a variety of commands you can use in Git. You can take a look at a list of the available commands by running:

```bash
$ git help -a
```

Even though there are lots of commands, in the course, we will really only need about 10.

<a id="git_basics"></a>
## Let's Git into it!: Code-Along (15 min)


First, create a directory on your Desktop.

```bash
$ cd ~/Desktop
$ mkdir hello-world
```

You can place this directory under Git revision control using the following command:

```bash
$ cd hello-world # dont forget to CD into the folder.
$ git init
```

Git will reply:

```bash
Initialized empty Git repository in <location>
```

You've now initialized the working directory.

#### The .git folder

We can look at the contents of this empty folder using this command:

```bash
ls -A
```

We should see that there is now a hidden folder called `.git`. This is where all of the information about your repository is stored. There is no need for you to make any changes to this folder. You can control all of the Git flow using `git` commands.

#### Add a file

Let's create a new file.

```bash
$ touch a.txt
```

If we run `git status`, we should get:

```bash
On branch master

Initial commit

Untracked files:
  (use "git add <file>..." to include in what will be committed)

	a.txt

nothing added to commit but untracked files present (use "git add" to track)
```

This means that there is a new, **untracked** file. Next, tell Git to take a snapshot of the contents of all files under the current directory. (Note the `.`).

```bash
$ git add .
```

This snapshot is now stored in a temporary staging area, which Git calls the "index."

#### Commit

To permanently store the contents of the index in the repository, (i.e., commit these changes to the "HEAD"), you need to run the following command:

```bash
$ git commit -m "Please remember this file at this time"
```

You should now get:

```bash
[master (root-commit) b4faebd] Please remember this file at this time
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 a.txt
```

#### Checking the log

If we want to view the commit history, we can run:

```bash
git log
```

As a result, you should see:

```bash
* b4faebd (HEAD, master) Please remember this file at this time
```
<a id="gh_ghe_accounts"></a>
## 'Git' on GitHub and GitHub Enterprise:

For those of you that have not already set up your GitHub and GitHub Enterprise accounts, lets take a minute to do that now.

Account creation for both is simple.  Create a _Username_, and provide an _email_ & _password_.

_Keep in mind while you **can** use the same email, username and password for both accounts, they are **wholly separate**._

**[GitHub](https://github.com/)**
 _This is yours_
 
**[GitHub Enterprise for General Assembly](https://git.generalassemb.ly/join?source=header)**
_This is ours_

You can use a GitHub account to create a GitHub Enterprise account, but that will be **your** enterprise; in that, you will not be able to use it to access the General Assembly Enterprise GitHub.

If in the futur,e you join another GitHub Enterprise you will also need to create another account for said enterprise.  



<a id="making_cloning"></a>
## Making and Cloning Repositories: Code-Along (15 min)

When using Git, GitHub and GHE it is common to have your repositories in several locations.  Typically when we use GitHub and GHE we will have two repository locations, **Remote** and **Local**.
- **Remote:** - Repositories that are not stored in our current location/machine. Usually where we store the repo.
- **Local:** - Repositories that are stored on our current machine. Usually where we work on the repo.


**Let's do this together:**

1. Go to your GitHub account.
2. On the right-hand side, hit the `+` button for `New repository`.
3. Name your repository `hello-world`.
4. **Initialize this repository with a `README`**. (Now we can `git pull`).
4. Click the big, green `Create Repository` button.

We now need to connect our local Git repository with our newly created remote repository on GitHub. We have to add a "remote" repository, an address where we can send our local files to be stored.

On the right-hand side of your GitHub there should be a green 'Clone or download' button. This button should reveal a tiny window with a URL.  Copy the provided URL, which is the path to this remote repo.  


_Make sure you changed directories into `hello-world` prior to running this_
```bash
git remote add origin git@github.com:github-name/hello-world.git
```

_At this point you **may** be prompted for a password, especially when using GHE_

#### Pushing to GitHub

In order to send files from our local machine to our remote repository on GitHub, we need to use the command `git push`. However, you also need to add the name of the remote repo — in this case, we called it `origin` — and the name of the branch, in this case `master`.

```bash
git push origin master
```

This should fail because of new files in the remote repo.

#### Pulling from GitHub

Just as we added the `README.md` in our repo, we need to first `pull` that file to our local repository to check that we don't have a "conflict."

```bash
git pull origin master
```

```bash
git status
```

```bash
git add .
```

```bash
git commit -m "README.md"
```

Once we've done this, you should see the `README` file on your computer as it has been added to your local HEAD.

```bash
ls
```

Open up the `README` and type some kind of modification and/or addition then save it.


```bash
git add .

git commit -m"Updated README"
```

Now you can push your changes to your remote on GitHub.

```bash
git push origin master
```

Refresh your GitHub web page, and the files should appear.

Using the `git remote add` method is useful for taking an existing local repository and creating a new remote one (putting it on GitHub).  

#### Independent Practice (10 min)

Repeat the steps above, starting from the creation of the remote repo, to create a _local_ and _remote_ repository with your GitHub Enterprise account.  

### Cloning your first repository

Alternatively, you can clone this repo from your GitHub link to have it automatically configured in a new directory.

```
git clone https://github.com/github-username/hello-world.git
```

Now that everyone has a repository on GitHub, let's clone one!

Cloning allows you to make a local copy of a remote repository.

Navigate back to your Desktop, and **delete your `hello-world` repository**.

```bash
cd ~/Desktop
rm -rf hello-world
```

Now, ask the person sitting next to you for his or her GitHub name and navigate to that repository on GitHub.

```bash
https://www.github.com/<github-username>/hello-world
```

On the right-hand side, you will see the green button 'Clone or download'.

#### Clone that repo!

To retrieve the contents of the repo, all you need to do is:

```bash
$ git clone git@github.com/<partners-github-username>/hello-world.git
```

Git should reply:

```bash
Cloning into 'hello-world'...
remote: Counting objects: 3, done.
remote: Total 3 (delta 0), reused 3 (delta 0), pack-reused 0
Receiving objects: 100% (3/3), done.
Checking connectivity... done.
```

You've now cloned your first repository!   The process will be the same with GitHub Enterprise.  

Cloning is must useful when there is a repo that exists remotely that we want on our local machines.


<a name="pulling"></a>
## Create a Pull Request on GitHub: Code-Along (10 min)

#### What's a "Pull Request"?
Often times when we are working on a project with other collaborators we all can't work on the same repo at the same time so we have these things called _branches_.  With branches we can create a branch off of the main repo or "Master Branch", perform our work whether that be additions or alterations and then merge the changes we made on _our_ branch back into the master.  

You can probably think of a few ways that multiple people trying to merge their work can get messy.  Fortunately, we have Pull Requests as means of queing and validating merges.  Rather than having your branch merge automatically, your request will go through an administrator who can review your changes and additions and approve or deny your request.  

_Even though we are trying to **push** our information into the master, it is called a pull request because we are making a request to the administrator to **pull** or branch into the master.

#### Creating a Pull Request
Before you can open a pull request, you must create a branch in your local repository, commit to it, and push that branch to a repository or fork on GitHub.

1. Visit the repository you've pushed to.
2. Click "Branch:master" on the left-hand side and create a branch called 'branch-edits' by typing in the box and hitting enter.  This should put you on your new branches page.
3. Make sure you're on your new branch and in GitHub create a new '.md' or '.txt' file using the 'Create new file' button. Call it what you like and place some text in it.
4. Click the "Compare & pull request" button in the repository ![pr](https://cloud.githubusercontent.com/assets/40461/8229344/d344aa8e-15ad-11e5-8578-08893bcee335.jpg).
5. You'll land right onto the compare page. Next, you can click "Edit" at the top to pick a new branch to merge to using the "Head Branch" dropdown menu.
4. Select the target branch that your branch should be merged to using the "Base Branch" dropdown menu.
5. Review your proposed change.
6. Hit "Click to create a pull request" for this comparison.
7. Enter a title and description for your pull request.
8. Click "Send pull request."

As you are working on your own repo in your own GitHub you will be able to merge the branch at your leisure.

---

By now you have have noticed that you are being prompted quite a bit for your password when interacting with GitHub or GitHub Enterprise via Git.  There are two ways to work around this. 

**[Catching your password in Git](https://help.github.com/articles/caching-your-github-password-in-git/)**

or

**Using SSH and SSH Agent** (_recommended_)  
You can use the guide in the [SSH Setup Guide](SSH-setup.md) or those available on github
- [Working with SSH key passphrases](https://help.github.com/articles/working-with-ssh-key-passphrases/)
- [Generating a new SSH key and adding it to the ssh-agent](https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/)
- [Adding a new SSH key to your GitHub account](https://help.github.com/articles/adding-a-new-ssh-key-to-your-github-account/)

<a id="ssh"></a>

#### Secure Shell (SSH)

SSH, or Secure Shell, is a common means of adding an additional layer of security.  Simply put, the SSH key is used to establish authenticity between a client and a server so that a secure connection or "tunnel" can be formed.  This can be useful for secure file sharing or remote application access.  

#### How SSH works

The SSH process at a high level is relatively simple.  
1. Client makes a request to the server.
2. Server responds asking for authentication.
3. Client provides authentication.
4. If authentication is correct, a connection is established.  

**Note**: You will need to complete which ever process you choose twice. Once for your GitHub account and once for your GitHub Enterprise account.

**Note:** Setting up the SSH Agent is critical if you don't want to be prompted for a password everytime you push or pull via SSH.

#### Additional SSH Troubleshooting:

**Access Denied**  
If you receive a message about "access denied," please notify an instructor or you can read [these instructions for diagnosing the issue.](https://help.github.com/articles/error-permission-denied-publickey/)

**HTTPS to SSH switch**  
If you're switching from HTTPS to SSH, you'll now need to update your remote repository URLs. For more information, see [Changing a remote's URL.](https://help.github.com/articles/changing-a-remote-s-url/)


---

<a id="independent_practice"></a>
## Assess: Independent Practice (10 min)
- Show a partner how to use the following commands: `init`, `add`, `commit`, `push`, `pull`, and `clone`.

<a id="conclusion"></a>
## Conclusion (5 min)
Feel comfortable with Git, GitHub and GitHub Enterprise? As we'll be using them in alot a lot of our coursework, let's make sure you are! 
