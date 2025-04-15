> 
**In the beginning, there were only sets.**  
Before numbers marched in line and equations ruled the realm, there were sets—vast, primordial groupings where elements first found their place. This was the first order: not to calculate, but to belong.

> In this ancient landscape, the universe of mathematics was still formless. From the dust of abstraction, **Metis**, the spirit of wisdom, unrolled the **Scroll of Belonging**, weaving structure across the void. Everything began to find its place. And from this foundation, all mathematical worlds would eventually rise.
<div style="background-color: #d4edda; padding: 10px; border-radius: 5px; color: #155724;">

Welcome to the world of *sets*—the foundation of mathematics, like organizing bins for the universe! Whether you're sorting numbers, letters, or ideas, sets bring clarity to the chaos. Let's dive in with our crew: **Athena**, the wise guide, and **Hermes**, the curious questioner!

In this section, we'll explore what sets are, how to notate them, the curious empty set, subsets, and operations that combine sets in powerful ways. Sets are everywhere—from organizing data to underpinning cryptography—so let's get started!
</div>

## 1. Sets—The Building Blocks of Math's Playground
### 1.1 What's a Set, Anyway?
A **set** is a well-defined collection of distinct objects, called **elements** (or members). These can be numbers, letters, or even quirky things like your favorite snacks. The key is clarity: we must know exactly what's included. We write sets using curly braces \\(\lbrace \rbrace\\), and neither order nor duplicates matter—\\(\lbrace 1, 2, 2, 3\rbrace\\)is simply   \\(\lbrace 1, 2, 3\rbrace\\). 


- **Example 1**: The set of vowels: \\(S =\lbrace  a, e, i, o, u\rbrace \\). Here, \\(a \in S \\), but \\(z \notin S \\).  
- **Example 2**: Even numbers less than 10: \\(T = \lbrace 2, 4, 6, 8\rbrace \\). So, \\(4 \in T \\), but \\(3 \notin T \\).  
- **Example 3**: A fun set: \\(W = \lbrace  \text{pizza}, \text{soccer}, \text{blue} , 2, {4}\rbrace \\). It's valid as long as the context is clear!

> ****Hermes** raises his hand, smirking. `So, Athena, can I make a set of *all* my brilliant ideas? Or is that too vague?`
> **Athena** smiles: `Sharp question, Hermes! Your ideas need a clear rule, like 'Hermes' ideas written today,' or it's too fuzzy for a set. Precision is key!`

**Challenge**:  

**Exercise**: Consider the set \\(A = \lbrace 1, \lbrace 2\rbrace\rbrace \\). Which of these are true?(write `true` or `false` and then check your answer!)  
<!DOCTYPE html>
<html>
<head>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.9/MathJax.js?config=TeX-AMS-MML_HTMLorMML"></script>
</head>
<body>
  <div class="exercise" data-question="1. \(1 \in A \)" data-answer="true">
    <p class="question"></p>
    <input type="text" class="answer" placeholder="Enter your answer (true/false)">
    <button class="submit">Submit</button>
    <p class="feedback"></p>
  </div>

  <div class="exercise" data-question="2. \(2 \in A\)" data-answer="false">
    <p class="question"></p>
    <input type="text" class="answer" placeholder="Enter your answer (true/false)">
    <button class="submit">Submit</button>
    <p class="feedback"></p>
  </div>

  <div class="exercise" data-question="3. \(\lbrace 2\rbrace \in A \)" data-answer="true">
    <p class="question"></p>
    <input type="text" class="answer" placeholder="Enter your answer (true/false)">
    <button class="submit">Submit</button>
    <p class="feedback"></p>
  </div>

  <script>
    document.querySelectorAll('.exercise').forEach(exercise => {
      // Set the question text
      const questionText = exercise.getAttribute('data-question');
      exercise.querySelector('.question').textContent = questionText;

      // Get elements
      const input = exercise.querySelector('.answer');
      const button = exercise.querySelector('.submit');
      const feedback = exercise.querySelector('.feedback');
      const correctAnswer = exercise.getAttribute('data-answer').toLowerCase();

      // Function to check the answer
      function checkAnswer() {
        const userAnswer = input.value.trim().toLowerCase();
        if (userAnswer === correctAnswer) {
          feedback.textContent = "✅ Correct!";
          feedback.style.color = "green";
        } else {
          feedback.textContent = "❌ Incorrect. Try again.";
          feedback.style.color = "red";
        }
      }

      // Submit on button click
      button.addEventListener('click', checkAnswer);

      // Submit on Enter key
      input.addEventListener('keypress', (event) => {
        if (event.key === 'Enter') {
          checkAnswer();
        }
      });
    });

    // Trigger MathJax to render LaTeX
    MathJax.Hub.Queue(["Typeset", MathJax.Hub]);
  </script>
</body>
</html>



**Answers**:  
- 1. **True**: \\(1 \\)is an element of \\(A = \lbrace 1, \lbrace 2\rbrace\rbrace \\), so \\(1 \in A \\).  
- 2. **False**: \\(2 \\)is not directly an element; \\(\lbrace 2\rbrace \\)is the element, so \\(2 \notin A \\).  
- 3. **True**: \\(\lbrace 2\rbrace \\)is explicitly listed as an element, so \\(\lbrace 2\rbrace \in A \\).  

This shows sets can contain other sets as elements—mind-bending but fun!

