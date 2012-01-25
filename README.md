# Use (Linux) PC as a terminal for N9 #

N9 virtual keyboard and small screen are useless for any serious work,
but it isw a convenient way to carry a Linux work environment around 
with you. When writing software for N9, it would be nice to debug and try 
out new things on actual device with proper keyboard and screen.

It would be nice to have a simple way to turn a PC laying around a terminal
for N9. This project tries to make it as easy as possible.

## Design ##

N9 provides many ways to connect to it. There is SDK mode over USB. 
I haven't use it, but I guess it is basically serial terminal connection 
because USB has serial port profile. N9 has bluetooth, which has at least
keyboard HID profile, but I don't know if it is supported by N9. Also, AFAIK 
there is no display profile. You can still have terminal connection over bt.

N9 has internet connection over wifi or 3G. To simplify things, we will 
only use wifi because 3G would require traversing public internet and possibly
multiple firewalls/NATs. (Or access to operator network, which isn't any 
simpler.) Two most common methods for connecting teerminal over TCP/IP network
are SSH and VNC. Since N9 already has sshd, using SSH and X11 forwarding is 
the first approach.

We have ended up with following solution: N9 and our PC is in the same wifi
network and we will make an ssh connection (with X11 forwarding) from N9 to PC.

## Configuration ##

1. Connect PC to wifi
2. Connect N9 to same wifi
3. find out N9 IP address
4. ssh to that address

