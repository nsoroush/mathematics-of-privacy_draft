# ⚙️ Modular Arithmetic: The Clockwork Realm of Cryptography

## 🔐 Why Modular Arithmetic?

Cryptography requires mathematics that is:
1. **Finite**: Computers need bounded sets, not infinite ones.
2. **Efficient**: Operations like encryption must be fast.
3. **Hard to Reverse**: Without a secret key, reversing operations (e.g., decryption) should be nearly impossible.

### Introduction to Modular Arithmetic

> **Athena**: We reviewed sets and integers, but the integers (\\(\mathbb{Z}\\)) are infinite and lack a robust division operation suitable for cryptography. We need a finite, structured system. Let’s dive into modular arithmetic, step by step.

> One clever way to shrink the infinite integers is to view them through a lens called \\(\mathbb{Z}_7\\). In this world, we reduce each integer to its remainder when divided by 7, using the modular operation.

> For example, consider the number 10:
> \\[
> 10 = 7 \cdot 1 + 3 \quad \Rightarrow \quad 10 \equiv 3 \pmod{7}
> \\]
> So, in \\(\mathbb{Z}_7\\), \\(10\\) is represented as 3.

> **Chad**: "Okay, cool. What about 17? I can write \\(17 = 7 \cdot 2 + 3\\), so 17 is 3 in \\(\mathbb{Z}_7\\), right?"

> **Hermes**: "Hold on! What if I write \\(17 = 7 \cdot 1 + 10\\)? Does that mean 17 is 10 in \\(\mathbb{Z}_7\\)? That’s confusing!"

> **Athena**: "Great catch, Hermes! This is where the **Division Theorem** saves us. Let’s recall it:

> > **Division Theorem**: For any integer \\(n\\) and positive integer \\(m\\), there exist unique integers \\(q\\) (quotient) and \\(r\\) (remainder) such that:
> > \\[
> > n = m \cdot q + r, \quad 0 \leq r < m
> > \\]

> This ensures a unique remainder \\(r\\) between 0 and \\(m-1\\). For 17 in \\(\mathbb{Z}_7\\):
> \\[
> 17 = 7 \cdot 2 + 3 \quad \Rightarrow \quad 17 \equiv 3 \pmod{7}
> \\]
> Writing \\(17 = 7 \cdot 1 + 10\\) violates the theorem because \\(r = 10 \geq 7\\)."

> **Hermes**: "Got it! So 17 is definitely 3 in \\(\mathbb{Z}_7\\)."

> **Chad**: "What about negative numbers? Do they work too?"

> **Hermes**: "Absolutely! The quotient \\(q\\) can be negative, but the remainder \\(r\\) must be between 0 and 6. Take \(-15\):
> \\[
> -15 = 7 \cdot (-3) + 6 \quad \Rightarrow \quad -15 \equiv 6 \pmod{7}
> \\]
> If you try \\(-15 = 7 \cdot (-2) + (-1)\\), the remainder \(-1\) is invalid since it’s negative."

> **Chad**: "Nice! And zero is just zero, right? \\(0 \mod 7 = 0\\). Numbers less than 7 stay the same, like \\(1 \equiv 1\\), \\(2 \equiv 2\\). But negatives flip, like:
> \\[
> -1 = 7 \cdot (-1) + 6 \quad \Rightarrow \quad -1 \equiv 6 \pmod{7}
> \\]
> That’s wild!"

> **Athena**: "You’re catching on fast! Now, let’s formalize this and explore how to operate in this finite world."

### Modular Arithmetic: When Infinity Meets the Finite — \\(\mathbb{Z}_n\\), the Magic Circle

