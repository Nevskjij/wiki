This page will go through how to download the bot and other tools.

# Downloading and installing the required programs

## Git

The way you download the bot is by using Git. Git is a distributed version-control system for tracking changes in source code during software development (https://en.wikipedia.org/wiki/Git).

(You don't need to use Git to download the bot, but it makes it a lot easier to update the bot)

### Windows

Download Git from https://git-scm.com/

### Mac / Linux

Git should already be installed, check if it is by opening the terminal and using the command `git -v`.

## NodeJS

#### Windows / Mac / Linux

Download from https://nodejs.org/.

# Downloading the bot

Once you have installed Git then you can follow these steps.

Open a command prompt or terminal and navigate to where you want the bot to be located. This location can always be changed later on. In this example, we just use the Desktop.

`cd Desktop` to navigate to the Desktop.

Use `git clone https://github.com/Nicklason/tf2-automatic.git --branch master` to clone the repository and choose the master branch. The master branch contains released code and is considered to be stable.

Once it has been cloned a new folder will be made called `tf2-automatic`.

# Installing TypeScript

The bot is made with TypeScript. This means that you need to compile the source code to be able to run it.

`npm install typescript@latest -g` will install TypeScript.

# Installing modules

When the bot has been downloaded you need to install the modules. Do this by navigating to the tf2-automatic folder with the command prompt or a terminal and using the command `npm install`.

# Compiling source

If you already have installed TypeScript, then `npm build` will compile the code. If you haven't then see [Installing TypeScript](https://github.com/Nicklason/tf2-automatic/wiki/Installation#installing-typescript).

Compile the source using `npm run build`

The compiled code will now be inside a folder called dist.

## Possible errors

### `npm install typescript@latest -g` failed

This is most likely because you are missing the permissions to install typescript globally. If you are on a VPS, then use `sudo npm install typescript@latest -g`.

***

Click [here](https://github.com/Nicklason/tf2-automatic/wiki/Configuration) to see how to configure the bot.