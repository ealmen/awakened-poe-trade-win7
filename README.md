# I have no idea what I'm doing, use at your own risk, or follow guide and compile it your self

Forked from https://github.com/SnosMe/awakened-poe-trade

This is Awakened POE Trade compiled with an older electron version, that is still compatible for Windows 7.
I'm doing this mostly for myself, and to document the steps I've done to get this to work, in case I need it myself again.



#How to compile it your self:
Pre-requisit, only needed once:
Install and use latest version of node.js
node.js officially doesn't work on windows 7 any more, but unoficially works quite well still, after a bit of tinkering.

Either do this bit of tinkering, or compile this from a modern Windows 10+ machine. You will suffer massivly trying to use old node.js. Don't try to go down that road.


How to force latest node.js in Windows 7:

Install some old version of node.js to start with. latest v12 or whatever, don't install the extra optional content, or do, doesn't matter but didn't work for me so pointless.
(I used x64.msi from https://nodejs.org/download/release/v12.22.12/ )

Download latest zip file of node.js from https://nodejs.org/en/download
(I used LTS 18.17.1, Windows Binary (.zip) 64-bit)


Go to C:\Program Files\nodejs  (from v12 we installed previously)
Either delete everything in here, or move nodejs folder and create a new one
extract content of v18 node.js zip here

Create a new enviroment variable: (right click on Computer -> properties. Advanced system settings. Advanced tab -> Environment Variables... -> click on New in the bottom half of the window)
NODE_SKIP_PLATFORM_CHECK
1


start cmd as admin
cd C:\Program Files\nodejs
npm install npm@latest -g
npm install corepack -g			// Not sure what I did here, but npm, yarn and corepack is installed globally for me
npm install yarn -g

close cmd, and from this point on, don't install anything else globally (-g), and don't run anything else as admin
(it can be a pain to mix globally installed newer versions of modules, and trying to forse older versions locally for a specific project. Only use local modules, except for npm and yarn)
(yarn isn't strictly needed. but slightly nicer than npm install I guess)



It can also help a lot for trouble shooting to set a larger screen buffer size, so that you can scroll up far to read larger error messages.
open cmd, as normal user, not admin.
right click on top left icon -> properties
 Screen Buffer Size:
  Width: 300
  Height: 9000

 Window Size:
  Width: 160
  Height: 80











-------------------
#Download source code for Awakaned POE Trade, and extract to C:\apt
(I've seen some issues with long path names, and non-ascii characters in C:\Users\your ñämé, so work in simple C:\apt is recommended, even if not strictly necessary)

Download latest source code (zip) from here:
https://github.com/SnosMe/awakened-poe-trade/releases

Extract to C:\apt, so that you have C:\apt\main and C:\apt\renderer etc


if you fuck something up, delete everything in C:\apt, and re-extract the zip



-------------------
#Edit C:\apt\main\packages.json
Go down to the row for "electron", and change version to latest that is still supported in windows 7.
Support was dropped in v23+, so check out https://releases.electronjs.org/releases/stable?version=22

as of writing this, row should be:
"electron": "22.3.23",


You also have a packages.json in C:\apt\renderer\, but as of writing this, no changes there are needed.



-------------------
#Compile it your self:

open cmd and run:
cd C:\apt\renderer
yarn					// downloads all modules needed specified in packages.json
yarn run make-index-files
yarn run lint
yarn run build				// build must be the last in renderer. re-run it if you are unsure. check if C:\apt\renderer\dist\data\en\items-name.index.bin exists or not. if not, re-run this. not sure if you need to run build in main before this, or what the issue was for me

cd C:\apt\main
yarn					// downloads all modules needed specified in packages.json. (you can also force specific electron version via: npm install electron@22.3.23   and that will edit packages.json)
yarn run build
yarn run package			// takes 1-2 min, and beeps a few times.



(you can use "yarn run dev" to just run it without compiling it to a .exe, might be faster for trouble shooting. You need to run dev in two cmd-windows, one in renderer and one in main. The one in renderer is pickier, and needs to run all/some of the other commands first. I struggled getting this to work, with http 404 errors and wrong ports used, but didn't spend much time on it)


-------------------
#Get the .exe's
you'll find them in C:\apt\main\dist
easy peasy, or spend hours trouble shooting.