---

## 2. Notation Tidbit

- **\\(\in \\)**: "is an element of."  
- **\\(\notin \\)**: "is not an element of."  
- **\\(|A| \\)**: The number of elements in set \\(A \\), called **cardinality**. For \\(A = \lbrace 1, 2, 3\rbrace \\), \\(|A| = 3 \\).

Sets can be **finite**, with a fixed number of elements, like \\(A = \lbrace 1, 2, 3\rbrace \\)(\\(|A| = 3 \\)), or **infinite**, with elements that go on forever, like the natural numbers \\(\mathbb{N} = \lbrace 0, 1, 2, \ldots\rbrace \\).

> **Hermes pipes up.**  
> "So, an infinite set's like an endless treasure chest?"  
> **Athena nods.**  
> "Exactly, Hermes! Its elements never run out, making sets so versatile."  

For finite sets, \\(|A| \\)is a simple count. For infinite sets, comparing sizes gets tricky—saying \\(|\mathbb{N}| = \infty \\)is informal, and we'll explore better ways later.

> **Hermes tilts his head, puzzled.**  
> "Hold on, Athena. Take the set \\(\lbrace 2, 4, \ldots\rbrace \\). It could be multiples of two, like \\(\lbrace 2, 4, 6, \ldots\rbrace \\), or powers of two, like \\(\lbrace 2, 4, 8, \ldots\rbrace \\). How do we avoid mix-ups?"  
> **Athena smiles.**  
> "Brilliant, Hermes! That's where **set representation** clears things up. We use two main methods to define sets precisely."

---

### Representing Sets

1. **Roster Notation**: List elements explicitly, ideal for finite sets or clear patterns.  
   - Example: Multiples of two (showing a pattern): \\(\lbrace 2, 4, 6, 8, \ldots\rbrace \\).  
   - Finite set: \\(\lbrace 2, 4, 6\rbrace \\)(first three even numbers).

2. **Set-Builder Notation**: Define elements by a rule: \\(\lbrace  x \mid \text{condition on } x\rbrace \\), read as "the set of all \\(x \\)such that [condition]."  
   - Multiples of two: \\(A = \lbrace 2n \mid n \in \mathbb{N}, n \geq 1\rbrace = \lbrace 2, 4, 6, \ldots\rbrace \\).  
   - Powers of two: \\(B = \lbrace 2^n \mid n \in \mathbb{N}, n \geq 1\rbrace = \lbrace 2, 4, 8, 16, \ldots\rbrace \\).

- **Example 4**: \\(A = \lbrace x \mid x \text{ is an odd integer and } x < 6\rbrace = \lbrace 1, 3, 5\rbrace \\).  
- **Example 5**: \\(C = \lbrace x \mid x \text{ is a positive multiple of } 3 \text{ less than } 10\rbrace = \lbrace 3, 6, 9\rbrace \\).

So, Hermes' sets are:  
- Multiples of two: \\(\lbrace 2n \mid n \in \mathbb{N}, n \geq 1\rbrace \\).  
- Powers of two: \\(\lbrace 2^n \mid n \in \mathbb{N}, n \geq 1\rbrace \\).

> **Hermes nods eagerly.**  
> "Got it! Set-builder notation makes it crystal clear!"  
> **Athena continues.**  
> "Exactly. Clear rules let us define sets, especially infinite ones, without confusion."

To make set-builder notation even stronger, we use standard symbols for common sets:

---

### Classic Sets

These sets are the superstars of math, especially in fields like cryptography:  
- **\\(\mathbb{N} \\)**: Natural numbers \\(\lbrace 0, 1, 2, 3, \ldots\rbrace \\)(for counting).  
- **\\(\mathbb{Z} \\)**: Integers \\(\lbrace \ldots, -2, -1, 0, 1, 2, \ldots\rbrace \\)(whole numbers, positive or negative).  
- **\\(\mathbb{Q} \\)**: Rational numbers \\(\lbrace \frac{a}{b} \mid a, b \in \mathbb{Z}, b \neq 0\rbrace \\), like \\(\frac{1}{2} \\), \\(-\frac{3}{4} \\).  
- **\\(\mathbb{R} \\)**: Real numbers (all points on the number line, like \\(\pi \\), \\(\sqrt{2} \\), \\(-1.5 \\)).  
- **\\(\mathbb{C} \\)**: Complex numbers \\(\lbrace a + bi \mid a, b \in \mathbb{R}, i^2 = -1\rbrace \\), like \\(2 + 3i \\).

> **Athena** `We can also visualize sets with **Venn diagrams** to show relationships, but we'll dive into those later. For now, let's see some examples in action!`

---

### Examples of Sets Using Classic Sets

1. Even positive integers: \\(\lbrace 2n \mid n \in \mathbb{N}, n \geq 1\rbrace = \lbrace 2, 4, 6, \ldots\rbrace \\).  
2. Even integers: \\(\lbrace 2a \mid a \in \mathbb{Z}\rbrace = \lbrace \ldots, -4, -2, 0, 2, 4, \ldots\rbrace \\).  
3. Positive rationals: \\(\lbrace \frac{p}{q} \mid p, q \in \mathbb{N}, q \neq 0\rbrace = \lbrace \frac{1}{2}, \frac{2}{3}, \frac{4}{1}, \ldots\rbrace \\).  
4. Non-negative reals: \\(\lbrace x \mid x \in \mathbb{R}, x \geq 0\rbrace = \lbrace 0, 1, \pi, \sqrt{2}, \ldots\rbrace \\).  
5. Integers divisible by 3: \\(\lbrace 3k \mid k \in \mathbb{Z}\rbrace = \lbrace \ldots, -6, -3, 0, 3, 6, \ldots\rbrace \\).

