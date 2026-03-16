# 🎮 Game Glitch Investigator: The Impossible Guesser

## 🚨 The Situation

You asked an AI to build a simple "Number Guessing Game" using Streamlit.
It wrote the code, ran away, and now the game is unplayable. 

- You can't win.
- The hints lie to you.
- The secret number seems to have commitment issues.

## 🛠️ Setup

1. Install dependencies: `pip install -r requirements.txt`
2. Run the broken app: `python -m streamlit run app.py`

## 🕵️‍♂️ Your Mission

1. **Play the game.** Open the "Developer Debug Info" tab in the app to see the secret number. Try to win.
2. **Find the State Bug.** Why does the secret number change every time you click "Submit"? Ask ChatGPT: *"How do I keep a variable from resetting in Streamlit when I click a button?"*
3. **Fix the Logic.** The hints ("Higher/Lower") are wrong. Fix them.
4. **Refactor & Test.** - Move the logic into `logic_utils.py`.
   - Run `pytest` in your terminal.
   - Keep fixing until all tests pass!

## 📝 Document Your Experience

- [ ] Describe the game's purpose.
This game is a Guessing game in which the user inputs a selected amount of guesses with or without hints to guess a number within a selected range. The game comes in three difficulty levels, each with a different number of attempts and range of numbers to guess from. 

- [ ] Detail which bugs you found.
Detail which bugs you found.  
I found three major bugs:
1. The hint logic was inconsistent and sometimes gave the wrong higher/lower direction.
2. Attempt handling was confusing, and the game could report "Out of attempts" in unexpected situations.
3. Difficulty ranges were inconsistent between what was shown and what the game logic used (especially for Easy/Hard).

- [ ] Explain what fixes you applied.
I refactored helper logic into logic_utils.py and updated imports in app.py. I fixed the higher/lower outcome handling, corrected difficulty range behavior, and improved input/attempt flow so invalid entries do not behave like valid attempts. I then used pytest tests for win/too high/too low outcomes and validated the app manually in Streamlit.

## 📸 Demo

- [ ] [Insert a screenshot of your fixed, winning game here]
![alt text](image-1.png)
![alt text](image.png)
## 🚀 Stretch Features

- [ ] [If you choose to complete Challenge 4, insert a screenshot of your Enhanced Game UI here]
