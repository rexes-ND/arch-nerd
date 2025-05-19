**4.1**

**4.1.1**

- RegWrite: true
- ALUSrc: 0
- ALUOp: 0000 (AND)
- MemWrite: false
- MemRead: X
- MemtoReg: 0

**4.1.2**

- Registers
- ALUSrc mux
- ALU
- MemtoReg mux

**4.1.3**

Data memory produces no output if MemRead is not set.

Imm Gen produces output that is not used.

**4.2**

For both `sw` and `beq`, RegWrite is set to false.
Therefore, MemtoReg can choose any input.

**4.3**

**4.3.1**

35%.

**4.3.2**

100%.

**4.3.3**

76%.

**4.3.4**

It sign extend every cycle but only its output is not used.

**4.4**

**4.4.1**

R-format.

**4.4.2**

`lw` and `sw`.

**4.5**

`sw 12 20(13)`

**4.5.1**

ALUOp is 00.

**4.5.2**

PC -> PC + 4 -> Branch mux -> PC

**4.5.3**

ALUSrc mux:

- 0: Reg[x12]
- 1: 20
- Output: 20

MemtoReg mux:

- 0: Reg[x13] + 20
- 1: X
- Output: X

Branch mux:

- 0: PC + 4
- 1: PC + 40
- Output: PC + 4

**4.5.4**

ALU:

- Reg[13]
- 20

PC adder:

- PC
- 4

Branch adder:

- PC
- 40

**4.5.5**

- Read register 1: 13
- Read register 2: 12
- Write Register: 20
- Write data: X
- RegWrite: false

**4.6**