### Exercises
Time to put your set skills to the test! These challenges will sharpen your thinking and prepare you for what's next. Dive in, and let's see those brilliant ideas shine!

1. **Notation Practice**:  
   - Write the set of prime numbers less than 10 in both roster and set-builder notation.  
   - **Hermes' Question**: Is this set finite or infinite? How do you know?

2. **Set-Builder and Cardinality**:  
   - Define the set of all positive integers divisible by 5 and less than 25 using set-builder notation.  
   - List the elements in roster form.  
   - What is the cardinality of this set? Show your reasoning.  

3. **Classic Sets Challenge**:  
   - Consider the set \\(B = \lbrace  x \mid x \in \mathbb{Q}, x = \frac{a}{2}, a \in \mathbb{Z}, -2 \leq a \leq 2 \rbrace \\).  
     - Write \\(B \\)in roster form.  
     - Is \\(B \subseteq \mathbb{Q} \\)? Explain.  
     - **Hermes' Twist**: If we change the condition to \\(a \in \mathbb{N} \\), how does \\(B \\)change?

4. **Infinite Sets Puzzle**:  
   - Let \\(C = \lbrace  4n \mid n \in \mathbb{Z} \rbrace \\).  
     - Give the first three positive and three negative elements of \\(C \\).  
     - Is \\(C \\)finite or infinite? Compare its cardinality to \\(\mathbb{Z} \\).  
     - **Athena's Hint**: Think about how \\(C \\)relates to even numbers!

5. **Empty Set Teaser**:  
   - Define a set \\(D \\)using set-builder notation such that it contains all integers \\(x \\)where \\(x^2 = -4 \\).  
   - What is \\(D \\)? Why does it have this form?  
   - **Hermes' Challenge**: Can you find another condition that gives the same set \\(D \\)?  

> **Athena** winks.`That last one's a clue to something curious we're about to explore—sets with *nothing* in them!`

### The Empty Set

Sometimes, we encounter sets with no elements at all! This is the **empty set**, denoted \\(\emptyset\\)or \\(\lbrace \rbrace\\), containing nothing—like an empty treasure chest. Just as zero grounds arithmetic, the empty set grounds set theory.

