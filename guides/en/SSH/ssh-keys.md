---
layout: en
title: 'How to: SSH keys'
---

# How to: SSH keys

Since an SSH client is now available in Windows this guide should work for whatever OS you are
running on. However, keys created this way don't seem to work with PuTTY right away if that's
the SSH client you use. You can look at that guide [here]({{ '/guides/en/SSH/ssh-keys-with-putty' | relative_url }})

1. [The simple way](#the-simple-way)
  * [Creating the SSH key](#creating-the-ssh-key)
  * [Using the SSH key](#using-the-ssh-key)
2. [The less simple way (It's still pretty simple)](#the-less-simple-way-its-still-pretty-simple)

## The simple way

### Creating the SSH key

```
$ ssh-keygen
...
# Leave all the prompts on defaults
...
```
Aaand you're done... This creates a key pair: the _public_ key and the _private_ key

It's highly recommended to protect the key with a _password_. It's one of the prompts
when creating the key so it's easy enough.

If someone requires your key, pubkey, public key or whatever, for authentication,
you should __ONLY__ provide them with the _public_ key, the file that ends with _.pub_,
or rather the contents of that file.

### Using the SSH key 

Presumably you will have added the key to the server. If that's something you have to do
and don't know how to, then look at [this guide]({{ '/guides/en/SSH/adding-key-to-server' | relative_url }})

By default the keys are stored in the users $HOME directory `$HOME/.ssh/id_rsa` and
`$HOME/.ssh/id_rsa.pub`

Connecting to a server is simple enough:
```
$ ssh <username>@<someserver>
# f.x. ssh lucifer@203.0.113.5
# username does not have to be specified if you have the same user on the
# host you are using to connect to the server
```
And you're in... 🕶️💻

## The less simple way (It's still pretty simple)

Sometimes you want to have multiple keys. You have multiple environments or you don't
always have to put in a password when pushing to Github.

You follow the same process but simply specify another path when prompted.
Watch out not to overwrite and old key if you're still using it somewhere, the
process will warn you.
```
# You can save the key in some other directory than $HOME/.ssh/ but the SSH client usually
# looks at the keys in $HOME/ssh/ and tries them until it finds one that works.

$ ssh-keygen
Generating public/private rsa key pair.
Enter file in which to save the key (/home/someuser/.ssh/id_rsa): /home/someuser/.ssh/bananakey
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /home/someuser/.ssh/bananakey
Your public key has been saved in /home/someuser/.ssh/bananakey.pub
```

And if it's under the default folder you can just go `$ ssh someserver.example`

However if it's not in the default directory, and even sometimes it tries multiple keys
and you get "too many authentication failures" you can manually specify the key to use

```
$ ssh someserver.example -i /PATH/TO/SECRET/KEY/FOLDER/key
# This tells SSH to explicitly to use that key.
```

And you're in... 🕶️💻



