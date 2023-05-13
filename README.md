Description: How to set up aria2 for it to work as a download manager for use with programs such as AriaNG and/or with additional browser extension (on Windows).

Note that the use of a frontend such as AriaNG is completely optional. By using the Download With Aria2 by jc3213 browser extension, you can already use it flawlessly and effortlessly as a download manager/accelerator without any additional software at all. With the extension, you can even get it to let you set the download location on a per-download basis, and notify you on start and completion of a download (with system notifications, not browser ones). AriaNG and similar programs have very poor performance and run on hundreds of MB of RAM, even on idle and system tray. By making use of the browser extension alone, you can get away with 3MB usage of RAM by the aria2c.exe process, which you can set to run on startup (how-to guide is down there).

I highly recommend you to read this readme in its entirety.

-

Tested on: Windows 10 2H22 64-bit using AriaNG Native 1.3.4 and Download with Aria2 
4.2.4.1968 on Librewolf 111.0-3.

working .conf file found on: https://github.com/RossWang/Aria2-Integration/tree/master/Bin

working .vbs and .bat originally created by: https://gist.github.com/maple3142

broken config file with explanations regarding the parameters (unfit for actual use as it is broken, but you can read it): https://gist.github.com/qzm/a54559726896d5e6bf21adf2363ad334#file-aria2-conf

Download aria2 at: https://aria2.github.io/

Download AriaNG at: https://github.com/mayswind/AriaNg-Native

Aria2 manual: https://aria2.github.io/manual/en/html/index.html

-

"Download With Aria2" browser addon: https://github.com/jc3213/download_with_aria2

The browser addon is needed to capture downloads that otherwise wouldn't be possible with traditional copy/paste of links. The addon by jc3213 was the only one that worked amongst those I've tested. When capturing downloads with it, they are sent to aria2 and therefore can be seen and managed with AriaNG Native, but the extension is so useful as-is that AriaNG isn't necessary.

The other addons I've tested: https://addons.mozilla.org/en-US/firefox/addon/aria2-integration-extension/ (had unecessary ariang interface), https://addons.mozilla.org/en-US/firefox/addon/aria2-extension/ (didn't work), https://addons.mozilla.org/en-US/firefox/addon/aria2-integration/ (didn't work).

After installing the addon, I recommend making the following changes on the Options page:

1 - Notifications when download starts and when it is complete

2 - Set user agent to be the same UA on the .conf file (currently "Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:56.0) Gecko/20100101")

3 - Enable both Capture Browser Downloads and Always Capture Downloads.

4 - Turn on Follow Browser Behavior (needs Capture Web Requests to be turned off) so that files get downloaded to the folder you select as if you were downloading with the browser. Very useful. You can ignore this if you want your files to always be downloaded to the same folder.

-

NOTE: I couldn't find a proper guide for this anywhere. No one tells you that you need to have a .conf file for it to work. What the hell?
Did everyone go mad? Why people offer aria2 and aria2 related programs if they don't even work without configuring them previously?
Or, rather, with it considered, why no one provides a FUCKING QUICKSTART GUIDE ON THIS SHIT? WHAT THE HELL?
DO I LOOK LIKE AN ORACLE? AM I SUPPOSED TO KNOW THAT THIS PROGRAM NEEDS MANUAL CREATION OF FOLDERS, CONFIG FILES AND PARAMETERS? HUH?
Anyway. If you're here, you probably feel just like me. Well, here's the solution everyone needed but no one provided... for some reason.

-

First and foremost, create a folder called aria2 on C:\\, then create aria2.session, aria2.log and stat.log inside it. Then, create a folder called aria2downloads on your Downloads directory. You can, of course, set different names for the aria2 and aria2downloads folders, and put them in other locations **(but you'll need to make sure paths on aria2.conf, init.vbs and init.bat are correct)**. Again, as mentioned before, this was made for use as a download manager. I did not include torrent settings on my .conf (in fact, I explicitly disabled DHT), but you can add it yourself with the links I provided, or with the help of AriaNG. Just copy the torrent-related parameters to the .conf file, **below the #---------- part** and it should be fine. After those steps, all you need to do is copy the three files of this repository to the aria2 folder, set your windows username on aria2.conf, and run init.bat. Provided your system drive is C, and aria2 folder is inside C as in C:\aria2, it should work right off the bat after editing the windows username on aria2.conf.

Configuration file is optimized for use as a download manager/accelerator. I don't recommend making changes to it unless you know what you are doing - aria2c.exe might not launch if the .conf file isn't properly organized. If you want to make changes to it but aren't sure what the parameters mean, check the Gist by user qzm, or the aria2 manual, or AriaNG which contains explanations for the parameters as well.

-

The .vbs allows hidden execution, the .bat works to start the .vbs. Why both? I don't know. It works, so...

-

In order to get it to run at startup, do this:

Create a shortcut for the init.bat, and place it in: "C:\Users\\-\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Startup".
It will now execute aria2 on startup. Replace "-" by your user.

-

Download Accelerator function won't significantly improve download speeds in sites whose speeds are unlimited, such as Pixeldrain.