- **Example 9**: The set of odd numbers divisible by 2 = \\(\emptyset\\)(no such numbers exist).  
- **Example 10**: \\(\lbrace x \mid x \in \mathbb{Z}, x^2 = -1\rbrace = \emptyset \\)(no integer's square is negative).  
- **Example 11**: \\(\lbrace x \mid x \in \mathbb{R}, x^2 + 1 = 0\rbrace = \emptyset \\)(no real number satisfies this equation).

> **Ares** jumps in, scratching his head. `Why bother with a set that's got *nothing* in it? What's the point?`
>
> **Athena:** `Great question, Ares! The empty set is like zero—it keeps our rules consistent. For instance, the intersection of two sets with no common elements, like` \\(\lbrace 1, 2\rbrace \\) `and` \\(\lbrace 3, 4\rbrace \\)`, gives` \\(\emptyset\\)`. It's a clear answer when there's nothing to show, and it'll shine in operations soon!`

### Subsets
<div style="display: flex; align-items: center; gap: 20px;">
    <img src="C:\Users\nilgo\Documents\the-school-of-athena\books\Mathematics Of Privacy\image\01_venn's.png" alt="Venn Diagram Example" style="width:200px;"/>
    <div>
        Athena steps forward, holding up a sketch. To make sets even clearer, let's introduce a handy tool: `Venn diagrams`! These are pictures where sets are shown as circles, and their relationships—like one set being inside another—are easy to see. They're perfect for understanding subsets, and we'll use them more as we go!
    </div>
</div>

A set \\(A \\) is a **subset** of \\(B \\), written \\(A \subseteq B \\), if every element of \\(A \\)is also in \\(B \\). If \\(A \neq B \\), it's a **proper subset**, denoted \\(A \subset B \\).  
- The empty set is a subset of every set: \\(\emptyset \subseteq A\\)(no elements to contradict!).  
- Every set is a subset of itself: \\(A \subseteq A \\).

- **Example 12**: Let \\(B = \lbrace 1, 2, 3\rbrace \\).  
  - \\(\lbrace 1, 2\rbrace \subseteq B \\), and \\(\lbrace 1, 2\rbrace \subset B\\)(proper subset).  
  - \\(\lbrace 1, 4\rbrace \not\subseteq B \\)(since \\(4 \notin B \\)).  
- **Example 13**: \\(\lbrace a, e\rbrace \subseteq \lbrace a, b, c, d, e\rbrace \\)(vowels in a small alphabet).


<div style="display: flex; align-items: center; gap: 20px;">
    <img src="C:\Users\nilgo\Documents\the-school-of-athena\books\Mathematics Of Privacy\image\02_venn.png" alt="Venn Diagram Example" style="width:200px;"/>

</div>

> **Hermes** leans forward, curious. `Athena, what about the cardinality of a set and its subsets? Is there a rule for their sizes?`
>
> **Athena**: `Excellent question, Hermes! Let's check the board!`
>
> If \\(A \subseteq B \\), the cardinality of \\(A \\), \\(|A| \\), is less than or equal to that of \\(B \\), \\(|B| \\). That is, \\(|A| \leq |B| \\). For example, if \\(B = \lbrace 1, 2, 3\rbrace \\)(\\(|B| = 3 \\)), a subset like \\(\lbrace 1, 2\rbrace \\)has \\(|A| = 2 \leq 3 \\), and \\(\emptyset \\)has \\(|\emptyset| = 0 \leq 3 \\). Proper subsets \\(A \subset B \\)have \\(|A| < |B| \\)if \\(B \\)is non-empty. This reflects that \\(A \\)can't have more elements than \\(B \\)—it's contained within it!

#### 4.1 Power Set

The **power set** \\(\mathcal{P}(A) \\)is the set of all subsets of \\(A \\).  
- **Example 14**: For \\(A = \lbrace 1, 2\rbrace \\), \\(\mathcal{P}(A) = \lbrace \emptyset, \lbrace 1\rbrace, \lbrace 2\rbrace, \lbrace 1, 2\rbrace\rbrace \\). It has \\(2^2 = 4 \\)subsets.  
- **Example 15**: For \\(A = \lbrace x\rbrace \\), \\(\mathcal{P}(A) = \lbrace \emptyset, \lbrace x\rbrace\rbrace \\), with \\(2^1 = 2 \\)subsets.

> **Athena** asks,`So, Athena, how many subsets does` \\(\lbrace 1, 2, 3\rbrace \\) `have?`
> **Hermes** replies: `Let's list them systematically, grouping by size—starting with zero elements and ending with all three. A subset can't have more elements than the set itself.`

Let's write the power set of \\(\lbrace 1, 2, 3\rbrace \\):  
- **0 elements**: \\(\emptyset \\) 
- **1 element**: \\(\lbrace 1\rbrace, \lbrace 2\rbrace, \lbrace 3\rbrace \\) 
- **2 elements**: \\(\lbrace 1, 2\rbrace, \lbrace 1, 3\rbrace, \lbrace 2, 3\rbrace \\) 
- **3 elements**: \\(\lbrace 1, 2, 3\rbrace \\) 

Total: \\(1 + 3 + 3 + 1 = 8 \\)subsets.  
So, \\(\mathcal{P}(\lbrace 1, 2, 3\rbrace) = \lbrace \emptyset, \lbrace 1\rbrace, \lbrace 2\rbrace, \lbrace 3\rbrace, \lbrace 1, 2\rbrace, \lbrace 1, 3\rbrace, \lbrace 2, 3\rbrace, \lbrace 1, 2, 3\rbrace\rbrace \\).

> **Athena** :` Looks right to me! Hermes, you're fast`
> **Hermes** `Okay, but is there a pattern? Does cardinality always tie to the power set like that?`
> **Athena** beams.`Sharp eye, Hermes! There is a math formula for it , and to check it carefully we need to go behinde the scene!

***Math Behind the Scene:*** For a set \\(A \\)with cardinality \\(|A| = n \\), its power set \\(\mathcal{P}(A) \\)has \\(2^n \\)elements. Why? Each element can be included or excluded—two choices per element. For \\(n = 3 \\), that's \\(2^3 = 8 \\). This holds for any finite set. Infinite sets? That's a whole new story!

**Challenge Exercise**:  
- Find a subset of \\(\lbrace 1, 2, 3\rbrace \\)with cardinality 2 and write it in roster form.  
- Is it a proper subset? Explain why or why not.  
- **Hermes' Twist**: Can you find all subsets with cardinality 2? How many are there?

---

### 5. The Universal Set

**Athena gestures broadly.**  
"Before we combine sets, we need a playground—the **universal set**, denoted \\(U \\), containing all possible elements in our context. Every set we discuss is a subset of \\(U \\), like treasures in a giant chest."

The universal set depends on the problem:  
- If \\(U = \mathbb{N} = \lbrace 0, 1, 2, 3, \ldots\rbrace \\), we focus on natural numbers.  
- If \\(U = \mathbb{Z} = \lbrace \ldots, -2, -1, 0, 1, 2, \ldots\rbrace \\), we include all integers.  
- If \\(U = \lbrace a, b, c, d, e\rbrace \\), we're limited to those letters.  
- If \\(U = \lbrace \text{Ace}, \text{King}, \text{Queen}, \ldots, \text{2}\rbrace \\)(a 52-card deck), we're dealing with cards.

**Athena** adds `In Venn diagrams, we draw the universal set as a rectangle, with all sets as circles inside it, showing how they fit within \\(U \\)'s boundaries.`

**[Venn Diagram Placeholder: Show \\(U = \lbrace a, b, c, d, e\rbrace \\)as a rectangle, with \\(B = \lbrace a, c\rbrace \\)as a circle inside, and \\(B^c = \lbrace b, d, e\rbrace \\)as the area outside \\(B \\)but within \\(U \\), to illustrate Example 17.]**

<div style="display: flex; align-items: center; gap: 20px;">
    <img src="C:\Users\nilgo\Documents\the-school-of-athena\books\Mathematics Of Privacy\image\03_complement.png" alt="Venn Diagram Example" style="width:200px;"/>
    <div>
        In Venn diagrams, we draw the universal set as a rectangle, with all sets as circles inside it, showing how they fit within \(U \)'s boundaries.
    </div>
</div>


> **Hermes, scribbling, looks up.**  
> "Hey, Athena, I'm exploring even numbers! I can write them as:  
> - \\(E = \lbrace \ldots, -4, -2, 0, 2, 4, \ldots\rbrace \\), or formally, \\(E = \lbrace 2i \mid i \in \mathbb{Z}\rbrace \\).  
> But what if I want even numbers in the natural numbers? I'm confused!"  
> **Athena smiles warmly.**  
> "Great catch, Hermes! The universal set clarifies this. Without \\(U \\), 'even numbers' is ambiguous:  
> - If \\(U = \mathbb{Z} \\), then \\(E_{\mathbb{Z}} = \lbrace 2i \mid i \in \mathbb{Z}\rbrace = \lbrace \ldots, -4, -2, 0, 2, 4, \ldots\rbrace \\).  
> - If \\(U = \mathbb{N} \\), then \\(E_{\mathbb{N}} = \lbrace 2i \mid i \in \mathbb{N}\rbrace = \lbrace 0, 2, 4, 6, \ldots\rbrace \\).  
> Defining \\(U \\)keeps our sets precise."

The universal set is crucial for operations like **complement**, which we'll explore next. The complement of a set \\(A \\), written \\(A^c \\), is all elements in \\(U \\)not in \\(A \\)—it depends entirely on \\(U \\).

- **Example 16**: Let \\(A = \lbrace 1, 2, 3\rbrace \\).  
  - If \\(U = \lbrace 0, 1, 2, 3, \ldots, 10\rbrace \\), then \\(A^c = \lbrace 0, 4, 5, 6, 7, 8, 9, 10\rbrace \\).  
  - If \\(U = \lbrace 1, 2, 3, \ldots, 30\rbrace \\), then \\(A^c = \lbrace 4, 5, \ldots, 30\rbrace \\).  

- **Example 17**: If \\(U = \lbrace a, b, c, d, e\rbrace \\), and \\(B = \lbrace a, c\rbrace \\), then \\(B^c = \lbrace b, d, e\rbrace \\). If \\(U = \lbrace a, b, \ldots, z\rbrace \\), then \\(B^c = \lbrace b, d, \ldots, z\rbrace \\).

- **Example 18**: If \\(U = \lbrace \text{Ace of Spades}, \text{Ace of Hearts}, \text{King of Spades}, \text{King of Hearts}\rbrace \\), and \\(C = \lbrace \text{Ace of Spades}\rbrace \\), then \\(C^c = \lbrace \text{Ace of Hearts}, \text{King of Spades}, \text{King of Hearts}\rbrace \\).

> **Hermes nods excitedly.**  
> "So, 'everything else' means 'everything else in \\(U \\)'! That's why \\(U \\)matters!"  
> **Athena chuckles.**  
> "Exactly, Hermes. The universal set sets the stage. Without it, we're guessing—and in set theory, precision is our superpower!"


### 🧠 Practice Exercises: Universal Sets & Complements

1. **Identify the Complement**  
   Let \\(U = \lbrace 0, 1, 2, \ldots, 9\rbrace \\), and \\(A = \lbrace 2, 4, 6, 8\rbrace \\).  
   a) List \\(A^c \\).  
   b) Is \\(5 \in A^c \\)?  
   c) Is \\(4 \in A^c \\)?

