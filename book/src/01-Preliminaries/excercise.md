# Examples and Exercises

## 📚 Examples

### Basic Divisibility Examples
1. **Simple Cases**
   - Does 8 divide 56?  
     ✅ Yes, because \\(56 = 8 \cdot 7\\)
   - Does 8 divide 50?  
     ❌ No, because \\(50 \div 8 = 6.25\\) (not an integer)

2. **Negative Numbers**
   - Divide -13 by 5:  
     \\(-13 = (-3) \cdot 5 + 2\\), where \\(q = -3\\) and \\(r = 2\\)
   - Note: \\(0 \leq r < 5\\) still holds

3. **Edge Cases**
   - Divide 0 by 4:  
     \\(0 = 0 \cdot 4\\), so \\(4 \mid 0\\)
   - Divide 4 by 0:  
     ❌ Undefined (no integer k makes \\(4 = k \cdot 0\\))

4. **Larger Numbers**
   - Divide 25 by 6:  
     \\(25 = 4 \cdot 6 + 1\\), where \\(q = 4\\) and \\(r = 1\\)
   - Note: Remainder is unique for each pair
<!DOCTYPE html>
<html>
<head>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.9/MathJax.js?config=TeX-AMS-MML_HTMLorMML"></script>
</head>
<body>
  <div class="exercise" data-question="1. Does \( 6 \mid 18 \)?" data-answer="true">
    <p class="question"></p>
    <input type="text" class="answer" placeholder="Enter your answer (true/false)">
    <button class="submit">Submit</button>
    <p class="feedback"></p>
  </div>

  <div class="exercise" data-question="2. For \( 13 \div 5 \), is the remainder 3?" data-answer="true">
    <p class="question"></p>
    <input type="text" class="answer" placeholder="Enter your answer (true/false)">
    <button class="submit">Submit</button>
    <p class="feedback"></p>
  </div>

  <div class="exercise" data-question="3. For \( 20 \div 7 \), what is the quotient?" data-answer="2">
    <p class="question"></p>
    <input type="text" class="answer" placeholder="Enter your answer (number)">
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
<script>
  // MathJax render
  MathJax.Hub.Queue(["Typeset", MathJax.Hub]);

  // Multiple-choice checking
  document.querySelectorAll('.mc-exercise').forEach(ex => {
    const correct = ex.getAttribute('data-correct');
    const button = ex.querySelector('.check-mc');
    const feedback = ex.querySelector('.mc-feedback');

    button.addEventListener('click', () => {
      const selected = ex.querySelector('input[type="radio"]:checked');
      if (!selected) {
        feedback.textContent = "❗ Please select an answer.";
        feedback.style.color = "orange";
      } else if (selected.value === correct) {
        feedback.textContent = "✅ Correct!";
        feedback.style.color = "green";
      } else {
        feedback.textContent = "❌ Incorrect. Try again.";
        feedback.style.color = "red";
      }
    });
  });

  // Fill-in-the-blank checking
  document.querySelectorAll('.fitb-exercise').forEach(ex => {
    const correct = ex.getAttribute('data-answer').trim();
    const input = ex.querySelector('.fitb-input');
    const button = ex.querySelector('.check-fitb');
    const feedback = ex.querySelector('.fitb-feedback');

    function check() {
      const user = input.value.trim();
      if (user === correct) {
        feedback.textContent = "✅ Correct!";
        feedback.style.color = "green";
      } else {
        feedback.textContent = "❌ Incorrect. Try again.";
        feedback.style.color = "red";
      }
    }

    button.addEventListener('click', check);
    input.addEventListener('keypress', (e) => {
      if (e.key === 'Enter') check();
    });
  });
</script>

</html>

<!DOCTYPE html>
<html>
<head>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.9/MathJax.js?config=TeX-AMS-MML_HTMLorMML"></script>
</head>
<body>

  <div class="exercise" data-question="1. \(3 \mid 12\)" data-answer="true">
    <p class="question"></p>
    <input type="text" class="answer" placeholder="Enter your answer (true/false)">
    <button class="submit">Submit</button>
    <p class="feedback"></p>
  </div>

  <div class="exercise" data-question="2. \(7 \mid 29\)" data-answer="false">
    <p class="question"></p>
    <input type="text" class="answer" placeholder="Enter your answer (true/false)">
    <button class="submit">Submit</button>
    <p class="feedback"></p>
  </div>

  <div class="exercise" data-question="3. In \(11 = 2 \cdot 4 + 3\), is 3 the remainder?" data-answer="true">
    <p class="question"></p>
    <input type="text" class="answer" placeholder="Enter your answer (true/false)">
    <button class="submit">Submit</button>
    <p class="feedback"></p>
  </div>

  <div class="exercise" data-question="4. The remainder when dividing 14 by 5 is 4." data-answer="true">
    <p class="question"></p>
    <input type="text" class="answer" placeholder="Enter your answer (true/false)">
    <button class="submit">Submit</button>
    <p class="feedback"></p>
  </div>

  <div class="exercise" data-question="5. \(9 \div 3\) has a remainder of 3." data-answer="false">
    <p class="question"></p>
    <input type="text" class="answer" placeholder="Enter your answer (true/false)">
    <button class="submit">Submit</button>
    <p class="feedback"></p>
  </div>

  <script>
    document.querySelectorAll('.exercise').forEach(exercise => {
      const questionText = exercise.getAttribute('data-question');
      exercise.querySelector('.question').textContent = questionText;

      const input = exercise.querySelector('.answer');
      const button = exercise.querySelector('.submit');
      const feedback = exercise.querySelector('.feedback');
      const correctAnswer = exercise.getAttribute('data-answer').toLowerCase();

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

      button.addEventListener('click', checkAnswer);
      input.addEventListener('keypress', (event) => {
        if (event.key === 'Enter') {
          checkAnswer();
        }
      });
    });

    MathJax.Hub.Queue(["Typeset", MathJax.Hub]);
  </script>
