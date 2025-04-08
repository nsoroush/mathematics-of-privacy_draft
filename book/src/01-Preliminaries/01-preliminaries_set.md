
### Chapter 1: Preliminaries

#### Sets: The Building Blocks of Math’s Playground

Welcome to the world of sets—think of them as the LEGO bricks of mathematics. We use them to build everything from secret codes to zero-knowledge proofs. If you've ever wondered how cryptography groups things together or plays number games in clever ways, sets are your starting point. Let’s explore these mathematical gangs with our crew.
---

##### What’s a Set, Anyway?

A set is a collection of distinct elements—numbers, letters, or even your favorite snacks. We write sets using curly braces, like \\(\{1, 2, 3\}\\), which just means: “Here’s a group containing 1, 2, and 3.” Order doesn’t matter, and duplicates don’t count—\\(\{1, 2, 2, 3\}\\) is still just \\(\{1, 2, 3\}\\).

- **Notation Refresher**:
  - \\(a \in A\\): “\(a\) is a member of set \(A\).”
  - \\(b \notin A\\): “\(b\) is not in \(A\).”
  - \\(|A|\\): The number of elements in \(A\). For \\(A = \{1, 2, 3\}\\), that’s \\(|A| = 3\\).

> **Athena Says**: “By the wisdom of Olympus, sets define the boundaries of cryptographic knowledge—who's in the circle, and who's out.”

---

##### The Usual Suspects: Number Sets

These sets show up everywhere in math and cryptography. Think of them as the guest list for every important proof.