2. **Changing the Universal Set**  
   Suppose \\(A = \lbrace 1, 2, 3\rbrace \\).  
   a) If \\(U = \lbrace 1, 2, 3, 4, 5\rbrace \\), what is \\(A^c \\)?  
   b) If \\(U = \lbrace 0, 1, 2, \ldots, 10\rbrace \\), what is \\(A^c \\)?  
   c) How do your answers differ? Why?

3. **True or False**  
   For each statement, write **True** or **False**, and justify your answer.  
   a) If \\(A \subseteq B \\), then \\(B^c \subseteq A^c \\).  
   b) If \\(A = U \\), then \\(A^c = \emptyset \\).  
   c) If \\(A = \emptyset \\), then \\(A^c = U \\).

4. **Venn Diagram Completion**  
   Given \\(U = \lbrace a, b, c, d, e, f\rbrace \\), \\(A = \lbrace a, b, c\rbrace \\), and \\(B = \lbrace b, c, d\rbrace \\):  
   a) Find \\(A^c \\), \\(B^c \\), and \\(A \cap B \\).  
   b) Draw a Venn diagram showing sets \\(A \\)and \\(B \\)inside \\(U \\). Shade \\(A^c \\)and label clearly.

5. **Real-World Sets**  
   Consider this scenario:  
   \\(U \\)= All students in a school.  
   \\(A \\)= Students who take math.  
   \\(B \\)= Students who take music.  
   a) Describe in words what \\(A^c \\)and \\(B^c \\)represent.  
   b) What does \\(A^c \cap B^c \\)mean in this context?  
   c) What does \\((A \cup B)^c \\)represent?

