# Node.js doesn't officially support Windows 7 anymore
But unofficially it still works quite well still, after a bit of tinkering.

## How to force latest node.js in Windows 7

Install some old version of node.js to start with. latest v12 or whatever

I used x64.msi from https://nodejs.org/download/release/v12.22.12/

---
Download latest zip file of node.js from https://nodejs.org/en/download

I used LTS 18.17.1, Windows Binary (.zip) 64-bit

---
Go to C:\Program Files\nodejs  (from v12 we installed previously)

Either delete everything in here, or move nodejs folder and create a new one

extract content of v18 node.js zip here

----
### Create a new environment variable:
right click on Computer -> properties.
Advanced system settings. Advanced tab -> Environment Variables... -> click on New in the bottom half of the window

```
NODE_SKIP_PLATFORM_CHECK
1
```
![environment](https://i.imgur.com/1ohFRFC.jpg)

----
start cmd as admin, and run
```
cd C:\Program Files\nodejs
npm install npm@latest -g
npm install corepack -g			// Not sure what I did here, but npm, yarn and corepack is installed globally for me
npm install yarn -g
```

close cmd, and from this point on, don't install anything else globally (-g), and don't run anything else as admin

It can be a pain to mix globally installed newer versions of modules, and trying to force older versions locally for a specific project. Only use local modules, except for npm and yarn.

(yarn isn't strictly needed. but slightly nicer than npm install I guess)

-----
## Test that it's working
open a new cmd as normal user, type in
```
npm --version      // 10.1.0 or newer
yarn --version     // 1.22.19 or newer
```

If you get error message, or older versions, you need to troubleshoot this more.

Check out: https://stackoverflow.com/a/64626035
and the comments there
