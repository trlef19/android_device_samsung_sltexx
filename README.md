Device configuration for the Samsung Galaxy Alpha

Copyright (C) 2014-2015 The LineageOS Project
Copyright (C) 2017      The LineageOS Project
Copyright (C) 2014-2017 Andreas Schneider <asn@cryptomilk.org>

 Licensed under the Apache License, Version 2.0 (the "License");
 you may not use this file except in compliance with the License.
 You may obtain a copy of the License [here](http://www.apache.org/licenses/LICENSE-2.0)

------------------------------------------------------------------

* Description

  This repository is for LineageOS 18.1 on Samsung Galaxy Alpha (slte)

    **THIS IS WORK IN PROGRESS.**


* How To Build LineageOS 18.1 for Samsung Galaxy Alpha

  - Make a workspace

  ```
  $ mkdir -p ~/android/lineage
  $ cd ~/android/lineage
  ```


  - Do repo init & sync

  ```
  $ repo init -u git://github.com/LineageOS/android.git -b ineage-18.1 --git-lfs --no-clone-bundle
  ```
  
  - Create .repo/local_manifests/roomservice.xml with the following content:
```
<?xml version="1.0" encoding="UTF-8"?>
 <manifest>
        <remote name="local" fetch="https://github.com/trlef19" />
        <remote name="los" fetch="https://github.com/LineageOS" />
        <remote name="them" fetch="https://github.com/TheMuppets" />
        <project name="omnirom/android_bootable_recovery" path="bootable/recovery-twrp" remote="github" revision="android-11" />
        <!--project name="android_external_stlport" path="external/stlport" remote="los" /-->
        <project path="device/samsung/sltexx" name="android_device_samsung_sltexx" remote="local"/>
        <project path="packages/apps/SamsungServiceMode" name="android_packages_apps_SamsungServiceMode" remote="los" revision="cm-14.1"/>
        <project path="hardware/samsung" name="android_hardware_samsung" remote="los"/>
        <project path="hardware/samsung_slsi/exynos" name="android_hardware_samsung_slsi_exynos" remote="los"/>
        <project path="hardware/samsung_slsi/exynos5" name="android_hardware_samsung_slsi_exynos5" remote="los"/>
        <project path="hardware/samsung_slsi/openmax" name="android_hardware_samsung_slsi_openmax" remote="los"/>
        <project path="hardware/samsung_slsi/exynos5430" name="android_hardware_samsung_slsi_exynos5430" remote="local"/>
        <project path="kernel/samsung/slte" name="android_kernel_samsung_slte" remote="local"/>
        <project path="vendor/samsung" name="proprietary_vendor_samsung" revision="cm-14.1" remote="them" />
 </manifest>
  ```
  ```
  $ repo sync
  ```
  
  - Setup environment

 ```
  $ source build/envsetup.sh
  $ lunch lineage_sltexx-userdebug
 ```

  - Build LineageOS

```
  $ export USE_CCACHE=1
  $ make -j10 bacon
```

* Thanks to

  LineageOS
  TeamWin

----
EOF
