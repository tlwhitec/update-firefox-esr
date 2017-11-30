# update-firefox-esr
A tiny shell script that will allow you to install/update the Firefox ESR browser on your Linux distro.

My employer has a set of Firefox browser-dependent tools, that (as one would expect) don't keep up the pace with the bleeding edge browser development. For those purposes there's an [ESR version](https://www.mozilla.org/en-US/firefox/organizations/), which maintains the browser security, but adopts the new stuff only after a much more graceful period.

There's usually no Linux distribution that takes care about regular updates of it. At least not Ubuntu or CentOS, which I made contact with. However, Mozilla maintains a [whole scale of ESR builds](https://www.mozilla.org/en-US/firefox/organizations/all/) available for several platforms.

This script is there to download whatever latest build there is for your platform, extract it and replace the "installation" you had before. Currently, this version deletes all the previous installation files and puts new ones in the same spot. It's crude, but as I don't do changes in the firefox directory, it works fine for me.

## Prerequisites
Among some very usual shell commands, this script uses the following tools which are not usually preinstalled, but can be found in your Linux distro's repositories:
- **curl** to check for the latest version
- **wget** to download the new file

## Operation
1. Check for the currently available Firefox ESR version online.
2. Check for your installed version in `/opt/firefox-esr`, if any.
2.1. If not, it creates a symlink in `/usr/local/bin/firefox`, which usually comes first when the shell is searching for the `firefox` executable, so there's no need to uninstall your distro's default firefox.
3. When all is sensible up to this point, the update is downloaded.
4. When any firefox instance is running, it asks you to close it. Y'know, just to be sure.
5. You are asked for your sudo password. Then the old installation is removed and replaced with the installed update.
