# FooBar CTF 2022 - Baby Rev

* **Category:** Reverse engineering
* **Points:** 100

## Challenge

> nothing to say just solve it ....
## Solution
<img src="https://user-images.githubusercontent.com/78451563/156916550-8a2e805a-7095-4e3f-a955-668a8f3023ec.png" width="360" height="340">
It asks for a 42 length input as seen in the "main" function then does a bunch of math conditions with our input, if it passes the check "if_true" will keep the value "1" else it will be given the value "0" meaning it's wrong.

We can use z3 to solve this:
```python
from z3 import *
sm = [BitVec(f'sm{i}', 8) for i in range(42)]
s = Solver()
s.add(sm[8] + sm[0xd] + sm[7] == 0x10d)
s.add(sm[0] + (sm[0] - sm[1]) + sm[0xe] == 0xa5)
s.add(sm[0x26] + sm[0x15] * sm[0x10] + sm[0x22] == 0x250a)
s.add(sm[0x17] + sm[0x29] + sm[6] * sm[8] == 0x157c)
s.add(-sm[0x15] - sm[0x29] == -0xdf)
s.add(sm[0x13] + sm[0x12] * sm[4] * sm[0xb] == 0x9c2de)
s.add(sm[0x22] * sm[0x21] + sm[0x17] == 0x1903)
s.add(sm[0xe] * sm[0x12] - sm[0x21] == 0x13d0)
s.add(((sm[0x18] - sm[0x27]) - sm[0x1e]) - sm[0x16] == -0x6e)
s.add(sm[1] + ((sm[0x1e] + sm[10]) - sm[0x13]) == 0x6e)
s.add((sm[0xf] - sm[0x14]) - sm[0x29] == -0xa9)
s.add(sm[0x23] * sm[0xf] - sm[8] * sm[0x29] == -0x27f7)
s.add((sm[0xb] * sm[0x1f] + sm[0x24]) - sm[0x20] == 0x20ec)
s.add(sm[0x28] + sm[0x19] + sm[0x1d] == 0x121)
s.add(sm[0x18] + (sm[7] - sm[0xc]) == 100)
s.add(sm[0x1e] * sm[0x15] - sm[6] == 0x242e)
s.add(sm[3] * sm[0x21] * sm[0x26] == 0x753f4)
s.add((sm[0x14] - sm[0] * sm[0x1f]) - sm[2] == -0x1742)
s.add(sm[0x15] * sm[0xc] + sm[0x1b] == 0x13e7)
s.add((sm[6] + sm[8] * sm[0xb]) - sm[8] == 0x2aba)
s.add(sm[0x18] * sm[7] + (sm[0x22] - sm[5]) == 0x1396)
s.add((sm[0x28] - sm[0x12]) - sm[2] == -0x53)
s.add(sm[0x18] * sm[9] + (sm[0xb] - sm[0x1f]) == 0x2782)
s.add((sm[0x1c] + sm[0x1e]) - sm[0x10] * sm[3] == -0x198f)
s.add(sm[0x19] * sm[0x12] - sm[0xb] == 0x16c4)
s.add(sm[0xb] * sm[9] * sm[8] == 0x109de8)
s.add(sm[0x19] * sm[3] - sm[6] * sm[0x1d] == 0x8ee)
s.add(sm[0x24] - sm[0x21] * sm[7] == -0xe3a)
s.add(sm[0x14] + (sm[0x20] - sm[1]) == 0x49)
s.add(sm[4] * sm[5] + sm[0x27] == 0x2073)
s.add(sm[8] * sm[0x27] * sm[0] == 0x7dd84)
s.add(sm[0x1f] + (sm[0xc] - sm[0xd]) == 0x19)
s.add(sm[0x29] + sm[0x29] + sm[10] + sm[0x12] == 0x15f)
s.add(sm[0x16] + sm[1] * sm[0xe] + sm[7] == 0x1dc8)
s.add(sm[0xe] + sm[0x12] * sm[0x18] + sm[0x1b] == 0x157c)
s.add(sm[0x12] + (sm[0x14] - sm[6] * sm[0x29]) == -0x16dd)
s.add((sm[0x21] - sm[2]) - sm[0x1f] * sm[0x19] == -0x2571)
s.add(sm[0x25] * sm[0xb] * sm[0x12] == 0x56540)
s.add((sm[7] + sm[8] + sm[0x11]) - sm[0x27] == 0xc0)
s.add((sm[0xb] - sm[0x23]) - sm[0x1f] * sm[9] == -0x205d)
s.add(sm[0x27] + (sm[0x17] - sm[0x1d]) == 0x28)
s.add(sm[0x14] * sm[0x19] * sm[10] + sm[0x1c] == 0x81959)
s.add(sm[3] * sm[0x1d] * sm[0x20] == 0x7142a)
s.add(sm[0x1e] + (sm[0x20] - sm[0x16]) == 0x62)
s.add(((sm[0] - sm[0xd]) + sm[0x28]) - sm[0x26] == -0x4a)
s.add((sm[0x15] + sm[0x11]) - sm[0x26] == 0x6c)
s.add(sm[0] - sm[0x17] * sm[0x29] == -0x2e1c)
s.add(sm[0x1b] * sm[0x1d] * sm[2] == 0xf390d)
s.add(sm[0x19] - sm[0x23] * sm[0x13] == -0x1d34)
s.add(sm[0x10] - sm[7] * sm[0x13] == -0x14af)
s.add(sm[0x16] + sm[0x21] + sm[0x1a] * sm[0xc] == 0xaa8)
s.add(sm[0x20] + sm[0x18] + sm[0x29] == 0x119)
s.add(sm[0xe] * sm[0x1f] * sm[0x17] == 0xc0e04)
s.add((sm[0x23] - sm[6] * sm[0x23]) - sm[0xe] == -0xd0e)
s.add((sm[0x1f] + sm[0x28]) - sm[0x19] * sm[0x11] == -0x2b8c)
s.add(sm[0x13] * sm[0xd] + sm[0x12] * sm[0x24] == 0x3fec)
s.add(sm[0x12] * sm[2] + (sm[0x28] - sm[5]) == 0x1137)
s.add(sm[3] + (sm[0x15] - sm[0x19]) == 0x37)
s.add((sm[0xd] + sm[0xe] + sm[0xe]) - sm[2] == 0xdf)
s.add(sm[0x23] * sm[0x24] - sm[0x1d] * sm[5] == -0x991)
s.add(sm[1] + (sm[0x29] - sm[0x27]) == 0x87)
s.add(sm[0] + (sm[0x23] - sm[0x23] * sm[0]) == -0x1297)
s.add((sm[8] - sm[0x15] * sm[10]) - sm[0x1f] == -0x12a8)
s.add(sm[0x1c] + (sm[0x1d] - sm[0x18]) == 0x7e)
s.add((sm[10] * sm[0] - sm[0x20]) - sm[8] == 0xcf3)
s.add(sm[0x29] + sm[0x20] * sm[0x1c] == 0x170f)
s.add(sm[0x20] + (sm[0x25] - sm[0x18]) == 0x14)
s.add(sm[0x1f] + (sm[10] * sm[0x14] - sm[0xf]) == 0x1250)
s.add((sm[0x24] - sm[9]) - sm[0x12] * sm[0x12] == -0xaa1)
s.add(sm[0x1e] * sm[0x10] + sm[7] * sm[9] == 0x3634)
s.add((sm[0x18] + sm[0x22] + sm[0x12]) - sm[7] == 0xbc)
s.add(sm[0x14] + sm[0x1b] * sm[0x10] == 0x245e)
s.add(((sm[0x16] - sm[0x1e]) - sm[0x25]) - sm[9] == -0xd3)
s.add(sm[0x1b] * sm[0x29] * sm[4] - sm[0x26] == 0x16c156)
s.add(sm[0xd] + (sm[0x23] - sm[8] * sm[0x1d]) == -0x334b)
s.add(((sm[0x17] - sm[7]) - sm[0x18]) - sm[0x16] == -0x6b)
s.add(sm[5] * sm[4] * sm[0x25] == 0x88d04)
s.add(sm[0x20] * sm[0x11] - sm[0xf] == 0x14af)
s.add((sm[0x20] + sm[0x12] * sm[0x17]) - sm[5] == 0x133f)
s.add(sm[0x27] + sm[3] + sm[0x27] * sm[8] == 0x1ce5)
s.add(sm[0x24] + (sm[0x19] * sm[7] - sm[3]) == 0x15dd)
s.add((sm[9] - sm[0x18]) - sm[0x21] == -0x4f)
s.add(sm[0x24] * sm[0xe] + sm[0x1e] == 0x2015)
s.check()
model = s.model()
flag = ''.join([chr(int(str(model[sm[i]]))) for i in range(len(model))])
print(flag)
```
```
Flag: GLUG{C01nc1d3nc3_c4n_b3_fr3aky_T6LSERDYB6}
```