6. **Build Your Own**  
   Design your own universal set \\(U \\)and create two sets \\(A \\)and \\(B \\)within it. Then:  
   a) List \\(A \\), \\(B \\), \\(A^c \\), and \\(B^c \\).  
   b) Find \\(A \cup B \\), \\(A \cap B \\), and \\((A \cup B)^c \\).  
   c) Share it with a friend (or classmate) and see if they get the same results!

## 6. Set Operations

**Athena waves her hand over an imaginary map.**  
Now that we've set up our universal set as the playground, let's mix up sets! To make things crystal clear, we'll use **Venn diagrams**—pictures showing sets as circles, often overlapping, to reveal their relationships.

### 6.1 Union (∪)

The **union** of sets \\(A \\)and \\(B \\), written \\(A \cup B \\), is the set of all elements in \\(A \\), \\(B \\), or both. Think of it as combining everything from two treasure chests into one big pile, with no duplicates.

- **Example 19**: Let \\(A = \lbrace 1, 2, 3\rbrace \\), \\(B = \lbrace 3, 4, 5\rbrace \\), with \\(U = \lbrace 1, 2, \ldots, 10\rbrace \\).  
  \\(A \cup B = \lbrace 1, 2, 3, 4, 5\rbrace \\). (We include 3 only once—no duplicates!)  
  
<div style="display: flex; align-items: center; gap: 20px;">
    <img src="C:\Users\nilgo\Documents\the-school-of-athena\books\Mathematics Of Privacy\image\04_union.png" alt="Venn Diagram Example" style="width:200px;"/>
    <div>
        In Venn diagrams, we draw the universal set as a rectangle, with all sets as circles inside it, showing how they fit within \(U \)'s boundaries.
    </div>
</div>


- **Example 20**: Let \\(A = \lbrace a, b, c\rbrace \\), \\(B = \lbrace c, d\rbrace \\), with \\(U = \lbrace a, b, c, d, e\rbrace \\).  
  \\(A \cup B = \lbrace a, b, c, d\rbrace \\).  
  **[Venn Diagram Placeholder: Show \\(A \\)'s circle with a, b, c, \\(B \\)'s with c, d, overlapping at c. Shade both circles to show \\(A \cup B \\).]**

- **Example 21**: Let \\(A = \lbrace \text{red}, \text{blue}\rbrace \\), \\(B = \lbrace \text{blue}, \text{green}\rbrace \\), with \\(U = \lbrace \text{red}, \text{blue}, \text{green}, \text{yellow}\rbrace \\).  
  \\(A \cup B = \lbrace \text{red}, \text{blue}, \text{green}\rbrace \\).  
  **[Venn Diagram Placeholder: Show circles overlapping at blue, with \\(A \\)holding red, blue, and \\(B \\)holding blue, green. Shade all of \\(A \\)and \\(B \\)for the union.]**

Venn diagrams help us visualize unions in different cases:

1. **Disjoint Sets**: When \\(A \\)and \\(B \\)have no common elements (e.g., \\(A = \lbrace 1, 2\rbrace \\), \\(B = \lbrace 3, 4\rbrace \\)).  
   **[Venn Diagram Placeholder: Show two non-overlapping circles, one for \\(A \\), one for \\(B \\). Shade both to show \\(A \cup B \\).]**  
   Here, the cardinality is simple: \\(|A \cup B| = |A| + |B| \\), since there's no overlap.

2. **Overlapping Sets**: When \\(A \\)and \\(B \\)share elements (e.g., \\(A = \lbrace 1, 2, 3\rbrace \\), \\(B = \lbrace 3, 4\rbrace \\)).  
   **[Venn Diagram Placeholder: Show two overlapping circles, with 3 in the middle. Shade both circles for \\(A \cup B \\).]**  
   **Hermes pipes up.** "What's the cardinality of \\(A \cup B \\)now, Athena?"  
   **Athena smiles.** "Great question, Hermes! When sets overlap, we can't just add \\(|A| + |B| \\)—that double-counts shared elements. Instead, use: \\(|A \cup B| = |A| + |B| - |A \cap B| \\). For \\(A = \lbrace 1, 2, 3\rbrace \\), \\(B = \lbrace 3, 4\rbrace \\), we have \\(|A| = 3 \\), \\(|B| = 2 \\), \\(|A \cap B| = |\lbrace 3\rbrace| = 1 \\), so \\(|A \cup B| = 3 + 2 - 1 = 4 \\). This ensures 3 is counted once!"

**Exercises**:  
1. What is \\(A \cup \emptyset \\)? Explain why.  
2. Are \\(A \cup B \\)and \\(B \cup A \\)the same? Why or why not?  
3. What is \\(A \cup U \\), where \\(U \\)is the universal set? Justify your answer.

### 6.2 Intersection (∩)

The **intersection** of sets \\(A \\)and \\(B \\), written \\(A \cap B \\), is the set of all elements common to both \\(A \\)and \\(B \\). It's like finding the treasures both chests share.

- **Example 22**: Let \\(A = \lbrace 1, 2, 3\rbrace \\), \\(B = \lbrace 3, 4, 5\rbrace \\), with \\(U = \lbrace 1, 2, \ldots, 10\rbrace \\).  
  \\(A \cap B = \lbrace 3\rbrace \\).  
  **[Venn Diagram Placeholder: Show two overlapping circles, one for \\(A \\)with 1, 2, 3, one for \\(B \\)with 3, 4, 5, overlapping at 3. Shade only the overlapping section to represent \\(A \cap B \\).]**

