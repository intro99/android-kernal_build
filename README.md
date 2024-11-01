:toochain
https://bitbucket.org/UBERTC/aarch64-linux-android-4.9/src/master/
:kali
https://www.kali.org/docs/nethunter/porting-nethunter-kernel-builder/
:compile guid:
https://xdaforums.com/t/reference-how-to-compile-an-android-kernel.3627297/


cd unbertc_toolchain
export CROSS_COMPILE=$(pwd)/bin/aarch64-linux-android-
export ARCH=arm64 && export SUBARCH=arm64

:::

#for test buld
cd ..
make clean
make mrproper
make <defconfig_name>
make -j$(nproc --all)

#for nethunter build:

make <defconfig_name>

make menuconfig ::(or make nconfig)

cp .config /arch/arm64/config/rosy-nethunter_defconfig

make clean && make mrproper
make rosy-nethunter_defconfig
make -j$(nproc --all) 


#anykernel3
https://github.com/osm0sis/AnyKernel3.git

::
parameters to change:
kernel.string=KernelName by YourName @ xda-developers (optional: just showes while instalation)

device.name1= (device codename) #in adb shell:: "getprop | grep device"

BLOCK=  (boot partion) #:: find /dev -name 'boot*'

IS_SLOT_DEVICE=0; ## 1 if a b partion (not applicable for rosy)


::
# to know kernal version 
cat /proc/version


::
#to zip anykernal3 (imp)

zip -r9 UPDATE-AnyKernel3.zip * -x .git README.md *placeholder

# if error :
zip -r9 UPDATE-AnyKernel3.zip * -x .git README.md *"placeholder"
