# 🧮 Mathematics of Privacy — Cheat Sheet: Sets & Set Theory

## 🔢 Number Sets: The VIPs of Math  
Meet the cool kids of numbers—cryptography’s favorite party guests!

**🧾 Table 1 — Number Set VIP List**

| Symbol | Set Name | What’s the Deal? |
|--------|----------|------------------|
| \\(\mathbb{N}\\) | Natural Numbers |\\(\{0, 1, 2, 3, \dots\}\\)or\\(\{1, 2, 3, \dots\}\\)— counting starts here! |
|\\(\mathbb{Z}\\)| Integers |\\(\{ \dots, -2, -1, 0, 1, 2, \dots \}\\)— the whole gang, positives and negatives! |
|\\(\mathbb{Q}\\)| Rational Numbers |\\(\frac{a}{b}\\)fractions (where\\(b \neq 0\\)) — math’s way of splitting the bill |
|\\(\mathbb{R}\\)| Real Numbers | Every spot on the number line — no gaps, just vibes |
|\\(\mathbb{C}\\)| Complex Numbers |\\(a + bi\\)where\\(i^2 = -1\\)— imaginary friends welcome! |
|\\(\mathbb{F}_p\\)| Finite Field (mod p) |\\(\{0, 1, \dots, p-1\}\\)with a prime\\(p\\)— crypto’s secret playground |


## 📚 Set Theory: Math’s LEGO Kit

### 🧮 Set Notation (aka How to Talk Set)
-\\(A = \{1, 2, 3\}\\): Consider these sets, as your set’s crew.
-\\(a \in A\\): “a’s in the club!, aka, a is in the set, we say\\(a\\)is the memebre.   
-\\(b \notin A\\): “b’s crashing elsewhere”  
-\\(|A|\\): How big’s the party? or how many memberes the set have, for examlpe\\(|A| = 3\\)and\\(|\mathbb{N}|\\)is infinity.

### 🧩 Set Operations: Mixin’ It Up

**📦 Table 2 — Set Operation Party Moves**

| Move | Symbol | What’s Happening? |
|------|--------|-------------------|
| Union |\\(A \cup B\\)| Everyone from A or B — no one’s left out! |
| Intersection |\\(A \cap B\\)| The VIP overlap of A and B |
| Difference |\\(A \setminus B\\)| A’s crew minus B’s gatecrashers |
| Complement |\\(\overline{A}\\)| Everything not invited to A’s bash |
| Cartesian Product |\\(A \times B\\)| Pairing up A and B like a math prom |
| Power Set |\\(\mathcal{P}(A)\\)| Every possible clique from A — party overload! |

### 🔁 Set Laws: Rules of the Dance Floor
- **Commutative:**\\(A \cup B = B \cup A\\)— order’s just a suggestion  
- **Associative:**\\((A \cup B) \cup C = A \cup (B \cup C)\\)— group hugs work either way  
- **Distributive:**\\(A \cap (B \cup C) = (A \cap B) \cup (A \cap C)\\)— sharing is caring  
- **De Morgan’s:**\\(\overline{A \cup B} = \overline{A} \cap \overline{B}\\)— opposites attract  
- **Identity:**\\(A \cup \emptyset = A\\)— empty’s no buzzkill here


## 🌐 Crypto’s Secret Sets
- \\(\mathbb{Z}_n\\): Numbers that loop at \\(n\\)— think of it as a math merry-go-round,
- \\( \mathbb{F}_p\\): Prime-powered fields where everyone’s got a dance partner (inverse)  
- \\( \mathbb{F}_{2^n}\\): Binary fields for SNARKs — the geekiest party in town  


# 🔢 Mathematics of Privacy — Cheat Sheet: Basic Number Theory  
This is your VIP pass to number theory—the sneaky math tricks behind cryptography’s coolest moves, from modular magic to zero-knowledge ninja skills!


## 🧮 The Basics: Number Nerd Starter Pack