- **Example 23**: Let \\(A = \lbrace a, b, c\rbrace \\), \\(B = \lbrace c, d\rbrace \\), with \\(U = \lbrace a, b, c, d, e\rbrace \\).  
  \\(A \cap B = \lbrace c\rbrace \\).  
  **[Venn Diagram Placeholder: Show \\(A \\)'s circle with a, b, c, \\(B \\)'s with c, d, overlapping at c. Shade the overlap for \\(A \cap B \\).]**

- **Example 24**: Let \\(A = \lbrace \text{red}, \text{blue}\rbrace \\), \\(B = \lbrace \text{blue}, \text{green}\rbrace \\), with \\(U = \lbrace \text{red}, \text{blue}, \text{green}, \text{yellow}\rbrace \\).  
  \\(A \cap B = \lbrace \text{blue}\rbrace \\).  
  **[Venn Diagram Placeholder: Show circles overlapping at blue, with \\(A \\)holding red, blue, and \\(B \\)holding blue, green. Shade the overlap for \\(A \cap B \\).]**

> **Hermes raises his hand.**  
> "Athena, what if two sets have nothing in common? And what about the size of the intersection?"  
> **Athena nods.**  
> "Sharp thinking, Hermes! If \\(A \\)and \\(B \\)have no common elements, their intersection is the empty set, \\(A \cap B = \emptyset \\). For example, \\(\lbrace 1, 2\rbrace \cap \lbrace 3, 4\rbrace = \emptyset \\). As for cardinality, \\(|A \cap B| \leq \min(|A|, |B|) \\), since the intersection can't have more elements than either set. In Example 22, \\(|A| = 3 \\), \\(|B| = 2 \\), and \\(|A \cap B| = |\lbrace 3\rbrace| = 1 \\), which is less than both!"

**[Venn Diagram Placeholder: Show two non-overlapping circles for \\(A = \lbrace 1, 2\rbrace \\), \\(B = \lbrace 3, 4\rbrace \\). No shaded overlap, indicating \\(A \cap B = \emptyset \\).]**

---

### 6.3 Difference (−)

The **difference** of sets \\(A \\)and \\(B \\), written \\(A - B \\), is the set of elements in \\(A \\)but not in \\(B \\). It's like keeping only the treasures unique to \\(A \\)'s chest, tossing out anything \\(B \\)has.

- **Example 25**: Let \\(A = \lbrace 1, 2, 3\rbrace \\), \\(B = \lbrace 3, 4, 5\rbrace \\), with \\(U = \lbrace 1, 2, \ldots, 10\rbrace \\).  
  \\(A - B = \lbrace 1, 2\rbrace \\).  
  **[Venn Diagram Placeholder: Show two overlapping circles, one for \\(A \\)with 1, 2, 3, one for \\(B \\)with 3, 4, 5. Shade only the part of \\(A \\)'s circle not overlapping \\(B \\)to represent \\(A - B \\).]**

- **Example 26**: Let \\(A = \lbrace a, b, c\rbrace \\), \\(B = \lbrace c, d\rbrace \\), with \\(U = \lbrace a, b, c, d, e\rbrace \\).  
  \\(A - B = \lbrace a, b\rbrace \\).  
  **[Venn Diagram Placeholder: Show \\(A \\)'s circle with a, b, c, \\(B \\)'s with c, d, overlapping at c. Shade \\(A \\)'s non-overlapping part for \\(A - B \\).]**

- **Example 27**: Let \\(A = \lbrace \text{Ace of Spades}, \text{King of Spades}\rbrace \\), \\(B = \lbrace \text{King of Spades}, \text{King of Hearts}\rbrace \\), with \\(U = \lbrace \text{Ace of Spades}, \text{King of Spades}, \text{Ace of Hearts}, \text{King of Hearts}\rbrace \\).  
  \\(A - B = \lbrace \text{Ace of Spades}\rbrace \\).  
  **[Venn Diagram Placeholder: Show circles overlapping at King of Spades, with \\(A \\)holding Ace of Spades, King of Spades, and \\(B \\)holding King of Spades, King of Hearts. Shade \\(A \\)'s non-overlapping part for \\(A - B \\).]**

> **Ares scratches his head.**  
> "Wait, Athena, is \\(A - B \\)the same as \\(B - A \\)? And what's its size?"  
> **Athena replies.**  
> "Good catch, Ares! Generally, \\(A - B \neq B - A \\), because \\(A - B \\)keeps what's only in \\(A \\), while \\(B - A \\)keeps what's only in \\(B \\). For Example 25, \\(A - B = \lbrace 1, 2\rbrace \\), but \\(B - A = \lbrace 4, 5\rbrace \\). For cardinality, \\(|A - B| \leq |A| \\), since you're removing elements from \\(A \\). In Example 25, \\(|A| = 3 \\), \\(|A - B| = 2 \\)."

---

### 6.4 Cartesian Product (×)

The **Cartesian product** of sets \\(A \\)and \\(B \\), written \\(A \times B \\), is the set of all ordered pairs \\((a, b) \\), where \\(a \in A \\)and \\(b \in B \\). It's like pairing every item from \\(A \\)'s chest with every item from \\(B \\)'s, creating a new kind of treasure map.

- **Example 28**: Let \\(A = \lbrace 1, 2\rbrace \\), \\(B = \lbrace x, y\rbrace \\).  
  \\(A \times B = \lbrace (1, x), (1, y), (2, x), (2, y)\rbrace \\).  
  **Note**: No Venn diagram here, as Cartesian products are best visualized as a grid or list, not circles.

- **Example 29**: Let \\(A = \lbrace \text{red}, \text{blue}\rbrace \\), \\(B = \lbrace \text{hat}, \text{scarf}\rbrace \\).  
  \\(A \times B = \lbrace (\text{red}, \text{hat}), (\text{red}, \text{scarf}), (\text{blue}, \text{hat}), (\text{blue}, \text{scarf})\rbrace \\).  
  **Note**: Think of pairing colors with accessories—every combination counts!

- **Example 30**: Let \\(A = \lbrace a\rbrace \\), \\(B = \emptyset \\).  
  \\(A \times B = \emptyset \\), since no pairs can be formed with an empty set.  
  **Note**: The Cartesian product needs elements in both sets to produce pairs.

> **Hermes tilts his head.**  
> "Athena, how big is this product? And does order matter?"  
> **Athena grins.**  
> "Excellent, Hermes! The cardinality of \\(A \times B \\)is \\(|A \times B| = |A| \cdot |B| \\), because you pair each of \\(|A| \\)elements with each of \\(|B| \\). In Example 28, \\(|A| = 2 \\), \\(|B| = 2 \\), so \\(|A \times B| = 2 \cdot 2 = 4 \\). And yes, order matters: \\(A \times B \neq B \times A \\), since \\((a, b) \neq (b, a) \\). For example, \\((1, x) \neq (x, 1) \\)."

---

### Comprehensive Exercises: Set Operations

**Athena claps her hands.**  
"Time to test your set operation skills! These challenges mix union, intersection, difference, and Cartesian product to see how well you can navigate the playground. Grab your Venn diagrams and let's dive in!"

1. **Basic Operations**  
   Let \\(U = \lbrace 1, 2, 3, 4, 5, 6\rbrace \\), \\(A = \lbrace 1, 2, 3\rbrace \\), \\(B = \lbrace 2, 4, 6\rbrace \\).  
   a) Find \\(A \cup B \\), \\(A \cap B \\), \\(A - B \\), and \\(B - A \\).  
   b) Compute \\(|A \cup B| \\)using the inclusion-exclusion formula. Verify by listing elements.  
   c) Draw a Venn diagram showing \\(A \\), \\(B \\), and shade \\(A \cap B \\).

