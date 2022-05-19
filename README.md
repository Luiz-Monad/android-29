# Docker for Android SDK 29

Docker for Android SDK 29 with preinstalled build tools and emulator image

> Edit from [mindrunner/docker-android-sdk](https://github.com/mindrunner/docker-android-sdk)

**Installed Packages**
```bash
# sdkmanager --list_installed
  Path                                        | Version      | Description                                | Location                                   
  -------                                     | -------      | -------                                    | -------                                    
  build-tools;30.0.2                          | 30.0.2       | Android SDK Build-Tools 30.0.2             | build-tools/30.0.2                         
  cmake;3.18.1                                | 3.18.1       | CMake 3.18.1                               | cmake/3.18.1                               
  cmdline-tools;latest                        | 7.0          | Android SDK Command-line Tools (latest)    | cmdline-tools/latest                       
  emulator                                    | 31.2.10      | Android Emulator                           | emulator                                   
  ndk;22.1.7171670                            | 22.1.7171670 | NDK (Side by side) 22.1.7171670            | ndk/22.1.7171670                           
  patcher;v4                                  | 1            | SDK Patch Applier v4                       | patcher/v4                                 
  platform-tools                              | 33.0.1       | Android SDK Platform-Tools                 | platform-tools                             
  platforms;android-29                        | 5            | Android SDK Platform 29                    | platforms/android-29                       
  system-images;android-29;google_apis;x86_64 | 12           | Google APIs Intel x86 Atom_64 System Image | system-images/android-29/google_apis/x86_64
```

**Usage**

- Interactive way
  ```bash
  $ docker run -it --rm --device /dev/kvm luizfelipestangarlin/debian-android-sdk-ndk:29-22.1.7171670 bash
  # check installed packages
  $ sdkmanager --list
  # create and run emulator
  $ avdmanager create avd -n first_avd --abi google_apis/x86_64 -k "system-images;android-29;google_apis;x86_64"
  $ emulator -avd first_avd -no-window -no-audio &
  $ adb devices
  # You can also run other Android platform tools, which are all added to the PATH environment variable
  ```

  To connect the emulator using `adb` on the docker host machine, start the container with `--network host`.
  You could also use [`scrcpy`](https://github.com/Genymobile/scrcpy) to do a screencast of the emulator.

- Non-interactive way
  ```bash
  # check installed packages
  $ docker run -it --rm luizfelipestangarlin/debian-android-sdk-ndk:29-22.1.7171670 sdkmanager --list_installed
  # list existing emulators
  $ docker run -it --rm luizfelipestangarlin/debian-android-sdk-ndk:29-22.1.7171670 avdmanager list avd
  # You can also run other Android platform tools, which are all added to the PATH environment variable
  ```