For a positive integer \\(n\\), we define the set \\(\mathbb{Z}_n\\), the **integers modulo \\(n\\)**, as:
\\[
\mathbb{Z}_n = \{[0], [1], [2], \dots, [n-1]\}
\\]
Each element \\([i]\\) is an **equivalence class**—a set of integers with the same remainder \\(i\\) when divided by \\(n\\). Formally, for integer \\(a\\):
\\[
[a] = \{ \dots, a - 2n, a - n, a, a + n, a + 2n, \dots \}
\\]
In practice, we write \\([i]\\) as \\(i\\) for simplicity in \\(\mathbb{Z}_n\\), so:
\\[
\mathbb{Z}_n = \{0, 1, 2, \dots, n-1\}
\\]
This shorthand avoids confusion, as \\(i\\) represents the class \\([i]\\). Let’s illustrate with \\(\mathbb{Z}_7\\):
- \\([0]\\): \\(\dots, -14, -7, 0, 7, 14, 21, \dots\\) (multiples of 7).
- \\([1]\\): \\(\dots, -13, -6, 1, 8, 15, 22, \dots\\) (remainder 1).
- \\([2]\\): \\(\dots, -12, -5, 2, 9, 16, 23, \dots\\) (remainder 2).
- \\([3]\\): \\(\dots, -11, -4, 3, 10, 17, 24, \dots\\) (remainder 3).
- \\([4]\\): \\(\dots, -10, -3, 4, 11, 18, 25, \dots\\) (remainder 4).
- \\([5]\\): \\(\dots, -9, -2, 5, 12, 19, 26, \dots\\) (remainder 5).
- \\([6]\\): \\(\dots, -8, -1, 6, 13, 20, 27, \dots\\) (remainder 6).

**Table of Equivalence Classes in \\(\mathbb{Z}_7\\)**:
\\[
\begin{array}{c|ccccccc}
\text{Remainder} & 0 & 1 & 2 & 3 & 4 & 5 & 6 \\
\hline
\text{Examples} & \dots, -7, 0, 7, \dots & \dots, -6, 1, 8, \dots & \dots, -5, 2, 9, \dots & \dots, -4, 3, 10, \dots & \dots, -3, 4, 11, \dots & \dots, -2, 5, 12, \dots & \dots, -1, 6, 13, \dots \\
\end{array}
\\]

> **Athena’s Wisdom**: The division theorem guarantees each integer belongs to exactly one class, making \\(\mathbb{Z}_n\\) finite with \\(n\\) elements (0 to \\(n-1\\)). This finiteness is key for cryptography.

**Congruence**: Two integers \\(a\\) and \\(b\\) are **congruent modulo \\(n\\)**, written \\(a \equiv b \pmod{n}\\), if \\(n\\) divides \\(a - b\\):
\\[
a \equiv b \pmod{n} \quad \Leftrightarrow \quad n \mid (a - b)
\\]
**Proof**: If \\(a \equiv b \pmod{n}\\), then:
\\[
a = n \cdot q_a + r, \quad b = n \cdot q_b + r \quad \Rightarrow \quad a - b = n \cdot q_a + r - (n \cdot q_b + r) = n (q_a - q_b)
\\]
Thus, \\(n \mid (a - b)\\). For example, \\(19 \equiv 12 \pmod{7}\\) since \\(19 - 12 = 7\\), and \\(7 \mid 7\\).

In \\(\mathbb{Z}_n\\), numbers are “equal” if they share the same remainder, redefining equality for cryptographic operations.

### Arithmetic Operations in \\(\mathbb{Z}_n\\)

In \\(\mathbb{Z}_n\\), we perform operations (addition, subtraction, multiplication, division) and reduce the result modulo \\(n\\). A powerful feature is that we can compute in two equivalent ways:
1. **Reduce First**: Compute the remainder of each operand modulo \\(n\\), then perform the operation in \\(\mathbb{Z}_n\\).
2. **Operate Then Reduce**: Perform the operation on the original numbers, then reduce modulo \\(n\\).

This flexibility simplifies computations, especially with large numbers, and is crucial for efficient cryptographic algorithms. Let’s explore each operation with examples in \\(\mathbb{Z}_7\\).

