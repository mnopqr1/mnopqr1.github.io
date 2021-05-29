---
layout: post
title:  "How to use Github with two identities"
---

I have one Github account for work stuff and one Github account for private stuff. Yes, a split identity on Github.

I always struggle to set up a new repository on Github because the identities will clash somehow and a work repository ends up receiving commits made by my private account, etc. This defeats the whole purpose of course.

Here's how to do it. For the purposes of this example, imagine I have two Github accounts, one called `samwork` and one called `samprivate`. I'll describe how to set up a repository called `awesomerepository` for `samwork`. There are ten steps, from 0-9.

### One-time setup of hostnames
Step 0. Make sure that the file `~/.ssh/config` contains the correct SSH identities. You need to give a "Host" name to the two different accounts. I chose `gh-samwork` and `gh-samprivate` We will use these host names later.[^ssh] For example, my SSH config file looks like:


    # Account Work
    Host gh-samwork
        HostName github.com
        User git
        IdentityFile ~/.ssh/id_rsa_samwork

    # Account Private
    Host gh-samprivate
        HostName github.com
        User git
        IdentityFile ~/.ssh/id_rsa_samprivate


### Creating a new repository under the correct account


1. Log in to Github.com with the correct account.

2. Initialize a new repository on the Github website by clicking "New repository". **Don't** make any commits or readme files.

3. In a Terminal, navigate to the local folder that you want to upload to the repository.

4. If it is not already a Git repository, do `git init`; make some `commit`.

5. If you previously added a remote called `origin` (for example for the wrong github account!) do `git remote remove origin`.

6. **The crucial step that always trips me up!!!** Now *add the correct remote* (this is where the "Host" from the ssh config file is used!) by doing `git remote add origin gh-samwork:samwork/awesomerepository.git`. 
Note that the standard github instructions tell you to use `git remote add origin git@github.com:samwork/awesomerepository.git`, which is **almost** the same but not quite. I changed the `git@github.com` part of this url into `gh-samwork`. As far as I understand, what this does is: it tells git to look in the `~/.ssh/config` file for a `Host` called `gh-samwork` and follow the instructions that are there. 
Under step 0, we set up the config file so that `gh-samwork` means: go to git@github.com *as the user* `samwork` and *using the identity file* in `~/.ssh/id_rsa_samwork`.

7.  Switch to the main branch by doing `git branch -M main`.

8.  Push the main branch by doing `git push -u origin main`.

9.  Go to Github.com and check that the commit was indeed pushed by `samwork`!

---

[^ssh]: If you need help with SSH keys, Github Docs has a [pretty good tutorial](https://docs.github.com/en/github/authenticating-to-github/connecting-to-github-with-ssh). I did this a while ago and I remember that it was a mild pain but I survived.