# valetudo_p2029
Tips and tricks for Valetudo for Dreamy L10 Pro.
It has 4x core CPU and around 0.5GB ram.
There is around 250MB free space, so enough for extra sounds etc.

# Extra sounds
The sound file should be in the following format and quality:
- Ogg data, Vorbis audio, mono, 16000 Hz, ~48000 bps

Some other format/qualities may work too, but not tested.

IMPORTANT: Surely stereo does not work.

## Playing sounds
You can play sounds with the following shell command:
- `/ava/script/mediad_script.sh /data/personalized_voice/DE/300 28`

The 28 at the end is probably volume.
The 300 is the file name (whereas the full filename is 300.ogg).

## Converting using ffmpeg
For lazy people:
- `ffmpeg -i input.wav -ar 16000 -ac 1 output.ogg`

- ar is bitrate
- ac is channel number (1 channel - mono)

# Improving linux side
Maybe, hopefully we can have some more fun with it.

We can out of the box lower the swappiness, increase max cpu speed (if not set already) and change the governor.
- `echo 5 > /proc/sys/vm/swappiness`
- `echo 1512000 > /sys/devices/system/cpu/cpufreq/policy0/scaling_max_freq`
- `echo schedutil > /sys/devices/system/cpu/cpufreq/policy0/scaling_governor`

Not necessary, but also if sleeping a lot of cpu is consumed, so lowering priority of ava and valetudo (whereas valetudo is fine here).
- ``renice 1 `ps -Ta | grep "ava\ " | awk '{print $1}' | xargs```
- ``renice 1 `ps -Ta | grep "/valetudo" | awk '{print $1}' | xargs```

By doing so, the linux kernel and stuff has slightly higher priority.

## Consumption
The following processes consume a lot of CPU even if sleeping.
- ava_log_file
- ROUTE_TREE

Maybe there is a possibility to put to sleep too if not needed.

# UPGRADE
Clearly, it is necessary to upgrade Valetudo and firmware of the vacuum separately (as those are completely separate parts).

IMPORTANT: Do not upgrade to official firmware, as this will remove valetudo and un-root your device (usually it is not possible after rooting, but if it is, just do not do it, as it can be harder to root the device with newer firmware).

- Updating valetudo is very simple, and can be done in the Web GUI of the vacuum (on the left side Update). You may need to do it a few times, as it always upgrades step by step.
- Updating firmware can be done on the device, using Dustbuilder.


You do not need to worry, as your SSH Keys and Wifi data stays intact, so no issues there.

IMPORTANT: Clearly the /tmp directory will be cleaned after the reboot, so download the update package to the /data directory, which does not change during upgrade or reboot.

# Summary
It works, and valetudo is really great !
