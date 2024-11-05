<!---

This file is used to generate your project datasheet. Please fill in the information below and delete any unused
sections.

You can also include images in this folder and reference them in the markdown. Each image must be less than
512 kb in size, and the combined size of all images must be less than 1 MB.
-->

## How it works

This is WokProc, a processor coded entirely in Wokwi.  It works by "feeding" it opcodes and data via the ui[7:0] and ui[0] input pins and then executing them by toggling the uio[1] input pin.

The accumulator WokProc has an 8-bit accumulator and 4 8-bit working registers and can perform ADD, SUBTRACT and the standard logical functions AND,OR,XOR and NOT.

## How to test

## Opcodes supported:

0000_0000:  A <= A + IMM
0001_0000:  A <= A - IMM
0010_0000:  A <= A + R[1:0]
0011_0000:  A <= A - R[1:0]
0100_0000:  A <= IMM
0110_0000:  A <= R[1:0]
0110_0100:  A <= A ^ R[1:0]
0110_1000:  A <= A | R[1:0]
0110_1100:  A <= A & R[1:0]
0111_0000:  A <= Zero
0111_0001:  A <= !A
0111_0100:  A <= !R[1:0]

1000_0000:  R[1:0] <= A + IMM
1001_0000:  R[1:0] <= A - IMM
1010_0000:  R[1:0] <= A + R[2:0]
1011_0000:  R[1:0] <= A - R[2:0]
1100_0000:  R[1:0] <= IMM
1101_0000:  R[1:0] <= A
1110_0000:  R[1:0] <= R[3:2]

## Hardware needed:

Dip switches and LEDs.
