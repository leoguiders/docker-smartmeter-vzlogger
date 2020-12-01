## vzlogger docker image
vzlogger based on jsurf/rpi-raspbian
(https://hub.docker.com/r/jsurf/rpi-vzlogger/)

Fork of https://github.com/treban/docker-smartmeter-vzlogger
(https://hub.docker.com/r/treban/smartmeter-vzlogger-rpi/)

### Pull the image

docker pull jsurf/rpi-vzlogger

### Run the container

The container needs a mounted volume in /cfg.
In this folder must be placed the vzlogger.conf

You can also passthrough the usb device with the data logger hardware connected. 

docker run -i -t -v /path-to-data-on-host:/cfg --device=/dev/ttyUSB0 jsurf/rpi-vzlogger

