# CastScreen
Cast Android screen via WiFi or USB

Demo video: https://youtu.be/D_DSuvFz_sg

## Requirments
* Gstreamer 1.0 with H264 decoder (h264parse, avdec_h264) 
* adb for mirror via USB
### for building the CastScreen android app
* install android studio (on arch, do `yaourt -S android-studio`)

## With native receiver
* If you are not on an ARM machine, ignore outputs from *_arm targets, or remove them from the Makefile.
* Compile the receiver
```
$ cd receiver
$ make
```

## Building the CastScreen android app
* open app/ directory as a project in android studio
* build the project
* the apk is in `app/build/outputs/apk/debug/app-debug.apk`


### Via WiFi
1. Launch receiver
```
$ cd receiver
$ ./cs_receiver autovideosink
```
2. Open CastScreen APP
3. Wait the receiver to appear on the list
4. Select the receiver
5. Tap **Start** on right corner

### Via USB
1. Enable debug mode on the Android device
2. Make sure adb is available on your PC
3. Open CastScreen APP
4. Select **Server mode**
5. Tap **Start** on right corner
6. Launch receiver
```
$ cd receiver
$ ./wait_adb.sh
```

## With python receiver
### Via WiFi
1. Launch receiver
```
$ cd receiver
$ python cs_receiver.py
```
2. Open CastScreen APP
3. Wait the receiver to appear on the list
4. Select the receiver
5. Tap **Start** on right corner

### Via USB
1. Enable debug mode on the Android device
2. Make sure adb is available on your PC
3. Open CastScreen APP
4. Select **Server mode**
5. Tap **Start** on right corner
6. Launch receiver
```
$ cd receiver
$ adb forward tcp:53516 tcp:53515
$ python cs_receiver_conn.py
```

## Closing receivers
### Ubuntu
Open system monitor, look up using the word receiver, and kill the process.

## Using an alternative app.
You can use the receiver with the [All Cast Receiver App](https://play.google.com/store/apps/details?id=com.koushikdutta.cast.receiver&rdid=com.koushikdutta.cast.receiver) as well. Just start a receiver as described above (the native receiver is faster than the python one).

## License
Copyright (c) 2015-2016 Jones Chi. Code released under the Apache License.
