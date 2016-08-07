# alexa-echo-raspi
Facts and configuration for my Raspberry PI/Raspberry Pi Zero and Amazon Alexa SDK

## Static IP in local network (lastest RASPBIAN JESSIE):

```
sudo vim /etc/wpa_supplicant/wpa_supplicant.conf
```
```
network={
        ssid="########"
        psk="######################"
        key_mgmt=WPA-PSK
}
```

```
sudo vim /etc/dhcpcd.conf
```
```
interface eth0
static ip_address=192.168.1.101/24
static routers=192.168.1.1
static domain_name_servers=8.8.8.8 8.8.4.4
static domain_search=

interface wlan0
inform 192.168.1.101/24
static routers=192.168.1.1
static domain_name_servers=8.8.8.8 8.8.4.4
```

## Devices

Raspberry Pi 2.0 Model B:
https://www.raspberrypi.org/products/raspberry-pi-2-model-b/

Raspberry Pi Zero:
https://www.raspberrypi.org/products/pi-zero/

## Audio output/input

None of Raspberry Pi have input audio. The Zero has limited number of inputs.
To provide output/input for Audio I'm using Sound Blaster Play! 2 external USB card:

[![](https://cloud.githubusercontent.com/assets/14539/17273055/44645fde-56a8-11e6-9ab8-fc1ff68f6b94.png)](https://cloud.githubusercontent.com/assets/14539/17273055/44645fde-56a8-11e6-9ab8-fc1ff68f6b94.png 'Sound Blaster Play! 2')

### Speaker
Creative Labs Woof v.3:
http://us.creative.com/p/speakers/creative-woof-3
![Creative Labs Woof](http://d287ku8w5owj51.cloudfront.net/inline/products/22600/Woof3_lifestyle_1.jpg)

### Microphone

A cheap USB microphone with tripod:

![TRUST Starzz](https://stat-s3.ms-online.pl//media/cache/gallery_1090_800/rc/i8JoIdsD/bdk/47/477338_0.jpg)

## Amazon SDK examples

Amazon's Java :disappointed: SDK examples fails on setup:
```
line with format PCM_SIGNED 16000.0, 16 bit, mono, 2 bytes/frame, little-endian not supported
```
The mike and speaker are available for system `arecord` and related tools but not in Java SDK.
See: https://github.com/amzn/alexa-avs-raspberry-pi/issues?q=is%3Aissue+mono+label%3APCM_SIGNED


> NOTE: There are ways to configure audio device on Linux: https://gist.github.com/peterblazejewicz/f6c14c3a6f7b78ab820399d856e9bbd7 and https://gist.github.com/peterblazejewicz/f6c14c3a6f7b78ab820399d856e9bbd7


Also view this video for useful bits on external sound card usage on Pi:

<iframe width="854" height="480" src="https://www.youtube.com/embed/6fAdBehSYiA" frameborder="0" allowfullscreen></iframe>

## Author
@peterblazejewicz
