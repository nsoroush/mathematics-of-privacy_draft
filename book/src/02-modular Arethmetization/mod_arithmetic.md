# Modular Arithmetic: When Infinity Meets the Finite 


> Atop the boundless peaks of Olympus, where the gods held infinite power, numbers were born. Boom, boom, boom… one, two, three, and onward to eternity, they marched in an eternal dance, each following the other. **Apollo**, god of light and order, gifted numbers to mortals, yet how could a finite grasp the infinite. Among the endless lines and spirals of eternity, **Harmonia**, goddess of balance and cycles, stepped forward. With delicate fingers, she traced a circle in the sands of abstraction—closed, perfect, eternal.
> This circle created a cycle that tied the infinite to the finite. Numbers, like stars on a cosmic dial, spun around this sacred plane, returning to their origin with each turn. **Euterpe**, muse of harmony, struck her lyre, and the **Cycle of Remainders** was born. No longer did numbers stretch endlessly; they danced in harmonious rings, each step measured by the sacred modulus, weaving patterns of repetition and unity across the mathematical cosmos.
> In this new realm of modular arithmetic, mathematics revealed the hidden music of numbers. Time folded upon itself, calculations became cyclical, and every number found its place through remainders and return. Within Harmonia's circle, the infinite rested in the finite, and numbers spun forever in an eternal dance of return."


### 🎯Learning Objectives
By the end of this lecture, you will be able to:

- Define modular arithmetic and the set \\(\mathbb{Z}_n\\).
- Perform addition, subtraction, multiplication, and exponentiation in \\(\mathbb{Z}_n\\).
- Compute multiplicative inverses in \\(\mathbb{Z}_n\\) using trial-and-error and the Extended Euclidean Algorithm.
- Understand why modular arithmetic is fundamental to cryptographic systems.
- Solve linear congruences and apply them to simple cryptographic problems.

## 1. The need for finite systems in cryptography


> **Athena**: We've reviewed sets and integers, but for our cryptographic needs, the infinite expanse of \\( \mathbb{Z} \\) is unwieldy—like trying to store the ocean in a cup. Integers lack a robust division structure, and infinity offers little structure to build on.  
>  
> We need something different: a system that is **finite yet powerful**, **structured yet flexible**. This is where modular arithmetic performs its quiet alchemy.  
>  
> Let us dive into it, step by step.

> One elegant way to shrink the infinite is to view the integers through a new lens: \\(\mathbb{Z}_7\\). In this modular world, every integer is reduced to its **remainder when divided by 7**, allowing us to work within a finite, circular universe using the modular operation.


> For example, consider the number 10:
> \\[
> 10 = 7 \cdot 1 + 3 \quad \Rightarrow \quad 10 \equiv 3 \pmod{7}
> \\]
> So, in \\(\mathbb{Z}_7\\), \\(10\\) is represented as 3.

> **Chad**: "Okay, cool. What about 17? I can write \\(17 = 7 \cdot 2 + 3\\), so 17 is 3 in \\(\mathbb{Z}_7\\), right?"

> **Hermes**: "Hold on! What if I write \\(17 = 7 \cdot 1 + 10\\)? Does that mean 17 is 10 in \\(\mathbb{Z}_7\\)? That's confusing!"

> **Athena**: "Great catch, Hermes! This is precisely why we invoke the Division Theorem - our mathematical anchor in these modular seas."
>   Let's recall it:

> **Division Theorem**: For any integer \\(n\\) and positive integer \\(m\\), there exist unique integers \\(q\\) (quotient) and \\(r\\) (remainder) such that:
> \\[
> n = m \cdot q + r, \quad 0 \leq r < m
> \\]

> This ensures a unique remainder \\(r\\) between 0 and \\(m-1\\). For 17 in \\(\mathbb{Z}_7\\):
> \\[
> 17 = 7 \cdot 2 + 3 \quad \Rightarrow \quad 17 \equiv 3 \pmod{7}
> \\]
> Writing \\(17 = 7 \cdot 1 + 10\\) violates the theorem because \\(r = 10 \geq 7\\)."

