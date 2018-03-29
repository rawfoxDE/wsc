# wsc
wine source control

This bash script will download the needed files and is able to compile a wow64 build of Vanilla Wine.
It also can rebase the wine vanilla source to the actual wine staging version, inject all staging patches and built it.

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
