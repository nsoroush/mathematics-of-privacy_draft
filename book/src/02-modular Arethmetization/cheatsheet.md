
### 📜 Cheatsheet: Modular Arithmetic in \( \mathbb{Z}_n \)

**Definition**: \( \mathbb{Z}_n = \{0, 1, 2, \dots, n-1\} \), where each integer is represented by its remainder modulo \( n \), based on the **Division Theorem**: for any integer \( a \), there exist unique \( q, r \) such that \( a = n \cdot q + r \), \( 0 \leq r < n \), and \( a \equiv r \mod n \).

**Operations**:
1. **Addition**: \( (a + b) \mod n \)
   - Example: In \( \mathbb{Z}_6 \), \( 4 + 5 = 9 \mod 6 = 3 \).
2. **Subtraction**: \( (a - b) \mod n \)
   - Example: In \( \mathbb{Z}_6 \), \( 2 - 4 = -2 \mod 6 = 4 \).
3. **Multiplication**: \( (a \cdot b) \mod n \)
   - Example: In \( \mathbb{Z}_6 \), \( 3 \cdot 4 = 12 \mod 6 = 0 \).
4. **Division**: Multiply by the multiplicative inverse of \( a \), where \( a \cdot x \equiv 1 \mod n \), if \( \gcd(a, n) = 1 \).
   - Example: In \( \mathbb{Z}_5 \), inverse of 3 is 2 (since \( 3 \cdot 2 = 6 \mod 5 = 1 \)).
5. **Exponentiation**: \( a^b \mod n \)
   - Example: In \( \mathbb{Z}_6 \), \( 2^5 = 32 \mod 6 = 2 \).

Now after defining the arethmetization in Z_n, let's go and see some properties 
**Properties**:
- **Closure**: For \( a, b \in \mathbb{Z}_n \), the results of addition, subtraction, and multiplication are in \( \mathbb{Z}_n \). 
- **Commutativity**:
  - Addition: \( a + b \equiv b + a \mod n \).
  - Multiplication: \( a \cdot b \equiv b \cdot a \mod n \).
- **Associativity**:
  - Addition: \( (a + b) + c \equiv a + (b + c) \mod n \).
  - Multiplication: \( (a \cdot b) \cdot c \equiv a \cdot (b \cdot c) \mod n \).
- **Distributivity**: \( a \cdot (b + c) \equiv (a \cdot b) + (a \cdot c) \mod n \).
- **Identity Elements**:
  - Addition: 0, since \( a + 0 \equiv a \mod n \).
  - Multiplication: 1, since \( a \cdot 1 \equiv a \mod n \).
- **Additive Inverses**: For each \( a \in \mathbb{Z}_n \), there exists \( b \) such that \( a + b \equiv 0 \mod n \) (e.g., in \( \mathbb{Z}_6 \), the inverse of 5 is 1 since \( 5 + 1 = 6 \mod 6 = 0 \)).
- **Multiplicative Inverses**: For \( a \in \mathbb{Z}_n \), an inverse \( x \) such that \( a \cdot x \equiv 1 \mod n \) exists if \( \gcd(a, n) = 1 \).
- **Group Structure**: \( \mathbb{Z}_n \) is a commutative group under addition (closed, associative, identity, inverses).
- **Field Structure**: If \( n \) is prime, \( \mathbb{Z}_n \) is a field (all non-zero elements have multiplicative inverses).
- **Modular Properties**:
  - \( a \equiv b \mod n \implies a + c \equiv b + c \mod n \), \( a \cdot c \equiv b \cdot c \mod n \).
  - \( (a \mod n) + (b \mod n) \equiv (a + b) \mod n \).
  - \( (a \mod n) \cdot (b \mod n) \equiv (a \cdot b) \mod n \).

**Cryptographic Relevance**: Finite set ensures efficiency, inverses enable division-like operations, and hard-to-reverse operations (e.g., exponentiation) ensure security.

---

### 🌟 Properties in Action: Examples in \( \mathbb{Z}_n \)

To solidify our understanding, let’s explore the properties of modular arithmetic through examples in \( \mathbb{Z}_6 \) and \( \mathbb{Z}_5 \). These examples will demonstrate addition, subtraction, multiplication, division (via inverses), and exponentiation, while highlighting the algebraic properties listed in the cheatsheet.

> **Athena’s Guidance**: Watch how these operations wrap around like a clock, preserving structure and enabling cryptographic magic.

#### Example 1: Addition and Commutativity in \( \mathbb{Z}_6 \)
Compute \( 4 + 3 \) and \( 3 + 4 \):
- \( 4 + 3 = 7 \mod 6 = 1 \).
- \( 3 + 4 = 7 \mod 6 = 1 \).
**Property**: Commutativity (\( a + b \equiv b + a \mod n \)). The order doesn’t matter, which simplifies computations in cryptographic algorithms.

#### Example 2: Associativity of Addition in \( \mathbb{Z}_6 \)
Compute \( (2 + 3) + 4 \) and \( 2 + (3 + 4) \):
- Left: \( 2 + 3 = 5 \), then \( 5 + 4 = 9 \mod 6 = 3 \).
- Right: \( 3 + 4 = 7 \mod 6 = 1 \), then \( 2 + 1 = 3 \mod 6 = 3 \).
**Property**: Associativity (\( (a + b) + c \equiv a + (b + c) \mod n \)). This ensures consistent results regardless of grouping.