> **Hermes**: "Got it! So 17 is definitely 3 in \\(\mathbb{Z}_7\\)."

> **Chad**: "What about negative numbers? Do they work too?"

> **Hermes**: "Absolutely! The quotient \\(q\\) can be negative, but the remainder \\(r\\) must be between 0 and 6. Take \\(-15\\):
> \\[
> -15 = 7 \cdot (-3) + 6 \quad \Rightarrow \quad -15 \equiv 6 \pmod{7}
> \\]
> If you try \\(-15 = 7 \cdot (-2) + (-1)\\), the remainder \\(-1\\) is invalid since it's negative."

> **Chad**: "Nice! And zero is just zero, right? \\(0 \mod 7 = 0\\). Numbers less than 7 stay the same, like \\(1 \equiv 1\\), \\(2 \equiv 2\\). But negatives flip, like:
> \\[
> -1 = 7 \cdot (-1) + 6 \quad \Rightarrow \quad -1 \equiv 6 \pmod{7}
> \\]
> That's wild!"

> **Athena**: "You're catching on fast! Now, let's formalize this and explore how to operate in this finite world."


## 2. \\(\mathbb{Z}_n\\), the Magic Circle


For any positive integer n, the set of integers modulo n is:
\\[
ℤ_n = \{[0], [1], [2], \dots, [n-1]\}
\\]

Each element [k] represents an equivalence class containing all integers congruent to k modulo n:
\\[
[k] = \{\dots, k-2n, k-n, k, k+n, k+2n, \dots\}
\\]

#### **Simple Examples**

**1. ℤ₂ - The Binary System**
The smallest non-trivial case has two equivalence classes:
- [0] = {..., -4, -2, 0, 2, 4, ...} (all even numbers)
- [1] = {..., -3, -1, 1, 3, 5, ...} (all odd numbers)

Operations in ℤ₂:
- 0 + 0 ≡ 0 mod 2
- 0 + 1 ≡ 1 mod 2
- 1 + 1 ≡ 0 mod 2 (since 2 ≡ 0 mod 2)
- 1 × 1 ≡ 1 mod 2

**2. ℤ₃ - Three-Class System**
- [0] = {..., -6, -3, 0, 3, 6, ...}
- [1] = {..., -5, -2, 1, 4, 7, ...}
- [2] = {..., -4, -1, 2, 5, 8, ...}

Sample operations:
- 2 + 2 ≡ 1 mod 3 (since 4 ≡ 1 mod 3)
- 2 × 2 ≡ 1 mod 3 (since 4 ≡ 1 mod 3)

#### **General Structure**
For any ℤₙ:
1. **Additive Structure**: Forms a cyclic group under addition
2. **Multiplicative Structure**: Units form a group when n is prime
3. **Canonical Representation**: Typically use {0, 1, ..., n-1} as class representatives

#### **Visualization: ℤ₅ as a Cycle**
```
0 → 1 → 2 → 3 → 4
↑_____________↓
```
All arithmetic "wraps around" after reaching 5.

#### **Example: ℤ₇**
The modular arithmetic system ℤ₇ consists of seven equivalence classes:
- [0] contains all multiples of 7: {..., -14, -7, 0, 7, 14, ...}
- [1] contains integers congruent to 1 mod 7: {..., -13, -6, 1, 8, 15, ...}
- This pattern continues through [6]: {..., -8, -1, 6, 13, 20, ...}

The Division Theorem ensures this classification is both complete and unambiguous - every integer belongs to exactly one equivalence class in ℤₙ, creating a finite system of n distinct elements.


**Congruence**: Two integers \\(a\\) and \\(b\\) are **congruent modulo \\(n\\)**, written \\(a \equiv b \pmod{n}\\), if \\(n\\) divides \\(a - b\\):
\\[
a \equiv b \pmod{n} \quad \Leftrightarrow \quad n \mid (a - b)
\\]
**Proof**: If \\(a \equiv b \pmod{n}\\), then:
\\[
a = n \cdot q_a + r, \quad b = n \cdot q_b + r \quad \Rightarrow \quad a - b = n \cdot q_a + r - (n \cdot q_b + r) = n (q_a - q_b)
\\]
Thus, \\(n \mid (a - b)\\). For example, \\(19 \equiv 12 \pmod{7}\\) since \\(19 - 12 = 7\\), and \\(7 \mid 7\\).

