FROM codenvy/ubuntu_jdk8


ENV ARDUINO_IDE_VERSION 1.6.7
RUN wget -q -O- https://downloads.arduino.cc/arduino-${ARDUINO_IDE_VERSION}-linux64.tar.xz | sudo tar xJ -C /opt
RUN sudo ln -s /opt/arduino-${ARDUINO_IDE_VERSION}/arduino /usr/local/bin/
RUN sudo ln -s /opt/arduino-${ARDUINO_IDE_VERSION}/arduino-builder /usr/local/bin/

ENV ARDUINO_BUILDER_HOME=/opt/arduino-${ARDUINO_IDE_VERSION}

WORKDIR /opt/arduino-${ARDUINO_IDE_VERSION}/hardware
RUN sudo wget -q  https://github.com/esp8266/Arduino/releases/download/2.3.0/esp8266-2.3.0.zip
RUN sudo unzip -qq esp8266-2.3.0.zip  && sudo rm esp8266-2.3.0.zip
RUN sudo mvesp8266-2.3.0 esp8266
WORKDIR /opt/arduino-${ARDUINO_IDE_VERSION}/hardware/esp8266
RUN sudo /usr/bin/sh tools/get.py
RUN sudo chown -R user.user /opt/arduino-${ARDUINO_IDE_VERSION}/
WORKDIR /projects