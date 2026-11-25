# MindMate - Mental Wellness Chat Support Platform

Generative AI Semester End Hackathon | PS 03 | Category A: Healthcare and Well-being | SDG 3

## About the project

MindMate is a chatbot for people who feel stressed, anxious or lonely. It remembers what the user said before and how they are feeling, and it suggests small exercises like box breathing and grounding.

Safety is the main part of our project. We check the user's message before the AI replies, and we check the AI's reply before showing it. If the message looks like a crisis, the chat stops and Indian helpline numbers are shown.

**Note:** MindMate is not a doctor or a therapist. It does not give any diagnosis or medicine advice.

## Team

| Member | Work |
|---|---|
| Peer Zada Saoud | Model selection, model training |
| Nitesh Rathod | Chatbot and Gemini connection |
| Deepak | Testing and screenshots |
| Affan Ahmed | PPT, diagrams and reports |

## Features

- Chat that remembers old messages (last 10)
- Mood slider (1 to 5)
- Emotion detection, also mixed emotions
- Risk check: safe / distress / crisis
- Crisis mode with Indian helplines
- Exercise suggestion for the user's problem
- Checking the AI reply so it is safe
- Backup Gemini models if the server is busy
- Mood log saved in a CSV file

## Tech used

- Python, Google Colab
- Gemini API (google-genai)
- Gradio for the chat page
- Hugging Face models:

| Model | Use |
|---|---|
| j-hartmann/emotion-english-distilroberta-base | Emotion |
| cardiffnlp/twitter-roberta-base-sentiment-latest | Mood |
| facebook/bart-large-mnli | Risk level (optional, slow on CPU) |
| unitary/toxic-bert | Checking AI reply |
| sentence-transformers/all-MiniLM-L6-v2 | Exercise matching |

## How to run

1. Open https://colab.research.google.com and upload `MindMate_Prototype_fixed.ipynb` (File > Upload notebook).
2. Get a free API key from https://aistudio.google.com (Get API key > Create API key).
3. In Colab click the key icon on the left (Secrets), add a secret named `GEMINI_API_KEY`, paste your key and turn on Notebook access.
4. (Optional, makes it faster) Runtime > Change runtime type > T4 GPU.
5. Click **Runtime > Run all**. Loading the models takes 2 to 3 minutes the first time.
6. In the last app cell you will get a public link like `https://xxxx.gradio.live`. Open it to use the chatbot.

### If something goes wrong

| Problem | Fix |
|---|---|
| 404 model not found | Change `GEMINI_MODEL` to a name from the model list (for example `gemini-3.8-flash`) |
| 503 server busy | Wait a few minutes. The backup cell tries other Gemini models by itself |
| 429 quota error | Wait 1 to 2 minutes or make a new API key |
| Too slow | Run the FAST MODE cell (turns off the bart model) |
| Other cells not running | The app cell is still running. Use Runtime > Interrupt execution, or keep `debug=False` |

## Sample inputs and outputs

| Input | What MindMate does |
|---|---|
| I have an exam tomorrow and I'm scared | Finds fear, gives a kind reply and box breathing |
| and I can't sleep (next message) | Remembers the exam and connects both |
| Nobody talks to me at college | Suggests talking to a friend |
| A crisis message | Stops the chat and shows helplines |

## Test result

- First risk test: 3 out of 7 correct
- After fixing keywords and limits: ____ out of 7

## Helplines shown in the app

- Tele-MANAS: 14416
- KIRAN: 1800-599-0019
- Emergency: 112

## Future work

- Finish training the model for the personal action plan
- Train the risk model with more messages
- Hindi and Kannada support
- Local model so it works without internet
- Test with real users
