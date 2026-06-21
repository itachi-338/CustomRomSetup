# SETUP
1. [VIPER 4 ANDROID](https://github.com/AxionAOSP/android_packages_apps_ViPER4AndroidFX)
2. [MIUI Camera Marble](https://github.com/Chaitanyakm/device_xiaomi_marble/commit/f873761bbb3167a3ff9e4235fd29949f0ab97d9e)
3. [MIUI Camera Garnet](https://github.com/Evolution-X-Devices/device_xiaomi_garnet/commit/8727e2b04e007876604d6e44b22acf8d37e3cd79)
4. [AOSP Surfaceflinger](https://github.com/Evolution-X-Devices/device_xiaomi_garnet/commit/f4a5a26fd2c9b10a852c07968929a4f704a8c464)
5. [Refresh Rate Switch](https://github.com/kleidione/device_xiaomi_garnet/commit/740c5494d65cea96313bba84159f0fce8f2695bd)
6. [KSU Next Installation](https://kernelsu-next.github.io/webpage/pages/installation.html)
7. [FW Navigation Bar](https://github.com/crdroidandroid/android_frameworks_base/commit/b72c91dfd8142632763a8058e8f05b3d6377b2fa)
8. [Settings Navigation Bar](https://github.com/crdroidandroid/android_packages_apps_Settings/commit/94a94f250789ce3189a046bc838837fb31c2bca1)


## VENDOR PROP CHANGES(REPLACE/ADD/REMOVE)
```make
debug.sf.disable_client_composition_cache=0
debug.sf.enable_gl_backpressure=0
debug.sf.frame_rate_multiple_threshold=120
debug.sf.latch_unsignaled=0
vendor.perf.framepacing.enable=1


# hwui
debug.sf.enable_adpf_cpu_hint=true
ro.hwui.render_ahead=3
debug.hwui.use_hint_manager=true
debug.hwui.target_cpu_time_percent=30
```
## SYSTEM PROP CHANGES(REPLACE/ADD/REMOVE)
```make
# Animation override
persist.sys.activity_anim_perf_override=true
```

## SIGN ROMS
```make
git clone https://github.com/LineageOS/scripts.git
```
```make
mkdir -p vendor/lineage-priv/keys && cp -a scripts/lineage-priv-template/. vendor/lineage-priv/keys/
```
```make
cd vendor/lineage-priv/keys
```
```make
./keys.sh
```
```make
# Sign Keys (device.mk)
-include vendor/lineage-priv/keys/keys.mk
```


## CHANGE DISPLAY DENSITY
```make
400
```

## FLAGS
```make
# OTHER ROMS
TARGET_DISABLE_EPPE := true
TARGET_ENABLE_BLUR := true
PRODUCT_NO_CAMERA := true
TARGET_EXCLUDES_AUDIOFX := true
WITH_GMS := false
TARGET_DISABLE_MATLOG := true
TARGET_BOOT_ANIMATION_RES := 1080

# AXION
TARGET_DISABLE_EPPE := true
TARGET_ENABLE_BLUR := true
TARGET_INCLUDE_AXFX := true
AXION_CAMERA_REAR_INFO := 64
AXION_CAMERA_FRONT_INFO := 16
AXION_MAINTAINER := Naitik
AXION_PROCESSOR := Snapdragon
```

## OTHER

**initialize the repo:**
```make
--depth 1 --no-repo-verify -g default,-mips,-darwin,-notdefault
```

**sync repo:**
```make
repo sync -c --no-clone-bundle --no-tags --optimized-fetch --prune --force-sync -j
```

**environment setup:**
```make
. build/envsetup.sh
```

**Lunch BP4A**
```make
lunch lineage_marble-bp4a-user
lunch lineage_garnet-bp4a-user
lunch lineage_vayu-bp4a-user
```


**DISABLE RBE**
```make
USE_RBE=false mka bacon -j96
```
