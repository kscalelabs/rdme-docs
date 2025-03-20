---
title: Teleop
deprecated: false
hidden: false
metadata:
  robots: index
---
## Requirements

* linuks-kbot v0.0.4+
* kos-kbot 0.1.3+

## Starting WebRTC stream

```Text bash
docker run --rm -it --network=host   --device=/dev/video45   --add-host xr.kscale.ai:10.33.20.104   --add-host host.docker.internal:127.0.0.1   ghcr.io/kscalelabs/gst-rs-webrtc:latest gst-launch-1.0   webrtcsink name=ws meta="meta,name=kbot-$(cat /sys/class/net/wlan0/address | tr -d ':')"   enable-control-data-channel=true signaller::uri="wss://xr.kscale.ai:8585"   v4l2src device=/dev/video45 io-mode=2 ! video/x-raw,format=YUY2,width=1280,height=1080,framerate=30/1  !   videoconvert ! videoflip method=vertical-flip ! video/x-raw,format=I420 ! ws.
```

## Teleop script

[https://github.com/kscalelabs/gst-rs-webrtc/blob/master/robot\_data\_channel.py](https://github.com/kscalelabs/gst-rs-webrtc/blob/master/robot_data_channel.py)

## VR Headset link

[https://kscale.ai/webrtcflask/www/stereo-video.html](https://kscale.ai/webrtcflask/www/stereo-video.html)