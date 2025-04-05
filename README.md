# 🤖 AI-Powered Customer Service Chatbot

This project is a simple AI-powered chatbot built using the **Hugging Face Inference API** and **Gradio UI**. It's designed for customer service applications and runs easily in **Google Colab** or any Python environment.

---

## 🔧 Features

- Uses Hugging Face models (e.g., `DialoGPT`, `Flan-T5`) to generate chatbot replies
- Lightweight, serverless deployment using Hugging Face’s free API tier
- Clean and minimal **Gradio UI**
- Supports basic conversation memory (chat history)

---

## 🚀 Getting Started

### 1. Clone or Open in Google Colab
You can either copy the code to Colab or use it locally.

### 2. Install Dependencies
```bash
pip install gradio requests
```

### 3. Get a Hugging Face API Token

- Go to [https://huggingface.co/settings/tokens](https://huggingface.co/settings/tokens)
- Click “New Token”
- Set permission to **Read**
- Copy the token (starts with `hf_...`)
- Replace the token in your script:
```python
API_TOKEN = "your_huggingface_api_token"
```

---

## 💻 How It Works

### Model

By default, the chatbot uses:
```
microsoft/DialoGPT-medium
```

This is a dialogue model but may generate generic or low-quality answers. We recommend switching to a better model like:

- `google/flan-t5-large` (task-tuned)
- `mistralai/Mixtral-8x7B-Instruct`
- `meta-llama/Llama-2-7b-chat`

### API Integration

Your query is sent as a POST request to Hugging Face's Inference API:
```python
url = "https://api-inference.huggingface.co/models/microsoft/DialoGPT-medium"
headers = {"Authorization": f"Bearer {API_TOKEN}"}
payload = {"inputs": prompt}
```

The response is parsed and returned to the UI.

### UI

Gradio provides a web interface with:
- Input text box
- Chat history display

Example snippet:
```python
gr.Interface(fn=chat, inputs="text", outputs="text").launch()
```

---

## 📈 How to Improve

### ✅ Switch to a Better Model

Update the model URL in the `query_huggingface_model` function:
```python
url = "https://api-inference.huggingface.co/models/google/flan-t5-large"
```

Adjust the prompt accordingly for task-specific response.

### ✅ Use RAG (Retrieval-Augmented Generation)

Train your chatbot on:
- FAQ documents
- Customer queries
- Knowledge base

Tools you can use:
- `LangChain`
- `Haystack`
- `LlamaIndex`

### ✅ Use GPT-4 or Claude (if budget allows)

With OpenAI or Anthropic, you can achieve human-level answers.

---

## 🛠️ File Structure (if applicable)

```
📁 chatbot-project/
├── ai_chatbot.py         # Main Python script
├── README.md             # This file
```

---

## 📌 Limitations

- Response quality depends on the model used
- No long-term memory/context across sessions
- Hugging Face free API has rate limits

---

## 📬 Contact

Built by **Prem Chandrakant Patil**  
Email: `premcpatil1604@gmail.com`  
LinkedIn: [https://www.linkedin.com/in/prem-patil-740014282](https://www.linkedin.com/in/prem-patil-740014282`)
