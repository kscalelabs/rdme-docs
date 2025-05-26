---
title: Electronic Components
deprecated: false
hidden: false
metadata:
  robots: index
---
### Electronics

The power board distributes the power from the input, be that battery or power supply, to the limbs.

Supply power at 48 volts. For the current there are spikes that can reach up to 50A, which the battery can provide. But if just using for manipulation (rather than locomotion) a power supply reaching up 20A, such as [this one](https://www.amazon.com/NICE-POWER-Variable-Adjustable-Switching-Regulated/dp/B0F4CYF5XB/ref=sr_1_3), should suffice. THere is also an output of 24V (labeled below) that can be used to power the head via a XT30 to barrel jack (5.5x2.1mm DC power jack). The plugs are XT60 for the 48V lines and XT30 for the 24V.

<Image align="center" src="https://files.readme.io/55eaa1319a126cf3a62a5d013654ebede9faa52276cd61d2b6a55baddb843c19-IMG_7191.JPG.jpeg" />

The CAN to usb board takes the CAN bus from the actuators and converts it to a USB C output that communicates with the compute in the head using serial. Plug in the USB C to the port on the back of the head.

<Image align="center" src="https://files.readme.io/418372a59e7db6cec2f6ccc2857946a7758dbb48a721a4ffe3bb2daf1d5f5cc3-IMG_7190.JPG" />