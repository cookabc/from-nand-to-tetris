### 13.1 Hardware Realizations
---



&emsp;&emsp;Every hardware module presented in the book was software-based and HDLSIMULATED. This, in fact, is how hardware is actually designed. However, at some point the HDL designs are committed to silicon, becoming “real computers.” Wouldn’t it be nice to make Hack or Jack also run on some “real platform,” made from some “real stuff”? Several different approaches may be taken towards this goal. On one extreme, you can attempt to nearly directly fabricate a real chip using the existing HDL design of Hack, and then deal with implementation issues related to the RAM, ROM, and I/O devices. Another extreme approach may be to attempt emulation (of either Hack, the VM, or even the Jack platform) on some existing hardware device like a cell phone or a PDA. It seems that any such project would want to reduce the size of the Hack screen as to keep the cost of the hardware resources reasonable.
