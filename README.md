# wsc
wine source control

This bash script will download the needed files and is able to compile a wow64 build of Vanilla Wine.
It also can rebase the wine vanilla source to the actual wine staging version, inject all staging patches and built it.

Concept:

The incredible modularity of the wine sources give a lot of options to reach a good working wine core that can serve all the certain prefixes for your best gaming experience with Windows games on Linux, using wine.
Out of experience, a wow64 build of wine has the most flexibility when it comes to handle the different modes like 32bit, 64bit, DX7,8,9,10,11, WinXP to Windows10 so i've been exclusivly focusing that build type, Windows on Windows64.

Actually i needed a tool to
1. download vanilla and staging
2. build and install me a vanilla-wine
3. build and install me a wine-staging
4. build a modified local source
5. patch the source with own patches
6. prepare a source and inject staging

The directories are:

./              - a empty dir with wsc in it or wsc in path called from inside a empty dir is the basic dir for wsc.
./bak/          - with the 'r' command, the source in this dir will be restored to ./wine-test
./build/wine32  - build dir for the 32bit wine
./build/wine64  - build dir for the 64bit wine, contents of both is deleted on a new build
./wine-staging  - contains the wine staging patches, download with '9' or copy in from local source
./wine-test     - this is Workdir, in this dir the sources get modified, patched, restored
./wine-vanilla  - contains the wine vanilla source, can be used to copy to workdir for a fresh source in there ('k') or 
                  build directly from there with 'v'

Usage:

Very first look into the script!
Check what the single functions do, this script is just a tool to reduce the typing in the console ^^
Wsc will always create a wow64 wine build, building the 32bit and 64bit versions in relation.

Create a directory in what you gonna work with wsc.
Get a bash up, join your directory and call the script with ./wsc
Start with getting new sources for vanilla-wine (press '0') and wine-staging (press '9').

Building Vanilla:
Wsc is focusing a workdir for a modified wine build, but can build a vanilla-wine as well (press 'v').
After building, you have to install it (press 'i') and it will install to /usr/local/* - the default installation location.
If you want other install targets, just modify the script to your needs.

To build wine-staging, you want rebase the vanilla sources to the actual wine staging version.
(press 'k') to copy the Vanilla source to workdir.
(press 'a') to get the actual wine-staging hash tag.
(press 'b') to base/set the wine vanilla sources to the wine-staging hash version.
(press '5') to inject the wine-staging patches.
(press '6') to build wine staging.
(press 'i') to install wine-staging.

Again, look into the script, visit the compiler calls and modify to your needs !