</body>
</html>

<div class="mc-exercise" data-correct="b">
  <p><strong>Which of the following correctly expresses 17 divided by 5 as quotient and remainder?</strong></p>
  <form>
    <label><input type="radio" name="mc1" value="a"> \( 17 = 5 \cdot 4 + 3 \)</label><br>
    <label><input type="radio" name="mc1" value="b"> \( 17 = 5 \cdot 3 + 2 \)</label><br>
    <label><input type="radio" name="mc1" value="c"> \( 17 = 5 \cdot 2 + 7 \)</label><br>
    <label><input type="radio" name="mc1" value="d"> \( 17 = 5 \cdot 1 + 12 \)</label><br>
    <button type="button" class="check-mc">Submit</button>
    <p class="mc-feedback"></p>
  </form>
</div>

<div class="fitb-exercise" data-answer="4">
  <p><strong>What is the remainder when 19 is divided by 5?</strong></p>
  <input type="text" class="fitb-input" placeholder="Enter a number">
  <button type="button" class="check-fitb">Submit</button>
  <p class="fitb-feedback"></p>
</div>

<script>
  // MathJax render
  MathJax.Hub.Queue(["Typeset", MathJax.Hub]);

  // Multiple-choice checking
  document.querySelectorAll('.mc-exercise').forEach(ex => {
    const correct = ex.getAttribute('data-correct');
    const button = ex.querySelector('.check-mc');
    const feedback = ex.querySelector('.mc-feedback');

    button.addEventListener('click', () => {
      const selected = ex.querySelector('input[type="radio"]:checked');
      if (!selected) {
        feedback.textContent = "❗ Please select an answer.";
        feedback.style.color = "orange";
      } else if (selected.value === correct) {
        feedback.textContent = "✅ Correct!";
        feedback.style.color = "green";
      } else {
        feedback.textContent = "❌ Incorrect. Try again.";
        feedback.style.color = "red";
      }
    });
  });

  // Fill-in-the-blank checking
  document.querySelectorAll('.fitb-exercise').forEach(ex => {
    const correct = ex.getAttribute('data-answer').trim();
    const input = ex.querySelector('.fitb-input');
    const button = ex.querySelector('.check-fitb');
    const feedback = ex.querySelector('.fitb-feedback');

    function check() {
      const user = input.value.trim();
      if (user === correct) {
        feedback.textContent = "✅ Correct!";
        feedback.style.color = "green";
      } else {
        feedback.textContent = "❌ Incorrect. Try again.";
        feedback.style.color = "red";
      }
    }

    button.addEventListener('click', check);
    input.addEventListener('keypress', (e) => {
      if (e.key === 'Enter') check();
    });
  });
</script>





## 📝 Exercises

### Basic Practice (Easy to Moderate)

#### Divisibility Checks
1. Determine whether the following statements are true or false:
   a) \\(9 \mid 81\\)
   b) \\(7 \mid 45\\)
   c) \\(5 \mid 0\\)

2. List all the divisors of:
   a) 24
   b) 30
   c) 100

#### Division with Remainders
3. For each of the following, write in the form \\(a = q \cdot d + r\\), with \\(0 \le r < d\\):
   a) \\(22 \div 5\\)
   b) \\(15 \div 4\\)
   c) \\(29 \div 6\\)

### Conceptual Exercises (Moderate to Challenging)

4. **Prove or disprove**: If \\(a \mid b\\) and \\(a \mid c\\), then \\(a \mid (b + c)\\)

5. Given \\(n = 97\\) and \\(d = 9\\), find \\(q\\) and \\(r\\) such that:
   \\(n = q \cdot d + r\\), with \\(0 \le r < d\\)

6. Explore uniqueness:
   For \\(n = 17\\) and \\(d = 5\\), show why both:
   \\(17 = 3 \cdot 5 + 2\\) and \\(17 = 2 \cdot 5 + 7\\)
   are true, but only one satisfies the Division Theorem.

### Applied Exercises (Crypto Focus)

7. **Crypto Scenario—Modular Seeds**
   - In a crypto system, a key starts at 23, reduced modulo 7
   - Compute:
     a. The remainder of \\(23 \div 7\\)
     b. Repeat for \\(23 - 7\\), then \\(23 - 14\\)
   - What pattern emerges?
   - Why do remainders matter for secure key generation?

8. **Divisibility and Cryptography**
   - Let \\(n = 35\\)
   - List all positive divisors of 35
   - If \\(d \mid 35\\), could \\(d\\) be a modular base in a crypto system?
   - Test with \\(d = 5\\): compute \\(35 \div 5\\)
   - Why avoid divisors that produce non-integer results in crypto?

### Creative Questions

9. What would "remainder" mean if we allowed negative remainders? Would the division theorem still hold?

10. Write a Python function to compute \\(q\\) and \\(r\\) for any integers \\(n\\) and \\(d > 0\\)

11. Suppose you're encrypting messages using "divide-and-drop-the-remainder" rules. Why is it important that the remainder is predictable and well-defined?

## Implementation Notes

### Python Example
```python
def div_rem(n, d):
    q = n // d
    r = n % d
    return q, r

# Example usage
print(div_rem(11, 4))  # Outputs (2, 3)
```
