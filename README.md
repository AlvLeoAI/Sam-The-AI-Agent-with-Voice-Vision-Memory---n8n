# Sam: The AI Agent with Voice, Vision & Memory - n8n

---

<aside>

### **Goal:**

To build a fully autonomous AI agent capable of handling multimodal user interactions (text, voice, image) inside Telegram, with memory and access to external tools like email, calendar, contacts, and web search.

### **Problem:**

Most chatbots are limited to one input type (text) and lack context, memory, or connection to external tools. Real-life productivity assistants need to understand multiple input types, store short-term memory, and execute real-world tasks autonomously.

### **Solution:**

### 🔷 Step 1:

Set up a Telegram bot using BotFather and connect it to n8n with `Telegram Trigger`.

### 🔷 Step 2:

Create a `Switch` node to classify incoming messages into 3 types: text, voice, image.

### 🔷 Step 3:

For image input, create a branch that downloads the image, fixes the file extension, and sends it to OpenAI Vision for analysis.

### 🔷 Step 4:

For voice input, download the audio file and use OpenAI Whisper to transcribe it to text.

### 🔷 Step 5:

For text input, capture and normalize it using a `Set` node to structure the prompt.

### 🔷 Step 6:

Pass all text into the `AI Agent` node (LangChain Agent) using an OpenAI GPT model with `Window Buffer Memory`.

### 🔷 Step 7:

Define a powerful system prompt that explains the agent’s tools and expected response formats.

### 🔷 Step 8:

Connect tools to the AI Agent: Get Emails, Send Email, Get Calendar, Set Calendar, Contacts (Airtable), Google Search (SerpAPI).

### 🔷 Step 9:

Use `LangChain Tools` node types to expose all tools in the agent’s environment.

### 🔷 Step 10:

Set up the email tools using Gmail API with OAuth for reading and sending messages.

### 🔷 Step 11:

Configure Google Calendar tools to check and schedule meetings based on LLM intent.

### 🔷 Step 12:

Connect Airtable as a contact database and allow AI to perform filtered searches by name.

### 🔷 Step 13:

Connect SerpAPI for live web search via Google, returning snippets and URLs.

### 🔷 Step 14:

Add conditional logic (`If`) to decide whether the AI response should be sent as voice or text.

### 🔷 Step 15:

If audio response is needed, use OpenAI TTS to convert the reply into an mp3.

### 🔷 Step 16:

Send voice reply through Telegram using `sendAudio`.

### 🔷 Step 17:

If no audio is required, send a text message using `sendMessage`.

### 🔷 Step 18:

Group sticky notes visually to separate Voice Chat, Image Chat, Agent Core, and Response Handler blocks.

### 🔷 Step 19:

Test multimodal prompts: image captioning, audio commands, contact queries, and email actions.

### 🔷 Step 20:

Enable logging and memory persistence by session ([chat.id](http://chat.id/) as memory key).

---

### **Tools Used:**

- n8n
- OpenAI (GPT, Whisper, TTS)
- Telegram
- Airtable
- Gmail API
- Google Calendar API
- SerpAPI

### **Impact:**

This project showcases a fully modular and extensible AI assistant capable of handling dynamic human interaction. It simulates real-world use cases like managing a calendar, sending emails, understanding images, and replying by voice. Perfect for showcasing advanced AI x automation architecture.

### **🧠Learnings:**

- How to combine LangChain agents with tool execution inside n8n
- How to handle multimodal inputs in automation workflows
- The power of context memory and conditional outputs
- Managing credentials securely and exporting production-ready flows
- Importance of human-like responses for user engagement
</aside>
