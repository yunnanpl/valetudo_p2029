# valetudo_p2029
Tips and tricks for Valetudo for Dreamy L10 Pro

# Extra sounds
The sound file should be in the following format and quality:
- Ogg data, Vorbis audio, mono, 16000 Hz, ~48000 bps

Some other format/qualities may work too, but not tested.

IMPORTANT: Surely stereo does not work.

# Playing sounds
You can play sounds with the following shell command:
- /ava/script/mediad_script.sh /data/personalized_voice/DE/300 28

The 28 at the end is probably volume.
The 300 is the file name (whereas the full filename is 300.ogg).

# Converting using ffmpeg
For lazy people:
- ffmpeg -i input.wav -ar 16000 -ac 1 output.ogg

- ar is bitrate
- ac is channel number (1 channel - mono)

# Summary
It works, and valetudo is really great !
