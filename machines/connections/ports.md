# Ports

Your [machine](README.md) connects to the MakerHub computer via a "serial port" (e.g., a USB cable).

## Port Names

Your computer automatically assigns a name to each port, which will generally remain the same even if the cable is reconnected.

To determine what port your machine is using, try unplugging the USB cable while looking at the port selection in MakerHub.
You should see the port name disappear from the list of available ports.

## Connection

In order to talk to your machine, the port must be opened.
A port may only be opened by one program at a time.
This means that if another program has opened the port, MakerHub will be unable to open a connection.

## Communication

MakerHub needs to know what [firmware](firmware/) the machine is using so that it knows how to communicate.
