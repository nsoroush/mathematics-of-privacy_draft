
### Chapter 1 (Continued): Preliminaries

#### Number Theory: From Counting to Crypto

Last time, we played with sets as math’s LEGO bricks. Now, we zoom into numbers—specifically \\(\mathbb{N}\\) (natural numbers) and \\(\mathbb{Z}\\) (integers)—and start messing with them. With Athena’s wisdom, Chad’s dares, and Hermes’ tricks, we’ll uncover why number theory is crypto’s secret weapon. Let’s keep it chill and throw in some SageMath to see it pop!


##### Arithmetic in \\(\mathbb{N}\\) and \\(\mathbb{Z}\\): Why + and - Are Chill

Let’s kick off with **arithmetic**—\\(+, -, \times, \div\\). You’ve known these since sandbox days, but here’s the cryptographer’s spin:

- **Addition**: \\(a + b \in \mathbb{Z}\\). No drama—always stays in \\(\mathbb{Z}\\).
- **Subtraction**: \\(a - b \in \mathbb{Z}\\). Works too (in \\(\mathbb{Z}\\), not \\(\mathbb{N}\\)—no negatives there!).
- **Multiplication**: \\(a \times b \in \mathbb{Z}\\). Grows fast, but still cozy in \\(\mathbb{Z}\\).
- **Division**: Not so clean. \\(7 \div 3 = 2.333\dots \notin \mathbb{Z}\\). Leftovers? Messy!

> **Athena Notes**: “By the wisdom of Olympus, crypto loves operations that stay in the set. \\(\mathbb{Z}\\) is our playground—but multiplication? That’s where the magic sparks!”

###### Why Multiplication is Crypto’s Best Friend
- It’s repeated addition—builds structure.
- It’s a one-way street—multiplying is easy, factoring is *hard*.
- It shifts gears in different sets—sometimes reversible, sometimes a lock.


##### Rational Numbers \\(\mathbb{Q}\\): Smooth, But Too Smooth for Security

Allow division, and you’re in \\(\mathbb{Q}\\)—fractions galore. Here, you can divide anything (except by 0). It’s slick math, but crypto says “nah”:

- Too continuous—no edges to grip.
- Too predictable—no surprises.
- No wrapping structure—boring!

> **Hermes Whispers**: “Let’s use \\(\mathbb{Q}\\) and divide by \\(\pi\\) for chaos!”
>
> **Athena Replies**: “Nice try, trickster. Chaos breaks security—crypto needs control, not infinity!”


##### The Division Theorem (a.k.a. Division Algorithm)

Back to integers—division’s messy, but predictable. Here’s the golden rule:

> For any integer \\(a\\) and positive integer \\(b > 0\\), there are unique integers \\(q\\) (quotient) and \\(r\\) (remainder) such that:
>
> \[ a = b \cdot q + r \quad \text{where } 0 \leq r < b \]

- **Example**: \\(23 \div 5\\):
  - \\(23 = 5 \cdot 4 + 3\\) → \\(q = 4\\), \\(r = 3\\).
- **Negative Twist**: \\(-7 \div 3\\):
  - \\(-7 = 3 \cdot (-3) + 2\\) → \\(q = -3\\), \\(r = 2\\).

This is the launchpad for **modular arithmetic**—crypto’s everything!

###### SageMath Spotlight: Division in Action
Check it with SageMath:

```python
a = 23
b = 5
q = a // b  # Integer quotient
r = a % b   # Remainder
print(f"{a} = {b} * {q} + {r}")  # Prints: 23 = 5 * 4 + 3

# Negative test
a = -7
b = 3
q = a // b
r = a % b
print(f"{a} = {b} * {q} + {r}")  # Prints: -7 = 3 * -3 + 2
```

> **Athena Says**: “This remainder \\(r\\) is your modulo ticket—crypto hides secrets in those leftovers!”

---

##### Factorization & Prime Numbers: The Hard Problem

A **factor** divides a number cleanly:
- \\(6\\)’s factors: \\(1, 2, 3, 6\\).
- **Prime**: Only divisible by 1 and itself—\\(2, 3, 5, 7, 11, \dots\\).

Why primes rule:
- They’re multiplication’s “atoms.”
- Every number splits into primes uniquely (e.g., \\(12 = 2^2 \cdot 3\\)).
- Factoring big numbers (like 2048-bit RSA keys)? Super hard!

> **Hermes Whispers**: “Fast to multiply, slow to un-multiply—that’s the trapdoor magic!”

---