### ✅ Divisibility: Who’s Splitting the Bill?
**WDefinition** \\(a\\) divides\\(b\\)(aka\\(a \mid b\\)) if\\(b = a \cdot k\\)for some integer\\(k\\).  
**Example:** \\(3 \mid 12\\) because \\(12 = 3 \times 4\\). 

### ✅ Prime Numbers: The Lone Wolves
Numbers bigger than 1 that only hang with 1 and themselves.  
**Why They Rule:** Crypto’s obsessed with these bad boys—big primes are the VIPs of security!

### ✅ Composite Numbers: The Group Chat
Numbers with extra buddies besides 1 and themselves.  
**Example:** 6 is composite—\\(2 \mid 6\\) and \\(3 \mid 6\\). It’s a social butterfly!


## 📐 Greatest Common Divisor (GCD): The Peacemaker

### ✅ What’s the Deal?
\\(\gcd(a, b)\\): The biggest number that crashes both\\(a\\)and\\(b\\)’s parties.  
**Fancy Name:** Sometimes just\\((a, b)\\)—math’s shorthand for “best buds.”

### ✅ Superpowers
-\\(\gcd(a, 0) = |a|\\)— zero’s a pushover!  
-\\(\gcd(a, b) = \gcd(b, a \mod b)\\)— Euclidean Algorithm’s remix magic  
-\\(\gcd(a, b) = 1 \Rightarrow a, b\\)are coprime (aka BFFs with no drama)

### ✅ Euclidean Algorithm: Math’s Dance-Off
How to find\\(\gcd(a, b)\\):  
1. Divide\\(a\\)by\\(b\\), grab the remainder\\(r\\) 
2. Swap it up:\\(a \leftarrow b\\),\\(b \leftarrow r\\) 
3. Keep grooving ‘til\\(r = 0\\)

**Party Example:**\\(\gcd(48, 18)\\) 
48 ÷ 18 = 2, leftover 12  
18 ÷ 12 = 1, leftover 6  
12 ÷ 6 = 2, leftover 0 → GCD = 6. Dance floor cleared!


## 🔁 Least Common Multiple (LCM): The Group Hangout

### ✅ What’s It About?
\\(\text{lcm}(a, b)\\): The smallest number that\\(a\\)and\\(b\\)both high-five.  
**Secret Handshake:**\\[\text{lcm}(a, b) = \frac{|a \cdot b|}{\gcd(a, b)}\\]
**Example:**\\(\text{lcm}(12, 18) = \frac{12 \cdot 18}{6} = 36\\). Everyone’s invited!


## 🔄 Multiplicative Inverses: Math’s Wingmen

### ✅ The Scoop
\\(x\\)is\\(a\\)’s modular inverse mod\\(n\\)if:  
\\(a \cdot x \equiv 1 \mod n\\)
Basically,\\(x\\)gets\\(a\\)back to 1 in the modulo club.

### ✅ VIP Access?
Only works if\\(\gcd(a, n) = 1\\)— no gatecrashers allowed!  
**How to Find It:** Bust out the Extended Euclidean Algorithm like a pro.



## 📊 Divisibility Rules: Quick Math Hacks

**🔍 Table 3 — Quick Divisibility Hacks**

| Divisor | Cheat Code (in base 10) |
|---------|--------------------------|
| 2 | Ends in an even number—easy peasy! |
| 3 | Add the digits, check if 3 likes it |
| 5 | Ends in 0 or 5—high-five! |
| 9 | Sum the digits, 9’s gotta approve |



## 🧠 Cool Terms to Flex

- **Relatively Prime (Coprime):**\\(\gcd(a, b) = 1\\)— these two don’t share secrets!  
- **Unit (mod n):**\\(a\\)with\\(\gcd(a, n) = 1\\)— it’s got a modular inverse and swagger.  
- **Congruence:**\\(a \equiv b \mod n \Rightarrow n \mid (a - b)\\)— numbers in sync!  
- **Modular Arithmetic:** Math with a wrap-around vibe—think of it as a number carousel!