> **Athena’s Wisdom**: Whether you reduce first or operate then reduce, the result is the same—modular arithmetic’s magic ensures consistency!

#### Addition
\\[
(a + b) \mod n
\\]
**Example 1**: Compute \\(5 + 4 \mod 7\\).
- **Reduce First**: \\(5 \mod 7 = 5\\), \\(4 \mod 7 = 4\\), then \\(5 + 4 = 9 \mod 7 = 2\\).
- **Add Then Reduce**: \\(5 + 4 = 9 \mod 7 = 2\\).

**Example 2**: Compute \\(12 + 19 \mod 7\\).
- **Reduce First**: \\(12 \mod 7 = 5\\) (since \\(12 = 7 \cdot 1 + 5\\)), \\(19 \mod 7 = 5\\) (since \\(19 = 7 \cdot 2 + 5\\)), then \\(5 + 5 = 10 \mod 7 = 3\\).
- **Add Then Reduce**: \\(12 + 19 = 31 \mod 7 = 3\\) (since \\(31 = 7 \cdot 4 + 3\\)).

**Property**: Commutative (\\(a + b \equiv b + a \mod n\\)). Try \\(4 + 5 \mod 7\\): both give 2.

#### Subtraction
\\[
(a - b) \mod n
\\]
**Example 1**: Compute \\(6 - 3 \mod 7\\).
- **Reduce First**: \\(6 \mod 7 = 6\\), \\(3 \mod 7 = 3\\), then \\(6 - 3 = 3 \mod 7 = 3\\).
- **Subtract Then Reduce**: \\(6 - 3 = 3 \mod 7 = 3\\).

**Example 2**: Compute \\(15 - 8 \mod 7\\).
- **Reduce First**: \\(15 \mod 7 = 1\\) (since \\(15 = 7 \cdot 2 + 1\\)), \\(8 \mod 7 = 1\\) (since \\(8 = 7 \cdot 1 + 1\\)), then \\(1 - 1 = 0 \mod 7 = 0\\).
- **Subtract Then Reduce**: \\(15 - 8 = 7 \mod 7 = 0\\).

**Property**: Each element has an additive inverse (e.g., \\(6 + 1 = 7 \mod 7 = 0\\), so 1 is the inverse of 6).

#### Multiplication
\\[
(a \cdot b) \mod n
\\]
**Example 1**: Compute \\(3 \cdot 4 \mod 7\\).
- **Reduce First**: \\(3 \mod 7 = 3\\), \\(4 \mod 7 = 4\\), then \\(3 \cdot 4 = 12 \mod 7 = 5\\).
- **Multiply Then Reduce**: \\(3 \cdot 4 = 12 \mod 7 = 5\\).

**Example 2**: Compute \\(12 \cdot 7001 \mod 7\\).
- **Reduce First**: \\(12 \mod 7 = 5\\) (since \\(12 = 7 \cdot 1 + 5\\)), \\(7001 \mod 7 = 1\\) (since \\(7001 = 7 \cdot 1000 + 1\\)), then \\(5 \cdot 1 = 5 \mod 7 = 5\\).
- **Multiply Then Reduce**: \\(12 \cdot 7001 = 84012 \mod 7 = 5\\) (since \\(84012 = 7 \cdot 12001 + 5\\)).

**Property**: Distributive (\\(a \cdot (b + c) \equiv a \cdot b + a \cdot c \mod n\\)). For example, \\(2 \cdot (3 + 4) \equiv 2 \cdot 3 + 2 \cdot 4 \mod 7\\).

#### Division
Division by \\(b\\) requires the multiplicative inverse \\(b^{-1}\\), where:
\\[
b \cdot b^{-1} \equiv 1 \pmod{n}, \quad \gcd(b, n) = 1
\\]
Then:
\\[
a \div b \equiv a \cdot b^{-1} \pmod{n}
\\]
An inverse exists only if \\(\gcd(b, n) = 1\\). In \\(\mathbb{Z}_7\\), since 7 is prime, all non-zero elements have inverses.

