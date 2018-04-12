# RICOH THETA V with HTC Vive Using SteamVR

Sample project for using RICOH THETA HTC Vive with SteamVR for telepresence applications.
![](doc/img/thetav-in-game-screenshot.png)

Display the 4K video stream from a THETA V inside a HTC Vive headset. 


## Overview
The RICOH THETA is the world's most popular 360 camera. The THETA V model was released in late 2017. The "V" outputs a 4K equirectangular video stream with H264 compression 3840×1920/29.97fps as well as a 2K 1920x960/29.97 stream.

You can easily use a Unity webcam texture to wrap
the THETA V 4K video stream onto a sphere to provide a telepresence experience for industrial or
experiential applications.

This test application is illustrates the following techniques:

- identify THETA V camera inside of Unity
- assign THETA V to a texture
- use flip normals on a Blender sphere to display the webcam texture to the inside of the Sphere. The Blender sphere is imported into Unity
- use negative scale values to solve *mirroring* problem of objects in sphere appearing in reverse
- display THETA V stream inside of a HTC Vive headset with SteamVR
- track head movements and controller movements with SteamVR
- use THETA V as a microphone and output audio to HTC Vive
- initial configuration tests to orient the headset and the camera to simulate real-world telepresence

These techniques are compiled from the theta360.guide community in the 
[Unity Development discussion conference](https://community.theta360.guide/c/theta-media/unity-development). If you have 
any questions or would like to tell us about your project
please join this free and independent community of developers.  We'd love to hear from you.

![](doc/img/htc-vive-theta-gear.png)

Communications gear for the next gen! Join us.

## Software Used in This Test

Tests were done with the following:

- Unity 2017.4.0f1 (earlier version should work)
  - [SteamVR Plugin for Unity](https://assetstore.unity.com/packages/templates/systems/steamvr-plugin-32647)
- [RICOH THETA V](https://theta360.com/en/about/theta/v.html)
  - RICOH THETA V firmware 2.11.1 (or higher)
- [RICOH THETA V live streaming driver 1.0.1](https://theta360.com/en/support/faq/c_06_v/304_1/) 64 bit  - You NEED 1.0.1 or higher to work with Unity

## Thanks and Credits
Thanks to the great community of contributors at theta360.guide. 

Special thanks to Ricoh for working with the independent development community and updating the THETA V live streaming driver to work with Unity.

This is based on the [project](https://community.theta360.guide/t/tutorial-live-ricoh-theta-s-dual-fish-eye-for-steamvr-in-unity/938) by [@zimmermegan](https://community.theta360.guide/u/zimmermegan/summary) for the THETA S.

Additional credits:

- [DrustZ](https://community.theta360.guide/u/DrustZ) for the initial hack of the THETA S registry that led to [ZimmerMegan](https://community.theta360.guide/u/zimmermegan/summary) getting Unity to work with the THETA V. This led to Ricoh updating the driver.
- [joshapplman](https://community.theta360.guide/u/joshappleman/summary) for the technique of using negative scale to reverse the mirroring effect inside of the sphere

- [Nima](https://community.theta360.guide/u/nima/summary) for the technique to use the THETA V microphones with 
Unity.




## Quick Test Without Installing Unity
This is a skeleton project for
developers using Unity and is not intended for use as a binary.
If you want to check it out quickly, I 
have included a binary in the directory `release`.  If you don't want to download the entire repo, it may be easier for you to download zipped package from the [releases section of GitHub](https://github.com/codetricity/theta-v-htc-vive-steamvr/releases). The release file is 15.2MB.


![](doc/img/download-binary.png)

Extract the file. There should be a Windows 10 64 bit executable with a green THETA logo. 

![](doc/img/app-binary.png)

### Turn on THETA V in Live Streaming Mode

To simulate the perspective a standing person, put the
THETA V on a tripod at eye level. Connect the THETA V
with a USB cable and put it into live streaming mode.

![](doc/img/thetav-livestream.jpg)



### Connect HTC Vive to Your Computer

![](doc/img/htc-vive-connection.png)

## Align Camera and Headset
The HTC Vive default position is pointed in the same direction as the rear THETA V camera lense. The rear lense is the one that is facing away from the shutter button. A person talking directly to the rear lense will appear to be talking to the face of the person wearing the HTC Vive headset.

![](doc/img/vive-theta-alignment.png)


### Start SteamVR

![](doc/img/steamvr.png)

### Start Application on Windows

Double-click on __theta_v_htc_vive_test.exe__ on your Windows 10 computer.

![](doc/img/binary-click-me.png)



### Wait for App to Load

The app should load in less than 5 seconds.

![](doc/img/unity-app.png)

The screen will turn black as the headset adjusts to the THETA V input.

### Put Headset On and Enjoy Telepresence

![](doc/img/app-screenshot.png)



## Controllers
With the default SteamVR features, you can do the following:

- track both controllers inside of the headset. Position is accurate
- take screenshots from inside of the headset using the controller buttons

![](doc/img/htc-vive-screenshot.png)

I am not using the controllers to grab anything right now.


## Audio

The script will use the first audio device it finds. Adjust this line in the code to properly identify the THETA V. The script will display the connected 
microphones to the debug console of Unity.


	public const int THETA_V_AUDIO_NUMBER = 0;   





## Update RICOH THETA V Live Streaming Driver
You need 1.0.1 or later. Earlier versions will not work. See [this](https://community.theta360.guide/t/solved-unity-cant-display-theta-v-live-stream-on-windows-10/1688/39) article for info. Note how Ricoh updated the driver is response to our community feedback. :-)  


## Viewing Inside of Sphere
I am using a flip-normals sphere that I created in blender. This should be included in the package.

If you're interested in building your own sphere with Blender, 
[this](https://youtu.be/56QGJ76YM-s) video will give you a step-by-step process.

![](doc/img/flip-normals.png)



## Mirroring
The flip-normals sphere causing the scene to appear like a mirror image. To correct this problem, I am inverting the sphere with negative scale. -8, -8, -8.
Original hack by [@joshapplman](https://community.theta360.guide/u/joshappleman/summary) 

![](doc/img/sphere-negative-value.png)

## Inverted Camera

I needed to rotate the X axis of the SteamVR rig by 180 degrees in order to get it to work.

![](doc/img/invert-camera.png)

## Specifying the Correct RICOH THETA V driver

The script should automatically detect the webcams on your system.  By default, the script
will look for `RICOH THETA V 4K`. If you want to use a different resolution or a different
driver, you will need to modify the script. 

![](doc/img/webcam_name.png)

The script will also display all webcams attached
to your computer for debugging.

![](doc/img/webcam-detect.png)

## Height of THETA V

Put the bottom of the THETA V at eye level for a 
telepresence experience that is close the real
world. If the camera is at eye level, the person you are talking to should
be face the lense that is opposite the shutter
button. 

Alternately, you can change the perspective to
a surreal experience. Several people wearing the headset have mentioned
that they like it when the THETA V is close to the ground
as they feel like a small animal.


## Fun 

The cool thing about developing for the VR headset is that you are forced to stand away from your computer to test it. You may even need your friend to help you with the headset.  :-)

![](doc/img/testing-fun.png)

Thanks to Ricoh for these cool THETA V t-shirts they
gave out at CES.

![](doc/img/testing-fun2.png)



