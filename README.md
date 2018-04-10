# RICOH THETA V with HTC Vive Using SteamVR

Sample project for using RICOH THETA HTC Vive with SteamVR for telepresence applications.
![](doc/img/thetav-in-game-screenshot.png)

The 4K video stream from the THETA V will appear in HTC headset. 

## Controllers
With the default SteamVR features, you can do the following:

- track both controllers inside of the headset. Position is accurate
- take screenshots from inside of the headset using the controller buttons

![](doc/img/htc-vive-screenshot.png)

I am not using the controllers to grab anything right now.


## Thanks
Thanks to the great community of contributors at theta360.guide. 

Special thanks to Ricoh for working with the independent development community and updating the THETA V live streaming driver to work with Unity.

This is based on the [project](https://community.theta360.guide/t/tutorial-live-ricoh-theta-s-dual-fish-eye-for-steamvr-in-unity/938) by [@zimmermegan](https://community.theta360.guide/u/zimmermegan/summary) for the THETA S.

Additional credits:

- [DrustZ](https://community.theta360.guide/u/DrustZ) for the initial hack of the THETA S registry that led to [ZimmerMegan](https://community.theta360.guide/u/zimmermegan/summary) getting Unity to work with the THETA V. This led to Ricoh updating the driver.
- [joshapplman](https://community.theta360.guide/u/joshappleman/summary) for the technique of using negative scale to reverse the mirroring effect inside of the sphere


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

You will need to modify the script to detect the webcam on your system.  By default, the script
will look for `RICOH THETA V 4K`. If you want to use a different resolution or a different
driver, you will need to modify the script. 

![](doc/img/webcam_name.png)

The script will also display all webcams attached
to your computer for debugging.

![](doc/img/webcam-detect.png)

## Height of THETA V

Right now, the height of the scene and the height of 
the THETA V are not matched to provide a good 
telepresence experience. I'll run more tests in the 
future.

## Fun 

The cool thing about developing for the VR headset is that you are forced to stand away from your computer to test it. You may even need your friend to help you with the headset.  :-)

![](doc/img/testing-fun.png)

Thanks to Ricoh for these cool THETA V t-shirts they
gave out at CES.

![](doc/img/testing-fun2.png)

## Software Used in This Test

Tests were done with the following:

- Unity 2017.4.0f1 (earlier version should work)
  - [SteamVR Plugin for Unity](https://assetstore.unity.com/packages/templates/systems/steamvr-plugin-32647)
- [RICOH THETA V](https://theta360.com/en/about/theta/v.html)
  - RICOH THETA V firmware 2.11.1 (or higher)
- [RICOH THETA V live streaming driver 1.0.1](https://theta360.com/en/support/faq/c_06_v/304_1/) 64 bit  - You NEED 1.0.1 or higher to work with Unity

