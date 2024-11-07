<!---

This file is used to generate your project datasheet. Please fill in the information below and delete any unused
sections.

You can also include images in this folder and reference them in the markdown. Each image must be less than
512 kb in size, and the combined size of all images must be less than 1 MB.
-->

## What is WocProc Trainer?

WocProc Trainer is a partial CPU implementation coded entirely in Wokwi!  While it is
not a fully functional CPU capable of fetching it's own instructions and running code,
it does provide the ALU, registers and instruction deocde for performaing CPU operations
when you manually "feed" it instructions.  Turning it into a fully Turing CPU would
require addition of a Program Counter (PC), execution state machine, program control
opcodes (jump, call, return, conditional branches, etc.), and an interface for fetching
opcodes.

## How it works

It works by "feeding" it opcodes and data via the ui[7:0] and ui[0] input pins and then executing them by toggling the uio[1] input pin.  Some instructions require additional "Immediate Data" to be supplied
via the ui[7:0] input pins prioro to toggling the uio[1] "execute" input.

The WokProc has an 8-bit accumulator and 4 8-bit working registers and can perform ADD, SUBTRACT and the standard logical functions AND,OR,XOR and NOT.  It also keeps track of CARRY and ZERO bits to reflect the results of operations.

## How to test

## Opcodes supported:

 | Opcode    | Operation                |
 | --------- | ------------------------ |
 | 0000_0000 | A <= A + IMM             |
 | 0000_1000 | A <= A + IMM + Carry     |
 | 0001_0000 | A <= A - IMM             |
 | 0001_1000 | A <= A - IMM - Borrow    |
 | 0010_0000 | A <= A + R[1:0]          |
 | 0010_1000 | A <= A + R[1:0] + Carry  |
 | 0011_0000 | A <= A - R[1:0]          |
 | 0011_1000 | A <= A - R[1:0] - Borrow |
 | 0100_0000 | A <= IMM                 |
 | 0110_0000 | A <= R[1:0]              |
 | 0110_0100 | A <= A ^ R[1:0]          |
 | 0110_1000 | A <= A | R[1:0]          |
 | 0110_1100 | A <= A & R[1:0]          |
 | 0111_0000 | A <= Zero                |
 | 0111_0001 | A <= !A                  |
 | 0111_0100 | A <= !R[1:0]             |
 | 0111_1000 | Cy <= 0                  |
 | 0111_1001 | Cy <= !Cy                |
 | 1000_0000 | R[1:0] <= A + IMM        |
 | 1001_0000 | R[1:0] <= A - IMM        |
 | 1010_0000 | R[1:0] <= A + R[1:0]     |
 | 1011_0000 | R[1:0] <= A - R[1:0]     |
 | 1100_0000 | R[1:0] <= IMM            |
 | 1101_0000 | R[1:0] <= A              |
 | 1110_0000 | R[1:0] <= R[3:2]         |

## Hardware needed:

Dip switches and 7-Segment LED.

