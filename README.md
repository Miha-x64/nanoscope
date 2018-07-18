# Nanoscope

An extremely accurate Android method tracing tool.

![](images/nanoscope.gif?raw=true)

## Overview

Nanoscope is a method tracing tool optimized for extreme accuracy. The tool's overhead has been measured at around ~20 nanoseconds per method (on a Nexus 6P). To achieve this performance, the interesting pieces of Nanoscope are implemented as a [fork of AOSP](https://github.com/uber/nanoscope-art). For this reason, **you'll need to use the Nanoscope Emulator or a device running the Nanoscope OS in order to make use of this tool**. The entrypoint for launching the Nanoscope emulator, provisioning a device with the custom OS, and starting/stopping tracing is the `nanoscope` command-line tool described below.

For more information on motivation and architecture, check out our [blog post](https://eng.uber.com/nanoscope/) and the [wiki](https://github.com/uber/nanoscope/wiki).

## Installation

**Install the `nanoscope` command**

```bash
$ brew tap uber/nanoscope
$ brew update
$ brew install nanoscope
```

## Nanoscope Emulator / Devices

Nanoscope only works with the Nanoscope Emulator or with a device that's running the Nanoscope OS.

**Launch Nanoscope Emulator**

```bash
# Prerequisites
#   - $ANDROID_HOME environment variable is set
#   - macOS

$ nanoscope emulator
```

**Flash ADB-connected phone with the Nanoscope OS**

If you want to use Nanoscope with a real device, you can execute the following command to replace your stock Android OS with the Nanoscope OS.

*IMPORTANT: This will only work with a Nexus 6P - do not attempt to flash any other device*

*IMPORTANT: This command installs a custom operating system onto the device. There is no way to undo this operation.*

```bash
# Prerequisites
#   - Nexus 6p is the only supported device at this time
#   - OEM Unlocking is enabled (Settings -> Developer Options -> OEM unlocking)
#   - Device is connected via ADB

$ nanoscope flash
```

## Usage

**Start tracing on ADB-connected device**
```bash
$ nanoscope start
Tracing... (Press ENTER to stop)
```

**Trace a specific app**
```bash
$ nanoscope start --package=com.example.app
Tracing... (Press ENTER to stop)
```

## Upgrade

**Client**
```
$ brew update && brew upgrade nanoscope
```

**OS**
```
$ brew update && brew upgrade nanoscope
$ nanoscope flash
```

## License

```
Copyright (C) 2017 Uber Technologies

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```