**Example 1**: Compute \\(3 \div 5 \mod 7\\) (i.e., solve \\(5x \equiv 3 \mod 7\\)).
- Find inverse of 5: \\(5 \cdot 3 = 15 \mod 7 = 1\\) (since \\(15 = 7 \cdot 2 + 1\\)), so \\(5^{-1} = 3\\).
- Then: \\(x \equiv 3 \cdot 3 = 9 \mod 7 = 2\\).

**Example 2**: Solve \\(4x \equiv 2 \mod 7\\).
- Inverse of 4: \\(4 \cdot 2 = 8 \mod 7 = 1\\), so \\(4^{-1} = 2\\).
- Then: \\(x \equiv 2 \cdot 2 = 4 \mod 7 = 4\\).

**Property**: Since 7 is prime, \\(\mathbb{Z}_7\\) is a field, ideal for cryptographic operations like decryption.

### Arithmetic Operations in \\(\mathbb{Z}_n\\)

In \\(\mathbb{Z}_n\\), we perform operations and reduce modulo \\(n\\). We can compute in two ways:
1. **Reduce First**: Compute the remainder of each operand modulo \\(n\\), then perform the operation.
2. **Operate Then Reduce**: Perform the operation, then reduce modulo \\(n\\).

**Exercise**:
1. Compute \\(20 + 13 \mod 7\\) using both methods.
2. Compute \\(15 - 9 \mod 7\\) using both methods.
3. Compute \\(10 \cdot 16 \mod 7\\) using both methods.
4. Solve \\(3x \equiv 6 \mod 7\\) using the inverse method.

**Solutions (for instructors)**:
1. **Reduce First**: \\(20 \mod 7 = 6\\), \\(13 \mod 7 = 6\\), \\(6 + 6 = 12 \mod 7 = 5\\). **Add Then Reduce**: \\(20 + 13 = 33 \mod 7 = 5\\).
2. **Reduce First**: \\(15 \mod 7 = 1\\), \\(9 \mod 7 = 2\\), \\(1 - 2 = -1 \mod 7 = 6\\). **Subtract Then Reduce**: \\(15 - 9 = 6 \mod 7 = 6\\).
3. **Reduce First**: \\(10 \mod 7 = 3\\), \\(16 \mod 7 = 2\\), \\(3 \cdot 2 = 6 \mod 7 = 6\\). **Multiply Then Reduce**: \\(10 \cdot 16 = 160 \mod 7 = 6\\) (since \\(160 = 7 \cdot 22 + 6\\)).
4. Inverse of 3: \\(3 \cdot 5 = 15 \mod 7 = 1\\), so \\(3^{-1} = 5\\). Then \\(x \equiv 6 \cdot 5 = 30 \mod 7 = 2\\). Verify: \\(3 \cdot 2 = 6 \mod 7\\).

### 📈 Modular Exponentiation: Big Powers, Small Results

Modular exponentiation computes \\(a^b \mod n\\), raising a number to a power and taking the remainder modulo \\(n\\). It’s vital for RSA encryption, handling large exponents efficiently. Reducing first is practical for cryptography, as it keeps numbers manageable.

> **Athena’s Guidance**: Exponentiation in \\(\mathbb{Z}_n\\) is like a merry-go-round—big spins land on the same few spots!

#### Key Property: Exponentiation and Congruence
If \\(a \equiv b \pmod{n}\\), does \\(a^m \equiv b^m \pmod{n}\\)? Yes, always!

**Proof**: If \\(a \equiv b \pmod{n}\\), then:
\\[
a = b + k n \quad \text{for some integer } k
\\]
For \\(m = 2\\):
\\[
a^2 = (b + k n)^2 = b^2 + 2 b k n + (k n)^2 \equiv b^2 \mod n
\\]
Since \\(2 b k n\\) and \\((k n)^2\\) are divisible by \\(n\\). For general \\(m\\), \\(a^m = (b + k n)^m\\) has terms with \\(n\\), so:
\\[
a^m \equiv b^m \mod n
\\]

