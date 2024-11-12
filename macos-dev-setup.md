# macOS Dev Setup

My personal guide on how to set up a new Mac as a web developer workstation.

## Command Line Goodness

I like to use the plain terminal for macOS with the RedSands profile and the Jovial Theme which includes all the interesting features of Oh My ZSH. If you are used to bash config files, this is the way.

An interesting alternative to Oh My ZSH and Jovial is [iTerm2](https://iterm2.com/) that you can customize to reach a feature equivalence. That approach will minimize interactions with bash config files and offer customization options through the settings in the iTerm2 interface. Note that iTerm2 does not conflict with any Oh My ZSH or Jovial installation. iTerm2 configuration is not covered by this guide, but should be intuitive enough should you follow that path.

### 1. Install macOS' Command Line Tools

Command Line Tools are an optional component of Xcode that bring a variety of advanced utilities to the Mac command line, including compilers, debuggers, and other essentials for software development and command line tinkering.[*](https://osxdaily.com/2024/09/30/how-install-command-line-tools-macos-sonoma/)

These are required for building packages from source with Homebrew. Nowadays Homebrew installs this automatically, but I prefer to do it manually for transparency purposes.

```shell
xcode-select --install
```

### 2. Install Homebrew, The Missing Package Manager for macOS

[Homebrew](https://brew.sh/) helps install the commands you need that Apple didn’t include with macOS. It is the macOS equivalent of apt-get on Debian/Ubuntu linux distros. Note that the CLI command is brew and not homebrew.

```shell
/bin/zsh -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

### 3. Generic Shell Utilities

Install GNU Core Utils. I use this here for the Gnu LS command `gls` that allows the `--group-directories-first` flag.
It is referred in the `ll` shortcut in the [.zlogin](.zlogin) file

```shell
brew install coreutils
```

### 4. Install Jovial

[Jovial](https://github.com/zthxxx/jovial) is a nice [Oh My Zsh](https://ohmyz.sh/) theme that keeps things simple. It means that you don't have to dive deep in the Oh My ZSH universe to customize a theme and 500 options and plugins.

```shell
curl -sSL https://github.com/zthxxx/jovial/raw/master/installer.sh | sudo -E zsh -s ${USER:=`whoami`}
```

No special font is needed, your typical monospaced font will do. _(Monaco, Menlo, JetBrains Mono)_

| NOTE: Set font line-height to 1.0 for the multiline theme graphics to display properly.

#### Jovial & Oh My Zsh Fine-Tuning
Now is the time to copy the [.zlogin](/assets/.zlogin) file to your $HOME folder. This will remove the weird squiggly faces that Jovial displays on a clean or dirty state for git repository folders. 

This also overrides Jovial's `ll` shortcut that is not to my liking with gls from `coretuils` (see above). The main benefit is that it allows listing of folders before files.

## Install programming tools

What's your stack? Mine is of many.

### Node.js

Here I install [nvm](https://github.com/nvm-sh/nvm), an open-source Node Version Manager that is really helpful if you have multiple apps that require a different Node.js version. Should you just want the latest version, you can simply run `brew install node` instead. 

```shell
# Node.js packages
brew install nvm 
# Set NVM - Node Version Manager - To use the latest Node version
nvm install node
# OR Set NVM - Node Version Manager - To use the latest Long-Term Support version
nvm install --lts
```

### Install Java through SDKMan

Use [SDKMan](https://sdkman.io/), the # Software Development Kit Manager to help manage Java, [Kotlin](https://kotlinlang.org/), [Apache Groovy](https://www.groovy-lang.org/), [Gradle Build Tool](https://gradle.org/), [Apache Maven](https://maven.apache.org/) and many more related software.

```shell
curl -s "https://get.sdkman.io" | bash
```

Open a new shell, then run

```shell
source "$HOME/.sdkman/bin/sdkman-init.sh"
```

to finish the installation process.

List available Java JDK and install the one you like.

```shell

sdk list java
sdk install java # Append desired specifier from the list command or leave empty for default
```

Repeat for `gradle` , `kotlin` and all the other formulas you need.

### Install [Python](https://www.python.org/)

I have encountered permission issues with Python's venv — Virtual Environments — using the Homebrew version. I needed to sudo all the time, which is contrary to Homebrew's principles usually. That is why I now prefer to use the official binaries from Python's [Download Page](https://www.python.org/downloads/)

### PHP

[PHP](https://www.php.net/) & [Composer](https://getcomposer.org/) should be all you need, and maybe [PHPbrew](https://github.com/phpbrew/phpbrew) to help with managing multiple PHP versions on your machine.

```shell
# PHP packages
brew install php phpbrew composer
```

## ZSH Config files

This repository includes 3 zsh config files

- [.zprofile](/assets/.zprofile)
    - Loads before .zshrc
    - Contains NVM, SDKMan and Homebrew configs
    - If anything you put in there does not behave as expected, or is not loaded, it might be the victim of an override
      from the theme setup. Therefore, try moving your lines to the .zlogin file
    - Includes a daily auto-update automation for Node.js through nvm, homebrew packages and global npm packages
- [.zshrc](/assets/.zshrc)
    - Loads in second place
    - Contains Oh My ZSH with Jovial Theme config
    - Other setups will recommend using this file for config, I prefer to keep Jovial / Oh my ZSH in there on its own
      and use the other two, depending on the use case.
- [.zlogin](/assets/.zlogin)
    - Loads after `.zshrc`
    - I use it to override Oh my ZSH Jovial settings that I do not like

Reminder: The load order for zsh config files is the
following[*](https://zsh.sourceforge.io/Doc/Release/Files.html#Startup_002fShutdown-Files):

- .zshenv
- .zprofile
- .zshrc
- .zlogin
- .zlogout (loaded when quitting)

You should have copied [.zlogin](.zlogin) already from earlier steps. Now is the time to copy
over [.zprofile](.zprofile) and [.zshrc](.zshrc). You can copy them as-is, but using a diff tool is
better here to make sure you only take what you need from these files.

## IDE

Now's the time for installing your favorite IDE.

### The JetBrains Collection

If you are using any JetBrains IDE, especially if you use more than one, I recommend using the [JetBrains Toolbox App](https://www.jetbrains.com/toolbox-app/).

[WebStorm](https://www.jetbrains.com/webstorm/), a personal favourite, is now free for personal use since October 2024. Its diff tool, for file merging, is legendary, and it uses JS Doc to detect type inference so well that you don't need TypeScript anymore.

### Visual Studio Code

[Visual Studio Code](https://code.visualstudio.com/) is also a safe bet. Although I appreciate Microsoft's turn towards open-source and plugin oriented solutions, I still prefer JetBrains' IDEs. 

JetBrains make very reliable plugins. When searching for a plugin that they don't provide, you will generally only have one option, and it will be just what you
need, therefore avoiding the need to evaluate a plethora of candidates.

However, VS Code is a better solution for Shopify development, since Liquid syntax support is clearly outdated and neglected in JetBrains solutions (as of 2023/2024).

### Zed

[Zed](https://zed.dev/) is an up-and-coming IDE, superfast and with an AI first mindset. I love it, but at the time of
this writing, it is missing a critical feature a [diff view](https://github.com/zed-industries/zed/issues/4523).

## Additional Useful Software

- [Bitwarden](https://bitwarden.com/) - affordable password manager
- [Deskflow](https://github.com/deskflow/deskflow) - Replaces Synergy as a KVM software to share your mouse and keyboard
  between multiple devices. Haven't tried this yet, I'll have to replace my Synergy install soon.
- [Docker Desktop](https://www.docker.com/products/docker-desktop/) - For container management
- [Handbrake](https://handbrake.fr/downloads.php) - Super Useful Video compression app
- [ImageOptim](https://imageoptim.com/mac) - Reduces image file sizes
- [Insomnia](https://insomnia.rest/download) - For testing API endpoints, GraphQL and REST
- [Karabiner](https://karabiner-elements.pqrs.org/) for customizing Keyboard Keys
- [Sequel Ace](https://sequel-ace.com/) - Mysql/MariaDB Database Management & Visualizer
- [TextMate](https://macromates.com/) - TextEditor that compares to Notepad++
- [TinkerTool](https://www.bresink.com/osx/TinkerTool.html) - TinkerTool is an application that gives you access to
  additional preference settings Apple has built into macOS.
- [Transmission](https://transmissionbt.com/download.html) - Bittorrent Client
- [VLC](https://www.videolan.org/vlc/) - Universal Media Player