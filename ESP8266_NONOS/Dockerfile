FROM codenvy/ubuntu_jdk8

RUN sudo apt-get update && sudo apt-get -y install git autoconf build-essential gperf bison flex texinfo libtool libncurses5-dev wget gawk libc6-dev-i386 python-serial libexpat-dev
RUN wget -q  https://github.com/codebendercc/esp-deps/blob/master/xtensa-lx106-elf-ccf1cfd2.tar.bz2?raw=true  -O - | sudo tar -xj -C /opt

ENV ESP8266_NONOS_VERSION 1.5.4
ENV ESP8266_nonos_RELEASE_DATE 16_05_20
RUN sudo mkdir /opt/sdks
WORKDIR /opt/sdks
RUN echo https://espressif.com/sites/default/files/sdks/esp8266_nonos_sdk_v${ESP8266_NONOS_VERSION}_${ESP8266_nonos_RELEASE_DATE}.zip
RUN sudo wget -q  https://espressif.com/sites/default/files/sdks/esp8266_nonos_sdk_v${ESP8266_NONOS_VERSION}_${ESP8266_nonos_RELEASE_DATE}.zip --no-check-certificate

RUN sudo unzip -qq esp8266_nonos_sdk_v${ESP8266_NONOS_VERSION}_${ESP8266_nonos_RELEASE_DATE}.zip -d /opt/sdks
RUN sudo rm esp8266_nonos_sdk_v${ESP8266_NONOS_VERSION}_${ESP8266_nonos_RELEASE_DATE}.zip
RUN sudo ln -s /opt/sdks/ESP8266_NONOS_SDK /opt/ESP8266_NONOS_SDK

RUN sudo chown -R user.user /opt/xtensa-lx106-elf
RUN sudo chown -R user.user /opt/sdks
RUN sudo chown -R user.user /opt/ESP8266_NONOS_SDK

RUN echo "export PATH=/opt/xtensa-lx106-elf/bin:$PATH" >> /home/user/.bashrc

ENV SDK_PATH /opt/ESP8266_NONOS_SDK
WORKDIR /projects
