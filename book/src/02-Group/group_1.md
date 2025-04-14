# Groups
Here is the example 

\\(a_u\\)
# Example Exercise


**Exercise**: What is `2 + 2`?

<input type="text" id="answer" placeholder="Enter your answer">
<button onclick="checkAnswer()">Submit</button>
<p id="feedback"></p>

<script>
  function checkAnswer() {
    const answer = document.getElementById("answer").value.trim();
    const feedback = document.getElementById("feedback");

    if (answer === "4") {
      feedback.textContent = "✅ Correct!";
      feedback.style.color = "green";
    } else {
      feedback.textContent = "❌ Incorrect. Try again.";
      feedback.style.color = "red";
    }
  }
</script>