##### GCD: Greatest Common Divisor

- \\(\gcd(a, b)\\): Biggest number dividing both \\(a\\) and \\(b\\).
- \\(\gcd(24, 36) = 12\\).
- \\(\gcd(a, b) = 1\\) → \\(a\\) and \\(b\\) are **coprime** (no common factors but 1).

###### Euclidean Algorithm (for GCD)
Fast trick:
\[ \gcd(a, b) = \gcd(b, a \mod b) \]
Repeat until \\(b = 0\\).

- **Example**: \\(\gcd(48, 18)\\):
  - \\(48 \mod 18 = 12\\)
  - \\(18 \mod 12 = 6\\)
  - \\(12 \mod 6 = 0\\) → Done! \\(\gcd = 6\\).

---

##### LCM: Least Common Multiple

- Smallest number both \\(a\\) and \\(b\\) divide into.
- Formula: \[ \text{lcm}(a, b) = \frac{|a \cdot b|}{\gcd(a, b)} \]
- \\(\text{lcm}(12, 18) = \frac{12 \cdot 18}{6} = 36\\).

###### SageMath Bonus: GCD and LCM
Try this:

```python
a = 48
b = 18
g = gcd(a, b)
l = lcm(a, b)
print(f"GCD of {a} and {b}: {g}")  # Prints: GCD of 48 and 18: 6
print(f"LCM of {a} and {b}: {l}")  # Prints: LCM of 48 and 18: 36
```

---

##### From Infinite to Finite: Why Cryptography Needs Boundaries

\\(\mathbb{Z}\\) and \\(\mathbb{Q}\\) go on forever—cool, but impractical:
- Computers can’t handle infinity.
- Security needs big, *finite* spaces.
- We want arithmetic that loops, not sprawls.

###### Why Finite = Secure?
Finite sets create:
- **Easy forward**: \\(a \times b \mod n\\).
- **Hard reverse**: Factor \\(n\\) or solve discrete logs.
This *asymmetry* powers public-key crypto!

> **Hermes Breaks Infinity**: “Let’s use real numbers! Divide a key by \\(\pi\\) for total chaos!”
>
> **Athena (sternly)**: “No chaos in crypto, trickster. Precision breaks with \\(\pi\\)—security needs finite control.”
>
> **Chad**: “So we slice infinity into finite chunks? Epic move!”
>
> **Athena**: “Exactly. Finite fields are controlled universes—elegant and tough.”

---

##### Welcome to Modular Arithmetic

Using the Division Theorem, we carve \\(\mathbb{Z}\\) into finite sets:
- **\\(\mathbb{Z}_n\\)**: \\(\{0, 1, 2, \dots, n-1\}\\).
- Add, subtract, multiply—then take \\(\mod n\\) to loop back.

- **In \\(\mathbb{Z}_5\\)**:
  - \\(3 + 4 = 7 \equiv 2 \pmod{5}\\).
  - \\(2 \times 4 = 8 \equiv 3 \pmod{5}\\).
  - \\(-1 \equiv 4 \pmod{5}\\).

> **Athena Notes**: “It’s clock math—hit the max, wrap around. This is the backbone of encryption and hashing!”

###### SageMath Wrap-Around
See \\(\mathbb{Z}_5\\) loop:

```python
n = 5
for i in range(10):
    r = mod(i, n)
    print(f"{i} mod {n} = {r}")  # Prints: 0, 1, 2, 3, 4, 0, 1, 2, 3, 4
```

---

##### 🔍 Quick Practice: Which Numbers Are in \\(\mathbb{Z}_7\\)?

Which belong to \\(\mathbb{Z}_7\\)?
a) 3  
b) 11  
c) -2  
d) 15

> **Chad Challenges**: “Bet you can’t crack this in ten seconds!”
>
> *Answers*:
> - a) 3 → ✅ (in range)
> - b) 11 \\(\equiv 4 \pmod{7}\\) → ✅
> - c) -2 \\(\equiv 5 \pmod{7}\\) → ✅
> - d) 15 \\(\equiv 1 \pmod{7}\\) → ✅

---

##### 🔢 Modular Arithmetic Wrap-Around

A peek at \\(\mathbb{Z}_5\\):

```
ℤ:   ... -2 -1  0  1  2  3  4  5  6  7  8 ...
ℤ₅:            [0][1][2][3][4][0][1][2][3]...
```



Next up: diving deeper into \\(\mathbb{Z}_n\\), modular inverses, and finite fields—crypto’s playground!

