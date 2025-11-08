Update of https://github.com/squeeb/JUNO-106-M4L/blob/main/README.md correction on Pubo's 106 max4live patch.
I added change to every slider object in order to filter data sent as the amount of message sent was creating a bottleneck.

I also added my version of it, you can use all the sliders of your juno 106 in real time, it's missing from now a way to use switch and buttons from the 106 interface, i'll try to make it work asap.
The buttons are in reverse order, as it's theirs binary logical order.
There's also a 106 user's manual included..

here is the Help to use implement my system :

Use this M4L device to use my version : juno_106_2.amxd
entrance_2.maxpat should be open at the same time as the amxd, but outside Ableton Live (VERY IMPORTANT).

Your Juno Function 3 positions button (on the back panel) should be set on III : "all" to allow all types of in/out messages.
Please also use the "manual" mode for the Juno to avoid any interferance from presets.

When using "entrance" patch (outside live), you should select under the two "midifinfo" objects present at the Top and bottom of the patch your midi I/O interface.

the two patches are communicating with each other using udpsend/receive objects, in order to use this function you should allow Max/Live to communicate with the network.
The choice of the UDP port number is up to you, but be aware to use the consistent host : local host aka 127.0.0.1

In the amxd device
udpsend 127.0.0.1 1002 =>sends datas to entrance within the localhost network on the port 1002

In entrance.maxpat
udpsend 127.0.0.1 1001 =>sends datas to Live within the localhost network on the port 1001

What I would recommend to do as "Best practices" to use the patch :

Do not use at the same time data input recording and data output, this may result in conflicts and makes juno unable to understand what it does.
- So record first then edit in live the recorded datas.
- Please use Live's bundled version of MAX/MSP otherwise there are some risks of conflicts when two instances of a single MAX version are opened.
- Also, if you are on PC, please be sure to deasble RNBO server on MAX 9 versions :
it generates CPU overflow with cracks which are quite annoying (but still does permit to use the patch).
Be sure to switch off the RNBO Server in preferences for both bundled version and your standard installed version.
Cycling puts this on by defaults but it's likely to cause audio buffer overflow for some reasons, which quite annoying.

I Hope this helps 

