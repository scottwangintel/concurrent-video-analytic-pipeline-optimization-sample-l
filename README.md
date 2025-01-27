# Concurrent Video Analytic Pipeline Optimzation Sample 
Support users to quickly setup and adjust the core concurrent video analysis workload through configuration file to obtain the best performance of video codec, post-processing and inference based on Intel® integrated GPU according to their product requirements.
Users can use the sample application video_e2e_sample to complete runtime performance evaluation or as a reference for debugging core video workload issues.

## Typical workloads
Sample par files can be found in par_files directory. Verfied on i7-8559U. Performance differs on other platforms.
* 16 1080p H264 decoding, scaling, face detection inference, rendering inference results, composition, saving composition results to local H264 file, and display
* 4 1080p H264 decoding, scaling, human pose estimation inference, rendering inference results, composition and display
* 4 1080p H264 decoding, scaling, vehicle and vehicle attributes detection inference, rendering inference results, composition and display
* 16 1080p RTSP H264 stream decoding, scaling, face detection inference, rendering inference results, composition and display.
* 16 1080p H264 decoding, scaling, face detection inference, rendering inference results, composition and display. Plus 16 1080p H264 decoding, composition and showing on second display. 

# Dependencies
The sample application depends on [Intel® Media SDK](https://github.com/Intel-Media-SDK/), [Intel® OpenVINO™](https://software.intel.com/en-us/openvino-toolkit) and [FFmpeg](https://www.ffmpeg.org/)

# FAQ
See [FAQ](./doc/FAQ.md)

# Table of contents

  * [License](#license)
  * [How to contribute](#how-to-contribute)
  * [Documentation](#documentation)
  * [System requirements](#system-requirements)
  * [How to build](#how-to-build)
    * [Build steps](#build-steps)
  * [Known limitations](#know-limitations)

# License
The sample application is licensed under MIT license. See [LICENSE](./video_e2e_sample/LICENSE) for details.

# How to contribute
See [CONTRIBUTING](./doc/CONTRIBUTING.md) for details. Thank you!

# Documentation
See [user guide](./doc/concurrent_video_analytic_sample_application_user_guide.pdf)

# System requirements

**Operating System:**
* Ubuntu 20.04

**Software:**
* [MediaSDK 21.1.3](https://github.com/Intel-Media-SDK/MediaSDK/releases/tag/intel-mediasdk-21.1.3)
* [OpenVINO™ 2021.4](https://software.intel.com/en-us/openvino-toolkit)

**Hardware:** 
* Intel® platforms supported by the MediaSDK 21.1.3 and OpenVINO 2021.4. 
* For Media SDK, the major platform dependency comes from the back-end media driver. https://github.com/intel/media-driver
* For OpenVINO™, see details from here: https://software.intel.com/en-us/openvino-toolkit/documentation/system-requirements

# How to build

Run build_and_install.sh to install dependent software packages and build sample application video_e2e_sample. 

Please refer to ”Installation Guide“ in [user guide](./doc/concurrent_video_analytic_sample_application_user_guide.pdf) for details.

## Build steps

Get sources with the following git command: 
```sh
git clone https://github.com/intel-iot-devkit/concurrent-video-analytic-pipeline-optimization-sample-l.git cva_sample 
```

```sh
cd cva_sample 
./build_and_install.sh
```
This script will install the dependent software packages by running command "apt install". So it will ask for sudo password. Then it will download libva, libva-util, media-driver and MediaSDK source code and install these libraries. It might take 10 to 20 minutes depending on the network bandwidth.

After the script finishing, the sample application video_e2e_sample can be found under ./bin.

In order to enable the media SDK installed by SVET to coexist with different versions of media SDK installed on the same computer, we suggest (we have done so in our build script) that the media SDK environment variables of SVET should only be set in the current bash, not saved to the global system environment.
So please run 'source ./svet_env_setup.sh' first when you start a new shell (or change user in shell such as run 'su -') to run ./bin/video_e2e_sample".

```sh
cd cva_sample
source ./svet_env_setup.sh
```
Please refer to "Run sample application" in [user guide](./doc/concurrent_video_analytic_sample_application_user_guide.pdf) for details.

# Known limitations

The sample application has been validated on Intel® platforms Skylake(i7-6770HQ), Coffee Lake(i7-8559U i7-8700), Whiskey Lake(i7-8665UE) and Tiger Lake U(i7-1185G7E, i5-1135G7E).


