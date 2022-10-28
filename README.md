## vzlogger docker image
vzlogger based on jsurf/rpi-raspbian
(https://hub.docker.com/r/jsurf/rpi-vzlogger/)

Fork of https://github.com/JSurf/docker-smartmeter-vzlogger
(https://hub.docker.com/r/jsurf/rpi-vzlogger)

### What's new
- GPIO access using sysfs is deprecated, this image is using the experimental GPIOD patch by Wolfram Richter: https://github.com/wrichter/vzlogger

### Building the image

```
# create source directory
mkdir vzlogger
cd vzlogger

# checkout this repo
git clone https://github.com/leoguiders/docker-smartmeter-vzlogger.git
cd docker-smartmeter-vzlogger

# build the image (using the tag vzlogger)
docker build -t vzlogger .

# create a config directory on your host system 
sudo mkdir /etc/vzlogger

# create a config file, see https://github.com/volkszaehler/vzlogger/blob/master/etc/vzlogger.conf for examples
sudo wget -O /etc/vzlogger/vzlogger.conf https://raw.githubusercontent.com/volkszaehler/vzlogger/master/etc/vzlogger.conf

# edit /etc/vzlogger/vzlogger.conf to your needs
...

```

### Run the container

The container needs a mounted volume in /cfg.
In this folder must be placed the vzlogger.conf

You can also passthrough the usb device with the data logger hardware connected. 
```
docker run -v /etc/vzlogger:/cfg --device=/dev/gpiochip0 --device=/dev/ttyUSB0 --name vzlogger vzlogger
```
