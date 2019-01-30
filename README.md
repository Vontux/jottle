# jottle

> jot + bottle

> jot, v. To write briefly, quickly or perhaps even hastily.

> bottle, n. A glass or plastic container with a narrow neck, used for storing drinks or 
other liquids. An umbrella term for a variety of such things, including a **Flask**.

Jottle is a [BROWSE](http://paul-m-jones.com/archives/291) app written with [Flask](http://flask.pocoo.org/). It allows the user to keep and edit text files on a server.

I often find myself needing to write text or code with a computer, usually running Windows, that does not have vim. One way of overcoming this is ssh-ing into my phone and using vim from there. However, all too often, the computer I am using does not have [putty](http://www.putty.org/) installed and getting all the keys and things set up is a bit of a chore, especially if I only want to make a quick note of something. I could just make do with a basic text editor like notepad. I could even just use Google Docs, but I generally prefer to keep my files with me and use other, perhaps cloud based, back up solutions if necessary.

Jottle is my solution to this pretty specific need. It runs on my android phone in [termux](https://termux.com/) on top of [nginx](http://nginx.org/) and [gunicorn](http://gunicorn.org/). So all I need do is open a web browser, point it at my phone and now I can refer to notes stored on my phone and edit them using the [ace](https://ace.c9.io/) editor set up to emulate vim.

It's portable vim in my pocket for when I can't ssh and don't want to upload stuff to someone else's server.

## Fork
This is a fork of the version of jottle found at https://github.com/madacoo/jottle , its primary purpose is to add functionality to create directories as subdirectories and files in the root text folder you specify in config.py. All usage of "I" prior to this section of the readme refer to the author of the original this was forked from "madacoo", in this section it refers to me, Vontux. I decided that since the usecases where file and directory creation is only possible through the user interface controls on the webpage and where they are creatable by just inputting a path that doesn't exist in the url are different enough for it to not quite make sense to do a pull request and instead doing a fork made more sense.

## usage

Once the flask app is running, simply point a browser at its address.

![](example.png)

## dependencies

python 3.6.1
flask 0.12.2
markdown 1.7

## installation

Before jottle will function corrently, config.py must be set up. It contains three properties:

    root        the path to the folder in which you'd like jottle to store files
    key         a key stored as a cookie on any computers authenticated to use jottle
    passhash    a hashed password

root will usually point at the 'root' folder inside the jottle directory, but that's not necessary. key can be anything you like, a random uuid works well. To generate a passhass, you can run hashpassword.py.

Once config.py is ready, deploy jottle as a flask app and you're done. It should work with whichever web server software but is currently only tested with termux + nginx + gunicorn, since that's how I built it to be used.

## license

GPLv3
