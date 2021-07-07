# DD-Dot-Matrix-Printer-BCD-
**Designed and simulated a system that works like a dot-matrix printer. The user inputs a hexadecimal number, the output is a 5x5 LED bank that gets "written" from left to right. Using Logisim.**

DESIGN AND EXPLANATION
● The button array contains the Hexadecimal digits (0-F) with a clear function and forms
the input to the circuit. The output is represented in the form of a 5x5 LED Panel
designed to take inputs column-wise.
● The PAD, with the help of priority encoders, generates a 7-bit binary signature inspired
by the ASCII values of the digits and stores it in a register. It also outputs a ‘change’
signal which goes high when a button is pressed and resets any previous display.
● This 7-bit binary output along with the ‘change’ signal goes into the LOGIC. Every
column block in the LOGIC has two decoders (one each for a letter and a number and
enabled accordingly) which form the basic logic of the output using minterms. This logic
is common across all 5 columns. Each column block generates a 5-bit binary
output corresponding to the LED Panel column. As an example, if the ‘button 1’ is
pressed, the 7-bit binary signature will be ‘0010001’ and the 5-bit output of
COLUMN 2 will be ‘01001’. This pattern can be seen in the accompanying figure if
we move from top to bottom in COLUMN 2.
● This 5-bit output is fed into a 2:1 MUX. If the input is a valid Hexadecimal digit then this
5-bit output is passed through. Otherwise, a premade symbol ‘-’ is designated for
erroneous input.
● The multiplexer output goes into a 5-bit register that stores the value for its
corresponding column. Each register is triggered using a custom Ring Counter which
stops after 5 ticks of the clock and the output appears in a left to right fashion. The
change signal is used here to asynchronously reset all registers and the Ring Counter.
● Finally, all the 5-bit output from the registers form one 25-bit output which is displayed
through the 5x5 LED Panel
ASSUMPTIONS IN DESIGN
● An underlying assumption made in the circuit is that the output must be ready within one
clock cycle. This means that we have neglected the effect of propagation delay.
However, we have made several intelligent design choices to make the circuit more
efficient and less prone to the effect of propagation delay and human input errors.
● In case of the ring counter, the state 00000 may hypothetically exist, however, for normal
working, the CHANGE signal resets counter to 10000 before every transition and hence
00000 state never occurs in working conditions.
● Resistances, Inductance and Capacitance effects of all connection components
and any external field effects are assumed to be negligible and hence do not affect
the normal functioning of IC’s.
● In case of added functionality, the user must not operate logisim keyboard and adder
mode simultaneously.

