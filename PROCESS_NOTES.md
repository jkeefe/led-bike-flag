# LED Bike Flag process notes

Notes along my exploration. Not documentation. Proceed with caution.

## Hardware

Plan to use the Trinket Pro 5V 16 mhz I have.

- [Pinout](https://learn.adafruit.com/introducing-pro-trinket/pinouts)
- [Guide](https://learn.adafruit.com/introducing-pro-trinket/guided-tour)

While riding, going to run this from a USB pack.

- Power through mini USB
- Colors will cycle through a set pattern
- LEDs running off 5V, GND and a data pin

While parked, plan to use attached LiPo battery.

- Power from LiPo goes to BAT+
- Inline on/off switch will be on that line
- Separate analog switch will flag to go through the sleep/wake cycle
- Trinket automatically detects which power source to use, drawing from the higher voltage

## Software

In sleep/wake mode, plan is to wake every 2 minutes and do a recognizable pattern/color for 1 minute.

To do so, we'll use the [Arduino Low Power library](https://github.com/rocketscream/Low-Power/blob/master/Examples/powerDownWakePeriodic/powerDownWakePeriodic.ino)

Every 8 seconds (the max available with the watchdog timer), code will increment the `sleep_increment` varialbe: 15 rounds of 8 seconds is 2 minutes.

After 60000 milliseconds, `sleep_increment` gets set to zero and we power down again.




