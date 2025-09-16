# AI Avatar sketchpad

An interactive prototype where an AI tutor **speaks, chats, animates and sketches explanations in realtime**.
Built to showcase agentic AI design, multimodal coordination and rapid prototyping.

## Problem Statement

Traditional chatbots explain concepts only with **text**.  
This project explores: **Can AI tutors feel more engaging by combining text, speech, avatar animation, and live sketching?**


## Timebox & Scope

**Timebox** ~ 48 hours
**Implemented (MVP ✅):**
Backend(Flash + Socket.io)
LLM Integartion ( OpenAI -> JSON drawing plans)
Frontend with chat, sketchpad, avatar
Browser TTS + mouth sync
Basic drawing primitives (line, circle, rect, text, avatar_mouth)

## 🏗️ Architecture

```mermaid
flowchart LR
    U[User] <--> F[Frontend (HTML + Canvas + JS)]
    F <--> S[Socket.IO]
    S <--> B[Flask Backend]
    B <--> L[OpenAI LLM]

Frontend:
Chat UI
Avatar canvas (animated mouth)
Sketchpad canvas for step-by-step drawings
Speech output via browser speechSynthesis

Backend:
Flask + Socket.IO server
Handles chat + drawing plan generation
Prompts LLM with examples → structured JSON
Validates JSON (fallback to mock if invalid)


Data Contract (LLM -> Frontend)
{
  "text": "Explanation in plain text",
  "steps": [
    {
      "id": 1,
      "delay_ms": 0,
      "duration_ms": 600,
      "primitives": [
        { "type": "line", "x1":100, "y1":300, "x2":400, "y2":300, "stroke":"black", "width":3 }
      ],
      "annotation": "Draw base"
    }
  ]
}
Supported primitives:

line, circle, rect, text, avatar_mouth

Running the Demo
Requirements:
Python 3.9+
OpenAI API key
Google Colab (recommended) or local Python environment
ngrok (for public URL)

Steps (Colab)
Install dependencies:
pip install openai flask flask-socketio eventlet pyngrok

Set your API key:
import os
os.environ["OPENAI_API_KEY"] = "sk-..."

Run server.py in background.
Start ngrok tunnel on port 5000.
Open the ngrok public URL in your browser → interact with the tutor.

Example Prompts

Try these in the chat box:
“Draw a right triangle and label sides a, b, c.”
“Explain the equation of a circle.”
“Say hello and write ‘Welcome’ on the board.”

You’ll see:
Text reply in chat
Browser speech output
Avatar mouth synced with speech
Step-by-step sketchpad drawings

Future Work
Richer avatar (blinking eyes, gestures)
Save/replay sessions
Collaborative classrooms
Streaming generation (draw while speaking)
Open-source LLM support (HuggingFace, local inference)

Human Note
This is a timeboxed prototype — the goal was to prove the concept that AI tutors can be more natural by combining
speech, animation, and sketches, not to deliver production-level polish.

    
