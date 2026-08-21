# CHATBOT
🤖 Simple AI chatbot built with Streamlit and Ollama. Users can enter questions and receive AI-generated responses locally using the Gemma 2B language model through the Ollama API.
# 🤖 Streamlit Ollama AI Chatbot

A simple **AI chatbot application** built using **Python, Streamlit, Requests, and Ollama**.

The application allows users to enter a question and receive an AI-generated response using the **Gemma 2B** language model running locally through the Ollama API.

This project is a beginner-friendly example of connecting a Streamlit web interface with a locally hosted Large Language Model (LLM).

---

## 🚀 Features

* 🤖 AI-powered question answering
* 💬 Simple chat-style interface
* 🖥️ Built with Streamlit
* 🧠 Uses Gemma 2B
* 🏠 Runs the AI model locally using Ollama
* 🔗 Communicates with Ollama through its REST API
* ⚡ Simple and lightweight implementation
* 🌐 No external AI API key required

---

## 🛠️ Technologies Used

| Technology | Purpose                   |
| ---------- | ------------------------- |
| Python     | Main programming language |
| Streamlit  | Web interface             |
| Requests   | API communication         |
| Ollama     | Local LLM server          |
| Gemma 2B   | AI language model         |

> **Note:** Pandas, NumPy, Matplotlib, and Plotly are imported in the current code but are not used by the chatbot functionality.

---

# 🧠 How It Works

The application has a simple workflow:

```text
       User
        │
        ▼
 Enter Question
        │
        ▼
   Streamlit UI
        │
        ▼
 HTTP POST Request
        │
        ▼
   Ollama Server
        │
        ▼
    Gemma 2B
        │
        ▼
 AI Generated Response
        │
        ▼
   Streamlit UI
        │
        ▼
       User
```

---

# 📁 Project Structure

```text
Streamlit-Ollama-Chatbot/
│
├── app.py
├── requirements.txt
└── README.md
```

### `app.py`

Contains the Streamlit interface and Ollama API communication.

### `requirements.txt`

Contains the Python packages required to run the Streamlit application.

### `README.md`

Contains project documentation and setup instructions.

---

# ⚙️ Installation

## 1. Clone the Repository

```bash
git clone https://github.com/YOUR-USERNAME/Streamlit-Ollama-Chatbot.git
```

Move into the project directory:

```bash
cd Streamlit-Ollama-Chatbot
```

---

# 🐍 2. Create a Virtual Environment

For Windows:

```powershell
python -m venv .venv
```

Activate it:

```powershell
.venv\Scripts\activate
```

---

# 📦 3. Install Dependencies

Install the required packages:

```powershell
pip install streamlit requests
```

Because the current code also imports the following libraries:

```text
pandas
numpy
matplotlib
plotly
```

you can alternatively install all imported packages:

```powershell
pip install streamlit pandas numpy matplotlib plotly requests
```

---

# 📄 requirements.txt

For the current code, you can create:

```text
requirements.txt
```

with:

```text
streamlit
pandas
numpy
matplotlib
plotly
requests
```

If you remove the unused imports from `app.py`, the requirements can be simplified to:

```text
streamlit
requests
```

---

# 🤖 Ollama Setup

This project requires **Ollama** to be installed and running on your computer.

Check whether Ollama is installed:

```powershell
ollama --version
```

Download the Gemma 2B model:

```powershell
ollama pull gemma2:2b
```

Check the installed models:

```powershell
ollama list
```

You should see:

```text
gemma2:2b
```

---

# 🧪 Test Ollama

Before starting Streamlit, test the model:

```powershell
ollama run gemma2:2b
```

Ask the model something like:

```text
What is Python?
```

If Ollama responds correctly, the AI model is ready.

---

# ▶️ Run the Streamlit Application

From the project directory:

```powershell
python -m streamlit run app.py
```

Streamlit will start a local server.

Open the URL displayed in the terminal, usually:

```text
http://localhost:8501
```

---

# 💬 Using the Chatbot

Once the application opens, you will see:

```text
Ask Me Anything
```

Enter your question.

For example:

```text
What is machine learning?
```

Click:

```text
Ask AI
```

The question will be sent to Ollama.

The generated answer will then appear on the Streamlit page.

---

# 🔌 Ollama API

The application communicates with Ollama using:

```text
http://localhost:11434/api/generate
```

The request is sent using:

```python
response = requests.post(
    "http://localhost:11434/api/generate",
    json={
        "model": "gemma2:2b",
        "prompt": question,
        "stream": False,
        "temperature": 0.7
    }
)
```

---

# 🧠 Request Parameters

| Parameter     | Value         | Purpose                       |
| ------------- | ------------- | ----------------------------- |
| `model`       | `gemma2:2b`   | Specifies the AI model        |
| `prompt`      | User question | Input sent to the model       |
| `stream`      | `False`       | Returns the complete response |
| `temperature` | `0.7`         | Controls response randomness  |

---

# 📤 Getting the AI Response

Ollama returns a JSON response.

The application extracts the generated answer using:

```python
answer = response.json()["response"]
```

The answer is then displayed using:

```python
st.write(answer)
```

---

# 🔄 Complete Workflow

```text
1. User opens Streamlit application
              │
              ▼
2. User enters a question
              │
              ▼
3. User clicks "Ask AI"
              │
              ▼
4. Streamlit sends HTTP POST request
              │
              ▼
5. Ollama receives the request
              │
              ▼
6. Gemma 2B processes the prompt
              │
              ▼
7. Ollama returns JSON response
              │
              ▼
8. Streamlit extracts "response"
              │
              ▼
9. AI answer is displayed
```

---

# ⚠️ Troubleshooting

## `'streamlit' is not recognized`

If Windows shows:

```text
'streamlit' is not recognized
```

use:

```powershell
python -m streamlit run app.py
```

---

## Ollama Connection Error

If the application cannot connect to Ollama, make sure Ollama is running.

Test:

```powershell
ollama run gemma2:2b
```

Then restart Streamlit:

```powershell
python -m streamlit run app.py
```

---

## Model Not Found

If you see an error related to `gemma2:2b`, download the model:

```powershell
ollama pull gemma2:2b
```

Then verify:

```powershell
ollama list
```

---

## AI Button Does Nothing

Make sure a question has been entered before clicking:

```text
Ask AI
```

The application sends the value stored in:

```python
question
```

to Ollama.

---

# 🔐 Privacy

Because the application uses Ollama locally, the question is sent to the Ollama server running on your own computer at:

```text
localhost:11434
```

The application does not require an external AI API key.

---

# 🔮 Future Improvements

The current application is intentionally simple. It can be improved by adding:

* 💬 Chat history
* 🧠 Conversation memory
* 🎨 Better UI
* ⏳ Loading indicator
* ⚠️ API error handling
* 🗑️ Clear conversation button
* 📋 Copy response button
* 🎤 Voice input
* 🔊 Text-to-speech
* 📄 PDF question answering
* 🧠 RAG implementation
* 🔍 Web search integration
* ⚙️ Model selection
* 🌡️ Adjustable temperature
* 💾 Conversation export

---

# 🎯 Learning Objectives

This project demonstrates:

* Python programming
* Streamlit application development
* REST API communication
* HTTP POST requests
* JSON request/response handling
* Local LLM integration
* Ollama
* Gemma 2B
* Basic AI chatbot development

---

# 👨‍💻 Author

**Ayush**

A beginner-friendly project created to learn **Streamlit, REST APIs, Ollama, and local AI/LLM integration**.

---

# ⭐ Support

If you found this project useful, consider giving the repository a ⭐ on GitHub.
