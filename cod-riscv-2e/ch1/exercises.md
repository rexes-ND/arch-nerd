**1.1**

- PC(s)
  - Low cost
  - Focus on response time
- Servers
  - Focus on throughput
  - Accessed over network
- Embedded computers
  - IoT
  - Designed to do one function well

**1.2**

- a. Perf via Pipelining
- b. Redundancy
- c. Perf via Prediction
- d. Common Case Fast
- e. Hierarchy of Memories
- f. ?
- g. Abstraction

**1.3**

1. Compiler: C program to assembly code
2. Assembler: Assembly code to binary code

**1.4**

a. There are 3 bytes per each pixel.
Minimum size of the frame buffer is 1280 x 1024 x 3 B = 3932160 B.

b. 3932160 \* 8 bits / 100 Mbit/s = 0.3146 second.

**1.5**

?

**1.6**

Assumption: instruction count is same for all processors.

a. Instructions per second is clock rate divided by CPI.
P2 is the highest and executes 2.5 G instructions per second.

b. `instr = exec_time * clock_rate / CPI` and `cycles = CPI * instr`.

- P1 executes 20 G instructions and 30 G cycles.
- P2 executes 25 G instructions and 25 G cycles.
- P3 executes 18.18 G instructions and 40 G cycles.

c. Assuming that number of instructions is same for each processor: `clock_rate ~ CPI / exec_time`. The clock rate has to improve 1.2 / 0.7 times.

- P1's clock rate should be 5.1429.
- P2's clock rate should be 4.2857.
- P3's clock rate should be 6.8571.

**1.7**

a.

- P1's CPI is 2.6.
- P2's CPI is 2.

b. `clock_cycles = CPI * instr`

- P1's clock cycles is 2.6 M.
- P2's clock cycles is 2 M.

**1.8**

a. `CPI = exec_time / (instr * clock_cycle_time)`

- Compiler A's CPI = 1.1.
- Compiler B's CPI = 1.25.

b.

`clock_rate = CPI * instr / exec_time`

`clock_rate_B / clock_rate_A = CPI_B * instr_B / (CPI_A * instr_A)` = 1.25 x 1.2 / 1.1 = 1.36.

c. `exec_time = CPI * instr * clock_rate` = 0.66 second.

- 1.67 times faster than A.
- 2.27 times faster than B.

**1.9**

`power_dynamic = 1/2 * capacitive_load * voltage ^ 2`.

**1.9.1**

- Prescott: 32 x 10 ^ -9
- Ivy Bridge: 29.05 x 10 ^ -9

**1.9.2**

- Prescott: 10 %
- Ivy Bridge: 42.8 %

**1.9.3**
`power_static = current_leak * voltage`.

If voltage is scaled by `s`, then static power is scaled by `s` and dynamic power is scaled by `s ^ 2`.

So, the equation is:
`s ^ 2 * power_dynamic  + s * power_static = 0.9 * (power_dynamic + power_static)`.

- Prescott: 5.4 % lower voltage
- Ivy Bridge: 6.5 % lower voltage

**1.10**

Formula for each type of instruction:
`exec_time = CPI * instr / clock_rate`.

For multiple cores,
`instr = (instr_arith + instr_ls) / (0.7 * p) + instr_branch`.

**1.10.1**

| Core Count | Execution Time (s) | Speedup |
| ---------- | ------------------ | ------- |
| 1 core     | 9.60               | 1.00×   |
| 2 cores    | 7.04               | 1.36×   |
| 4 cores    | 3.85               | 2.50×   |
| 8 cores    | 2.24               | 4.29×   |

**1.10.2**

| Core Count | Execution Time (s) |
| ---------- | ------------------ |
| 1 core     | 10.88              |
| 2 cores    | 7.95               |
| 4 cores    | 4.29               |
| 8 cores    | 2.46               |

**1.10.3**

CPI should be 3.

**1.11**

Assuming that the number of critical steps is 1.

`wafer_area = pi * diameter ^ 2 / 4`.
`die_area = wafer_area / die_cnt`.
`yield = 1 / (1 + die_area * defects_per_area)`.
`cost_per_die = cost / (yield * die_cnt)`

**1.11.1**

Yields are:

- 0.9596
- 0.9113

**1.11.2**

Cost per die:

- 0.1488
- 0.1646

**1.11.3**

Die area:

- 1.9115
- 2.8545

Yield:

- 0.9579
- 0.9076

**1.11.4**

`defects_per_area = (1 / yield - 1) / die_area`.

- 0.043
- 0.026

**1.12**

**1.12.1**
`CPI = exec_time * CR / I`.
CPI is 0.9418.

**1.12.2**
`SPECratio = ref_time / exec_time`.
SPECratio is 12.87.

**1.12.3**
10%.

**1.12.4**
15.5%.

**1.12.5**
SPECratio is 11.14.

**1.12.6**
New CPI is 1.379.

**1.12.7**

- 4 / 3 = 1.33
- 1.379 / 0.9418 = 1.46

Not similar since the ratio between execution time and number of instruction is not constant.

**1.12.8**
6.67% reduction

**1.12.9**
`instr = exec_time * clock_rate / CPI`.
Number of instruction is 2147.

**1.12.10**
4.44 GHz

**1.12.11**
3.1875 GHz

**1.13**

**1.13.1**

Execution time:

- P1: 1.125
- P2: 0.25

P2 (3GHz) is faster than P1 (4GHz).

**1.13.2**

P1: `10 ^ 9` instructions.
P2: `0.9 * 10 ^ 9` instructions.

**1.13.3**

P1: 4444 MIPS
P2: 4000 MIPS

**1.13.4**

P1: 1778 MFLOPS
P2: 1600 MFLOPS

**1.14**

**1.14.1**

5.6%

**1.14.2**

91% assuming that INT operations takes 55 sec.

**1.14.3**
Impossible since branch instruction takes only 16% of total time.

**1.15**

**1.15.1**

FP execution time takes only 9.7%, so impossible.

**1.15.2**

CPI of L/S should be 0.8 (5 times lower).

**1.15.3**

1.4953 times faster.

**1.16**

| Core Count | Execution Time | Speedup | Ratio |
| ---------- | -------------- | ------- | ----- |
| 1          | 100            | 1       | 1     |
| 2          | 54             | 1.85    | 0.93  |
| 4          | 29.0           | 3.45    | 0.86  |
| 8          | 16.5           | 6.06    | 0.76  |
| 16         | 10.25          | 9.76    | 0.61  |
| 32         | 7.12           | 14.04   | 0.44  |
| 64         | 5.56           | 17.98   | 0.28  |
| 128        | 4.78           | 20.92   | 0.16  |
