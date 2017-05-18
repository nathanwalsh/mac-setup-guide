# Mac Install Guide

This document describes how I set up my developer environment on a new Mac for Python, Node (JavaScript) and PHP projects.

A big credit to Sourabh Bajaj's excellent [Mac OS X Setup Guide](http://sourabhbajaj.com/mac-setup/), some sections of this document have come almost directly from there.

## Table of Contents

<!-- MarkdownTOC -->

- [System Preferences](#system-preferences)
	- [Finder](#finder)
- [Xcode](#xcode)
- [Install Homebrew](#install-homebrew)
- [Install Applications](#install-applications)
	- [Essentials](#essentials)
	- [Recommended](#recommended)
	- [Quick Look Plugins](#quick-look-plugins)
- [Install Developer Packages](#install-developer-packages)
	- [Essential](#essential)
	- [Media](#media)
	- [Misc](#misc)
- [Iterm2](#iterm2)
- [Git Setup](#git-setup)
	- [Setup Your Identity](#setup-your-identity)
	- [Generating a New SSH Key](#generating-a-new-ssh-key)
	- [GitHub Authentication](#github-authentication)
	- [Cache Git Passwords in Keychain](#cache-git-passwords-in-keychain)
	- [Setting up Sublime Text as the Git Mergetool](#setting-up-sublime-text-as-the-git-mergetool)
- [Create Projects Directory](#create-projects-directory)
- [Install ZSH](#install-zsh)
	- [Install Oh My Zsh](#install-oh-my-zsh)
	- [env.sh](#envsh)
	- [Install the Pure Theme of ZSH](#install-the-pure-theme-of-zsh)
	- [Note on Virtual Environments](#note-on-virtual-environments)
	- [Custom ZSH Options](#custom-zsh-options)
	- [The Fuck](#the-fuck)
	- [Custom Aliases](#custom-aliases)
	- [Dev Command](#dev-command)
- [EditorConfig](#editorconfig)
- [Python](#python)
- [Node](#node)
	- [NVM Auto Activation](#nvm-auto-activation)
	- [Yarn](#yarn)
- [MySQL](#mysql)
- [Memcached](#memcached)
- [Redis](#redis)
- [PHP & WordPress](#php--wordpress)
	- [Install Packages](#install-packages)
	- [Configure Apache](#configure-apache)
	- [Adding a vhost](#adding-a-vhost)
	- [PHP Code Sniffer](#php-code-sniffer)
- [Sublime Text](#sublime-text)
	- [Install Package Control Plugin](#install-package-control-plugin)
	- [Install Plugins](#install-plugins)
	- [Preferences](#preferences)
	- [File Associations](#file-associations)
	- [SublimeLinter Settings](#sublimelinter-settings)
	- [Markdown Table of Contents Settings](#markdown-table-of-contents-settings)

<!-- /MarkdownTOC -->

---

## System Preferences

#### Trackpad

- Point & Click
	- Enable Tap to click with one finger
- Scroll & Zoom
	- Uncheck Scroll direction: Natural
- More Gestures
	- Change Swipe between pages to swipe with three fingers


#### Security & Privacy

- General
	- Change to require a password immediately after the screen saver appears
- FileVault
	- Turn on


#### Keyboard

- Shortcuts
	- Change the tab behaviour to all controls


#### Mission Control

- Unselect 'Automatically rearrange Spaces based on most recent use'


### Finder

- Show status bar (⌘/)
- Toolbar
	- Update to add path, new folder
- Sidebar
	- Add home and code directory
	- New finder window to open in the home directory


## Xcode

Install Xcode from the AppStore.

Install the Xcode command line tools.

```shell
xcode-select --install
```

## Install Homebrew

```shell
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

## Install Applications


### Essentials

```shell
brew cask install diffmerge
brew cask install google-chrome
brew cask install iterm2
brew cask install sequel-pro
brew cask install sourcetree
brew cask install sublime-text
```

### Recommended

```shell
brew cask install alfred
brew cask install android-file-transfer
brew cask install cheatsheet
brew cask install cyberduck
brew cask install deezer
brew cask install docker-toolbox
brew cask install dropbox
brew cask install evernote
brew cask install firefox
brew cask install google-drive
brew cask install google-hangouts
brew cask install handbrake
brew cask install keepingyouawake
brew cask install lastpass
brew cask install macdown
brew cask install microsoft-office
brew cask install opera
brew cask install postman
brew cask install skype
brew cask install slack
brew cask install spotify
brew cask install vagrant
brew cask install virtualbox
```

### Quick Look Plugins

From https://github.com/sindresorhus/quick-look-plugins

```shell
brew cask install qlcolorcode qlstephen qlmarkdown quicklook-json qlprettypatch quicklook-csv betterzipql qlimagesize webpquicklook suspicious-package quicklookase qlvideo
```


## Install Developer Packages

### Essential

```shell
brew install git
brew install git-flow-avh
brew install lynx
brew install ssh-copy-id
brew install tig
brew install wget
```

### Media

```shell
brew install imagemagick
brew install ffmpeg
```

### Misc

```shell
brew install plantuml
brew install par2
brew install unrar
```

## Iterm2

1. Go to Profiles > Default > Terminal and check silence bell
2. In Profiles > Default > Colors change the blue colour to `51c6ff` to make it easier to see on the dark background or [download and use one the iTerm2 color schemes](https://github.com/mbadolato/iTerm2-Color-Schemes/tree/master/schemes)
3. In Profiles > Default > Window set the window size to 125 columns and 35 rows

## Git Setup

### Setup Your Identity

```shell
git config --global user.name "Your Name Here"
git config --global user.email "your_email@youremail.com"
```

### Generating a New SSH Key

You may need to generate a new SSH key and add it to the ssh-agent, see the documentation on [GitHub](https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/#platform-mac).

### GitHub Authentication

Read and follow the instructions at https://help.github.com/articles/which-remote-url-should-i-use/ on [Cloning with HTTPS URLs](https://help.github.com/articles/which-remote-url-should-i-use/#cloning-with-https-urls-recommended) and  [Cloning with SSH URLs](https://help.github.com/articles/which-remote-url-should-i-use/#cloning-with-ssh-urls).

**If you are using two-factor authentication (and you should) then you must [provide a personal access token](https://help.github.com/articles/creating-a-personal-access-token-for-the-command-line) instead of entering your password for HTTPS Git.**

### Cache Git Passwords in Keychain

Enable Git password caching as described [here](https://help.github.com/articles/set-up-git):

```shell
git config --global credential.helper osxkeychain
```


### Setting up Sublime Text as the Git Mergetool

```shell
git config --global mergetool.sublime.cmd "subl -w \$MERGED"
git config --global mergetool.sublime.trustExitCode false 
git config --global merge.tool sublime
git mergetool -y
```


## Create Projects Directory

```shell
mkdir ~/Projects
```

## Install ZSH

```shell
brew install zsh zsh-completions zsh-syntax-highlighting
```

### Install Oh My Zsh

```shell
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```

Edit your `.zshrc` by opening the file in a text editor and edit the plugins lines with the following:

```
plugins=(git colored-man colorize github jira vagrant virtualenv pip python osx zsh-syntax-highlighting)
```

and add the following lines to the end of the file
 
```
source /usr/local/share/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh

# Add env.sh
source ~/Projects/config/env.sh
```

### env.sh

Copy the following into `~/Projects/config/env.sh` replacing `YOUR NAME` with your username.


```
#!/bin/zsh

# PATH
export PATH=/usr/local/share/npm/bin:$PATH
export PATH=/usr/local/bin:/usr/local/sbin:$PATH
export EDITOR='subl -w'

# Owner
export USER_NAME="YOUR NAME"
eval "$(rbenv init -)"

# FileSearch
function f() { find . -iname "*$1*" ${@:2} }
function r() { grep "$1" ${@:2} -R . }

#mkdir and cd
function mkcd() { mkdir -p "$@" && cd "$_"; }

# Aliases
alias cppcompile='c++ -std=c++11 -stdlib=libc++'

# Use sublimetext for editing config files
alias zshconfig="subl ~/.zshrc"
alias envconfig="subl ~/Projects/config/env.sh"
```


### Install the Pure Theme of ZSH

The [Pure theme](https://github.com/sindresorhus/pure) is a pretty, minimal and fast ZSH prompt.

**Follow the instructions to install Node and NVM then come back to here.**

To install run the following:

```shell
npm install --global pure-prompt
```

Add the following to the bottom of your `~/Projects/config/env.sh` file:

```
# Pure prompt
autoload -U promptinit; promptinit
prompt pure
```

Edit `.zshrc` and disable oh-my-zsh themes:

```
ZSH_THEME=""
```

Reload your shell

```shell
source ~/.zshrc
```

### Note on Virtual Environments

At the moment the display of the virtualenv name is not supported, see [PR #254](https://github.com/sindresorhus/pure/pull/254).

Until this this issue resolved the solution is to remove `virtualenv` from the list of Oh My Zsh plugins in your `.zshrc` file.


### Custom ZSH Options

To disable the automatic tab completion behaviour of ZSH add the following to your `~/Projects/config/env.sh` file:

```
# Custom ZSH options
setopt noautomenu
setopt nomenucomplete
```

### The Fuck

[The Fuck](https://github.com/nvbn/thefuck) is an app which corrects your previous console command.

Install it with:

```shell
brew install thefuck
```

Then add the following the end of `~/Projects/config/env.sh`

```
eval "$(thefuck --alias)"
```

### Custom Aliases

Add the following the end of `~/Projects/config/env.sh`.

```
alias flushmc="echo 'flush_all' | nc localhost 11211"
alias flushredis="echo 'FLUSHALL' | nc localhost 6379"
alias flushdns="dscacheutil -flushcache; sudo killall -HUP mDNSResponder"

alias stripsvn="find . -type d -name '.svn' -exec rm -rf {} \;"
alias stripmac="find . -type d -name '__MACOSX' -exec rm -rf {} \;"
alias stripds="find . -type f -name '.DS_Store' -exec rm -rf {} \;"
alias strippyc="find . -type f -name '*.pyc' -exec rm -rf {} \; find . -name '__pycache__' -exec chflags hidden {} \;"
alias fixperms="find . -type f -perm -ugo+x -not -path \"./.git/*\" -print -exec chmod -x {} \;"

alias edithosts="subl /usr/local/etc/apache2/2.4/extra/httpd-vhosts.conf /etc/hosts"

alias fixopenwith="/System/Library/Frameworks/CoreServices.framework/Frameworks/LaunchServices.framework/Support/lsregister -kill -r -domain local -domain system -domain user; killall Finder"
```

### Dev Command

Add the following the end of `~/Projects/config/env.sh`.

```
export DEV_HOME="$HOME/Projects"
dev () {
    typeset dir="$1"
    cd $DEV_HOME

    # deactivate old virtual env
    if [[ "$VIRTUAL_ENV" != "" ]] ; then
        deactivate
    fi

    if [ ! "$dir" = "" ] ; then
        cd $dir

        # activate the virtualenv
        if [ -d "$WORKON_HOME/$dir" ] ; then
            workon "$dir"
        fi
    fi
}

#
# Set up tab completion.  (Adapted from Arthur Koziel's version at
# http://arthurkoziel.com/2008/10/11/virtualenvwrapper-bash-completion/)
#
cddev_show_options () {
    # NOTE: DO NOT use ls here because colorized versions spew control characters
    #       into the output list.
    # echo seems a little faster than find, even with -depth 3.
    # (for f in `ls -l $DEV| egrep '^d' | awk '{ print $9 }'`; do echo $f; done) 2>/dev/null | \sed 's|^\./||' | \sed 's|/bin/activate||' | \sort | (unset GREP_OPTIONS; \egrep -v '^\*$')
    (cd "$DEV_HOME"; for f in */; do echo $f; done) 2>/dev/null | \sed 's|^\./||' | \sed 's|/||' | \sort | (unset GREP_OPTIONS; \egrep -v '^\*$')
}
if [ -n "$BASH" ] ; then
    _cddev_dirs () {
        local cur="${COMP_WORDS[COMP_CWORD]}"
        COMPREPLY=( $(compgen -W "`cddev_show_options`" -- ${cur}) )
    }
    complete -o default -o nospace -F _cddev_dirs dev
elif [ -n "$ZSH_VERSION" ] ; then
    compctl -g "`cddev_show_options`" dev
fi
```

The `dev` command then be used to switch between projects, automatically activating their python virtual environments, e.g. `dev project1`.


## EditorConfig

To have a standard in case a project does not include it's own EditorConfig file create a `.editorconfig` file in your home directory with the following contents:

```
# http://editorconfig.org
root = true

[*]
indent_style = space
indent_size = 4
end_of_line = lf
charset = utf-8
trim_trailing_whitespace = true
insert_final_newline = true

[*.md]
trim_trailing_whitespace = false
indent_size = 4
indent_style = tab

[*.js]
indent_size = 2

[*.json]
indent_size = 2

[*.html]
indent_style = tab

[*.yml]
indent_size = 2
```


## Python

We will use pyenv to install multiple versions of Python, this is preferable to Homebrew as it allows full control over minor versions.

```shell
brew install python pyenv
```

After installing, add the following to `~/Projects/config/env.sh`

```
# Python
export PYTHONIOENCODING=utf-8
eval "$(pyenv init -)"
```

Restart your shell so the path changes take effect. You can now begin using pyenv.

```shell
exec $SHELL
```

To list the all available versions of Python, including Anaconda, Jython, pypy, and stackless, use:

```shell
pyenv install --list
```

Then install the desired versions:

```shell
pyenv install 2.7.13
pyenv install 3.5.3
```

Use the `global` command to set global version(s) of Python to be used in all shells. For example, if you prefer 2.7.13 over 3.5.3:

```shell
pyenv global 3.5.3 2.7.13
pyenv rehash
```

The leading version takes priority. All installed Python versions can be located in `~/.pyenv/versions`. You can run `pyenv versions` to see the list of all the Python versions available, an asterisk `*` is displayed next to the currently active version.

#### Homebrew Warnings

The use of pyenv causes [brew to output warning](https://github.com/pyenv/pyenv/issues/106), to resolve this we use [randy3k's solution of creating an alias](https://github.com/pyenv/pyenv/issues/106#issuecomment-94921352).

Add the following to the bottom of your `~/Projects/config/env.sh`:

```
alias brew="env PATH=${PATH//$(pyenv root)\/shims:/} brew"
```


#### Virtualenv

As we're using `pyenv` we will use `pyenv-virtualenvwrapper`, install it with the following.

```shell
brew install pyenv-virtualenvwrapper
```

Make sure `virtualenvwrapper` is installed.

```shell
pip install virtualenvwrapper
```

Add the following to your `~/Projects/config/env.sh`:

```
export PYENV_VIRTUALENVWRAPPER_PREFER_PYVENV="true"
pyenv virtualenvwrapper
```

After restarting your shell you will be able to create virtual environments using the `mkvirtualenv` command.


## Node

Install NVM so that multiple versions of Node can be managed, to do this run the latest install script from [the README](https://github.com/creationix/nvm#install-script).

This install script automatically adds the nvm source strings to the bottom `.zshrc` which is in the wrong place for us as we need all the commands to execute in the right order. To correct this remove the following lines from your   `.zshrc` file.

```
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion
```

Add them to the to bottom of your `~/Projects/config/env.sh` file:

```
# Node
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion
```

Reload your shell

```shell
source ~/.zshrc
```

Check the nvm is installed, the following should output 'nvm' if the installation was successful.

```shell
command -v nvm
```

List all the node versions you can install

```shell
nvm ls-remote
```

Install most recent nodejs LTS version

```shell
nvm install --lts
```

List installed node version

```shell
nvm ls
```

Use latest LTS as current version

```shell
nvm use lts/*
```

Set the installed LTS version as the default node 

```shell
nvm alias default lts/*
```


### NVM Auto Activation

Add the following to your `~/Projects/config/env.sh` file so that `nvm use` will automatically be called whenever you enter a directory that contains an `.nvmrc` file with a string telling nvm which node to use. [See here](https://github.com/creationix/nvm#calling-nvm-use-automatically-in-a-directory-with-a-nvmrc-file).

```
# NVM auto activation
autoload -U add-zsh-hook
load-nvmrc() {
  local node_version="$(nvm version)"
  local nvmrc_path="$(nvm_find_nvmrc)"

  if [ -n "$nvmrc_path" ]; then
    local nvmrc_node_version=$(nvm version "$(cat "${nvmrc_path}")")

    if [ "$nvmrc_node_version" = "N/A" ]; then
      nvm install
    elif [ "$nvmrc_node_version" != "$node_version" ]; then
      nvm use
    fi
  elif [ "$node_version" != "$(nvm version default)" ]; then
    echo "Reverting to nvm default version"
    nvm use default
  fi
}
add-zsh-hook chpwd load-nvmrc
load-nvmrc
```

### Yarn

Install the Yarn package manager:

```shell
brew install yarn
```

## MySQL

Install:

```shell
brew install mysql
```

To have launchd start MySQL now and restart at login:

```shell
brew services start mysql
```

## Memcached

Install:

```shell
brew install memcached
```

To have launchd start memcached now and restart at login:

```shell
brew services start memcached
```

## Redis

Install:

```shell
brew install redis
```

To have launchd start redis now and restart at login:

```shell
brew services start redis
```


## PHP & WordPress

### Install Packages

```shell
brew install httpd24 --with-privileged-ports
brew install homebrew/php/php71 --with-httpd24
brew install homebrew/php/php71-intl
brew install homebrew/php/php71-mcrypt
brew install homebrew/php/php71-memcached
brew install homebrew/php/php71-opcache
brew install homebrew/php/php71-redis
brew install homebrew/php/wp-cli
brew install composer
```

### Configure Apache

Edit `/usr/local/etc/apache2/2.4/httpd.conf` and make the following changes:

1. Uncomment `#LoadModule rewrite_module libexec/mod_rewrite.so`
2. Change `User daemon`, replacing `daemon` with your username
3. Change `Group daemon` to `Group #-1`
4. Change `DirectoryIndex index.html` to `DirectoryIndex index.php index.html`
5. Uncomment `#Include /usr/local/etc/apache2/2.4/extra/httpd-vhosts.conf`
6. Check that when PHP installed it added a `LoadModule php7_module` line, if not add `LoadModule php7_module /usr/local/opt/php71/libexec/apache2/libphp7.so` to the bottom of the LoadModule block


Edit `/usr/local/etc/apache2/2.4/extra/httpd-vhosts.conf` and add the following, replacing `username` with your username:

```
DocumentRoot "/Users/username/Projects"
<Directory "/Users/username/Projects">
    Options All
    AllowOverride All
    Require all granted
</Directory>
```

Start Apache:

```shell
sudo brew services start homebrew/apache/httpd24
```

### Adding a vhost

Run the `edithosts` alias to automatically open up `/usr/local/etc/apache2/2.4/extra/httpd-vhosts.conf` and `/etc/hosts` for editing.

Add the following to `httpd-vhosts.conf`, replacing `project-name` and `username` accorindgly:

```
<FilesMatch .php$>
    SetHandler application/x-httpd-php
</FilesMatch>
    
<VirtualHost *:80>
    ServerName project-name.dev
    DocumentRoot "/Users/username/Projects/project-name"
</VirtualHost>
```

Add the following to `/etc/hosts`

```
127.0.0.1	project-name.dev
```

Restart Apache:

```shell
sudo brew services restart homebrew/apache/httpd24
```

### PHP Code Sniffer

phpcs will be installed as part of the [WordPress coding standards](https://github.com/WordPress-Coding-Standards/WordPress-Coding-Standards) project which is installed using:

```shell
composer create-project wp-coding-standards/wpcs /usr/local/opt/wpcs --no-dev
```

Composer installs binaries to `~/.composer/vendor/bin` so this directory must be added to the shell path 

Add the composer bin directory to your shell path by adding the following to your `~/Projects/config/env.sh` file:

```
export PATH=/usr/local/opt/wpcs/vendor/bin:$PATH # phpcs
```

Reload your shell

```shell
source ~/.zshrc
```

You should then see WordPress-Core et al listed when you run `phpcs -i`.


## Sublime Text

By installing sublime text using Homebrew Cask the command-line shortcut `subl` should already be setup, however if it isn't create it manually with:

```shell
ln -s /Applications/Sublime\ Text.app/Contents/SharedSupport/bin/subl /usr/local/bin/subl
```

### Install Package Control Plugin

Follow the instructions on https://packagecontrol.io/installation to install the latest version of the plugin.

### Install Plugins

Install the following plugins:

- [Babel](https://packagecontrol.io/packages/Babel): Syntax definitions for ES6 JavaScript with React JSX extensions.
- [Git](https://packagecontrol.io/packages/Git): Plugin for some git integration into sublime text
- [GitGutter](https://packagecontrol.io/packages/GitGutter): A Sublime Text 2/3 plugin to see git diff in gutter
- [EditorConfig](https://packagecontrol.io/packages/EditorConfig): Helps developers maintain consistent coding styles between different editors
- [FileDiffs](https://packagecontrol.io/packages/FileDiffs): Shows diffs between the current file, or selection(s) in the current file, and clipboard, another file, or unsaved changes.
- [Markdown Preview](https://packagecontrol.io/packages/Markdown%20Preview): Markdown preview and build plugin for sublime text 2/3
- [MarkdownTOC](https://packagecontrol.io/packages/MarkdownTOC): Plugin for generating a Table of Contents (TOC) in a Markdown document.
- [MarkdownEditing](https://packagecontrol.io/packages/MarkdownEditing): Powerful Markdown package for Sublime Text with better syntax understanding and good color schemes.
- [Material Theme](https://packagecontrol.io/packages/Material%20Theme): Material Theme, the most epic theme for Sublime Text 3 by Mattia Astorino
- [Pretty JSON](https://packagecontrol.io/packages/Pretty%20JSON): Prettify/Minify/Query/Goto/Validate/Lint JSON plugin for Sublime Text 2 & 3
- [Sass](https://packagecontrol.io/packages/Sass): Sass support for TextMate & Sublime Text (2 & 3)
- [SideBarEnhancements](https://packagecontrol.io/packages/SideBarEnhancements): Enhancements to Sublime Text sidebar. Files and folders.
- [SublimeCodeIntel](https://packagecontrol.io/packages/SublimeCodeIntel): Full-featured code intelligence and smart autocomplete engine
- [SublimeLinter](https://packagecontrol.io/packages/SublimeLinter): Interactive code linting framework for Sublime Text 3
- [SublimeLinter-contrib-eslint](https://packagecontrol.io/packages/SublimeLinter-contrib-eslint): This linter plugin for SublimeLinter provides an interface to ESLint
- [SublimeLinter-pep8](https://packagecontrol.io/packages/SublimeLinter-pep8): SublimeLinter plugin for python, using pep8.
- [SublimeLinter-phpcs](https://packagecontrol.io/packages/SublimeLinter-phpcs):  SublimeLinter plugin for PHP, using phpcs.


### Preferences

Edit the preferences configuration (`⌘+,`) and paste the following:

```
{
  "color_scheme": "Packages/Material Theme/schemes/Material-Theme.tmTheme",
  "theme": "Material-Theme.sublime-theme",
  "folder_exclude_patterns": [
    ".git",
    "node_modules"
  ],
  "font-size": 12.0,
  "ignored_packages": [
    "Vintage"
  ],
  "rulers": [
    79,
    99
  ],
  "shift_tab_unindent": true,
  "sublimelinter": "save-only",
  "trim_trailing_white_space_on_save": true,
  "bold_folder_labels": true,
  "font_options": [
    "subpixel_antialias"
  ],
  "indent_guide_options": [
    "draw_normal",
    "draw_active"
  ],
  "overlay_scroll_bars": "enabled",
  "always_show_minimap_viewport": true,
  "word_wrap": false
}
```

### File Associations

Set JavaScript files to open with the Babel plugin:

1. Open a file with that extension
2. Select View from the menu
3. Then Syntax -> Open all with current extension as... -> Babel -> JavaScript (Babel).
4. Repeat this for each extension (e.g.: .js and .jsx).

 
### SublimeLinter Settings

Install pep8 for Python:

```shell
pip install pep8
```

Install eslint globally for Node:

```shell
npm install -g eslint
```

Edit the SublimeLinter settings (found in the menus under Sublime Text > Preferences > Package Settings > Sublime Linter > Settings – User) and make the following changes:

Change the value of the `paths` property to the following, replacing `username` and the node version to accordingly:


```json
"paths": {
    "linux": [],
    "osx": [
        "/Users/username/.pyenv/shims",
        "/Users/username/.nvm/versions/node/v6.10.3/bin",
        "/usr/local/bin",
        "/usr/local/sbin"
    ],
    "windows": []
}
```

For WordPress projects edit the project specific settings to use the wordpress-extra using the following:

```json
"SublimeLinter": {
  "linters": {
      "phpcs": {
          "standard": "wordpress-extra"
      }
  }
}
```


### Markdown Table of Contents Settings

The MarkdownTOC plugin easily generates and updates the table of contents for markdown files but it's default behaviour is not to automatically create the links which are commonly used on GitHub.

Edit the MarkdownTOC settings (found in the menus under Sublime Text > Preferences > Package Settings > MarkdownTOC > Settings – User) and make the following changes:

```json
{
  "default_autolink": true,
  "default_bracket": "round",
  "default_lowercase_only_ascii": true
}
```
