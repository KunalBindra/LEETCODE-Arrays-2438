# LEETCODE-Arrays-2438
---

### **Understanding the Code**
* You have a number `n`.
* You break `n` into powers of 2 that make up its binary representation.
* For each query `[start, end]`, you take the **product** of the powers of 2 from `start` to `end` in that list, modulo `1e9+7`.

Key points in code:

1. `power` list: stores powers of two corresponding to set bits of `n`.
2. Outer loop (0 → 31) checks which bits are set in `n` and adds `2^i` to `power`.
3. For each query, multiply the corresponding powers, apply modulo, and store the result.

---

### **Sample Dry Run**

Let’s test with:

```java
n = 13
queries = [[0, 0], [0, 1], [1, 2]]
```

#### Step 1 — Building the `power` list

Binary of `13` = `1101`
From LSB to MSB:

* i=0 → `(n & (1<<0))` = `(13 & 1)` = `1` → set → add `2^0 = 1`
* i=1 → `(13 & 2)` = `0` → skip
* i=2 → `(13 & 4)` = `4` → set → add `2^2 = 4`
* i=3 → `(13 & 8)` = `8` → set → add `2^3 = 8`
* i=4...31 → all zero → skip

`power = [1, 4, 8]`

---

#### Step 2 — Processing Queries

**Query 1:** `[0, 0]`

* product = 1
* i=0 → product = `(1 * power[0]) % MOD` = `(1 * 1) % 1e9+7` = `1`
* result.add(1)

**Query 2:** `[0, 1]`

* product = 1
* i=0 → product = `(1 * 1) % MOD` = `1`
* i=1 → product = `(1 * 4) % MOD` = `4`
* result.add(4)

**Query 3:** `[1, 2]`

* product = 1
* i=1 → `(1 * 4) % MOD` = `4`
* i=2 → `(4 * 8) % MOD` = `32`
* result.add(32)

---

#### Step 3 — Final result

`result = [1, 4, 32]`
Return as `int[]`: `[1, 4, 32]`

---

✅ **Dry Run Output** for this example:

```
power: [1, 4, 8]
query[0,0] -> 1
query[0,1] -> 4
query[1,2] -> 32
final array: [1, 4, 32]
```

---

o you want me to do that next?
