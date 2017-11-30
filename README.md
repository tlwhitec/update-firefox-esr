# update-firefox-esr
A tiny shell script that will allow you to install/update the Firefox ESR browser on your Linux distro.

My employer has a set of Firefox browser-dependent tools, that (as one would expect) don't keep up the pace with the bleeding edge browser development. For those purposes there's an [ESR version](https://www.mozilla.org/en-US/firefox/organizations/), which maintains the browser security, but adopts the new stuff only after a much more graceful period.

There's usually no Linux distribution that takes care about regular updates of it. At least not Ubuntu or CentOS, which I made contact with. However, Mozilla maintains a [whole scale of ESR builds](https://www.mozilla.org/en-US/firefox/organizations/all/) available for several platforms.

This script is there to download whatever latest build there is for your platform, extract it and replace the "installation" you had before. Currently, this version deletes all the previous installation files and puts new ones in the same spot. It's crude, but as I don't do changes in the firefox directory, it works fine for me.

## Prerequisites
Among some very usual shell commands, this script uses the following tools which are not usually preinstalled, but can be found in your Linux distro's repositories:
- **curl** to check for the latest version
- **wget** to download the new file
