Device configuration for the Samsung Galaxy Alpha

Copyright (C) 2014-2015 The LineageOS Project

Copyright (C) 2017      The LineageOS Project

Copyright (C) 2014-2017 Andreas Schneider <asn@cryptomilk.org>

 Licensed under the Apache License, Version 2.0 (the "License");
 you may not use this file except in compliance with the License.
 You may obtain a copy of the License at

      http://www.apache.org/licenses/LICENSE-2.0

------------------------------------------------------------------

* Description

  This repository is for LineageOS 15.0 on Samsung Galaxy Alpha (slte)

    THIS IS WORK IN PROGRESS.


* How To Build LineageOS 15.0 for Samsung Galaxy Alpha

  - Make a workspace

```
  $ mkdir -p ~/android/lineage
  $ cd ~/android/lineage
```

  - Do repo init & sync

```
  $ repo init -u https://github.com/LineageOS/android.git -b lineage-15.0 --git-lfs --no-clone-bundle
```
  
  - Create .repo/local_manifests/roomservice.xml with the following content:

```
  <?xml version="1.0" encoding="UTF-8"?>
  <manifest>
      <remote  name="trlef" fetch="https://github.com/trlef19" />
      <project name="omnirom/android_bootable_recovery" path="bootable/recovery-twrp" remote="github" revision="android-8.0" />
      <project name="LineageOS/android_external_stlport" path="external/stlport" remote="github" />
      <project name="LineageOS/android_packages_apps_SamsungServiceMode" path="packages/apps/SamsungServiceMode" remote="github" />
      <project name="LineageOS/android_hardware_samsung" path="hardware/samsung" remote="github" />
      <project name="LineageOS/android_hardware_samsung_slsi_exynos" path="hardware/samsung_slsi/exynos" />
      <project name="LineageOS/android_hardware_samsung_slsi_exynos5" path="hardware/samsung_slsi/exynos5" />
      <project name="LineageOS/android_hardware_samsung_slsi_openmax" path="hardware/samsung_slsi/openmax" />
      <project name="android_hardware_samsung_slsi_exynos5430" path="hardware/samsung_slsi/exynos5430" remote="trlef" />
      <project name="android_kernel_samsung_slte" path="kernel/samsung/slte" remote="trlef" />
      <project name="android_device_samsung_sltexx" path="device/samsung/sltexx" remote="trlef" />
      <project name="proprietary_vendor_samsung_sltexx" path="vendor/samsung/sltexx" remote="trlef" revision="lineage-18.1"/>
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



  - If you ever need to copy proprietary vendor files

  There are two options to to that. Connect your device with adb enabled and run:

```
    ./extract-files.sh
```
  Or if you have the system image unpacked on your disk, then simply run:

```
    STOCK_ROM_DIR=/path/to/system ./extract-files.sh
```

* Thanks to

  LineageOS
  TeamWin

----
EOF
