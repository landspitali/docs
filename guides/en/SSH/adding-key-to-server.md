---
layout: en
title: 'How to: Adding SSH public key to a server'
---

# How to: Add SSH key to server

There are a few ways to add a key to a server. But here we focus on the basics.
Remember, this only concerns __public keys__

1. [Using the SSH client if you already have access](#using-the-ssh-client-if-you-already-have-access)
2. [Manually adding with access to the server](#manually-adding-with-access-to-the-server)
3. [Get someone else to do it](#get-someone-else-to-do-it)


## Using the SSH client if you already have access

You can use the command _ssh-copy-id_ to plop it in there
```
$ ssh-copy-id someserver.example

# Or if you wan't to copy a specific key
$ ssh-copy-id someserver.example -i /PATH/TO/SPECIFIC/key
```

You will be prompted for a password if you haven't already added a key.
Some servers don't allow ssh with password, then this probably won't work for you.

## Manually adding with access to the server

If you don't already have SSH access to a server for a specific user but you have
other means to get on there, the process is a little more involved.

Authorized keys are stored in a file aptly called _authorized_keys_ under the users
_$HOME/.ssh/_ directory. The process is a bit more involved but simple enough.
```
# If the $HOME/.ssh directory doesn't exist, create it
$ mkdir ~/.ssh

# This folder requires specific permissions
$ chmod 700 ~/.ssh

# Then you can edit the authorized_keys file with whatever text editor
# (vi, vim, nano, etc) and copy the public key in there
$ vim ~/.ssh/authorized_keys

# Or you can simply echo the public key into it
$ echo '<KEY HERE>' >> ~/.ssh/authorized_keys

# This file also needs specific permissions
$ chmod 600 ~/.ssh/authorized_keys
```

And you're done.

## Get someone else to do it

Send your key to someone who has administrator access to the server and tell them
to do it. Ez-pz. If you don't like them, send it to them in a format that can't be
easily copied (jpeg screenshot or whatever).

