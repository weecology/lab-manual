---
title: "SSH"
type: book
description: >
  How to use SSH to access remote servers and GitHub 
---

## What is SSH?

SSH (short for "secure shell") is a computer protocol for encrypting access to computers over a network. Typical use cases are:
* accessing HiPerGator and Serenity servers from a laptop or desktop machine, while on the UF network
* cloning, pulling, or pushing to GitHub repositories

## What software do I need?

SSH should be pre-installed with Mac OS, Windows 10, and Linux.
On other versions of Windows, you might want to download [Git Bash](https://gitforwindows.org/) which also contains some other useful tools.

## What is an SSH key?

Access to servers through SSH involves authenticating yourself with a username and password (the same as if you were logging in directly to the machine).

Alternatively, you can generate a digital "key" that provides access to the keyholder. Typically, you generate an SSH key for your computer, and then set up the appropriate file on the server(s) you wish to access. Then, instead of authenticating yourself with your username and password for the server, you instead use the SSH key, which is verified by the paired file previously copied to the server. (You can also provide a passphrase in order to use your SSH key, but as it's stored on your laptop or desktop and requires you to be logged in, this security step is optional - opinions vary on this.)

## Setup Instructions (GitHub)

GitHub has fairly detailed [instructions](https://help.github.com/en/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent) on creating a new SSH key;

and further [instructions](https://help.github.com/en/github/authenticating-to-github/adding-a-new-ssh-key-to-your-github-account) to enable it for use on Github.

## Setup Instructions (Serenity / HiPerGator / generic)

To setup an SSH key for use on Serenity, we assume you have gone through the steps described in the instructions for GitHub to create an SSH key. This creates both the key itself (usually located in `~/.ssh/id_rsa`), and a paired file that verifies that the key is correct (usually located in `~/.ssh/id_rsa.pub`).

**If you are setting up an SSH key on HiPerGator, note that you probably already have one in the default location, which is used for communicating between different HiPerGator nodes. You may only need to follow the [instructions](https://help.github.com/en/github/authenticating-to-github/adding-a-new-ssh-key-to-your-github-account) to enable its usage for github, as well.**

1. Log in to the server you wish to use the SSH key on.
2. Edit the `~/.ssh/authorized_keys` file *on the server*. It may already have contents, in which case, go to a new, blank line.
3. Copy over the contents of the `~/.ssh/id_rsa.pub` from your local computer. It will look something like:
```
ssh-rsa *************long-string of random characters************* <email address>
```

**(If you see something like: `-----BEGIN RSA PRIVATE KEY-----`, you are using the wrong file!!)**

4. Save the modified `~/.ssh/authorized_keys` file on the server.
5. Try to connect using ssh. In the command line on your local computer:
```bash
ssh <username>@<server>
```

You should authenticate without having to enter your password.

