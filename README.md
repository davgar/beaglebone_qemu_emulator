# beaglebone_qemu_emulator

The following instructions should work in Windows, OS X, and Linux the same.

** all commands are issued from a command prompt/terminal

1. Install Vagrant and Virtual Box
2. Create a folder and within the folder enter "vagrant init boxcutter/debian82-i386; vagrant up --provider virtualbox"
3. Once it is finished downloading and says machine booted ready type to enter the vagrant ssh
4. Run the following commands sudo apt-get update and sudo apt-get upgrade
5. sudo apt-get install gcc and g++ build-essential flex bison dh-autoreconf gdisk libglib2.0-dev zlib1g-dev libpixman-1-dev libfdt-dev git linaro-image-tools qemu-system
6. sudo apt-get remove qemu-system-arm
6. mkdir downloads 
7. cd downloads
8. wget http://releases.linaro.org/platform/linaro-n/nano/final/linaro-natty-nano-tar-20110527-1.tar.gz
9. wget http://releases.linaro.org/platform/linaro-n/nano/final/hwpack_linaro-omap3_20110526-1_armel_supported.tar.gz
10. cd ..
11. mkdir linaro
12. cd linaro
13. git clone git://git.linaro.org/qemu/qemu-linaro.git
14. cd qemu-linaro
15. mkdir build
16. cd build
17. ../configure --prefix=/opt --target-list=arm-softmmu --enable-kvm
18. make -j8
19. sudo make install
20. ../../../downloads/
21. sudo linaro-media-create --image_file beagle_sd.img --dev beagle --binary linaro-natty-nano-tar-20110527-1.tar.gz --hwpack hwpack_linaro-omap3_20110526-1_armel_supported.tar.gz
22. sudo /opt/bin/qemu-system-arm -M beagle -m 256 -sd ./beagle_sd.img -clock unix -serial stdio
23. At this point you should be logged into the newly created image. 


Sources :
http://stackoverflow.com/questions/28564692/set-up-beagleboard-emulator-with-qemu-in-ubuntu
http://www.cnx-software.com/2011/09/26/beagleboard-emulator-in-ubuntu-with-qemu/
