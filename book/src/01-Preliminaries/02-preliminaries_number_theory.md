# When the Gods Split Numbers: A Tale of Division and Primal Power

Last time, we explored sets like natural numbers \\(\mathbb{N}\\), integers \\(\mathbb{Z}\\), rationals \\(\mathbb{Q}\\), and reals \\(\mathbb{R}\\). Now, let's find the perfect set for cryptography—a set where numbers follow strict rules, keeping our computations safe. 

This property, called closure, means operations like adding or multiplying stay inside the set, like moves on a secure chessboard. In cryptography, we define a set and prove our secrets are safe as long as we stay within it. If a computation jumps out, we risk exposing vulnerabilities—our secrets could leak!

Let's start with the natural numbers, \\(\mathbb{N} = \lbrace 1, 2, \ldots\rbrace\\). Start at 5 and add 4 repeatedly:
\\[5 \to 5 + 4 = 9 \to 9 + 4 = 13 \to 13 + 4 = 17 \to \ldots \\]
Each result \\(9, 13, 17, \ldots\\) is in \\(\mathbb{N}\\). Addition is closed—safe so far!

> Hermes claps: `Natural numbers are crypto-ready, right!`
>
> Athena: `Not yet, Hermes! Try subtraction. Start at 23, subtract 7 each time:`
\\[23 \to 23 - 7 = 16 \to 16 - 7 = 9 \to 9 - 7 = 2 \to 2 - 7 = -5\\]
>`Danger,! -5 isn't in` \\(\mathbb{N}\\)`! Subtraction breaks closure—we've jumped out of the set, risking our secret!`


To fix this, let's try a bigger set: the integers, \\(\mathbb{Z} = \lbrace \ldots, -2, -1, 0, 1, 2, \ldots\rbrace\\). 

Start at 6:
- Addition: \\(6 \to 6 + 5 = 11 \to 11 + 5 = 16 \to \ldots\\) Integers—safe!
- Subtraction: \\(6 \to 6 - 5 = 1 \to 1 - 5 = -4 \to \ldots\\) Integers—safe!
- Multiplication: \\(6 \to 6 \cdot 5 = 30 \to 30 \cdot 5 = 150 \to \ldots\\) Integers—safe!
- Division: \\(6 \to 6 \div 2 = 3 \to 3 \div 2 = 1.5\\)

> Hermes whispers. `Trouble in paradise! 1.5 isn't in` \\(\mathbb{Z}\\)`! What about` \\(\mathbb{Q}\\)—`it's got fractions!`

Yes! Division's tricky in \\(\mathbb{Z}\\), and using \\(\mathbb{Q}\\) seems a nice try, it's closed for addition, subtraction, multiplication, and division (except by zero) but \\(\mathbb{Q}\\) has its own issues. , for example, fractions like \\(1.5\\) or \\(\frac 2 3\\) are messy to compute precisely. Also:
- Too many, too continuse,! Here's why \\(\mathbb{Q}\\) fails crypto:”
- Too complex: Fractions require arbitrary precision, slowing computations.
- Not finite: Cryptography needs compact sets for keys, not infinite rationals.
- Messy structure: \\(\mathbb{Q}\\) lacks the discrete clarity of \\(\mathbb{Z}\\) for modular systems.
We'll soon see modular arithmetic's finite sets—crypto's true home! 

Athena conclude: Integers \\(\mathbb{Z}\\) are our crypto champions! Closed for addition, subtraction, and multiplication, they offer a structured playground. Division's hiccups? They lead us to modular arithmetic, where we wrap numbers like a clock, keeping everything discrete. Unlike fractions or reals, integers' clear, countable nature ensures precision and security—cryptography's must-haves.


### What About Division?

Now, let's tackle **division**—it's trickier than the others. Division doesn't always play nice in \\(\mathbb{Z}\\). Let's start with a simple case. Suppose we divide 6 by 3:  

 \\(6 = 2 \cdot 3\\), so \\(6 \div 3 = 2\\)—an integer. Perfect!  
 But try dividing 6 by 5? Nope.  
 \\(6 \div 5 = 1.2\\), and 1.2 is **not** an integer.  
 Some pairs work smoothly, others don't.”

This brings us to a key idea: **divisibility**.

#### **🟩 Definition: Divisibility**

An integer \\(a\\) **divides** an integer \\(b\\), written \\(a \mid b\\), if there's an integer \\(k\\) such that:
\\[b = a \cdot k\\]
If no such \\(k\\) exists, we write \\(a \nmid b\\).

- Example: \\(3 \mid 6\\), because \\(6 = 3 \cdot 2\\)  
- But \\(5 \nmid 6\\), since no integer \\(k\\) satisfies \\(6 = 5 \cdot k\\)

