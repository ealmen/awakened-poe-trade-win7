# How to compile it yourself:

## Have an up to date version of Node.js installed and working

The only thing you need to compile Awakened POE Trade is [Node.js](https://nodejs.org/en)

Node.js has dropped official support for Windows 7 since v14, but unofficially still works quite well on Windows 7.

It is _much_ easier to compile this using a modern version of node.js.  
So either force it in Windows 7.  
Or use a Windows 10+ machine to compile this from.

[Follow this guide if you want to force it in Windows 7](https://github.com/ealmen/awakened-poe-trade/blob/master/Install%20latest%20Node.js%20in%20Windows%207.md)


> The rest of this guide assumes you have Node.js v18+ installed and working.

-----

## Download source code for Awakened POE Trade, and extract to C:\apt
(I've seen some issues with long path names, and non-ascii characters in C:\Users\your ñämé, so work in simple C:\apt is recommended, even if not strictly necessary)

Download latest source code (zip) from here:
https://github.com/SnosMe/awakened-poe-trade/releases

Extract to C:\apt, so that you have C:\apt\main and C:\apt\renderer etc.


> If you mess something up below, delete everything in C:\apt, and re-extract the zip



-------------------
## Edit C:\apt\main\packages.json
Go down to the line for "electron", and change version to one that is still supported in windows 7.

Win7 support was dropped in electron v23+, so we want to use the latest v22.  
You can use "22.x.x" to automatically get the latest version in the v22 branch, or manually specify an exact version number.  
Check versions and changelog here if needed: https://releases.electronjs.org/releases/stable?version=22

The line for electron should be:
```
"electron": "22.x.x",
```

> You also have a packages.json in C:\apt\renderer\, but no changes there are needed as of writing this.



-------------------
## Compile it yourself:

### open cmd and run:
```
cd C:\apt\renderer
yarn					// downloads all modules needed specified in packages.json
yarn run make-index-files
yarn run lint
yarn run build				// build must be the last you run in renderer

cd C:\apt\main
yarn					// downloads all modules needed specified in packages.json
yarn run build
yarn run package			// packages the .exe's up from what you've compiled so far. takes 1-2 min, and beeps a few times. must be the last step you do
```
<details>

<summary>screenshots</summary>

![renderer](https://i.imgur.com/5tvnQ0c.jpeg)

![main](https://i.imgur.com/ZEEXKv2.jpg)

</details>

> If you want, you can also use "yarn run dev" to just run it without compiling it to a .exe. It might be faster to trouble shoot that way.  
> You need to run dev in two cmd-windows, one in renderer and one in main. The one in renderer is pickier, and needs to run all/some of the other commands first.  
> I struggled getting this to work, with http 404 errors and wrong ports used, but didn't spend much time on it. I think it was because I didn't first run make-index-files and lint.


-------------------
## Get the .exe's

You'll find them in C:\apt\main\dist

Should be really easy.  
Or you'll spend hours troubleshooting.
