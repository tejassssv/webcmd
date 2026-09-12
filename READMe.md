# 🧠 Autonomous Web Research Agent

### An AI agent that can take a research goal, search the web, understand the results, and remember what it learned.

We built this project as a simple experiment to see how far we could take an AI assistant beyond just asking questions and getting answers.

Normally, an AI works like this:

```text
Question → AI → Answer
```

Our idea was a little different:

The agent gets a goal from the user, uses **Groq** to decide what to do, uses **webcmd** to interact with the web, and then uses Groq again to understand the results.

It also saves useful learnings in a local `memory.json` file so that those learnings can be used in future tasks.

---

## 🚀 What We Built

The main idea is to make the AI responsible for more than just generating text.

For every task, our agent goes through these steps:

1. **Understand the user's goal**
2. **Create a research instruction**
3. **Use webcmd to search the web**
4. **Read and analyze the results**
5. **Give the user a final answer**
6. **Save one useful learning for the next task**

So the agent doesn't just answer once. It can also carry something useful from one task into the next.

---


For example, if the user asks:

> "Research the latest developments in AI agents."

Groq first decides what kind of web research should be done. That instruction is passed to `webcmd`.

Once the results come back, Groq analyzes them and creates the final response.

At the end, the agent also tries to identify something useful that it learned from the task and saves it.

---

## 🧠 Memory

One part we wanted to experiment with was **memory**.

The agent stores its learnings in:

```text
memory.json
```

For example:

```json
{
  "learnings": [
    "Use more specific searches when researching fast-changing technology topics."
  ]
}
```

When another task starts, these previous learnings are given to the planner.

This means the agent has at least a basic form of **experience from previous tasks**, instead of starting completely from zero every time.

We kept the memory system as a simple JSON file for this prototype so that it is easy to understand, test, and improve later.

---

## 🛠️ Technologies We Used

| Technology     | Why we used it                              |
| -------------- | ------------------------------------------- |
| **Node.js**    | Main application and agent logic            |
| **Groq API**   | Connecting our application to the AI model  |
| **Groq Model** | Planning and understanding research results |
| **webcmd**     | Searching/interacting with the live web     |
| **JSON**       | Storing agent memory                        |
| **VS Code**    | Development and testing                     |

We used the OpenAI-compatible interface provided by Groq through the Node.js SDK.

---

## 💻 Running the Project

Install the dependencies:

```bash
npm install
```

Create a `.env` file:

```env
GROQ_API_KEY=your_groq_api_key
```

Then run the agent:

```bash
node index.js "Research the latest developments in AI agents"
```

You can also start it without a command and enter the research goal manually:

```bash
node index.js
```

---

## 🧪 Testing

We developed and tested the project in **VS Code**.

During testing, we focused on the complete flow rather than just checking whether the AI could generate an answer.

We tested whether the agent could:

* Understand different research goals
* Generate useful instructions for `webcmd`
* Process the returned web information
* Generate a meaningful final response
* Save new learnings
* Use previous learnings in later tasks
* Handle incorrect or unexpected responses from the API

This helped us improve the flow and make the different parts work together reliably.

---

## 📁 Project Structure

```text
.
├── index.js
├── memory.json
├── package.json
├── .env
├── .gitignore
└── README.md
```

The main logic is inside `index.js`.

Some of the important functions are:

* `runAgent()` — controls the complete process
* `createGroqClient()` — connects to Groq
* `useLiveWeb()` — handles web research through webcmd
* `loadMemory()` — loads previous learnings
* `saveMemory()` — saves new learnings
* `parseJsonSafely()` — safely handles model responses

---

## 🎯 Why We Think This Is Interesting

We didn't want to build just another chatbot.

The interesting part of our project is the connection between **AI reasoning, a real web tool, and memory**.

The AI decides what to research.

`webcmd` actually performs the web interaction.

The AI then looks at what came back and decides what is useful.

Finally, the agent saves something from that experience for later.

That gives us a small but working example of an **agent that can plan, act, observe, and learn**.

---

## 🔮 What's Next?

There is a lot we can build on top of the current version.

Some of the things we would like to add are:

* Better long-term memory
* Multi-step research
* Source verification
* Multiple tools
* Parallel research
* Automatic report generation
* Multiple specialized agents

The current version is our starting point for exploring these ideas.

---

## 💡 Our Goal

The bigger idea behind this project is simple:

> **We want to move from AI that only answers questions to AI that can actually work toward a goal.**

Give it a goal.

Let it figure out what to do.

Let it use the right tools.

Let it learn from what happened.

And use that experience the next time.

### 🧠 Plan. Search. Understand. Learn.
