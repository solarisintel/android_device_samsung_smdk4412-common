# Initialize local repository
$ repo init -u git://github.com/LineageOS/android.git -b lineage-16.0

# Sync
$ repo sync -j16 --current-branch --no-tags --force-sync

# Replace system files
  
bionic  
$ git clone -b lineage-16.0 --single-branch https://github.com/CustomROMs/android_bionic.git --depth 1  
$ rm -rf bionic  
$ mv android_bionic bionic  
  
frameworks/base  
$ git clone -b lineage-16.0 --single-branch https://github.com/CustomROMs/android_frameworks_base.git --depth 1  
$ rm -rf frameworks/base  
$ mv android_frameworks_base frameworks/base  
  
frameworks/native  
$ git clone -b lineage-16.0 --single-branch https://github.com/CustomROMs/android_frameworks_native.git --depth 1  
$ rm -rf frameworks/native  
$ mv android_frameworks_native frameworks/native  
  
frameworks/opt/telephony   
$ git clone -b lineage-16.0 --single-branch https://github.com/CustomROMs/android_frameworks_opt_telephony.git --depth 1  
$ rm -rf frameworks/opt/telephony  
$ mv android_frameworks_opt_telephony frameworks/opt/telephony  

hardware/samsung   
$ git clone -b lineage-16.0 --single-branch https://github.com/CustomROMs/android_hardware_samsung.git --depth 1  
$ rm -rf hardware/samsung  
$ mv android_hardware_samsung hardware/samsung 

# gnss interface modules do not refer device/xxx/include/hardware
$ cp device/samsung/sc03e/include/hardware/gps.h   hardware/libhardware/include/hardware

# Set up environment
$ source build/envsetup.sh

# Choose a target, build
$ blunch sc03e
