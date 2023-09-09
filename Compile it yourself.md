# How to compile it your self:

## Pre-requisit: Install and use latest version of node.js

This requires a bit of tinkering to work in Windows 7, or you can use a modern Windows 10+ machine to compile from.

Follow this guid if you want to force it in Windows 7


## Download source code for Awakaned POE Trade, and extract to C:\apt
(I've seen some issues with long path names, and non-ascii characters in C:\Users\your ñämé, so work in simple C:\apt is recommended, even if not strictly necessary)

Download latest source code (zip) from here:
https://github.com/SnosMe/awakened-poe-trade/releases

Extract to C:\apt, so that you have C:\apt\main and C:\apt\renderer etc


if you fuck something up, delete everything in C:\apt, and re-extract the zip



-------------------
## Edit C:\apt\main\packages.json
Go down to the row for "electron", and change version to latest that is still supported in windows 7.

Support was dropped in v23+, so check out https://releases.electronjs.org/releases/stable?version=22

as of writing this, row should be:
```
"electron": "22.3.23",
```

You also have a packages.json in C:\apt\renderer\, but as of writing this, no changes there are needed.



-------------------
## Compile it your self:

### open cmd and run:
```
cd C:\apt\renderer
yarn					// downloads all modules needed specified in packages.json
yarn run make-index-files
yarn run lint
yarn run build				// build must be the last in renderer. re-run it if you are unsure. check if C:\apt\renderer\dist\data\en\items-name.index.bin exists or not. if not, re-run this. not sure if you need to run build in main before this, or what the issue was for me


cd C:\apt\main
yarn					// downloads all modules needed specified in packages.json. (you can also force specific electron version via: npm install electron@22.3.23   and that will edit packages.json)
yarn run build
yarn run package			// takes 1-2 min, and beeps a few times.
```

You can use "yarn run dev" to just run it without compiling it to a .exe, might be faster for trouble shooting. You need to run dev in two cmd-windows, one in renderer and one in main. The one in renderer is pickier, and needs to run all/some of the other commands first. I struggled getting this to work, with http 404 errors and wrong ports used, but didn't spend much time on it


-------------------
## Get the .exe's

you'll find them in C:\apt\main\dist

easy peasy, or spend hours trouble shooting.
