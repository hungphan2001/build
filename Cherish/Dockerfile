# Import Ubuntu 18.04 Image
FROM ubuntu:18.04

# Install dependencies
RUN apt-get update
RUN DEBIAN_FRONTEND=noninteractive apt-get install bison repo libssl-dev build-essential curl flex git gnupg gperf liblz4-tool libncurses5-dev libsdl1.2-dev libxml2 libxml2-utils lzop pngcrush schedtool squashfs-tools xsltproc zip zlib1g-dev build-essential kernel-package libncurses5-dev bzip2 git python sudo gcc g++ openssh-server tar gzip ca-certificates -y

RUN apt-get purge openjdk-8-jdk openjdk-8-jre openjdk-11-jdk openjdk-11-jre -y

RUN apt-get install openjdk-8-jdk openjdk-8-jre -y

RUN rm -rf /var/lib/apt/lists/*

# Link Timezone
RUN ln -sf /usr/share/zoneinfo/Asia/Ho_Chi_Minh /etc/localtime

# Add User
# Why? Well for avoid something wrong
# I've seen some notes for not using root when build
RUN useradd -ms /bin/bash hungphan2001
RUN echo "hungphan2001 ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers
USER hungphan2001
WORKDIR /home/hungphan2001

# Git
RUN git config --global user.email "phandinhhungvp2001@gmail.com"
RUN git config --global user.name "hungphan2001"
RUN git config --global color.ui false

RUN sudo git clone https://github.com/akhilnarang/scripts /scripts

RUN cd /scripts && bash setup/android_build_env.sh && bash setup/install_android_sdk.sh
