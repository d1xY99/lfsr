## How it works

This design is a 32-bit Fibonacci linear feedback shift register. On an asynchronous reset the register is loaded with the matriculation number 11830458. Each clock cycle shifts the register left by one bit and inserts a new feedback bit. The feedback bit is the XOR of taps 27, 23, 19, 18, 15, 11, 7, 4, and 1.

The lower 16 bits of the register are brought out on the TinyTapeout pins: `uo[7:0]` carries bits 7 through 0, and `uio[7:0]` carries bits 15 through 8.

## How to test

Hold reset active so the register contains 11830458, then release reset and apply a clock. The output pins should follow the LFSR sequence, one new state per rising clock edge. The cocotb test in `test/` checks that the lower 8 output bits match one step of this sequence.

## External hardware

None. The outputs can be observed on the TinyTapeout demo board or in the GDS viewer.