SO in fact in \\(\mathbb{Z}_n\\), numbers are "equal" if they share the same remainder, redefining equality for cryptographic operations.


#### **Key Properties**
1. **Finiteness**: Exactly n distinct classes despite infinite ℤ
2. **Consistency**: a ≡ b mod n ⇒ a and b behave identically in ℤₙ
3. **Computational Use**: Enables working with large numbers via small residues



## 3. Arithmetic Operations in \\(\mathbb{Z}_n\\)

Modular arithmetic in ℤₙ supports four fundamental operations (addition, subtraction, multiplication, and division) with results reduced modulo n. A key computational advantage is the flexibility to:

1. **Reduce-then-operate**: Simplify operands first, then perform the operation
2. **Operate-then-reduce**: Compute first, then simplify the result

Both methods yield identical results, enabling optimization based on computational context. We illustrate these operations using ℤ₇ as our working example.

> **Key Insight**: The equivalence of these approaches stems from modular arithmetic's fundamental property: congruence is preserved under addition, subtraction, and multiplication.

#### 1. Addition in ℤₙ
The sum (a + b) mod n can be computed as:

**Example 1**: 5 + 4 mod 7
- Reduce-then-operate: (5 mod 7) + (4 mod 7) = 5 + 4 = 9 ≡ 2 mod 7
- Operate-then-reduce: 5 + 4 = 9 ≡ 2 mod 7

**Example 2**: 12 + 19 mod 7
- Reduce-then-operate: (12 mod 7) + (19 mod 7) = 5 + 5 = 10 ≡ 3 mod 7
- Operate-then-reduce: 12 + 19 = 31 ≡ 3 mod 7

**Properties**:
- Commutative: a + b ≡ b + a mod n
- Associative: (a + b) + c ≡ a + (b + c) mod n
- Additive identity: a + 0 ≡ a mod n

#### 2. Subtraction in ℤₙ
The difference (a - b) mod n follows similar rules:

**Example 1**: 6 - 3 mod 7
- Both approaches yield 3 mod 7

**Example 2**: 15 - 8 mod 7
- Reduce-then-operate: (15 mod 7) - (8 mod 7) = 1 - 1 = 0 mod 7
- Operate-then-reduce: 15 - 8 = 7 ≡ 0 mod 7

**Key Property**: Every element has a unique additive inverse. For a ∈ ℤₙ, its inverse is (n - a) mod n.

#### 3. Multiplication in ℤₙ
The product (a · b) mod n demonstrates modular arithmetic's power:

**Example 1**: 3 · 4 mod 7
- Both methods yield 12 ≡ 5 mod 7

**Example 2**: 12 · 7001 mod 7
- Reduce-then-operate: (12 mod 7) · (7001 mod 7) = 5 · 1 = 5 mod 7
- Operate-then-reduce: 12 · 7001 = 84012 ≡ 5 mod 7

**Properties**:
- Commutative and associative
- Distributive over addition
- Multiplicative identity: a · 1 ≡ a mod n

#### Computational Note
The equivalence of both computation methods provides crucial flexibility:
- Reduce-then-operate minimizes intermediate values
- Operate-then-reduce may simplify complex expressions

**Exercises**:
1. Compute 20 + 13 mod 7 using both methods
2. Compute 15 - 9 mod 7 using both methods
3. Compute 10 · 16 mod 7 using both methods
4. Solve 3x ≡ 6 mod 7 using inverses


## 4. Modular Exponentiation: Big Powers, Small Results

Modular exponentiation, the computation of \\( a^b \mod n \\), serves as a cornerstone for modern cryptographic systems. This operation combines the efficiency of modular reduction with the power of exponentiation, enabling secure computations even with extremely large numbers.