- \\(\mathbb{N}\\): **Natural Numbers**—\\(\{0, 1, 2, 3, \dots\}\\). (Some skip 0—we're flexible.)
- \\(\mathbb{Z}\\): **Integers**—\\(\{\dots, -2, -1, 0, 1, 2, \dots\}\\).
- \\(\mathbb{Q}\\): **Rational Numbers**—All fractions \\(\frac{a}{b}\\) with integers \\(a\\), \\(b \neq 0\\).
- \\(\mathbb{R}\\): **Real Numbers**—All values along the number line, like \\(\pi\\), \\(\sqrt{2}\\).
- \\(\mathbb{C}\\): **Complex Numbers**—Numbers like \\(a + bi\\), where \\(i^2 = -1\\).

And in crypto-land:
- \\(\mathbb{Z}_n\\): Integers modulo \(n\)—numbers that wrap around.
- \\(\mathbb{F}_p\\): Finite field with prime order \(p\)—small, structured, and perfect for cryptography.

---

##### Cool Example: Secret Club Membership

Imagine a secret crypto club:
- \\(A = \{ \text{Alice}, \text{Bob}, \text{Charlie} \}\\): The coders.
- \\(B = \{ \text{Bob}, \text{Dave} \}\\): The math nerds.

> **Chad Challenges**: “Bet you can crack this—what’s \\(A \cap B\\)? Who’s got double credentials?”
>
> *Answer*: \\(A \cap B = \{ \text{Bob} \}\\). Bob’s doing double duty.

Want the full list?  
\\(A \cup B = \{ \text{Alice}, \text{Bob}, \text{Charlie}, \text{Dave} \}\\).  
A packed conference!

**Another Example**:  
- \\(C = \{ \text{Charlie}, \text{Eve}, \text{Frank} \}\\): The protocol designers.  
- What’s \\(A \cap C\\)?  
  *Answer*: \\(\{ \text{Charlie} \}\\). Charlie’s bridging coding and design.  
- And \\(B \cup C\\)?  
  *Answer*: \\(\{ \text{Bob}, \text{Dave}, \text{Charlie}, \text{Eve}, \text{Frank} \}\\). A bigger party now!

---

##### Set Shenanigans: Operations

Here are the main ways we manipulate sets, with extra examples to flex your brain:

- **Union (\\(A \cup B\\))**: \\(\{1, 2\} \cup \{2, 3\} = \{1, 2, 3\}\\)  
  *More*: \\(\{ \text{apple}, \text{banana} \} \cup \{ \text{banana}, \text{cherry} \} = \{ \text{apple}, \text{banana}, \text{cherry} \}\\). No duplicates!
- **Intersection (\\(A \cap B\\))**: \\(\{1, 2\} \cap \{2, 3\} = \{2\}\\)  
  *More*: \\(\{ \text{red}, \text{blue} \} \cap \{ \text{blue}, \text{green} \} = \{ \text{blue} \}\\). Just the overlap.
- **Difference (\\(A \setminus B\\))**: \\(\{1, 2, 3\} \setminus \{2\} = \{1, 3\}\\)  
  *More*: \\(\{ \text{cat}, \text{dog}, \text{bird} \} \setminus \{ \text{dog} \} = \{ \text{cat}, \text{bird} \}\\). Dog’s out!
- **Complement (\\(\overline{A}\\))**: If \\(U = \{1, 2, 3, 4\}\\), \\(A = \{1, 2\}\\), then \\(\overline{A} = \{3, 4\}\\)  
  *More*: If \\(U = \{a, b, c\}\\), \\(A = \{a\}\\), then \\(\overline{A} = \{b, c\}\\).
- **Cartesian Product (\\(A \times B\\))**: \\(\{1, 2\} \times \{3\} = \{(1, 3), (2, 3)\}\\)  
  *More*: \\(\{ \text{heads}, \text{tails} \} \times \{1, 2\} = \{ (\text{heads}, 1), (\text{heads}, 2), (\text{tails}, 1), (\text{tails}, 2) \}\\). Coin flip combos!
- **Power Set (\\(\mathcal{P}(A)\\))**: \\(A = \{1, 2\}\\) → \\(\{\emptyset, \{1\}, \{2\}, \{1, 2\}\}\\)  
  *More*: \\(A = \{x\}\\) → \\(\{\emptyset, \{x\}\}\\). Small but mighty.

> **Hermes Crashes In**: “Wait! What’s the power set of the empty set?”
>
> **Athena Replies**: “Nice one, Hermes. It’s \\(\{\emptyset\}\\). Even nothing has something.”

---

##### Rules of the Set Party

Some basic laws we’ll use later:
- **Commutative**: \\(A \cup B = B \cup A\\)
- **Distributive**: \\(A \cap (B \cup C) = (A \cap B) \cup (A \cap C)\\)
- **De Morgan’s Laws**: \\(\overline{A \cup B} = \overline{A} \cap \overline{B}\\)

---

##### Coding Corner: Sets in Rust

Let’s bring in a bit of Rust code to show how you’d work with sets:

```rust
use std::collections::HashSet;

fn main() {
    let set_a: HashSet<i32> = [1, 3, 5].into_iter().collect();
    let set_b: HashSet<i32> = [3, 6].into_iter().collect();

    let intersection: Vec<_> = set_a.intersection(&set_b).collect();
    println!("Overlap crew: {:?}", intersection); // Prints: [3]
}
```

> **Athena Adds**: “This mirrors shared keys in cryptography—small intersections, big impact.”

---

##### Exercise: Chad’s Set Smackdown

> **Chad Challenges**: Take \\(A = \{1, 3, 5\}\\), \\(B = \{3, 6\}\\), \\(U = \{1, 2, 3, 4, 5, 6\}\\). Can you find:
> 1. \\(A \cup B\\)
> 2. \\(A \cap B\\)
> 3. \\(\overline{A}\\)
> Bonus: Code the intersection in Rust!
>
> **Answers**:
> - \\(A \cup B = \{1, 3, 5, 6\}\\)
> - \\(A \cap B = \{3\}\\)
> - \\(\overline{A} = \{2, 4, 6\}\\)

**Extra Challenge**: Now try \\(C = \{2, 4, 6\}\\), \\(D = \{4, 5, 6\}\\), same \\(U\\). Find:  
1. \\(C \cup D\\)  
2. \\(C \cap D\\)  
3. \\(D \setminus C\\)  
**Answers**:  
- \\(C \cup D = \{2, 4, 5, 6\}\\)  
- \\(C \cap D = \{4, 6\}\\)  
- \\(D \setminus C = \{5\}\\)

> **Hermes Interrupts**: “But what if \\(U = \emptyset\\)? Then what?”
>
> **Athena Replies**: “Good catch! If the universal set is empty, so is its complement. No battlefield, no battle.”


