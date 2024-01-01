# Awakened POE Trade with Windows 7 compatibility
Forked from https://github.com/SnosMe/awakened-poe-trade

Changes made:
- I've added back Win7 compatibility by using older Electron version.   
  Short term this is an easy fix without any real issues (other than not working so nice in Win11 etc).   
  Long term this will probably not be that great of a solution in a year or two.   
  Win7 is dying. Start planning to switch to modern OS/hardware if you want to keep playing POE.
  
- The auto-update feature points to this repo and downloads my releases rather than the non-Win7 version from the main repo.
  This avoids the "The procedure entry point DiscardVirtualMemory could not be located in the dynamic link library KERNEL32.dll" bug each time a new version is released.
  
  If you install the **Setup**-version you will automatically get new version when I release them (soon after SnosMe releases new versions to the main repo).
  
  If you run the **portable / non-Setup** version, auto-update is disabled (same as in the non-Win7 version in the main repo), but checking if a new version exist in Settings -> About still works, and you can manually click the link there to open my download page.

- I've changed the name of the app from "Awakened PoE Trade" to "Awakened PoE Trade Win7" in Settings -> About and when hovering over the tray icon, to make you be able to differentiate this version from the main version.   
  I have not changed the name of the .exe's since that also changes the folder name in the install dir, and that looked ugly when testing it.   
  I have not changed the internal name, since this changes the path to the config folder, making the Win7-version lose all settings and you would have to start over from scratch.   
  In most ways this Win7 version still acts like the main version, and you can only have one of them installed, only run one of them at once etc.   
  I don't really want to change anything more than absolutely needed. This isn't "my" version of APT. All I'm trying to do is fix the Win7 compatibility bug.

----

I'm new to GitHub, sorry for any noob-mistakes on GitHub/forking best practices etc.  
I'm probably not the best person to keep win7 compatibility alive, but since no one else has stepped up I guess I'll do it.

Feel free to compile it yourself if you want, it's not that hard actually, and only needs a single line of code changed.  
Here is a guide on how to [compile it yourself](https://github.com/ealmen/awakened-poe-trade/blob/master/Compile%20it%20yourself.md).

I'm doing this mostly for myself, and to document the steps I've done to get this to work, for next version when I'll need the guide myself again.
And so that if/when I stop releasing new versions there is a guide on how someone else can take over. But I'll probably continue to release new versions even after I no longer need them myself, as long as it doesn't require huge amounts of work.