#### **Fundamental Congruence Property**
A crucial property governs modular exponentiation:
If \\( a \equiv b \pmod{n} \\), then \\( a^m \equiv b^m \pmod{n} \\) for any positive integer \\( m \\).

**Proof**:  
Let \\( a = b + kn \\) for some integer \\( k \\). Expanding \\( a^m \\) via the binomial theorem:
\\[
a^m = (b + kn)^m = b^m + m b^{m-1}(kn) + \cdots + (kn)^m
\\]
All terms except \\( b^m \\) contain \\( n \\) as a factor, thus:
\\[
a^m \equiv b^m \pmod{n}
\\]

This property allows us to reduce the base before exponentiation, dramatically simplifying computations.

---

#### **Computational Techniques**
1. **Direct Reduction**  
   Reduce the base modulo \\( n \\) first, then exponentiate:
   \\[
   a^b \mod n = (a \mod n)^b \mod n
   \\]

2. **Step-wise Reduction**  
   For larger exponents, reduce modulo \\( n \\) at each step to control intermediate values:
   \\[
   a^b \mod n = \underbrace{(a \times a \times \cdots \times a)}_{b \text{ times}} \mod n
   \\]
   with reduction after each multiplication.

---

#### **Practical Examples**

**Example 1**: Compute \\( 21^{2025} \mod 5 \\)
1. Reduce base: \\( 21 \equiv 1 \mod 5 \\)
2. Thus \\( 21^{2025} \equiv 1^{2025} \equiv 1 \mod 5 \\)

**Example 2**: Compute \\( 3^3 \mod 7 \\)
- Direct: \\( 3^3 = 27 \equiv 6 \mod 7 \\) (since 27 - 3×7 = 6)
- Step-wise:
  \\[
  3^1 \equiv 3 \\\\
  3^2 \equiv 9 \equiv 2 \\\\
  3^3 \equiv 2 \times 3 = 6 \mod 7
  \\]

**Example 3**: Compute \\( 2^4 \mod 5 \\)
- Direct: \\( 16 \equiv 1 \mod 5 \\)
- Via congruence: \\( 2 \equiv 7 \mod 5 \\), so \\( 7^4 = 2401 \equiv 1 \mod 5 \\)

---

#### **Why This Matters in Cryptography**
1. **RSA Encryption**: Relies on \\( m^e \mod n \\) computations
2. **Diffie-Hellman**: Uses \\( g^x \mod p \\) for key exchange
3. **Efficiency**: Even with 1000-digit numbers, computations remain feasible

> **Security Insight**: While computing \\( a^b \mod n \\) is efficient, reversing it (the discrete logarithm problem) is computationally hard - this asymmetry enables secure cryptography. We will see a lot more soon!

Here's an enhanced version with a concise yet clear addition about Montgomery reduction, maintaining your original content's style while adding valuable technical depth:

### **Efficient Computation Methods**

While modular exponentiation provides the foundation, certain algorithms optimize these computations further. One particularly elegant solution is **Montgomery reduction**, which eliminates the need for expensive division operations in modular arithmetic.

