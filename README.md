# telemetry-injector

## Introduction

telemetry-injector takes a series of geotagged photos and creates a video with either CAMM or GPMD telemetry.

## How it works

We needed a way to upload to videos to the Google Street View API for our Trail Maker product.

Previously we uploaded videos alongside a gpx files as described in our blog; [Creating a Video File Ready to be Uploaded to the Google Street View API](https://www.trekview.org/blog/2022/create-google-street-view-video-publish-api/).

However, we wanted a way to inject telemetry into the video so that the video could be shared elsewhere, without the requirement to always share the GPX file alongside it.

Google Street View supports [CAMM](https://www.trekview.org/blog/2021/metadata-exif-xmp-360-video-files-camm-camera-motion-metadata-spec/) and [GPMD](https://www.trekview.org/blog/2020/metadata-exif-xmp-360-video-files-gopro-gpmd/) telemetry standards.

Therefore this script;

1. takes a series of geotagged images
2. parses out the telemetry into a gpx file
3. creates a camm / gpmd binary file from gpx
4. creates a video file from photos
5. injects the camm binary stream into the video

The specifics of how each step in this process works...

Karamvir TODO

## Installation

Download

```shell
git clone https://github.com/trek-view/telemetry-injector
cd telemetry-injector
```

Setup virtual environment

```shell
python3 -m venv telemetry-injector_venv
source telemetry-injector_venv/bin/activate
```

Install required libraries

```shell
pip3 install -r requirements.txt
```

## Usage

```shell
python3 telemetry-injector.py -c -i INPUT_IMAGE_DIRECTORY/ -o OUTPUT_VIDEO_FILE.mp4
```

* `-g`: Flag to use gpmf metadata injection.
* `-c`: Flag to use camm metadata injection.
* `-i`: Input image directory.
* `-v`: Input mp4 files, should be mp4 video.
* `-x`: Input gpx files, should be mp4 video.
* `-o`: Output video file conataining metadata.

### Image Input

For `camm` images metadata injection
	
```shell
python3 telemetry-injector.py -c -i input_image_directory -o OUTPUT_VIDEO_FILE.mp4
```

For `gpmf` images metadata injection

```shell
python3 telemetry-injector.py -g -i input_image_directory -o OUTPUT_VIDEO_FILE.mp4
```


### Video Input

For `camm` video metadata injection
	
```shell
python3 telemetry-injector.py -c -v input_mp4_video_file -x input_gpx_file -o output_mp4_video_file
```

For `gpmf` video metadata injection

```shell
python telemetry-injector.py -g -v input_mp4_video_file -x input_gpx_file -o output_mp4_video_file
```


### Make Cherry GPS video with telemetry-injector.py
```shell
python telemetry-injector.py -g -v ..\Q360_20241127_152954_000001.MP4 -x ..\Q360_20241127_152954_000001_Output.GPX -o ..\Q360_20241127_152954_000001_gpx.MP4 >1.txt 2>&1
```

mpeg4 [648077262]
 ©À©¤©¤ b'ftyp' [8, 20]
 ©À©¤©¤ b'free' [8, 0]
 ©À©¤©¤ b'mdat' [8, 647227202]
 ©À©¤©¤ b'moov' [8, 18443]
 ©¦   ©À©¤©¤ b'mvhd' [8, 100]
 ©¦   ©À©¤©¤ b'trak' [8, 11669]
 ©¦   ©¦   ©À©¤©¤ b'tkhd' [8, 84]
 ©¦   ©¦   ©À©¤©¤ b'edts' [8, 28]
 ©¦   ©¦   ©À©¤©¤ b'mdia' [8, 10509]
 ©¦   ©¦   ©¦   ©À©¤©¤ b'mdhd' [8, 24]
 ©¦   ©¦   ©¦   ©À©¤©¤ b'hdlr' [8, 37]
 ©¦   ©¦   ©¦   ©¸©¤©¤ b'minf' [8, 10424]
 ©¦   ©¦   ©¦       ©À©¤©¤ b'vmhd' [8, 12]
 ©¦   ©¦   ©¦       ©À©¤©¤ b'dinf' [8, 28]
 ©¦   ©¦   ©¦       ©¸©¤©¤ b'stbl' [8, 10360]
 ©¦   ©¦   ©¦           ©À©¤©¤ b'stsd' [8, 280]
 ©¦   ©¦   ©¦           ©¦   ©¸©¤©¤ b'hvc1' [8, 264]
 ©¦   ©¦   ©¦           ©À©¤©¤ b'stts' [8, 16]
 ©¦   ©¦   ©¦           ©À©¤©¤ b'stss' [8, 288]
 ©¦   ©¦   ©¦           ©À©¤©¤ b'stsc' [8, 2036]
 ©¦   ©¦   ©¦           ©À©¤©¤ b'stsz' [8, 4172]
 ©¦   ©¦   ©¦           ©¸©¤©¤ b'stco' [8, 3520]
 ©¦   ©¦   ©¸©¤©¤ b'uuid' [8, 1016]
 ©¦   ©À©¤©¤ b'trak' [8, 6552]
 ©¦   ©¦   ©À©¤©¤ b'tkhd' [8, 84]
 ©¦   ©¦   ©À©¤©¤ b'edts' [8, 28]
 ©¦   ©¦   ©¸©¤©¤ b'mdia' [8, 6416]
 ©¦   ©¦       ©À©¤©¤ b'mdhd' [8, 24]
 ©¦   ©¦       ©À©¤©¤ b'hdlr' [8, 37]
 ©¦   ©¦       ©¸©¤©¤ b'minf' [8, 6331]
 ©¦   ©¦           ©À©¤©¤ b'smhd' [8, 8]
 ©¦   ©¦           ©À©¤©¤ b'dinf' [8, 28]
 ©¦   ©¦           ©¸©¤©¤ b'stbl' [8, 6271]
 ©¦   ©¦               ©À©¤©¤ b'stsd' [8, 153]
 ©¦   ©¦               ©¦   ©¸©¤©¤ b'mp4a' [8, 137]
 ©¦   ©¦               ©¦       ©À©¤©¤ b'esds' [8, 45]
 ©¦   ©¦               ©¦       ©À©¤©¤ b'SA3D' [8, 28]
 ©¦   ©¦               ©¦       ©¸©¤©¤ b'btrt' [8, 12]
 ©¦   ©¦               ©À©¤©¤ b'stts' [8, 5544]
 ©¦   ©¦               ©À©¤©¤ b'stsc' [8, 284]
 ©¦   ©¦               ©À©¤©¤ b'stsz' [8, 12]
 ©¦   ©¦               ©À©¤©¤ b'stco' [8, 184]
 ©¦   ©¦               ©À©¤©¤ b'sgpd' [8, 18]
 ©¦   ©¦               ©¸©¤©¤ b'sbgp' [8, 20]
 ©¦   ©¸©¤©¤ b'udta' [8, 90]
 ©¦       ©¸©¤©¤ b'meta' [8, 82]
 ©À©¤©¤ b'kfix' [8, 1956]
 ©¸©¤©¤ b'kvar' [8, 829593]
mdat_size 647227202
pos 647227246
tkhd track_id 3 duration 35000 creation_time 3815566195
mdhd time_scale 1000 duration 35000 creation_time 3815566195
Processing: E:\projects\GPS\telemetry-injector\temp.mp4
Saved file settings
	Track 0
		Spherical = true
		Stitched = true
		StitchingSoftware = Spherical Metadata Tool
		ProjectionType = equirectangular
	Track 1
		Ambisonic Type: periphonic
		Contains Head-Locked Stereo: False
		Ambisonic Order: 1
		Ambisonic Channel Ordering: ACN
		Ambisonic Normalization: SN3D
		Number of Channels: 4
		Channel Map: [0, 2, 3, 1]
	Track 2



### Cherry GPS video verify with ffmpeg
```shell
ffmpeg -i ..\Q360_20241127_152954_000001_gpx.MP4
```

[mov,mp4,m4a,3gp,3g2,mj2 @ 000001bf53b87800] Ambisonic channel reordering is not supported
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '..\Q360_20241127_152954_000001_gpx.MP4':
  Metadata:
    major_brand     : isom
    minor_version   : 512
    compatible_brands: isomiso2mp41
    encoder         : Lavf60.16.100
  Duration: 00:00:35.00, start: 0.000000, bitrate: 148134 kb/s
  Stream #0:0[0x1](und): Video: hevc (Main) (hvc1 / 0x31637668), yuvj420p(pc, bt709, progressive), 3840x7680, 148784 kb/s, SAR 1:1 DAR 1:2, 30 fps, 30 tbr, 90k tbn (default)
    Metadata:
      handler_name    : VideoHandler
      vendor_id       : [0][0][0][0]
    Side data:
      spherical: equirectangular (0.000000/0.000000/0.000000)
  Stream #0:1[0x2](und): Audio: aac (HE-AAC) (mp4a / 0x6134706D), 48000 Hz, 4.0, fltp, 576 kb/s (default)
    Metadata:
      handler_name    : SoundHandler
      vendor_id       : [0][0][0][0]
  Stream #0:2[0x3](und): Data: bin_data (gpmd / 0x646D7067), 2 kb/s
    Metadata:
      creation_time   : 2024-11-27T15:29:55.000000Z
      handler_name    : GoPro MET

### Cherry GPS video verify with MediaInfo
```shell
MediaInfo.exe ..\Q360_20241127_152954_000001_gpx.MP4
```
General
Complete name                            : ..\Q360_20241127_152954_000001_gpx.MP4
Format                                   : MPEG-4
Format profile                           : Base Media
Codec ID                                 : isom (isom/iso2/mp41)
File size                                : 618 MiB
Duration                                 : 35 s 0 ms
Overall bit rate                         : 148 Mb/s
Frame rate                               : 30.000 FPS
Writing application                      : Lavf60.16.100

Video
ID                                       : 1
Format                                   : HEVC
Format/Info                              : High Efficiency Video Coding
Format profile                           : Main@L6@High
Codec ID                                 : hvc1
Codec ID/Info                            : High Efficiency Video Coding
Duration                                 : 34 s 667 ms
Bit rate                                 : 150 Mb/s
Width                                    : 3 840 pixels
Height                                   : 7 680 pixels
Display aspect ratio                     : 0.500
Frame rate mode                          : Constant
Frame rate                               : 30.000 FPS
Standard                                 : NTSC
Color space                              : YUV
Chroma subsampling                       : 4:2:0
Bit depth                                : 8 bits
Scan type                                : Progressive
Bits/(Pixel*Frame)                       : 0.170
Stream size                              : 615 MiB (99%)
Color range                              : Full
Color primaries                          : BT.709
Transfer characteristics                 : BT.709
Matrix coefficients                      : BT.709
Codec configuration box                  : hvcC

Audio
ID                                       : 2
Format                                   : AAC LC SBR
Format/Info                              : Advanced Audio Codec Low Complexity with Spectral Band Replication
Commercial name                          : HE-AAC
Format settings                          : NBC
Codec ID                                 : mp4a-40-5
Duration                                 : 34 s 646 ms
Bit rate mode                            : Constant
Bit rate                                 : 576 kb/s
Channel(s)                               : 4 channels
Channel layout                           : Ambisonics (W X Y Z)
ChannelLayout_Original                   : C L R Cb
Sampling rate                            : 48.0 kHz
Frame rate                               : 23.438 FPS (2048 SPF)
Compression mode                         : Lossy
Stream size                              : 2.38 MiB (0%)
Default                                  : Yes
Alternate group                          : 1

Other
ID                                       : 3
Type                                     : meta
Format                                   : gpmd
Codec ID                                 : gpmd
Duration                                 : 35 s 0 ms
Bit rate mode                            : Constant
Title                                    : GoPro MET
Default                                  : No
Encoded date                             : 2024-11-27 15:29:55 UTC
Tagged date                              : 2024-11-27 15:29:55 UTC
