**2.1**

```asm
addi x7, x7, -5
add x5, x6, x7
```

**2.2**

```c
f = i + g + h;
```

**2.3**

```asm
sub x30, x28, x29
slli x30, x30, 3
add x30, x10, x30
ld x30, 0(x30)
sd x30, 32(x11)
```

**2.4**

The book has some errors.

```asm
addi x12, x30, 8  # x12 = &A[f+1]
ld x30, 0(x12)    # x30 = A[f+1]
add x30, x30, x5  # x30 = A[f+1] + A[f]
sd x30, 0(x31)    # B[g] = x30
```

```c
B[g] = A[f] + A[f+1];
```

**2.5**

- Little-endian (LSB first):
  - 0: 0x12
  - 1: 0xef
  - 2: 0xcd
  - 3: 0xab
- Big-endian (MSB first):
  - 0: 0xab
  - 1: 0xcd
  - 2: 0xef
  - 3: 0x12

**2.6**

- unsigned: 2882400018
- signed: -1412567278

**2.7**

```asm
slli x28, x28, 3
add x28, x10, x28
ld x28, 0(x28)

slli x29, x29, 3
add x29, x10, x29
ld x29, 0(x29)

add x28, x28, x29
sd x28, 64(x11)
```

**2.8**

```asm
addi x30, x10, 8 # x30 = &A[1]
addi x31, x10, 0 # x31 = &A[0]
sd x31, 0(x30)   # A[1] = &A[0]
ld x30, 0(x30)   # x30 = A[1]
add x5, x30, x31 # f = A[1] + &A[0] = 2 * &A[0]
```

```c
f = 2 * &A[0];
```

**2.9**

TODO(rexes-ND): pain and no gain task

**2.10**

**2.10.1**

The value of `x30` is `0x50_00_00_00_00_00_00_00`.

**2.10.2**

There is an overflow.

**2.10.3**

The value of `x30` is `0xB0_00_00_00_00_00_00_00`.

**2.10.4**

From two's complement perspective, there is a desired result.

**2.10.5**

The value of `x30` is `0xD0_00_00_00_00_00_00_00`.

**2.10.6**

There is an overflow.

**2.11**

**2.11.1**

The largest positive 64-bit integer is `2^63 - 1`.

`128 + x6 > 2^63 - 1` or `x6 > 2^63 - 129` results in overflow.

**2.11.2**

`128 - x6 > 2^63 - 1` or `129 - 2^63` > x6 results in overflow.

The largest negative 64-bit integer is `-2^63`.

`-2^63 > 128 - x6` or `x6 > 2^63 + 128` but this is impossible.

**2.11.3**

The overflow occurs if:

- `x6 - 128 < -2^63` or `x6 < -2^63 + 128`.
- `x6 - 128 > 2^63 - 1` or `x6 > 2^63 + 127`. (impossible)

**2.12**

`instr: 0000000_00001_00001_000_00001_0110011`:

- `opcode: 0110011 -> R-type`.
- `rd: 1`.
- `funct3: 0 -> add`.
- `rs1: 1`.
- `rs2: 1`.

`add x1, x1, x2`.

**2.13**

`sw x5, 32(x30) -> S-type`:

- `opcode: 0100011`.
- `imm[4:0]: 00000`.
- `funct3: 010`.
- `rs1: 11110` or 30.
- `rs2: 00101` or 5.
- `imm[11:5]: 0000001`.

`0000_0010_0101_1111_0010_0000_0010_0011 -> 0x025F2023`.

**2.14**

- `opcode: 0x33 or 0110011`.
- `funct3: 0x0 or 000`.
- `funct7: 0x20 or 0100000`.
- `rs2: 5 or 00101`.
- `rs1: 7 or 00111`.
- `rd: 6 or 00110`.

R-type from opcode.

`sub` from funct3/7.

`sub x6, x7, x5: 0100 0000 0101 0011 1000 0011 0011 0011`.

**2.15**

- `opcode: 0x3 or 0000011`.
- `funct3: 0x3 or 011`.
- `rs1: 27 or 11011`.
- `rd: 3 or 00011`.
- `imm: 0x4 or 000000000100`.

I-type from opcode.

`ld` from funct3.

`ld x3, 4(x27): 0000 0000 0100 1101 1011 0001 1000 0011`.

**2.16**