#### Example 3: Subtraction and Additive Inverse in \( \mathbb{Z}_6 \)
Compute \( 5 - 2 \) and find the additive inverse of 5:
- \( 5 - 2 = 3 \mod 6 = 3 \).
- Additive inverse of 5: Find \( b \) such that \( 5 + b \equiv 0 \mod 6 \). Try \( b = 1 \): \( 5 + 1 = 6 \mod 6 = 0 \). So, the inverse is 1.
**Property**: Every element has an additive inverse, making \( \mathbb{Z}_n \) a group under addition, crucial for cryptographic operations like key cancellation.

#### Example 4: Multiplication and Distributivity in \( \mathbb{Z}_6 \)
Compute \( 2 \cdot (3 + 4) \) and \( 2 \cdot 3 + 2 \cdot 4 \):
- Left: \( 3 + 4 = 7 \mod 6 = 1 \), then \( 2 \cdot 1 = 2 \mod 6 = 2 \).
- Right: \( 2 \cdot 3 = 6 \mod 6 = 0 \), \( 2 \cdot 4 = 8 \mod 6 = 2 \), then \( 0 + 2 = 2 \mod 6 = 2 \).
**Property**: Distributivity (\( a \cdot (b + c) \equiv a \cdot b + a \cdot c \mod n \)). This is essential for algorithms like RSA, where operations combine addition and multiplication.

#### Example 5: Division via Inverse in \( \mathbb{Z}_5 \)
Solve \( 4x \equiv 3 \mod 5 \):
- Find the inverse of 4: Try values:
  - \( 4 \cdot 4 = 16 \mod 5 = 1 \). So, the inverse is 4.
- Multiply both sides by 4: \( 4 \cdot 4 \cdot x \equiv 4 \cdot 3 \mod 5 \), so \( 1 \cdot x \equiv 12 \mod 5 = 2 \).
- Solution: \( x = 2 \). Verify: \( 4 \cdot 2 = 8 \mod 5 = 3 \).
**Property**: Multiplicative inverses exist in \( \mathbb{Z}_5 \) for non-zero elements because 5 is prime, making \( \mathbb{Z}_5 \) a field. This enables division-like operations critical for decryption.

#### Example 6: No Inverse in \( \mathbb{Z}_6 \)
Does 3 have an inverse in \( \mathbb{Z}_6 \)?
- Try: \( 3 \cdot 1 = 3 \), \( 3 \cdot 2 = 6 \mod 6 = 0 \), \( 3 \cdot 3 = 9 \mod 6 = 3 \), \( 3 \cdot 4 = 12 \mod 6 = 0 \), \( 3 \cdot 5 = 15 \mod 6 = 3 \).
- No value gives \( 3 \cdot x \equiv 1 \mod 6 \). Since \( \gcd(3, 6) = 3 \neq 1 \), no inverse exists.
**Property**: Inverses require \( \gcd(a, n) = 1 \). In \( \mathbb{Z}_6 \), only 1 and 5 have inverses.

#### Example 7: Exponentiation in \( \mathbb{Z}_6 \)
Compute \( 2^4 \mod 6 \):
- \( 2^1 = 2 \), \( 2^2 = 4 \), \( 2^3 = 8 \mod 6 = 2 \), \( 2^4 = 16 \mod 6 = 4 \).
**Property**: Closure ensures results stay in \( \mathbb{Z}_6 \). Exponentiation is key in cryptography (e.g., RSA’s \( m^e \mod n \)).

#### Example 8: Modular Property in \( \mathbb{Z}_6 \)
Compute \( 15 + 23 \mod 6 \) two ways:
- **Reduce first**: \( 15 \mod 6 = 3 \), \( 23 \mod 6 = 5 \), \( 3 + 5 = 8 \mod 6 = 2 \).
- **Add then reduce**: \( 15 + 23 = 38 \mod 6 = 2 \) (since \( 38 = 6 \cdot 6 + 2 \)).
**Property**: \( (a \mod n) + (b \mod n) \equiv (a + b) \mod n \). This flexibility simplifies large computations.

> **Hermes’ Wink**: These properties make \( \mathbb{Z}_n \) a playground for cryptography—finite, structured, and full of secrets!

**Exercise**:
1. In \( \mathbb{Z}_6 \), verify commutativity: Compute \( 5 + 2 \) and \( 2 + 5 \).
2. In \( \mathbb{Z}_6 \), show distributivity: Compute \( 3 \cdot (4 + 2) \) and \( 3 \cdot 4 + 3 \cdot 2 \).
3. In \( \mathbb{Z}_5 \), solve \( 3x \equiv 4 \mod 5 \).
4. In \( \mathbb{Z}_6 \), does 4 have a multiplicative inverse? Why?

**Solutions (for instructors)**:
1. \( 5 + 2 = 7 \mod 6 = 1 \), \( 2 + 5 = 7 \mod 6 = 1 \). Commutative.
2. Left: \( 4 + 2 = 6 \mod 6 = 0 \), \( 3 \cdot 0 = 0 \). Right: \( 3 \cdot 4 = 12 \mod 6 = 0 \), \( 3 \cdot 2 = 6 \mod 6 = 0 \), \( 0 + 0 = 0 \). Distributive.
3. Inverse of 3: \( 3 \cdot 2 = 6 \mod 5 = 1 \), so inverse is 2. Multiply by 2: \( x \equiv 4 \cdot 2 = 8 \mod 5 = 3 \). Verify: \( 3 \cdot 3 = 9 \mod 5 = 4 \).
4. \( \gcd(4, 6) = 2 \neq 1 \), so no inverse exists.

---