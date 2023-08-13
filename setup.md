#!/bin/bash

#Packt Publishing https://github.com/PacktPublishing/Linux-Kernel-Debugging

#norm
#sudo apt-get update -y 

#whats needed for kern debugging
#sudo apt-get install -y bison flex libncurses5-dev ncurses-dev xz-utils libssl-dev libelf-dev util-linux tar git

#grab the repo
#git clone https://github.com/PacktPublishing/Linux-Kernel-Debugging

#whats needed for entire the book
sudo apt-get install -y bc bpfcc-tools bsdmainutils clang cmake cppcheck cscope curl dwarves exuberant-ctags fakeroot flawfinder gnome-system-monitor gnuplot \
hwloc indent kernelshark libnuma-dev libjson-c-dev linux-tools-$(uname -r) net-tools numactl openjdk-16-jre openssh-server perf-tools-unstable psmisc \
python3-distutils rt-tests smem sparse stress sysfsutils tldr-py trace-cmd tree tuna virt-what -y

#Optionsal: set up qemu
#sudo apt install git
#git clone https://gitlab.com/qemu-project/qemu.git
#cd qemu
#git submodule init
#git submodule update --recursive
#./configure
#make

#set up kernel production env 
#mkdir -p ~/lkd_kernels/productionk
#cd ~/lkd_kernels
#wget https://mirrors.edge.kernel.org/pub/linux/kernel/v5.x/linux-5.10.60.tar.xz

#define a tuned starting point for kern config. 
#lsmod > /tmp/lsmod.now
#make LSMOD=/tmp/lsmod.now localmodconfig
#This is prompt you for input, leave all default.

#Secure Prod Kernel:
#checker: https://github.com/a13xp0p0v/kconfig-hardened-check

#cd to kernel dr and run
make -j24 (24 jobs, nproc will show available cores. double this number)
#This will create a bzImage. 
#BUILD   arch/x86/boot/bzImage
#vmlinux  houses all the symbolic information.

#Run this in qemu.
#create .img spaceholder:
#qemu-img create -f qcow2 ubuntu20.qcow2 30G

#run qemu:
#https://itsfoss.com/qemu-ubuntu/
#make image:
#qemu-img convert kali-linux-2023.2-live-amd64.iso kali.qcow2
#qemu-system-x86_64 -enable-kvm -m 4G -smp 2 -hda /home/auxytocin/Documents/myVirtualDisk.qcow2 -boot d -cdrom /home/auxytocin/Documents/kali.qcow2 -vga qxl
#Qubes should not be installed in virtualization. 
#works - but still needs a partition for installtion. 

#setting up network in qemu
#https://ahelpme.com/linux/howto-do-qemu-full-virtualization-with-bridged-networking/