128 regs means that we need at least 2 more bits for instr format.
opcode needs at least need 2 more bits.

**2.16.1**

R-type has an opcode and 3 reg fields: 8 more bits.

**2.16.2**

I-type has an opcode and 2 reg fields: 6 more bits.

**2.16.3**

- Good for reg allocations since we have more regs.
- Program size increases since we need more bits for each instruction.

**2.17**

**2.17.1**

`x7 = (x5 << 4) | x6`.

`x7 = 0x1234567ABABEFEF8`.

**2.17.2**

`x7 = x6 << 4`.

`x7 = 0x2345678123456780`.

**2.17.3**

`x7 = (x5 >> 3) & 0xFEF`.

`x7 = 0x545`.

**2.18**

Assuming reg is 32-bit.

```asm
slri x7, x5, 11
slli x7, x7, 17
slli x6, x6, 6
slri x6, x6, 6
add x6, x7, x6
```

More general approach.

```asm
addi x7, x0, 0x3F # x7 = [5:0]
slli x7, x7, 11   # x7 = [16:11]
slli x28, x7, 15  # x28 = [31:26]
xori x28, x28, -1 # x28 = [64:32] + [25:0]
and x7, x5, x7    # x7 = x5[16:11]
slli x7, x7, 15   # x7 = x5[16:11] << 15
and x6, x6, x28   # x6 = x6[64:32] + x6[25:0]
add x6, x6, x7    # x6 = x6[64:32] + x5[16:11] << 15 + x6[25:0]
```

**2.19**

`xori x5, x6, -1`.

**2.20**

```asm
ld x6, 0(x17)
slli x6, x6, 4
```

**2.21**

Since x5 >= 0, it branches to `ELSE` and `x6 = 2`.

**2.22**

**2.22.1**

`imm` field is 20-bit and possible values are in `[-2^19, 2^19 - 1]`.

After jump, `PC` is in `[PC - 2^20, PC + 2^20 - 2]`.

**2.22.2**

After branch, `PC` is in `[PC - 2^12, PC + 2^12 - 2]`.

**2.23**

**2.23.1**

UJ-type

**2.23.2**

```asm
loop:
    addi x29, x29, -1
    bge x29, x0, loop
addi x29, x29, 1
```

**2.24**

**2.24.1**

The loop executes `x6` times. `x5 = x5 + 2 * x6 = 20`.

**2.24.2**

```c
acc = 0;
i = 10;
while (i-- != 0)
    acc += 2;
```

**2.24.3**

`4 * N + 1`.

**2.24.4**

```c
acc = 0;
i = 10;
while (i-- >= 0)
    acc += 2;
```

**2.25**

```asm
add x7, x0, x0                         # i = 0
LOOP1:
    bge x7, x5, EXIT1                  # i >= a, jump to EXIT1
    add x29, x0, x0                    # j = 0
    add x30, x7, x0                    # x30 = i
    add x31, x10, x0                   # x31 = D
    LOOP2:
        bge x29, x6, EXIT2

        sd x30, 0(x31)

        addi x29, x29, 1
        addi x30, x30, 1
        addi x31, x31, 32

        jal x0, LOOP2
    EXIT2:
        addi x7, x7, 1
        jal x0, LOOP1
EXIT1:
```

**2.26**

13 instructions in total.

a = 10, b = 1

- Outer
  - Outer loop setup = 1
  - Outer loop body = a \* (Inner loop setup + Inner loop + Inner loop exit)
  - Outer loop end = 1
  - Outer loop exit = 0
- Inner
  - Inner loop setup = 4
  - Inner loop: b \* 6
  - Inner loop end: 1
  - Inner loop exit = 2

Total instructions = 1 + a _ (4 + (6 _ b + 1) + 2) + 1 + 0 = 6ab + 7a + 2 = 132

**2.27**

```asm
    addi x6, x0, 0    # i = 0
    addi x29, x0, 100 # x29 = 100
LOOP:
    lw x7, 0(x10)     # x7 = MemArray[i]
    add x5, x5, x7    # result += x7
    addi x10, x10, 8  # &MemArray[i+1]
    addi x6, x6, 1    # i++
    blt x6, x29, LOOP # i < x29, LOOP
```

```c
i = 0;
result = 0;
while (i < 100) {
    result += MemArray[i];
    ++i;
}
```

**2.28**