> **Hermes’ Wink**: If two numbers look the same modulo \\(n\\), their powers do too—like twins who age identically!

#### Examples of Modular Exponentiation
**Example 1**: Compute \\(21^{2025} \mod 5\\).
- Reduce: \\(21 \mod 5 = 1\\) (since \\(21 = 5 \cdot 4 + 1\\)).
- Since \\(21 \equiv 1 \mod 5\\):
  \\[
  21^{2025} \equiv 1^{2025} \equiv 1 \mod 5
  \\]
- Verify: \\(21^2 = 441 \mod 5 = 1\\), so \\(21^{2025} \equiv 1 \mod 5\\).

**Example 2**: Compute \\(3^3 \mod 7\\).
- Direct: \\(3^3 = 27 \mod 7 = 6\\) (since \\(27 = 7 \cdot 3 + 6\\)).
- Step-by-step: \\(3^1 \equiv 3\\), \\(3^2 \equiv 9 \mod 7 = 2\\), \\(3^3 \equiv 2 \cdot 3 \equiv 6 \mod 7\\).
- Property: \\(3 \equiv 10 \mod 7\\), so \\(10^3 \equiv 1000 \mod 7 = 6\\).

**Example 3**: Compute \\(2^4 \mod 5\\).
- Direct: \\(2^4 = 16 \mod 5 = 1\\) (since \\(16 = 5 \cdot 3 + 1\\)).
- Step-by-step: \\(2^1 \equiv 2\\), \\(2^2 \equiv 4\\), \\(2^4 \equiv 4^2 \equiv 16 \mod 5 = 1\\).
- Property: \\(2 \equiv 7 \mod 5\\), so \\(7^4 \equiv 2401 \mod 5 = 1\\).

> **Chad**: “Shrinking big numbers first makes these powers easy? Perfect for cryptography!”

#### Fun Exercises: Exponentiation Quests
1. **Wizard’s Spell**: Compute \\(13^{2025} \mod 5\\). Hint: Reduce \\(13 \mod 5\\).
2. **Hermes’ Quick Trick**: Find \\(4^3 \mod 7\\). Use direct and step-by-step methods. Check with \\(4 \equiv 11 \mod 7\\).
3. **Athena’s Puzzle**: Compute \\(3^5 \mod 6\\). Why does \\(\mathbb{Z}_6\\) differ from \\(\mathbb{Z}_5\\)? Hint: Consider inverses.
4. **Crypto Challenge**: In toy RSA, message \\(m = 2\\) is encrypted as \\(c = m^3 \mod 7\\). Find \\(c\\). Verify with \\(m \equiv 9 \mod 7\\).

**Solutions (for instructors)**:
1. \\(13 \mod 5 = 3\\). Since \\(3^4 = 81 \mod 5 = 1\\), \\(3^{2025} = 3^{2024} \cdot 3 \equiv 1^{506} \cdot 3 \equiv 3 \mod 5\\).
2. Direct: \\(4^3 = 64 \mod 7 = 1\\). Step-by-step: \\(4^1 \equiv 4\\), \\(4^2 \equiv 16 \mod 7 = 2\\), \\(4^3 \equiv 2 \cdot 4 \equiv 1\\). Property: \\(11^3 = 1331 \mod 7 = 1\\).
3. \\(3^5 = 243 \mod 6 = 3\\). In \\(\mathbb{Z}_6\\), \\(\gcd(3, 6) \neq 1\\), so no inverse, unlike \\(\mathbb{Z}_5\\), a field.
4. \\(2^3 = 8 \mod 7 = 1\\). Since \\(9 \equiv 2 \mod 7\\), \\(9^3 = 729 \mod 7 = 1\\).

> **Athena’s Tip**: Exponentiation in \\(\mathbb{Z}_n\\) powers secure systems like RSA. Master it to unlock cryptography’s secrets!
