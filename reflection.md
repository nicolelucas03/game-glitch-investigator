# 💭 Reflection: Game Glitch Investigator

Answer each question in 3 to 5 sentences. Be specific and honest about what actually happened while you worked. This is about your process, not trying to sound perfect.

## 1. What was broken when you started?

- What did the game look like the first time you ran it?
- List at least two concrete bugs you noticed at the start  
  (for example: "the secret number kept changing" or "the hints were backwards").

Bug 1: 
Expectation: "Go Higher" and "Go Lower" should be indicators for users as to how far their guess is. 

What Happened: The game displayed "Go Higher" every time even though it was incorrect.

Bug 2: 
Expectation: "New Game" should restart the game and allow the user to have X number of attempts again.

What Happened: "Game over." continued displaying even though user entered a new guess after clicking "New Game".

Bug 3: 
Expectation: Expected x number of attempts listed in "Attempts Left:"

What Happened: Even though it says "Attempts left:1", the game outputs "Out of attempts!"

Bug 4: 
Expectation: Range on the left panel should state the range of numbers of which to guess from. 

What happened: The range of the left panel and main screen does not match fo Easy and Hard difficulty level games.
---

## 2. How did you use AI as a teammate?

- Which AI tools did you use on this project (for example: ChatGPT, Gemini, Copilot)?
- Give one example of an AI suggestion that was correct (including what the AI suggested and how you verified the result).
- Give one example of an AI suggestion that was incorrect or misleading (including what the AI suggested and how you verified the result).

- I used Copilot to help me fix the bug on indicator messages. The core problem was that the output continued displaying "Go Higher" after all guesses, which was unexpected behavior. I used Copilot to help me point out the error, offer solutions, and test cases. Copilot did a great job at helping me debug this issue and I was able to create 3 tests for it on the logic_utils.py file to make sure the output was as expected. 

- Copilot helped me create test cases for the Go Higher/Lower indicators, although I believe tha the agent could have made the test cases more specific and thorough. I also realized that while I was trying to fix some of the range indicators to make the panel and main screen match, Copilot tried switching the core logic and range threshold for the Hard difficulty level, which was not necessary. After testing out the game, I realized that the core logic for the Hard difficulty level was no longer the same, and made sure to tell Copilot exactly the specifications I needed for the core functionality. 
---

## 3. Debugging and testing your fixes

- How did you decide whether a bug was really fixed?
- Describe at least one test you ran (manual or using pytest)  
  and what it showed you about your code.
- Did AI help you design or understand any tests? How?

I decided a bug was fixed when it passed both a manual check in the running Streamlit app and the automated pytest suite. 
For the Go Higher/Lower indicator bug, I ran `pytest -q` in the terminal and confirmed that `test_hint_message_go_lower` and `test_hint_message_go_higher` both passed.This meant that the `get_hint_message("Too High")` correctly returns `"📉 Go LOWER!"` and the `get_hint_message("Too Low")` correctly returns `"📈 Go HIGHER!"`. I also verified manually by opening the app, enabling the debug panel to see the secret number, and deliberately guessing too high and too low to confirm the displayed hint matched the expected direction. Copilot helped me design the hint tests by suggesting `get_hint_message` as a separate testable function, which made it easier to isolate the display logic from the comparison logic in `check_guess`. However, Copilot could have been more specific over the tests it created.

---

## 4. What did you learn about Streamlit and state?

- In your own words, explain why the secret number kept changing in the original app.
- How would you explain Streamlit "reruns" and session state to a friend who has never used Streamlit?
- What change did you make that finally gave the game a stable secret number?
The secret number kept changing because Streamlit reruns the script from top to bottom after each interaction, like clicking Submit. If the number is generated in normal local code on each rerun, it gets replaced again and again. Reruns are a full refresh of your Python script, and session state is a storage box that survives those refreshes for one user session. Once I understood that, I only created the secret number when it was missing from session state instead of recreating it every run. That change made the game stable and predictable, and the same secret stayed in place until New Game was clicked.
---

## 5. Looking ahead: your developer habits

- What is one habit or strategy from this project that you want to reuse in future labs or projects?
  - This could be a testing habit, a prompting strategy, or a way you used Git.
- What is one thing you would do differently next time you work with AI on a coding task?
- In one or two sentences, describe how this project changed the way you think about AI generated code.

One strategy I want to reuse is pairing manual testing with small focused pytest checks, because it helped me confirm both player experience and logic correctness. I also want to ask AI to justify each logic change before I apply it, especially for core game rules like difficulty ranges. AI can sometimes accidentally change core logic that can mess with the functionality of the project, and I want to continue practicing to check over my AI before applying any direct changes. 
