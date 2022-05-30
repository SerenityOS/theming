# SerenityOS Theming Repo

## Folder Structure
```
.
├── cursor-themes
├── fonts
├── icon-themes
├── icons
│   └── themes
└── themes
```

Repo structure is similar to SerenityOS's `Base/res` repo or `/res` inside a running instance.
Folders contain system-wide resources, except `icons/themes` which is theme-specific

## How to use
First, ensure that you have a successfull working SerenityOS instance.
As of this writing, the recommended process of trying out the contents of the repo is to manually copy over to your SerenityOS branch. On GNU/Linux home directory, assume that you have both repos
- $HOME/serenity
- $HOME/theming

In this scenario, assume also that you want to try all contents of theming repo:
```
$ cd $HOME
$ cp -r $HOME/theming/* $HOME/serenity/Base/res/
```
Then you'll only do the following in order to build SerenityOS:
```
$ cd $HOME/serenity
$ Meta/serenity.sh run
```

Inside the running SerenityOS instance, you should have additional fonts, cursor-themes, icon-themes and themes for use.

## Safest method: Use Ports/serenity-theming application
```
$ cd $HOME/serenity/Ports/serenity-theming
$ ./package.sh
```
This will download contents of https://github.com/serenityos/theming repo (of a certain commit) and install it on your build.
Majority of the resources will be available and ready to use inside SerenityOS except `icon-themes`, since we still need manual process of installing them before doing `Meta/serenity.sh run`.

## How to use Icon Theme
Although theming repo is now a part of your SerenityOS build directory, using Icon Theme requires additional steps.
Currently, there are a couple of Icon themes to try, `Black-and-White`, `Chillychilly` and `Durrque`.
For safety purposes, create a Default Icon theme.
```
$ cd $HOME/serenity
# create a backup of Default Icon themes, run this command only once
~:serenity $ cp -r Base/res/icons Base/res/icon-themes/Default
# try out Black-and-White Icon theme, the next command will overwrite default icons
~:serenity $ cp -r Base/res/icon-themes/Black-and-White/* Base/res/icons/
# Build and run
~:serenity $ Meta/serenity.sh run
# Revert back to Default Icons
~:serenity $ cp -r Base/res/icon-themes/Default/* Base/res/icons/
# Build and run
~:serenity $ Meta/serenity.sh run
```

## To install only selected resources
- copy content(s) of $HOME/theming/fonts into $HOME/serenity/Base/res/fonts
- copy content(s) of $HOME/theming/themes into $HOME/serenity/Base/res/themes
- copy content(s) of $HOME/theming/icons/themes into $HOME/serenity/Base/res/icons/themes
- copy content(s) of $HOME/theming/cursor-themes into $HOME/serenity/Base/res/cursor-themes
- copy content(s) of $HOME/theming/icon-themes into $HOME/serenity/Base/res/icon-themes

We look forward to have these steps wrapped around a nice GUI interface soon-ish.
Meanwhile, enjoy :^) 
