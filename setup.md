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
mkdir -p ~/lkd_kernels/productionk
cd ~/lkd_kernels
wget https://mirrors.edge.kernel.org/pub/linux/kernel/v5.x/linux-5.10.60.tar.xz
