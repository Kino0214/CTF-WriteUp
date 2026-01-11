# RSA2026 (Crypto)

## 問題
**chall.py**
```python
import math
import os
import random
import sys
from Crypto.Util.number import isPrime

sys.set_int_max_str_digits(20 << 26)

flag = os.environ.get("FLAG", "Alpaca{****** REDACTED ******}").encode()
m = int(flag.hex(), 16)

primes = [x for x in range(2026) if isPrime(x) and m % x != 0]
ps = random.choices(primes, k=2026)
n = math.prod(ps)
assert m < n

e = 65537
c = pow(m, e, n)

print(f"{n = }")
print(f"{e = }")
print(f"{c = }")
```
**output.txt**
```python3
n = 377103... (省略) ...0000
e = 65537
c = 100662... (省略) ...3229
```

## 解法
1. $n$は小さな2026個の素数の積からなるため素因数分解することができる.

2. $n = p_1^{a_1} p_2^{a_2} \dots p_k^{a_k}$ に対して, $\phi(n) = \prod_{i=1}^{k} p_i^{a_i-1}(p_i - 1)$を計算する.

3. RSA秘密鍵 $d \equiv e^{-1}\pmod{\phi(n)}$ を求める.

4. $m \equiv c^d \pmod n$ を計算し、数値を文字列に戻す.


```python
n = gmpy2.mpz(3771033...(省略))
e = 65537
c = gmpy2.mpz(1006624...(省略))

tmp = sympy.factorint(n)
phi = 1
for p in range(2026):
  if sympy.isprime(p) and p in tmp:
    phi *= pow(p, tmp[p])*(p-1)
d = pow(e, -1, phi)
print(long_to_bytes(pow(c, d, n)))
```
フラグが獲得できる
```python
b'Alpaca{h4ppy_n3w_y34r_wi7h_RSA!!}'
```