2. **Complement and Difference**  
   Let \\(U = \lbrace a, b, c, d, e\rbrace \\), \\(A = \lbrace a, b\rbrace \\), \\(B = \lbrace b, c, d\rbrace \\).  
   a) Find \\(A^c \\), \\(B^c \\), and \\(A - B \\).  
   b) Is \\(A - B = A \cap B^c \\)? Explain why or why not.  
   c) Draw a Venn diagram and shade \\(A - B \\).

3. **Cartesian Product Practice**  
   Let \\(A = \lbrace x, y\rbrace \\), \\(B = \lbrace 1, 2, 3\rbrace \\).  
   a) List all elements of \\(A \times B \\)and \\(B \times A \\).  
   b) Compute \\(|A \times B| \\)and \\(|B \times A| \\). Are they equal?  
   c) If \\(C = \emptyset \\), what is \\(A \times C \\)? Why?

4. **Real-World Scenario**  
   Imagine \\(U \\)= All books in a library, \\(A \\)= Books in the mystery genre, \\(B \\)= Books in hardcover.  
   a) Describe in words: \\(A \cup B \\), \\(A \cap B \\), \\(A - B \\), \\(B^c \\).  
   b) If a book is in \\(A \cap B \\), what can you say about it?  
   c) Suggest a universal set and draw a Venn diagram showing \\(A \\)and \\(B \\).

5. **Venn Diagram Challenge**  
   Given \\(U = \lbrace 1, 2, \ldots, 8\rbrace \\), \\(A = \lbrace 1, 3, 5, 7\rbrace \\), \\(B = \lbrace 2, 3, 4, 5\rbrace \\):  
   a) Find \\(A \cup B \\), \\(A \cap B \\), \\(A - B \\), and \\(A^c \\).  
   b) Draw a Venn diagram and shade the region for \\((A \cup B) - (A \cap B) \\).  
   c) What is the cardinality of the shaded region? Show your work.

6. **Mix and Match**  
   Let \\(U = \lbrace p, q, r, s, t\rbrace \\), \\(A = \lbrace p, q, r\rbrace \\), \\(B = \lbrace q, s\rbrace \\).  
   a) Compute \\(A \cup B \\), \\(A \cap B \\), \\(A - B \\), \\(B^c \\), and \\(A \times B \\).  
   b) Verify: Is \\(|A \cup B| = |A| + |B| - |A \cap B| \\)?  
   c) If \\(C = \lbrace r, s\rbrace \\), find \\(A \cap (B \cup C) \\). Draw a Venn diagram to check.

7. **Create Your Own**  
   Design a universal set \\(U \\)with 6–8 elements and two sets \\(A \\), \\(B \\).  
   a) Compute \\(A \cup B \\), \\(A \cap B \\), \\(A - B \\), and \\(A \times B \\).  
   b) Draw a Venn diagram showing \\(A \cup B \\).  
   c) Share with a classmate—do your operations match?


