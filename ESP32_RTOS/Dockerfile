FROM codenvy/ubuntu_jdk8

RUN sudo apt-get update && sudo apt-get -y install git autoconf build-essential gperf bison flex texinfo libtool libncurses5-dev wget gawk libc6-dev-i386 python-serial libexpat-dev
RUN wget -q  https://github.com/codebendercc/esp-deps/blob/master/xtensa-esp108-elf.tar.bz2?raw=true  -O - | sudo tar -xj -C /opt

ENV ESP32_RTOS_VERSION 2.0.0
ENV ESP32_RTOS_RELEASE_DATE 16_02_26_0
RUN sudo mkdir /opt/sdks
WORKDIR /opt/sdks
RUN echo https://espressif.com/sites/default/files/sdks/esp32_rtos_sdk_v${ESP32_RTOS_VERSION}_${ESP32_RTOS_RELEASE_DATE}.zip
RUN sudo wget -q  https://espressif.com/sites/default/files/sdks/esp32_rtos_sdk_v${ESP32_RTOS_VERSION}_${ESP32_RTOS_RELEASE_DATE}.zip --no-check-certificate

RUN sudo unzip -qq esp32_rtos_sdk_v${ESP32_RTOS_VERSION}_${ESP32_RTOS_RELEASE_DATE}.zip -d /opt/sdks
RUN sudo rm esp32_rtos_sdk_v${ESP32_RTOS_VERSION}_${ESP32_RTOS_RELEASE_DATE}.zip
RUN sudo ln -s /opt/sdks/ESP32_RTOS_SDK_V${ESP32_RTOS_VERSION} /opt/ESP32_RTOS_SDK

RUN sudo chown -R user.user /opt/xtensa-esp108-elf
RUN sudo chown -R user.user /opt/sdks
RUN sudo chown -R user.user /opt/ESP32_RTOS_SDK

RUN echo "export PATH=/opt/xtensa-esp108-elf/bin:$PATH" >> /home/user/.bashrc

ENV SDK_PATH /opt/ESP32_RTOS_SDK
WORKDIR /projects
