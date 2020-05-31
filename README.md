# wsc
wine source control
--
This bash script will download the needed files and is able to build Wine in different modes.

Usage
--
Clone wsc from git and symlink wsc to your $PATH, for example /usr/local/bin/wsc, so you can just join a empty directory 
and call the script. Else the wsc script must be present in the directory you want to build wine in.

Concept:
--
The incredible modularity of the wine sources give a lot of options to reach a good working wine core that can serve all the 
certain prefixes for your best gaming experience with Windows games on Linux, using wine.

Actually i needed a tool to
- download vanilla and staging
- build and install me a vanilla-wine
- build and install me a wine-staging
- build a modified local source
- patch the source with own patches
- prepare a source and inject staging
- ...

The directories created by wsc are:

- ./              - a empty dir with wsc in it or wsc in path called from inside a empty dir is the basic dir for wsc.
- ./build/wine32  - build dir for the 32bit wine
- ./build/wine64  - build dir for the 64bit wine, contents of both is deleted on a new build
- ./wine-staging  - contains the wine staging patches, download with '9' or copy in from local source
- ./workdir       - this is Workdir, in this dir the sources get modified, patched, restored
- ./wine-vanilla  - contains the wine vanilla source, can be used to copy to workdir for a fresh source in there ('k') or build directly from there with 'v'
- ./cache         - contains version downloads from getting a wine release

Dirs created by you:
- ./patches       - a place for your patches

Usage:

Command overview:
==========================================================================================================

Build setup
--
- Here you can see and change the different options for your wine build.

Check Wine Staging
--
- Connects to the wine-staging github and executes 'git pull' in the wine-staging donload dir.

Check Wine Vanilla
--
- Connects to the wine github and makes a 'git pull' in the wine vanilla download dir.

Check installed Wine version
--
- Executes 'wine --version' to quick check the installed wine version

INJECT STAGING
--
- Before the wine-staging patches can be injected into the workdir, you need to copy the vanilla source to workdir with 'k'.
After that you need to get the current version from wine staging into a hashtag ('a') and set the vanilla wine source to the wine-staging version ('b').

COMPILE WORKDIR
--
- Builds your patched or modified wine in workdir

Get current wine-staging SHA1
--
- This command will get the hash tag from the current wine-staging version.

Rebase wine source to wine-staging Hash
--
- This will modify the sources in workdir to the current version of the wine-staging patchset.
You need to do this in order to get the wine.staging patches to apply.

Stash your changes and reset WORKDIR to vanilla wine
--
- This will reset the workdir source back to the current vanilla version

Install Prerequisits
--
- Fist hack to install the 32bit prerequisits on your system, in case you miss some.

Get a new Wine Staging source
--
- This just downloads a new wine-staging patchset from Github

Get a new Vanilla wine source
--
Get a new Vanilla source from the wine Github.
This goes not into workdir, its going into Vanilla dir so you can build vanilla anytime.
Workdir is the place for the modified/patched Vanilla build.

Get a certain wine-release version
--
- Lets you enter a wine release version of your choice, what is available in the main wine release repo. 
It will download and unpack to wine-vanilla and wine-staging dir's so to unite them, need to copy to workdir first (k).
No need to tweak the wine source to the wine-staging source because its a release version.

Reset the source to SHA1
--
- Resets the source in ./workdir to a given hash tag.

Apply my Patches
--
- Applies patches from ./patches dir to workdir.
For the case you need something special patched in :)

Use a custom install path
--
- Changes the installation path to a custom location within the users rights.
It does not install as superuser.

INSTALL
--
- Install your build default to /usr/local/* .
This is different from the most distribution packages as they went into /usr/* .

Very first look into the script!

Check what the single functions do, this script is just a tool to reduce the typing in the console ^^

Create a directory in what you gonna work with wsc.

Get a bash up, join your directory and call the script with 'wsc' (once you symlinked it to /usr/local/bin/wsc).

Start with getting new sources for vanilla-wine (press '0') and wine-staging (press '9').


- Building Vanilla:

Wsc is focusing a workdir for a modified wine build (press 'k' to copy Vanilla wine to the workdir).
The concept of working in a workdir has some advantages, as the sources stay untouched and can quick get modified.

After building, you have to install it (press 'I') and it will install to /usr/local/* - the default installation location.
If you want other install targets, you want to review the build settings (press '3') and change them to your needs.

To build a current wine-staging, you want rebase the vanilla sources to the actual wine staging version.

k -> a -> b -> j -> B -> I

(press 'k') to copy the Vanilla source to workdir.
(press 'a') to get the actual wine-staging hash tag.
(press 'b') to base/set the wine vanilla sources to the wine-staging hash version.
(press 'j') to inject the wine-staging patches.
(press 'B') to build wine staging.
(press 'I') to install wine-staging.

Again, look into the script, visit the compiler calls and modify to your needs !

![alt text](https://i.imgur.com/kmWNyCp.png)