### **Division With Remainders**

Now, what happens when division **isn't exact**—like dividing 7 by 4?


> Try \\(7 \div 4\\). We can write:  
> \\[> 7 = 1 \cdot 4 + 3> \\]  
> where 1 is the quotient, and 3 is the remainder—what's left after taking out 4 once.

Could we also write:
\\[
7 = 0 \cdot 4 + 7 \quad \text\lbrace or\rbrace \quad 7 = 2 \cdot 4 - 1?
\\]
Yes, mathematically, they're valid. But **when we talk about division with remainder**, we want the remainder to be:
- **what's left** after subtracting as many full 4s as we can
- and it must be **less than the divisor**

So, by repeatedly subtracting 4 from 7:
\\[
7 - 4 = 3 \quad \text\lbrace (and we stop)\rbrace
\\]
We're left with 3. So the correct remainder is 3:
\\[
7 = 1 \cdot 4 + 3
\\]

> ✅ **Important:**  
> The **remainder should always be less than the divisor**.


> **Hermes tilts his head:**  `So, division's messy because remainders pop up?`
>
> **Athena nods:**  `Exactly! In \\(\mathbb{Z}\\), division gives integers **only when** one number divides another exactly. Otherwise, we get fractions, like \\(7 \div 4 = 1.75\\), which kicks us **out of \\(\mathbb{Z}\\)**.This lack of closure under division is one reason we turn to **modular arithmetic** in cryptography—it **wraps remainders** into a neat, secure system.


### **Another Example: 11 Divided by 4**

\\[
11 = 2 \cdot 4 + 3
\\]

- 2 is the **quotient**
- 3 is the **remainder**, since \\(11 - 2 \cdot 4 = 3\\), and \\(3 < 4\\)

Even though we could write:
\\[
11 = 1 \cdot 4 + 7
\\]
that **7 is not a valid remainder**, because it's **not less than** 4.

This idea brings us to one of the **foundational theorems in mathematics**.

> **📜 Theorem: Division Theorem** 
> For any integer \\(n\\), and any **positive integer** \\(d\\), there exist **unique integers** \\(q\\) (the quotient) and \\(r\\) (the remainder) such that:
\\[
n = q \cdot d + r \quad \text\lbrace with\rbrace \quad 0 \leq r < d
\\]

This theorem guarantees:
- **Existence** of a quotient and remainder
- **Uniqueness** of that pair \\((q, r)\\) for a given \\(n\\) and \\(d\\)

It's not just useful—it's foundational to the **modular systems** cryptography is built on.

Now that we've mastered **divisibility**, let's explore deeper properties of numbers—starting with their **divisors**. Let's count how many **positive divisors** a number has. We'll use the notation \\(d(n)\\) to represent the **number of positive divisors** of a number \\(n\\).”


### 🟩 Challenge yourself: Define \\(d(n)\\) Using Set Theory

Let:
\\[
D_n = \\lbrace  a \in \mathbb{Z} \mid a > 0 \text\lbrace  and \rbrace \exists b \in \mathbb{Z} \text\lbrace  such that \rbrace n = a \cdot b \\rbrace
\\]
Then:
\\[
d(n) = |D_n|
\\]

Let's look at some examples:

- **Divisors of 12:**  
  \\[
  \\lbrace 1, 2, 3, 4, 6, 12\\rbrace \Rightarrow d(12) = 6
  \\]

- **Divisors of 15:**  
  \\[
  \\lbrace 1, 3, 5, 15\\rbrace \Rightarrow d(15) = 4
  \\]



> **Hermes jumps up, eyes wide:**  
> This reminds me of set theory! Divisors seem to pair up like subsets:  
> - For 6 → \\((1,6), (2,3)\\)  
> - For 15 → \\((1,15), (3,5)\\)  
> So maybe \\(d(n)\\) is always even!”



> **Athena raises an eyebrow:**  
> Interesting, Hermes. But let's test a few more before jumping to conclusions.”



Try:

- \\(d(4) = 3\\) from \\(\\lbrace 1, 2, 4\\rbrace\\)
- \\(d(9) = 3\\) from \\(\\lbrace 1, 3, 9\\rbrace\\)

These are **odd**! The reason? These are **perfect squares**, and the square root counts only once as a divisor (e.g., \\(2 \cdot 2 = 4\\)).



Now let's test numbers with exactly **two** divisors:

- \\(d(5) = 2\\): \\(\\lbrace 1, 5\\rbrace\\)  
- \\(d(7) = 2\\): \\(\\lbrace 1, 7\\rbrace\\)  
- \\(d(11) = 2\\): \\(\\lbrace 1, 11\\rbrace\\)

These are **prime numbers**.


### 🧠 Definitions: Prime and Composite Numbers

- A **prime number** is an integer \\(> 1\\) with exactly **two** positive divisors.
- A **composite number** has **more than two** divisors.



> **Athena concludes:**  
> Primes are the **building blocks** of the integers—and the backbone of cryptography. Primes lock secrets, and composites—especially large ones—are the keys to hiding them.”


## 🔐 GCD, LCM, Co-Primes & Algorithms That Power Privacy

With **divisors and primes** in our toolkit, we're ready to unlock more number-theoretic treasures—concepts that directly power cryptographic systems:  
- **Greatest Common Divisor (GCD)**  
- **Least Common Multiple (LCM)**  
- **Co-prime numbers**  
- **Euclidean Algorithm & Extended Euclidean Algorithm**



> **Athena holds up two numbers:**  
> Numbers talk to each other through their divisors. Let's see how they share common ground—and how we can use this structure to protect secrets.”



### 🧱 Greatest Common Divisor (GCD)

The **greatest common divisor** of two integers \\(a\\) and \\(b\\), not both zero, is the largest positive integer that divides both.



#### **Example 1: \\(\gcd(12, 18)\\)**

- \\(D_\lbrace 12\rbrace = \\lbrace 1, 2, 3, 4, 6, 12\\rbrace\\)  
- \\(D_\lbrace 18\rbrace = \\lbrace 1, 2, 3, 6, 9, 18\\rbrace\\)  
- Common divisors: \\(\\lbrace 1, 2, 3, 6\\rbrace\\)  
- ✅ So, \\(\gcd(12, 18) = 6\\)



### 🤝 Co-Prime Numbers

Two integers \\(a\\) and \\(b\\) are called **co-prime** (or **relatively prime**) if:
\\[
\gcd(a, b) = 1
\\]

They share **no common positive divisors** except 1.



#### **Example 2: Are 15 and 28 co-prime?**

- \\(D_\lbrace 15\rbrace = \\lbrace 1, 3, 5, 15\\rbrace\\)  
- \\(D_\lbrace 28\rbrace = \\lbrace 1, 2, 4, 7, 14, 28\\rbrace\\)  
- Common divisors: \\(\\lbrace 1\\rbrace\\)

✅ \\(\gcd(15, 28) = 1\\) → They are **co-prime**.



#### **Example 3: Are 12 and 9 co-prime?**

- \\(D_\lbrace 12\rbrace = \\lbrace 1, 2, 3, 4, 6, 12\\rbrace\\)  
- \\(D_\lbrace 9\rbrace = \\lbrace 1, 3, 9\\rbrace\\)  
- Common divisors: \\(\\lbrace 1, 3\\rbrace\\)

❌ \\(\gcd(12, 9) = 3\\) → Not co-prime.



### 🔁 Multiples and the Path to LCM

Let's talk about **multiples** of a single number.

> **Athena points to the board:**  
> While divisors go inward—asking *what divides this number?*—multiples go outward:  
> *What numbers can we build by multiplying this one?*”



### 📐 Definition: Multiples of a Number

For a positive integer \\(a\\), the **set of multiples** of \\(a\\) is:
\\[
M_a = \\lbrace  a \cdot k \mid k \in \mathbb{N} \\rbrace
\\]

This set is **infinite** and contains all numbers divisible by \\(a\\).



#### **Example 4: Multiples of 3 and 4**

\\[
M_3 = \\lbrace 3, 6, 9, 12, 15, 18, \ldots\\rbrace
\\]  
\\[
M_4 = \\lbrace 4, 8, 12, 16, 20, 24, \ldots\\rbrace
\\]

✅ First common multiple: **12**  
This is called the **Least Common Multiple (LCM)**.



### 📌 Definition: Least Common Multiple (LCM)

For two positive integers \\(a\\) and \\(b\\), the **Least Common Multiple** is the **smallest positive integer divisible by both**:
\\[
\text{lcm}(a, b) = \min (M_a \cap M_b)
\\]

Or more practically:
\\[
\text{lcm}(a, b) = \frac{ |a \cdot b|}{\gcd(a, b)}
\\]



#### **Example 5: \\(\text{lcm}(3, 4)\\)**

Since \\(\gcd(3, 4) = 1\\):
\\[
\text{lcm}(3, 4) = \frac{ 3 \cdot 4}{1\rbrace = 12
\\]

✅ Check: \\(12 \div 3 = 4\\), \\(12 \div 4 = 3\\)



> **Hermes scratches his head:**  
> Athena, how does \\(\text{lcm}(a, b) = \frac{ a \cdot b}{\gcd(a, b)}\\) make sense? It's like a puzzle!”



> **Athena smiles and explains:**  
> We know \\(a \cdot b\\) is a common multiple:  
\\[
a \cdot b \div a = b, \quad a \cdot b \div b = a
\\]  
It works—but it might be more than we need.  

Suppose \\(\gcd(a, b) = d\\). Then:
\\[
a = a' \cdot d, \quad b = b' \cdot d
\\]  
So:
\\[
a \cdot b = (a' \cdot d)(b' \cdot d) = a' \cdot b' \cdot d^2
\\]

That \\(d^2\\) means we've double-counted the shared factors. To get the LCM, we divide out one \\(d\\):
\\[
\text{lcm}(a, b) = \frac{ a \cdot b}{\gcd(a, b)}
\\]
One copy of \\(d\\) is enough to cover both sides.”



#### **Example 6: Let's try \\(a = 6\\), \\(b = 4\\)**

- \\(\gcd(6, 4) = 2\\) → so \\(d = 2\\)  
- Express:
  \\[
  6 = 3 \cdot 2, \quad 4 = 2 \cdot 2
  \\]
  So \\(a' = 3\\), \\(b' = 2\\)

Then:
\\[
a \cdot b = 6 \cdot 4 = 24, \quad \text{but} \quad \text{lcm}(6, 4) = 3 \cdot 2 \cdot 2 = 12
\\]

Or use the formula:
\\[
\text{lcm}(6, 4) = \frac{ 6 \cdot 4}{2} = \frac{ 24}{2}= 12
\\]

✅ Check: \\(12 \div 6 = 2\\), \\(12 \div 4 = 3\\)

> **Hermes claps:**  
> We just kicked out the extra \\(d\\)! That's clean math magic.”

> **Athena nods:**  
> And it's not just elegant—it's **efficient**. This is why the LCM formula is crucial for syncing systems and encrypting data.”



### ⚙️ Euclidean Algorithm

An efficient method to compute \\(\gcd(a, b)\\) without listing divisors.

> **Algorithm Steps:**
1. Divide: \\(a = q \cdot b + r\\)  
2. Replace: \\(\gcd(a, b) = \gcd(b, r)\\)  
3. Repeat until the remainder is 0. The last non-zero remainder is \\(\gcd\\)



#### **Example 7: \\(\gcd(48, 18)\\)**

- \\(48 = 2 \cdot 18 + 12\\) → \\(\gcd(48, 18) = \gcd(18, 12)\\)  
- \\(18 = 1 \cdot 12 + 6\\) → \\(\gcd(18, 12) = \gcd(12, 6)\\)  
- \\(12 = 2 \cdot 6 + 0\\) → Stop.

✅ \\(\gcd(48, 18) = 6\\)

> **Hermes blinks:**  
> It's like a number dance—keep stepping until you stop!”

> **Athena laughs:**  
> Perfect, Hermes! This ‘dance' makes crypto computations fast.”



### 🧠 Extended Euclidean Algorithm

We can go further—not just find the GCD, but **express it** as a combination of \\(a\\) and \\(b\\):

> **Bézout's Identity:**  
Given \\(a, b\\), find \\(x, y \in \mathbb{Z}\\) such that:
\\[
a \cdot x + b \cdot y = \gcd(a, b)
\\]



#### **Example 8: Extended GCD for 48 and 18**

From earlier steps:

- \\(12 = 48 - 2 \cdot 18\\)  
- \\(6 = 18 - 1 \cdot 12\\)

Substitute back:
\\[
6 = 18 - 1 \cdot (48 - 2 \cdot 18) = 3 \cdot 18 - 1 \cdot 48
\\]  
So:
\\[
6 = (-1) \cdot 48 + 3 \cdot 18
\\]

✅ \\(x = -1, y = 3\\)

> **Hermes gasps:**  
> We're writing the GCD as a combo of 48 and 18? That's magic!”

> **Athena winks:**  
> It's a powerful trick, Hermes—those coefficients unlock **modular inverses**, essential for decryption.”



### 🧬 Fundamental Theorem of Arithmetic

> **Theorem:**  
Every integer \\(n > 1\\) can be written as a product of **prime numbers**, uniquely (up to the order of factors).



#### **Example 9: Factorize 60**

\\[
60 = 2 \cdot 30 = 2 \cdot 2 \cdot 15 = 2^2 \cdot 3 \cdot 5
\\]



#### **Example 10: Factorize 28**

\\[
28 = 2 \cdot 14 = 2^2 \cdot 7
\\]

✅ Try different methods—you'll always get the same **prime "DNA"**!

> **Athena beams:**  
> This uniqueness is why primes are cryptography's atoms—each number's genetic code securing encryption.”
