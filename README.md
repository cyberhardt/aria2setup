Description: How to set up aria2 for it to work as a download manager for use with AriaNG Native and other similar programs on Windows, with additional browser extension.

-

Tested with: Windows 10 2H22 64-bit using AriaNG Native 1.3.4

working .conf file found on: https://github.com/RossWang/Aria2-Integration/tree/master/Bin

working .vbs and .bat originally created by: https://gist.github.com/maple3142

broken config file with explanations regarding the parameters (unfit for actual use as it is broken, but you can read it): https://gist.github.com/qzm/a54559726896d5e6bf21adf2363ad334#file-aria2-conf

Download aria2 at: https://aria2.github.io/

Download AriaNG at: https://github.com/mayswind/AriaNg-Native

-

Download aria2 browser addon: https://github.com/jc3213/download_with_aria2

The browser addon is needed to capture downloads that otherwise wouldn't be possible with traditional copy/paste of links. The addon by jc3213 was the only one that worked amongst those I've tested. When capturing downloads with it, they are sent to aria2 and therefore can be seen and managed with AriaNG Native.

The other addons I've tested: https://addons.mozilla.org/en-US/firefox/addon/aria2-integration-extension/ (had unecessary ariang interface), https://addons.mozilla.org/en-US/firefox/addon/aria2-extension/ (didn't work), https://addons.mozilla.org/en-US/firefox/addon/aria2-integration/ (didn't work).

-

I couldn't find a proper guide for this anywhere. No one tells you that you need to have a .conf file for it to work. What the hell?
Did everyone go mad? Why people offer aria2 and aria2 related programs if they don't even work without configuring them previously?
Or, rather, considering that is true, why no one provided a FUCKING QUICKSTART GUIDE ON THIS SHIT? WHAT THE HELL, YOU FUCKING MORONS?
DO I LOOK LIKE AN ORACLE? AM I SUPPOSED TO KNOW THAT THIS PROGRAM NEEDS MANUAL CREATION OF FOLDERS AND CONFIG FILES? HUH?
Anyway. If you're here, you probably feel just like me. Well, here's the solution everyone needed but no one provided... for some reason.

-

First and foremost, create a folder called aria2 on C:\\, then create aria2.session and aria2.log inside it. Then, create a folder called aria2downloads on your Downloads directory. You can, of course, set different names for the aria2 and aria2downloads folders. This was made with AriaNG Native in mind, for use as a download manager. I did not include torrent settings on my conf, but you can add it yourself with the links I provided. Just paste the torrent-related parameters on the conf below the #---------- part and it should be fine. After those steps, all you need to do is paste the three files of this repository inside aria2 folder, set your username on aria2.conf, and run init.bat. Provided your system drive is C, and aria2 folder is inside C as in C:\aria2, it should work right off the bat after editing the username on aria2.conf.

-

The .vbs allows for hidden execution, the .bat works to start the .vbs. Why both? I don't know. It worked, so...

-

In order to get it to run at startup, do this:
Create a shortcut for the init.bat, and place it in: "C:\Users\\-\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Startup".
It will now execute aria2 on startup. Replace "-" by your user.

-

IF YOU CHANGE ARIA2 PATH IN .config, YOU'LL HAVE TO MODIFY IT IN init.vbs AND initaria.bat AS WELL.