```asm
add x29, x10, 800
LOOP:
    lw x7, 0(x10)
    addi x5, x5, x7
    addi x10, x10, 8
    blt x10, x29, LOOP
```

**2.29**

```asm
fib:
    beq x10, x0, DONE   # n == 0, DONE
    addi x5, x0, 1      # x5 = 1
    beq x10, x5, DONE   # n == 1, DONE

    addi sp, sp, -16
    sd x10, 8(sp)       # save arg reg first
    sd x1, 0(sp)        # save ret address later

    addi x10, x10, -1   # n - 1
    jal x1, fib         # fib(n - 1)

    ld x5, 8(sp)        # x5 = n
    sd x10, 8(sp)       # put fib(n - 1) into stack
    addi x10, x5, -2    # x10 = n - 2
    jal x1, fib         # fib(n - 2)

    ld x5, 8(sp)        # x5 = fib(n - 1)
    add x10, x10, x5    # fib(n - 1) + fib(n - 2)

    ld x1, 0(sp)
    addi sp, sp, 16
    DONE:
        jalr x0, x1      # ret
```

**2.30**

Assuming `sp = 0x7ffffffc` initially:

1. first call:
   - `0x7fffffec: n`
   - `0x7ffffff4: x1`
2. second call:
   - `0x7fffffec: n`
   - `0x7ffffff4: fib(n-1)`

**2.31**

```asm
addi sp, sp, -16
sd x1, 0(sp)
add x5, x12, x13
sd x5, 8(sp)

jal x1, g

ld x11, 8(sp)
jal x1, g

ld x1, 0(sp)
addi sp, sp, 16
jalr x0, x1
```

**2.32**

Last call to `g` can directly return to the caller of `f`.

```asm
addi sp, sp, -16
sd x1, 0(sp)
add x5, x12, x13
sd x5, 8(sp)

jal x1, g

ld x11, 8(sp)
ld x1, 0(sp)     # Return to caller of f
addi sp, sp, 16
jal x0, g        # Call g
```

**2.33**

- `x10-x14`: `g` can modify them.
- `x8`, `x1`, `sp`: Callee-saved, so it stays same.

**2.34**

TODO(rexes-ND): Finish when you have a free time.

**2.35**

```asm
lb x6, 0(x7)
sw x6, 8(x7)
```

**2.35.1**

x6 = 0x00000000_00000011

- 0x10000000: 0x11
- 0x10000008: 0x00

**2.35.2**

x6 = 0xFFFFFFFF_FFFFFF88

- 0x10000000: 0x88
- 0x10000008: 0x88

**2.36**

```asm
lui x10, 0x12345
addi x10, 0x678
```

**2.37**

```asm
TRY:
    lr.d x5, 0(x10)
    bge x5, x11, EXIT
    add x5, x11, x0
EXIT:
    sc.d x6, x5, 0(x10)
    bne x6, x0, TRY

    jalr x0, x1
```

**2.38**

TODO(rexes-ND): Need very good understanding of `lr.d` and `sc.d`.

**2.39**

**2.39.1**

`exec_time = CPI * instr * clock_cycle_time`.

- Before addition: 3800 M clock cycles
- After addition: 4042.5 M clock cycles

Therefore, it is not good design choice.

**2.39.2**

The execution time of only arithmetic instructions is 500 M.

Execution time:

- Initial: 3800 M
- 2x: 3550 M (1.07x)
- 10x: 3350 M (1.13x)

**2.40**

**2.40.1**

The average CPI is 2.6 (1.4 + 0.6 + 0.6).

**2.40.2**

CPI = 0.75 x 2.6 = 1.95.

The 1.4 has fallen to 0.75 (1.95 - 1.2), which is 1.87x.

The CPI of arithmetic instruction is 1.07.

**2.40.3**

CPI = 0.5 x 2.6 = 1.3.

The 1.4 has fallen to 0.1 (1.3 - 1.2), which is 14x.

The CPI of arithmetic instruction is 0.14.

**2.41**

```asm
ld x30, [x10 + x5 * 8]
ld x31, [x10 + x5 * 8 + 8]
add x30, x30, x31
sd x30, [x11 + x6 * 8]
```

**2.42**

```asm
ld x28, [x10 + x28 * 8]
ld x29, [x10 + x29 * 8]
add x28, x28, x29
sd x28, 64(x11)
```
