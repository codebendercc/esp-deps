FROM codenvy/ubuntu_jdk8


ENV ARDUINO_IDE_VERSION 1.6.7
RUN wget -q -O- https://downloads.arduino.cc/arduino-${ARDUINO_IDE_VERSION}-linux64.tar.xz | sudo tar xJ -C /opt
RUN sudo ln -s /opt/arduino-${ARDUINO_IDE_VERSION}/arduino /usr/local/bin/
RUN sudo ln -s /opt/arduino-${ARDUINO_IDE_VERSION}/arduino-builder /usr/local/bin/

ENV ARDUINO_BUILDER_HOME=/opt/arduino-${ARDUINO_IDE_VERSION}

WORKDIR /opt/arduino-${ARDUINO_IDE_VERSION}/hardware
RUN sudo mkdir esp8266com
WORKDIR /opt/arduino-${ARDUINO_IDE_VERSION}/hardware/esp8266com
RUN sudo git clone https://github.com/esp8266/Arduino.git esp8266
WORKDIR /opt/arduino-${ARDUINO_IDE_VERSION}/hardware/esp8266com/esp8266/tools
RUN sudo /usr/bin/python get.py
RUN sudo chown -R user.user /opt/arduino-${ARDUINO_IDE_VERSION}/
WORKDIR /projects