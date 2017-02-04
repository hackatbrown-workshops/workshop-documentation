# Environment Setup

## Package Management

Package managers are tools for installing software and keeping it up to date. They handle all the little details about where to put files and how to check if there's a new version of something. Using your operating system's package manager makes life a lot easier!

Here, we have instructions for some common package managers. If your operating system isn't listed, ask us how to get started!

### Homebrew - macOS

According to its website, "Homebrew installs the stuff you need that Apple didn't." It's a third-party package manager for macOS that tries to work as smoothly as possible with the software already on your Mac. Installing is pretty straigtforward, just run the following command in a terminal and go through the prompts:

```shell
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

Now, let's install something! How about [HTTPie](https://httpie.org/) , a super helpful tool for making HTTP requests? In your terminal, run the following command:

```shell
brew install httpie
```

If you run `http` now, you should see a message about how to use HTTPie. Homebrew has way more packages than we could possibly list, almost anything you can think of. To find a package, you can use the `brew search` command, like this:

```shell
brew search ruby
# Produces something like this:
chruby imessage-ruby mruby ruby ✔ ruby-install
chruby-fish jruby rbenv-bundler-ruby-version ruby-build
```

### Chocolatey - Windows

 [Chocolatey](https://chocolatey.org/) is a third-party package manager for installing all kinds of Windows applications. To install, you need to open PowerShell [as an administrator](http://www.thewindowsclub.com/how-to-open-an-elevated-powershell-prompt-in-windows-10) (ask if you need a hand!). Then, run this command:

```shell
iwr https://chocolatey.org/install.ps1 -UseBasicParsing | iex
```

Now, let's install something! In a command line, run the following:

```shell
choco install git.install
```

We just installed Git with a single command! No more googling to find the download link or clicking through an installer wizard, it just works! Chocolatey has tons of packages available, and you can go through the list on their [website](https://chocolatey.org/packages) .

## Running a web server

If you're working on any kind of website, it's super helpful to run a web server locally. Web servers are the programs that make your HTML and CSS files available over the network. For testing, you could just open the files directly, but there are some differences in how your browser will process them.

We'll be setting up an easy-to-use web server called [Caddy](https://caddyserver.com/) ! On macOS, run `brew install caddy` in your terminal. For Windows, run `choco install caddy` . Caddy gets its settings from a file named `Caddyfile` , so make one with the following contents in the same folder as your website files.

```
localhost:8080 {
    browse
}
```

Then `cd` to this folder in your terminal and run `caddy` . That's it, your server should be up and running!

Go to [localhost:8080](http://localhost:8080) in your browser. If you had a file called `index.html` , that should be displayed. If not, you'll see a directory listing - that's what the `browse` line in our `Caddyfile` does! By convention, `index.html` is the file web servers load if the URL points to a directory.

There are lots of other [configuration options](https://caddyserver.com/docs) you can use, but this is enough to get us started!

## Python

 [Python](https://www.python.org/) is a popular programming language that's easy to get started with - great for a hackathon! Some systems already have it installed, but we'll go through assuming yours doesn't.

First, we have to actually have Python! There are two major versions in use, Python 2 and Python 3. If you don't have a particular preference, I suggest using Python 3.

```shell
# For macOS:
brew install python3
# For Python 2 on macOS:
brew install python

# For Windows:
choco install python3
# For Python 2 on Windows:
choco install python2
```

Since Python is so widely used, there are plugins for almost any editor you could imagine. If you don't have a preference, I recommend the free version of [PyCharm](https://www.jetbrains.com/pycharm/) . For Eclipse users, there's the [PyDev](http://www.pydev.org/) plugin. If you use Atom, that has some Python support already, but installing [autocomplete-python](https://atom.io/packages/autocomplete-python) for even more support.

While Python has an incredible standard library, there are also third-party packages for everything from web applications to robotics. There's a full listing [here](https://pypi.python.org/pypi) , but feel free to ask me or a mentor for a recommendations about which to use for your project.

Installing a package. is usually pretty straightforward once you find it. Use Pip (the Python package manager) from the command line like this:

```shell
pip install <package name>
```

Some packages are a bit trickier to install, and might give a strange error. If that happens and you're feeling adventurous, try Googling around a bit, or ask someone for help so you can get back to hacking!

It's a good practice to list your project's dependencies in a `requirements.txt` file. Pip can read this file and install them all at once, making it easier for your teammates to get set up. Requirements files just list each dependency on its own line, like this:

```
Django
OpenCV==3.2 # Requirements files can specify exact dependency versions too
```

To install the packages in a requirements file, run `pip install -r requirements.txt` .

## Node.js

 [Node.js](https://nodejs.org/en/) is a project for running JavaScript outside the browser, including for backend development. There's a workshop on getting started with web applications in Node.js right after this, so we'll focus on getting it installed.

On Windows, we can use Chocolatey:

```shell
choco install nodejs.install
npm install -g npm-windows-upgrade
npm-windows-upgrade
```

On a Mac, use Homebrew:

```shell
brew install node
```

This also sets up [npm](https://www.npmjs.com/) , the package manager for Node.js. The npm ecosystem is massive, with packages for everything from web servers to mobile apps. Lots of frontend tools like React use npm, so it's worth having installed even if you don't want to use Node.js directly.

## PostgreSQL

 [PostgreSQL](https://www.postgresql.org/) (often called Postgres) is an open-source SQL database. How you use it will depend on your project and choice of language, so we'll cover how to get it installed for now. Ask me if you have any questions about how to connect to it from your code!

On a Mac:

```shell
brew install postgresql
brew services run postgresql # Start Postgres (won't restart if you reboot your computer)
brew services stop postgresql # Stop Postgres
brew services start postgresql # Start Postgres and keep it running if you reboot your computer
```

Unfortunately, the PostgreSQL version Chocolatey has for Windows is out of date. Instead, we'll be using an installer listed on the PostgreSQL website that you can find [here](http://www.enterprisedb.com/products/pgdownload.do#windows) . After installing, open a terminal and run `setx path "%path%;C:\Program Files\PostgreSQL\9.6\bin` and restart the terminal to make the PostgreSQL tools available.

## MongoDB

 [MongoDB](https://www.mongodb.com/) is a NoSQL document database. That means that it stores data in _documents_ , structured blobs of data that resemble the objects in your program. Instead of using SQL for queries, it uses a JSON-like query language that describes which documents to retrieve.

Installing on a Mac is very similar to installing PostgreSQL:

```shell
brew install mongodb
brew services run mongodb # Start, but don't restart if you reboot
brew services stop mongodb # Stop MongoDB
brew services start mongodb # Start MongoDB and keep it running
```

On Windows, we can use Chocolatey:

```shell
choco install mongodb
setx path "%path%;C:\Program Files\MongoDB\Server\3.2\bin"
mkdir C:\data\db
# After this, restart your terminal to pick up the path change

mongod # Start MongoDB (press CTRL+C to stop it)
```

Once MongoDB is installed and running, we can connect to from the terminal by running `mongo` !

## Setting up a Git Repo

 [Git](https://git-scm.com/) is one of the most widely-used version control systems in the world. It lets you track changes to your code and makes it easy to collaborate. There are lots of great Git tutorials online, and we had a workshop on it during Hack Week! The Git command line can be a bit intimidating, but GitHub (a website for storing code with Git) has a [desktop app](https://desktop.github.com/) you can use as well.

On a Mac, we can install everything with Homebrew:

```shell
brew install git
brew cask install github-desktop
```

On Windows, Chocolatey has a comprehensive package for GitHub Desktop and a couple extra utilities:

```shell
choco install git
choco install github
```
