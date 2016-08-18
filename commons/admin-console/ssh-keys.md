---
title: SSH Keys
position: 2
shortdesc: Add and manage SSH keys for push and deployments
tags:
- account-setup
keywords:
- git
- deploy
- deployment
- push
- ssh
- sshkeys
---

# SSH keys

SSH keys are used to establish a secure connection between your computer and Clever Cloud.  
You need to add a SSH key to your Clever Cloud's account to deploy via Git.  
A user can have multiple SSH keys.

<div class="alert alert-hot-problems">
<h4>Warning:</h4>
<p>A SSH key can be used with only one account. A SSH key is used to identify the actions made by a user and must be
associated with only one account.<br />
If a key is used by more than one account, a warning will be displayed in the console.</p>
</div>

How to add your SSH key on Clever Cloud?

### Github account and SSH key on Clever Cloud

If your account is linked to GitHub, a new panel with your GitHub SSH key will appear in the "SSH Key" menu.
So you can add every key via a simple click and you don't have to add it manually.

## Find your SSH key

You can already have an SSH key and so do not need to generate a new one. To check if you have one, follow the steps:  

### Linux and Mac

1. Wether you use Mac or Linux, open your Terminal application.
2. Run `$ cd ~/.ssh/` in your Terminal.
3. If the folder exists, run `$ ls` and check if a pair of key exists : *id_rsa* and *id_rsa.pub*.
   If you can find them, you do not need to generate a new one, simply go to the following
   "Add you key on Clever Cloud" part!

<br/>

### Windows

1. If you don't have it, download [Git for Windows](https://git-for-windows.github.io/) and install it.
2. Run **Git Bash** (from the *Start Menu* or from the *Explorer* with the contextual menu (right click)).
3. Run `$ cd ~/.ssh/` in your Terminal.
4. If the folder exists, run `$ ls` and check if a pair of key exists : *id_rsa* and *id_rsa.pub*.
   If you can find them, you do not need to generate a new one, simply go to the following
   "Add you key on Clever Cloud" part!

## Create your SSH key

If you read the previous section, you should have a Terminal open.

1.  In your Terminal, enter the following bash line:

    ```bash
    $ ssh-keygen -t rsa -C "your_email@youremail.com"
    ```
    This command creates a new ssh key using the provided email, so that the owner of the key can be identified.

2.  When asked, enter a passphrase:

    ```bash
    Generating public/private rsa key pair.
    Enter file in which to save the key (/your_home_path/.ssh/id_rsa):
    # Now you should enter a passphrase.
    Enter passphrase (empty for no passphrase): [Type a passphrase]
    Enter same passphrase again: [Type passphrase again]
    ```

    Which should give you something like this:

    ```bash
    Your identification has been saved in /your_home_path/.ssh/id_rsa.
    Your public key has been saved in /your_home_path/.ssh/id_rsa.pub.
    The key fingerprint is:
    01:0e:e5:2d:ab:98:d6:17:a1:6d:f0:68:9f:d0:a2:db your_email@youremail.com
    ```

## Add your SSH key on Clever Cloud

### Public SSH Key
To declare your **public SSH Key** on Clever Cloud, in the left navigation bar, go in "Profile" and in the "SSH Keys" tab.

Add the key by entering a name and the public SSH key. The key is the entire content of the **id_rsa.pub** file.

<figure class="cc-content-img"><a href="/assets/images/ssh1.png"><img src="/doc/assets/images/ssh1.png"></a></figure>
<figcaption>
The SSH Key manager.
</figcaption>

In this tab, you can list all your *SSH Keys* available on Clever Cloud and delete them if necessary.
<div class="alert alert-hot-problems">
<h4>Remember</h4>
<p>Your public SSH key must be associated with only one account.</p
</div>

If you see "*access denied*" or "*password:*" when you
[push on Clever Cloud](https://www.clever-cloud.com/doc/clever-cloud-overview/add-application/#git-deployment),
your SSH Keys may be invalid or not available on Clever cloud. Please check that you SSH Key is present and valid in
your profile.

### Private SSH Key
If you want to clone a repository from a private repository, you can add a [Private SSH Key](https://www.clever-cloud.com/doc/clever-cloud-overview/common-application-configuration/#private-ssh-key).



<i class="icon-question-sign"></i> **Need help about SSH keys?**  
Contact us at <support@clever-cloud.com> or you can
[read more about SSH Keys](http://git-scm.com/book/en/Git-on-the-Server-Generating-Your-SSH-Public-Key).

## Check your ssh configuration

To check if your ssh key is correctly configured, you can try to run:

```bash
    ssh git@push.clever-cloud.com
```

The first time, you may have to type "yes" to continue.

If you see "Permission denied (publickey).", something went wrong, feel free to contact the support, otherwise everything should be fine.
