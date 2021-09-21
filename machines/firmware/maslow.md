# Maslow Firmware

The Maslow CNC is unique for its vertically-mounted hanging-pendant (chain) design.

## Two Types of "Maslow"

The Maslow CNC was originally designed for use with the [Arduino Mega](https://store.arduino.cc/products/arduino-mega-2560-rev3).
Later, MakerMade released the "M2" (a Maslow machine built on the [Arduino Due](https://store-usa.arduino.cc/products/arduino-due)).
MakerHub supports both versions, but requires that you choose the appropriate type.
If you are not sure which you own, click on the links in this paragraph to compare your [board](../hardware/board.md) to pictures of the two different versions.

## Unique Considerations

Because of the pendant design, Maslow-style machines lack fixed axes.
When the left or right motor moves, the machine actually moves in **both** the X and Y axis.
Moreover, the use of chains and a [sled](../hardware/sled) means that there is also [catenary](https://en.wikipedia.org/wiki/Catenary) to take into account, such that the actual position of the machine must be computed advanced techiques.
