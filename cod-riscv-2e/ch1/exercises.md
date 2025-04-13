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
