# PSAT-KELAS-X.-
<!DOCTYPE html><html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>PSAT English Test - Grade 10</title>
  <link rel="icon" href="favicon.ico" type="image/x-icon" />
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #f4f4f4;
      margin: 0;
      padding: 0;
    }
    .container {
      max-width: 900px;
      margin: 0 auto;
      background: white;
      padding: 2rem;
      margin-top: 3rem;
      border-radius: 8px;
      box-shadow: 0 0 10px rgba(0,0,0,0.1);
    }
    h1, h2 {
      text-align: center;
    }
    .question {
      margin-bottom: 1.5rem;
    }
    .question p {
      font-weight: bold;
    }
    .choices label {
      display: block;
      margin: 0.3rem 0;
    }
    button {
      display: block;
      margin: 2rem auto;
      padding: 0.7rem 2rem;
      font-size: 1rem;
      background-color: #3498db;
      color: white;
      border: none;
      border-radius: 5px;
      cursor: pointer;
    }
    button:hover {
      background-color: #2980b9;
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>PSAT Bahasa Inggris Kelas X</h1>
    <h2>Ujian Interaktif</h2>
    <form id="quizForm">
      <!-- Soal akan di-inject di sini -->
    </form>
    <button type="button" onclick="submitQuiz()">Submit Jawaban</button>
  </div>  <script>
    const questions = [
      // 1-3: Describing Picture
      { q: "What is the girl doing in the picture?", options: ["She is washing dishes", "She is watering the plants", "She is dancing in her room", "She is cooking dinner"] },
      { q: "Where is the dog in the picture?", options: ["On the roof", "Under the table", "Beside the car", "In the garden"] },
      { q: "What are the children doing?", options: ["Watching TV", "Riding bicycles", "Eating lunch", "Playing chess"] },

      // 4–7: Short Monolog (Listening)
      { q: "What does the speaker ask?", options: ["To describe a place", "To give direction", "To write a story", "To sing a song"] },
      { q: "Where should the listener go next?", options: ["Straight and turn right", "Go back and turn left", "Stay there", "Call someone"] },
      { q: "What is the location described?", options: ["Market", "School", "Hospital", "Post office"] },
      { q: "Which landmark is NOT mentioned?", options: ["Bridge", "Statue", "Mosque", "Cafe"] },

      // 8–13: Present Continuous Tense
      { q: "She ___ a book now.", options: ["read", "reads", "is reading", "was reading"] },
      { q: "They ___ in the garden.", options: ["are playing", "play", "played", "plays"] },
      { q: "My father ___ TV at the moment.", options: ["watch", "is watching", "watches", "watched"] },
      { q: "We ___ to the store.", options: ["go", "are going", "goes", "went"] },
      { q: "She ___ not working today.", options: ["is", "was", "are", "be"] },
      { q: "What ___ you doing now?", options: ["is", "are", "do", "does"] },

      // 14–18: Conditional Sentence Type 1
      { q: "If it rains, we ___ at home.", options: ["stay", "will stay", "stayed", "stays"] },
      { q: "He will come if you ___ him.", options: ["invite", "invited", "invites", "will invite"] },
      { q: "If I ___ early, I won't miss the bus.", options: ["wake up", "woke up", "wakes", "will wake"] },
      { q: "They won't pass if they ___ hard.", options: ["don’t study", "didn’t study", "studied", "study"] },
      { q: "You will get a reward if you ___ it right.", options: ["do", "did", "does", "done"] },

      // 19–25: Analytical Exposition
      { q: "What is the purpose of analytical exposition?", options: ["To entertain", "To describe", "To argue", "To instruct"] },
      { q: "Which structure belongs to analytical exposition?", options: ["Orientation, Events, Reorientation", "Thesis, Arguments, Reiteration", "Goal, Materials, Steps", "Issue, Argument, Conclusion"] },
      { q: "Which is a topic for analytical exposition?", options: ["My holiday", "How to make tea", "Should students wear uniforms?", "The tallest mountain"] },
      { q: "The language feature mostly used is:", options: ["Past tense", "Present tense", "Future tense", "Passive voice"] },
      { q: "Reiteration is used to:", options: ["State the issue", "Give argument", "Summarize viewpoint", "Describe process"] },
      { q: "Which conjunction is used in exposition?", options: ["First", "But", "Therefore", "Then"] },
      { q: "Analytical exposition is usually written in:", options: ["Narrative form", "Argumentative form", "Descriptive form", "Instructional form"] },

      // 26–35: Narrative Text
      { q: "What is the generic structure of narrative text?", options: ["Orientation, Complication, Resolution", "Introduction, Thesis, Argument", "Event, Description, Conclusion", "Opening, Body, Closing"] },
      { q: "Narrative texts are written to:", options: ["Inform", "Entertain", "Describe", "Convince"] },
      { q: "Which of these is narrative?", options: ["Snow White", "Manual Book", "News Report", "Recipe"] },
      { q: "Which tense is commonly used?", options: ["Present", "Past", "Future", "Present Perfect"] },
      { q: "Which is a complication in a story?", options: ["Living in a village", "A dragon appeared", "He slept", "Going to school"] },
      { q: "What is the function of resolution?", options: ["Begin story", "Describe event", "Solve problem", "Add conflict"] },
      { q: "Moral value is found in:", options: ["Orientation", "Complication", "Resolution", "Ending"] },
      { q: "The main character is:", options: ["Setting", "Place", "Protagonist", "Plot"] },
      { q: "Narrative uses what kind of verbs?", options: ["Action", "Linking", "Helping", "Passive"] },
      { q: "Stories are usually told in:", options: ["Chronological order", "Random", "Alphabetically", "None"] },

      // 36–40: Present Continuous (Cloze)
      { q: "He ___ (study) now.", options: ["is studying", "studies", "was studying", "study"] },
      { q: "They ___ (play) football.", options: ["are playing", "play", "played", "plays"] },
      { q: "I ___ (not watch) TV.", options: ["am not watching", "don’t watch", "didn’t watch", "won’t watch"] },
      { q: "We ___ (do) our homework.", options: ["are doing", "do", "did", "done"] },
      { q: "She ___ (make) a cake.", options: ["is making", "makes", "made", "make"] },

      // 41–45: Asking for and Giving Direction
      { q: "How do I get to the hospital?", options: ["Turn right and go straight", "Go home", "Stop here", "Go to sleep"] },
      { q: "Where is the nearest ATM?", options: ["Next to the bank", "Behind the tree", "Inside the park", "At the school"] },
      { q: "Excuse me, can you show me the way to the post office?", options: ["Go along this street", "No idea", "I’m busy", "I don’t like post"] },
      { q: "It’s on your ___", options: ["left", "right", "head", "arm"] },
      { q: "You will see it across ___", options: ["the street", "the roof", "the gate", "the window"] },

      // 46–50: Recount Text
      { q: "Recount text tells about:", options: ["Past events", "Future dreams", "Daily routine", "Instructions"] },
      { q: "What tense is used in recount?", options: ["Past tense", "Present", "Future", "Continuous"] },
      { q: "Structure of recount is:", options: ["Orientation, Events, Reorientation", "Introduction, Arguments", "Problem, Solution", "Facts, Opinions"] },
      { q: "What is the purpose of recount text?", options: ["To retell past events", "To explain", "To argue", "To entertain"] },
      { q: "Which is a recount?", options: ["My Vacation", "Why We Study", "How to Bake", "The Legend"] }
    ];

    const quizForm = document.getElementById('quizForm');

    questions.forEach((item, index) => {
      const div = document.createElement('div');
      div.classList.add('question');
      div.innerHTML = `
        <p>${index + 1}. ${item.q}</p>
        <div class="choices">
          ${item.options.map((opt, i) => `
            <label>
              <input type="radio" name="q${index}" value="${String.fromCharCode(65+i)}" required>
              ${String.fromCharCode(65+i)}. ${opt}
            </label>`).join('')}
        </div>
      `;
      quizForm.appendChild(div);
    });

    function submitQuiz() {
      const formData = new FormData(quizForm);
      const unanswered = questions.filter((_, i) => !formData.get(`q${i}`));
      if (unanswered.length > 0) {
        alert("Mohon jawab semua soal sebelum submit!");
        return;
      }
      alert("Terima kasih, jawaban Anda telah dikumpulkan!");
    }
  </script></body>
</html>
