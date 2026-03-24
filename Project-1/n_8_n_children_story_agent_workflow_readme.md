# 📚 Story Generation Agent with Input & Output Guard (n8n)

This repository contains an **n8n workflow** that implements a **safe AI-powered children's story generator** using a multi-agent architecture.

The workflow ensures:
- User input is validated (Input Guard)
- Story is generated (Story Agent)
- Output is reviewed and corrected (Output Guard)

---

## 🚀 Features

- 🛡️ Input validation for safe, child-friendly topics
- ✍️ AI-based story generation (age 3–10)
- 🔍 Output quality and safety checks
- 🔀 Conditional branching (approved vs rejected)
- 📦 Structured JSON parsing for reliability
- 💬 Chat-based interaction using n8n

---

## 🧠 Workflow Overview

```
User Input
   ↓
Input Guard Agent
   ↓
IF (Approved?)
   ├── Yes → Story Agent → Output Guard → Final Story
   └── No  → Suggest Safe Topic
```

---

## ⚙️ Node Breakdown

### 🔹 Chat Trigger
- Entry point of workflow
- Receives user topic input

### 🔹 Input Guard Agent
- Validates topic for:
  - Violence / harmful content
  - Adult or inappropriate themes
  - Scary elements (for kids under 10)
- Converts to child-friendly topic if needed

#### Output Format
```json
{
  "status": "approved",
  "cleaned_topic": "A friendly dragon helping kids"
}
```

or

```json
{
  "status": "rejected",
  "reason": "Too scary for children",
  "suggested_topic": "A brave puppy exploring a forest"
}
```

---

### 🔹 Structured Output Parser
- Enforces strict JSON schema
- Prevents malformed AI responses

---

### 🔹 IF Node
- Checks: `status === approved`
- Routes flow accordingly

---

### 🔹 Story Agent
- Generates story with:
  - Simple language
  - Positive themes
  - Clear structure (beginning, middle, end)
- Length: 150–400 words

---

### 🔹 Output Guard Agent
- Reviews story for:
  - Safety (no fear/violence)
  - Readability
  - Tone (positive, warm)
- Fixes only problematic parts

---

### 🔹 Chat Nodes
- ✅ Sends final story (approved flow)
- ❌ Sends rejection + suggestion (rejected flow)

---

## 🛠️ Requirements

- n8n (latest version)
- OpenAI API key
- LangChain nodes enabled

---

## 🔑 Setup Guide

1. Import the JSON workflow into n8n
2. Configure OpenAI credentials
3. Activate the workflow
4. Use n8n chat interface to test

---

## 🔄 Execution Flow

### ✅ Approved Case
1. User submits topic
2. Input Guard validates
3. Story Agent generates story
4. Output Guard refines story
5. Final story returned

### ❌ Rejected Case
1. Input Guard rejects topic
2. User receives:
   - Reason for rejection
   - Suggested safe alternative

---

## 📌 Example

### Input
```
A monster attacking children
```

### Output
```
Hey I can't generate story on the given topic. Try with - A friendly monster helping children
```

---

## 🔐 Safety Architecture

This workflow uses a **Guardrails Pattern**:

- Input filtering (before generation)
- Output filtering (after generation)
- Schema validation (structured responses)

---

## 🤖 Models Used

| Component       | Model            |
|----------------|------------------|
| Input Guard    | gpt-3.5-turbo    |
| Story Agent    | gpt-5.4          |
| Output Guard   | gpt-3.5-turbo    |

---

## 💡 Use Cases

- Kids storytelling apps
- Educational tools
- AI safety demos
- Agent-based AI learning

---

## 🚧 Future Enhancements

- 🌍 Multi-language support
- 🖼️ Image generation integration
- 💾 Story storage (DB)
- 👤 Personalized stories

---

## 🤝 Contribution

Feel free to fork and enhance this workflow with more agents or integrations.

---

## 📄 License

Open-source for learning and experimentation.

---

## 🙌 Credits

Built using:
- n8n
- OpenAI
- LangChain

---

✨ Happy Building with AI Agents!

