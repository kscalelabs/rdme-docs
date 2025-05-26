---
title: K-Bot
excerpt: An overview of the K-Bot hardware
deprecated: false
hidden: false
metadata:
  robots: index
---
![](https://files.readme.io/d46d39701961f72ee8b71cea1518ce2cc56a6e4dfcbfca9014336ce113cc7594-image.png)

<br />

<Cards columns={3}>
  <Card title="K-Bot Monorepo" href="https://github.com/kscalelabs/kbot" icon="fa-home" target="_blank">
    The main repository for K-Bot software and hardware
  </Card>

  <Card title="K-OS" href="https://github.com/kscalelabs/kos-kbot" icon="fa-user">
    The K-OS backend for K-Bot
  </Card>

  <Card title="K-Sim" href="https://github.com/kscalelabs/ksim-kbot" icon="fa-star">
    Policy training and deployment code for K-Bot
  </Card>
</Cards>

## Motor ID Mapping

Motors each have their own unique CAN ID. We use a consistent naming convention to make development easier.

<Image align="center" src="https://files.readme.io/ffef29a195fd46c11adf0da1ef05837b06cb454d57814b4c484b2d688b224df8-kbot.jpg" />

<br />

<br />

### Electronics

The power board distributes the power from the input, be that battery or power supply, to the limbs.

Supply power at 48 volts. For the current there are spikes that can reach up to 50A, which the battery can provide. But if just using for manipulation (rather than locomotion) a power supply reaching up 20A, such as [this one](https://www.amazon.com/NICE-POWER-Variable-Adjustable-Switching-Regulated/dp/B0F4CYF5XB/ref=sr_1_3), should suffice. THere is also an output of 24V (labeled below) that can be used to power the head via a XT30 to barrel jack (5.5x2.1mm DC power jack). The plugs are XT60 for the 48V lines and XT30 for the 24V.

<Image align="center" src="https://files.readme.io/55eaa1319a126cf3a62a5d013654ebede9faa52276cd61d2b6a55baddb843c19-IMG_7191.JPG.jpeg" />

<br />

The CAN to usb board takes the CAN bus from the actuators and converts it to a USB C output that communicates with the compute in the head using serial. Plug in the USB C to the port on the back of the head.

<Image align="center" src="https://files.readme.io/418372a59e7db6cec2f6ccc2857946a7758dbb48a721a4ffe3bb2daf1d5f5cc3-IMG_7190.JPG" />

<br />

<br />

### The Head

Early prototype of the K-Bot has a raspberry pi in the head, but will be changed out to a nvidia board prior to shipment. For testing with the prototype units, the raspberry pi has a default raspberry os. Once powered on you should see the GUI pop up on the head screen and plug in usb mouse and keyboard using the usb c port in the back.