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

**4.6.1**

No additional block is needed.

**4.6.2**

- Branch: false
- MemRead: X
- MemtoReg: 0
- ALUOp: 10
- MemWrite: false
- ALUSrc: 1
- RegWrite: true

**4.7**

**4.7.1**

Latency of an R-type instruction is 850 ps:

- Register Read
- I-Mem
- Register File
- ALUSrc mux
- ALU
- MemtoReg mux
- Register File
- Register Setup

**4.7.2**

Latency of `lw` is 1100 ps:

- Register Read
- I-Mem
- Register File
- ALUSrc mux
- ALU
- D-Mem
- MemtoReg mux
- Register File
- Register Setup

**4.7.3**

Latency of `sw` is 905 ps:

- Register Read
- I-Mem
- Register File
- ALUSrc mux
- ALU
- D-Mem

**4.7.4**

Latency of `beq` is 705 ps:

- Register Read
- I-Mem
- Register File
- ALUSrc mux
- ALU
- Gate
- Branch mux
- Register Setup

**4.7.5**

Latency of an I-type instruction is same as that of R-type instruction (850 ps).

**4.7.6**

The minimum clock period is 1100 ps.

**4.8**

The clock cycle time is 901.15 ps.

The speed up is x1.22.

**4.9**

**4.9.1**

- without improvement: 1100 ps.
- with improvement: 1400 ps.

**4.9.2**

1100 ps / (1400 x 0.95) ps = x0.83.

**4.9.3**

1100 / ((1100 + alu_addition) x 0.95) = 1.

The additional ALU latency is 57.89 ps.

The slowest the new ALU can be 257.89 ps.

**4.10**

**4.10.1**

The overall instruction count is reduced by 4.32%.

The clock cycle time is 1120 ps.

The speedup is 1100 / (1200 x 0.9568) = 1.0265.

**4.10.2**

- I-Mem x 1
- Register File x 1
- Mux x 3
- ALU x 1
- Adder x 2
- D-Mem x 1
- Single Register x 1
- Sign extend x 1
- Single gate x 1
- Control x 1

- Cost (before): 3996
- Cost (after): 4196
- Cost increase: ~5%

**4.10.3**

The speedup was 2.65% and the cost increase was ~5%.
The cost per performance got worse but if the performance is critical, adding more registers makes sense.

**4.11**

**4.11.1**

No new functional block is needed.

**4.11.2**

The control unit needs modification.

**4.11.3**

No new data path is needed.

**4.11.4**

No new signal is needed.

**4.12**

**4.12.1**

No new functional block is needed.

**4.12.2**

The register file need 1 more write address and 1 more write data.

**4.12.3**

The read data 2 must be forwarded back into write data 2 via a bus.

**4.12.4**

The new control signal (RegWrite 2) is needed for writing data 2 into write address 2.

**4.12.5**

- RegWrite -> RegWrite 1
- Add RegWrite 2
- New bus from Read data 2 to Write data 2

**4.13**

**4.13.1**

The necessary functional blocks are:

- a mux to choose between Read data 1 and 2 as a ALU's first input
- a mux to choose between Read data 1 and ALU result as a Address of Data memory
- a mux to choose between Read data 2 and ALU result as a Write data of Data memory

**4.13.2**

No functional block needs modification.

**4.13.3**

Explained in **4.13.1**.

**4.13.4**

One signal is needed for each mux.

**4.13.5**

One bus from Read data 2 to the first mux.
One bus from Read data 1 to the second mux.
One bus from ALU result to the third mux.

**4.14**

Imm Gen is not on the critical path.

**4.15**

**4.15.1**

Since ALU takes 200 ps, the clock cycle time becomes 900 ps.

**4.15.2**

The instruction count is increased by 36 %.

The speedup is 11 / (1.36 x 9) = 0.899 (slower).

**4.15.3**

The number of `lw` and `sw` is significant.

**4.15.4**

The new CPU design is more simpler but slower.

**4.16**

**4.16.1**

- 1250 ps (non-pipelined)
- 350 ps (pipelined)

**4.16.2**

- 1250 ps (non-pipelined)
- 1750 ps (pipelined)

**4.16.3**

It is better to split ID.
The new clock cycle time is 300 ps.

**4.16.4**

35%.

**4.16.5**

65%

**4.17**

It takes k cycles to execute first instruction.
After that, each cycle executes one instruction.
The answer is k + n - 1.

**4.18**

- x13: 33
- x14: 26

**4.19**

- x15: 54

**4.20**

```asm
addi x11, x12, 5
NOP
NOP
add  x13, x11, x12
addi x14, x11, 15
NOP
add  x15, x13, x12
```

**4.21**

**4.21.1**

The speedup is 1.4 x 250 / (1.05 x 300) = 1.11x.

**4.21.2**

250 \* 1.4 / 300 = 1.167. 0.167\*n NOP instructions.
If NOP is higher than 0.167\*n, the pipeline is slower.

**4.21.3**

If 250 \* (1 + x) > 300 \* (1 + y), the pipeline is faster.
5/6 \* x - 1/6 > y.

**4.21.4**

If x is 0.075, 5/6 \* x - 1/6 = -0.104.
The y can never be lower than this, so impossible.

**4.21.5**

The x must be at least 0.2.

**4.22**

**4.22.1**

```asm
sw   x29, 12(x16)
lw   x29, 8(x16)
sub  x17, x15, x14
NOP # sw at MEM
NOP # lw at MEM
beqz x17, label
add  x15, x11, x14
sub  x15, x30, x14
```

**4.22.2**

It is impossible to avoid since each instruction is fetched.

**4.22.3**

It must be handled by the hardware. The NOP itself must be fetched from memory.
The control should send a signal when it is safe to read an instruction.

**4.22.4**

0.36\*n
