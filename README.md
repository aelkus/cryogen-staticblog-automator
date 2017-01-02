# Cryogen Static Blogging Automator 

A small tool for automating the process of authoring posts using the [Cryogen](http://cryogenweb.org) static site blogging framework. Written on macOS Sierra 10.12.2. Minimally tested. Designed to make writing posts for static site blogs less rote. 

## Dependencies 

* [Python 2.7](https://docs.python.org/2/)
* [Git](https://git-scm.com)
* [Clojure](https://clojure.org)
* [Leiningen](http://leiningen.org)
* [Cryogen](http://cryogenweb.org)

## Usage 

### Installation 

First, install the dependencies if you do not already have them. You will also need to ensure you have two folders in your root directory: 

1. An offsite blog created using the command `lein new cryogen my-blog` (where my-blog could be any name you choose for the offsite blog). 
2. An github.io directory with your `username.github.io` blog cloned to it (where username is something like aelkus.github.io). 

Now, clone this repo to root, `cd` into the repo, and configure the `cfg.ini` file to fit your own needs. As this was created on OSX, I've used the OSX directory format for the fields in the `cfg.ini` file. Change `yourname`, `offsite_blog`, and `your_editor` to whatever you like. My own default setup for `editorCommand` is `sublime -w` for Sublime Text. 

```
rootDirectory = /Users/yourname/
stagingDirectory = /Users/yourname/offsite_blog/
postDirectory = /Users/yourname/offsite_blog/resources/templates/md/posts/
publicDirectory = /Users/yourname/offsite_blog/resources/public/*
siteDirectory = /Users/yourname/yourname.github.io/
editorCommand = your_editor -w 
```
### Startup 

Inside the repo, run the command `python postautomator.py` (if python2 is your default python) or run `python2 postautomator.py` with the date of your post and the name as commmand-line arguments. Example usage: `python postautomator.py 2017-01-01 revenge_for_harambe.md`. You will be then queried about about whether or not you would like to write a post. If so, type `y`. You will then be taken to your editor of choice to write/edit the new post. When you are done, close the post file you are editing. The program will prompt you to answer about whether you would like to publish. 

Type `y` for yes. The program then generates a local preview of your static site in the browser. Type control-c (CTRL-C) to exit from the preview (which will build the HTML files necessary for your static site). You will be asked one more time about whether you want to publish. If so, type `y`. The HTML files will be copied from your offsite blog to your github.io blog and git will be called to add, commit (with the message `new post`), and push your new static site files to Github. At this point, the script will end and you will be returned to your command line. 

If at any time you type `n` to a prompt, the program will close and you will be returned to the command line. 
