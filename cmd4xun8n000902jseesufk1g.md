---
title: "Creating a Personalized Storytelling AI with Google ADK"
datePublished: Mon Jun 30 2025 17:54:15 GMT+0000 (Coordinated Universal Time)
cuid: cmd4xun8n000902jseesufk1g
slug: creating-a-personalized-storytelling-ai-with-google-adk-55923651e8f0
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1752608500992/a45f8168-8177-4974-b533-37587d634863.jpeg

---

Photo by [Melanie Deziel](https://unsplash.com/@storyfuel?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

> ✨ *Turn names into magical stories with a warm, intelligent AI agent — built using Google’s Agent Development Kit (ADK).*

In the evolving world of AI agents, personalization is becoming the secret sauce to deeper engagement. Imagine an AI that greets you by name, uncovers the roots of your identity, and spins a personalized story just for *you*. That’s exactly what the `**name_story_agent**` does.

In this blog, we’ll explore how to build and run this charming conversational agent using [Google’s ADK (Agent Development Kit)](https://google.github.io/adk-docs/) — the toolkit designed to simplify and structure AI agent development with LLMs.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1752608499375/d06a1c03-0536-4ed5-8338-9063e0876ff8.png)

### 🔍 Meet the Agent

from google.adk.agents import Agent

root\_agent = Agent(  
    name="name\_story\_agent",  
    model="gemini-2.0-flash",  
    description=(  
        "An interactive agent that asks for the user's name and creates a personalized story based on the meaning and origin of their name."  
    ),  
    instruction=(  
        "You are a friendly and creative storytelling agent. Your task is to:\\n"  
        "1. Greet the user warmly and ask for their name\\n"  
        "2. Once you receive their name, research or provide information about the meaning, origin, or cultural significance of their name\\n"  
        "3. Create a short, imaginative, and positive story (2-3 paragraphs) that incorporates the meaning of their name\\n"  
        "4. Make the story personal and engaging, using the user's actual name as the protagonist\\n"  
        "5. If you don't know the exact meaning of a name, create a beautiful story based on how the name sounds or feels\\n"  
        "6. Always be encouraging and make the user feel special about their name\\n"  
        "Keep the tone warm, creative, and uplifting throughout the interaction."  
    )  
)

This is not just another chatbot. It’s a **story companion**, a creative assistant designed to connect emotionally through names and narratives.

### 🧠 How Does It Work?

The `Agent` class in ADK is a wrapper around Google’s Gemini models (or other LLMs), enhanced with custom instructions and project structure to guide behavior and ensure consistent deployment.

### 🏗️ Project Structure

ADK requires a specific structure to recognize and deploy agents:

your\_project/  
├── name\_story\_agent/  
│   ├── \_\_init\_\_.py       \# -> from . import agent  
│   ├── agent.py          \# -> contains \`root\_agent\`  
│   ├── .env              \# -> contains GOOGLE\_API\_KEY

### Required Files:

File Purpose `__init__.py` Ensures the agent is discoverable `agent.py` Where the `root_agent` is defined `.env` Stores your Gemini API key securely

✅ **Tip:** Always run `adk` commands from the **parent folder**, not the agent folder.

### 💡 What Makes `name_story_agent` Special?

Here’s a breakdown of its capabilities:

Feature Description ✨ **Personalized Interaction** Asks for the user’s name, remembers it 📜 **Name Origin Discovery** Provides meaning or cultural insight 🪄 **Creative Storytelling** Writes an uplifting 2–3 paragraph story 💬 **Warm Tone** Encouraging, friendly, and inclusive 💡 **Fallback Creativity** Even unknown names get beautiful, imagined meanings

### 🧪 Run It Live

To start chatting with your story agent:

### ✅ Step-by-Step Setup

\# Navigate to your project’s parent directory  
cd your\_project/

\# Start the ADK web server  
adk web

### 🌐 Visit

Open your browser and go to `http://localhost:8000`. Choose `name_story_agent` from the dropdown and start chatting!

### 🌍 Example Conversation

> ***Agent:*** *“Hello there! 🌟 I’m your story companion. What’s your name?”*

> ***User:*** *“Aarav”*

> ***Agent:*** *“Aarav — a beautiful name of Sanskrit origin, meaning ‘peaceful’ and ‘calm’. Let’s imagine a story just for you…*

> *In a quiet village nestled between whispering mountains, lived a young boy named Aarav. From a very young age, he had the power to calm storms — not with magic, but with the serene stillness of his heart. Villagers often said that the winds listened to him, and even the clouds softened at his gaze…”*

> …and the story continues, wrapping the user in the magic of their name.

### 🔍 Under the Hood: Why This Works

### ✅ Agent Instructions

The real “magic” comes from the carefully crafted **instructions**:

"You are a friendly and creative storytelling agent...  
1. Greet the user warmly...  
2. Research or invent the meaning...  
3. Create a short, imaginative story...  
...  
6. Always be encouraging..."

These guide the LLM to generate structured, emotionally resonant conversations.

### ⚙️ Customize It

Want to enhance your `name_story_agent`?

*   🌐 Add **external tools** for real-time name meaning lookup
*   🗣️ Use **multi-language support** for diverse users
*   🧑‍🎓 Add **learning tips** about cultures, naming customs, or history

### 🧠 Bonus: ADK Agent Capabilities Overview

### 🚀 What You’ve Learned

✅ Skill

✅ How to build an LLM agent with ADK

✅ How to define and structure agent instructions

✅ How to run and test agents locally

✅ How to design for personalization and user engagement

### 🛠️ Next Steps

Ready to go further? Try:

*   Using **Gemini Pro** for deeper reasoning
*   Deploying your agent to the **web or productio**

### 🙌 Final Thoughts

The `name_story_agent` is more than code — it's a joyful experience that connects users with their identity in a creative way. Whether you're building AI for fun, education, or products, ADK makes it easy to get started.

> *💬* “Every name holds a story. Your agent just unlocked it.”

Full Code : [Github Adk Course](https://github.com/Yash-Kavaiya/adk-course/blob/main/01_first_agent/README.md)

### 👉 Learn More

*   [📘 ADK Official Docs](https://google.github.io/adk-docs/)
*   [📦 ADK GitHub Repository](https://github.com/google/adk)
*   [💡 Gemini API](https://ai.google.dev/)