#### **Montgomery Reduction Overview**
This method transforms numbers into a special representation (Montgomery form) where modular reduction becomes a simple shift operation. The algorithm requires:
1. A modulus \\( n \\) (odd integer)
2. A radix \\( R > n \\) coprime with \\( n\\)
3. Precomputed value \\( n' = -n^{-1} \mod R \\)

**Core Algorithm**:
```python
def montgomery_reduce(T, n, n_prime, R):
    # T is the number to reduce
    m = (T * n_prime) % R  # Multiply by precomputed value
    t = (T + m * n) // R    # Shift right by log2(R) bits
    if t >= n:
        return t - n
    return t
```

**Why It Matters**:
- Replaces division with multiplication and shifts
- Particularly efficient for hardware implementations
- Essential for fast modular exponentiation in cryptography

> **Athena's Insight**: *"Montgomery's method is like giving our modular arithmetic a turbo boost - it transforms messy divisions into clean, efficient operations perfect for cryptographic computations."*

#### **Practical Impact**
When combined with exponentiation algorithms (like square-and-multiply), Montgomery reduction enables:
- Faster RSA operations
- Efficient elliptic curve cryptography
- Optimized implementations in cryptographic hardware

This mathematical innovation demonstrates how clever representations can dramatically improve computational efficiency in modular arithmetic - a crucial consideration for real-world cryptographic systems.

#### Fun Exercises: Exponentiation Quests
1. **Wizard's Spell**: Compute \\(13^{2025} \mod 5\\). Hint: Reduce \\(13 \mod 5\\).
2. **Hermes' Quick Trick**: Find \\(4^3 \mod 7\\). Use direct and step-by-step methods. Check with \\(4 \equiv 11 \mod 7\\).
3. **Athena's Puzzle**: Compute \\(3^5 \mod 6\\). Why does \\(\mathbb{Z}_6\\) differ from \\(\mathbb{Z}_5\\)? Hint: Consider inverses.
4. **Crypto Challenge**: In toy RSA, message \\(m = 2\\) is encrypted as \\(c = m^3 \mod 7\\). Find \\(c\\). Verify with \\(m \equiv 9 \mod 7\\).

## 5. Division in \\(\mathbb{Z}_n\\)
> **Athena**: So far, we've defined addition and multiplication in \\(\mathbb{Z}_n\\), and they behave similarly to \\(\mathbb{Z}\\). However, the primary motivation behind introducing \\(\mathbb{Z}_n\\) was to facilitate division.
>
> **Hermes**: Indeed, we aimed for a number system balancing:
> 1. **Finiteness** (unlike \\(\mathbb{Q}\\), which is infinite and "too continuous" for discrete applications).
> 2. **Division-friendliness** (unlike \\(\mathbb{Z}\\), where division frequently fails). By *wrapping* \\(\mathbb{Z}\\) into \\(\mathbb{Z}_n\\), we achieve finiteness. But does this system support division?
>
> **Athena**: Let's investigate!

### Additive Inverses: The Easy Case  
In \\(\mathbb{Z}_n\\), addition (and subtraction) work smoothly because every element has an additive inverse:
- For \\(a \in \mathbb{Z}_n\\), the additive inverse is \\(-a \equiv n - a \mod n\\).
- This property lets us reverse addition easily: \\(a + b \equiv c \mod n \implies c + (-b) \equiv a \mod n\\).

**Examples in \\(\mathbb{Z}_7\\)**:
- \\(3 + 4 \equiv 0 \mod 7\\), thus \\(-3 \equiv 4 \mod 7\\).
- \\(18 + 3 \equiv 0 \mod 7\\) since \\(18 \equiv 4 \mod 7\\), and indeed, \\(4 + 3 = 7 \equiv 0 \mod 7\\).

**Key Insight**: \\(\mathbb{Z}_n\\) mirrors \\(\mathbb{Z}\\)—every element can reach \\(0\\) through addition.

###  Multiplicative Inverses: The Division Challenge  
In \\(\mathbb{Q}\\), division uses multiplicative inverses: \\(a/b = a \cdot b^{-1}\\), where \\(b^{-1}\\) satisfies \\(b \cdot b^{-1} = 1\\). Can \\(\mathbb{Z}_n\\) replicate this?

###Finding Inverses by Brute Force  
**Example**: Find the multiplicative inverse of \\(3\\) in \\(\mathbb{Z}_7\\). Testing each candidate:

\\[
3 \cdot 5 \equiv 1 \mod 7 \quad (\text{Inverse found: } 3^{-1} \equiv 5 \mod 7)
\\]

Division by \\(3\\) equals multiplication by \\(5\\).

**Corrected Example**: Solve \\(3x \equiv 4 \mod 7\\):
- Multiply by inverse \\(5\\): \\(x \equiv 4 \cdot 5 \equiv 20 \equiv 6 \mod 7\\).
- Check: \\(3 \cdot 6 = 18 \equiv 4 \mod 7\\). Correct!

###  When Inverses Fail: Zero Divisors  
**Example**: Find inverse of \\(3\\) in \\(\mathbb{Z}_6\\). No inverse exists, as \\(\gcd(3, 6) = 3 \neq 1\\).

This illustrates **zero divisors**, a significant obstacle:
- **Definition**: Non-zero elements \\(a, b \in \mathbb{Z}_n\\) with \\(a \cdot b \equiv 0 \mod n\\).
- Example in \\(\mathbb{Z}_6\\): \\(2 \cdot 3 = 6 \equiv 0 \mod 6\\).

**Important Observation**:  
Zero divisors exist in \\(\mathbb{Z}_n\\) for composite \\(n\\). Prime moduli \\(\mathbb{Z}_p\\) lack zero divisors, as primes have no nontrivial factors, making all non-zero elements invertible. Hence, \\(\mathbb{Z}_p\\) forms a *field*, fundamental in cryptography.

**Exercises for Thought**:
- Find all zero divisors in \\(\mathbb{Z}_{10}\\).
- Why don't zero divisors appear in \\(\mathbb{Q}\\) or \\(\mathbb{Z}_p\\)?

###  Division in \\(\mathbb{Z}_n\\)  
With multiplicative inverses, division in \\(\mathbb{Z}_n\\) (where \\(\gcd(a, n) = 1\\)) is:
\\[
\frac{b}{a} \equiv b \cdot a^{-1} \mod n.
\\]

#### Examples of Division  
1. **Compute \\(\frac{4}{3}\\) in \\(\mathbb{Z}_7\\)**:  
   \\(\frac{4}{3} \equiv 4 \cdot 5 = 20 \equiv 6 \mod 7\\).

2. **Attempt \\(\frac{5}{2}\\) in \\(\mathbb{Z}_8\\)**:  
   No inverse; thus undefined, as \\(\gcd(2, 8) \neq 1\\).

3. **Solve \\(4x \equiv 3 \mod 11\\)**:  
   Inverse of \\(4\\) is \\(3\\), thus \\(x \equiv 3 \cdot 3 \equiv 9 \mod 11\\).

#### Tools for Finding Inverses  
Efficient methods include:

##### Extended Euclidean Algorithm  
Finds \\(\gcd(a, n)\\) and expresses it as \\(ax + ny = \gcd(a, n)\\). For \\(\gcd(a, n)=1\\), this provides inverses.

**Example**: Inverse of \\(3\\) in \\(\mathbb{Z}_7\\):
\\[
7 = 2 \cdot 3 + 1 \implies 1 = 7 - 2 \cdot 3 \equiv (-2) \cdot 3 \mod 7 \equiv 5 \cdot 3 \mod 7.
\\]
Thus, \\(3^{-1} \equiv 5\mod 7\\).

##### Fermat's Little Theorem  
For prime \\(p\\), inverse is given by:
\\[
a^{-1} \equiv a^{p-2} \mod p.
\\]
**Example**: Inverse of \\(3\\) in \\(\mathbb{Z}_7\\):
\\[
3^{5} = 243 \equiv 5 \mod 7.
\\]
Check confirms correctness.

#### Exercises  
1. Calculate \\(\frac{4}{3}\\) in \\(\mathbb{Z}_7\\).
2. Explain why \\(\frac{5}{2}\\) is undefined in \\(\mathbb{Z}_8\\).
3. Find inverse of \\(5\\) in \\(\mathbb{Z}_{11}\\) using Extended Euclidean Algorithm.
4. Use Fermat's Little Theorem to find inverse of \\(2\\) in \\(\mathbb{Z}_{13}\\).

Division in \\(\mathbb{Z}_n\\) relies on multiplicative inverses, available only when \\(\gcd(a, n)=1\\). Prime moduli ensure invertibility for all non-zero elements, ideal for cryptography. Tools like the Extended Euclidean Algorithm and Fermat's Little Theorem simplify computations, transforming division challenges into manageable tasks. Next, we'll explore how these concepts influence algebraic structures such as groups.
