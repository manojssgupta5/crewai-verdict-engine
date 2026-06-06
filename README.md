# AI Debate Crew

An AI powered multi agent debate system built using CrewAI.
The project simulates a structured debate between autonomous AI agents where each agent performs a specialized responsibility such as debating, validation, judgement, and email delivery.

Instead of relying on a single LLM response, the system breaks reasoning into multiple stages. This improves output quality, separation of concerns, and explainability.

---

# Project Goal

The goal of this project is to build a collaborative AI debate system where multiple autonomous agents independently research, argue, validate, and judge a debate topic.

The system demonstrates how agent based architectures can improve reasoning workflows by separating responsibilities across specialized agents.

The workflow includes:

* Argument generation for both sides
* Validation and fact checking
* Final judgement
* Automated email delivery

This project also demonstrates:

* Tool augmented AI agents
* Multi step reasoning pipelines
* Real world orchestration patterns
* Config driven agent design

---

# Architecture

```text
                    +------------------+
                    |   User Motion    |
                    +------------------+
                              |
                              v
                +------------------------+
                |   Favor Debater Agent  |
                +------------------------+
                              |
                              v
            +--------------------------------+
            | Favor Validation Agent         |
            +--------------------------------+
                              |
                              v
                +------------------------+
                | Against Debater Agent  |
                +------------------------+
                              |
                              v
           +---------------------------------+
           | Against Validation Agent        |
           +---------------------------------+
                              |
                              v
                    +----------------+
                    | Judge Agent    |
                    +----------------+
                              |
                              v
                    +----------------+
                    | Sender Agent   |
                    +----------------+
                              |
                              v
                         Email Result
```

---

# Features

* Multi agent debate execution
* Real time web research
* Validation and fact checking agents
* Judge based final decision
* Automated email sending
* Config driven agents and tasks
* Extendable architecture
* Tool integrated CrewAI agents

---

# Tech Stack

| Technology | Purpose                      |
| ---------- | ---------------------------- |
| Python     | Core language                |
| CrewAI     | Multi agent orchestration    |
| OpenAI API | LLM reasoning                |
| SerpAPI    | Web search                   |
| SendGrid   | Email delivery               |
| YAML       | Agent and task configuration |

---

# Project Structure

```text
debate/
│
├── crew.py
├── main.py
├── tools/
│   ├── sendgrid_tool.py
│   └── web_search_tool.py
│
├── config/
│   ├── agents.yaml
│   └── tasks.yaml
│
└── README.md
```

---

# Workflow

The system executes tasks sequentially:

1. Favor debater generates supporting arguments
2. Favor validator reviews the arguments
3. Against debater generates opposing arguments
4. Against validator reviews the arguments
5. Judge evaluates both sides
6. Sender emails the final outcome

This creates a layered reasoning pipeline instead of a single prompt response.

---

# Installation

## Clone Repository

```bash
git clone <your-repo-url>
cd debate
```

---

## Install Dependencies

```bash
pip install crewai
pip install openai
pip install sendgrid
pip install google-search-results
pip install serpapi
```

---

# Environment Variables

Create a `.env` file:

```env
OPENAI_API_KEY=
SERPAPI_API_KEY=
SENDGRID_API_KEY=
EMAIL_ADDRESS=
```

---

# Run Project

```bash
python main.py
```

---

# Example Input

```python
inputs = {
    "motion": "Supplement vitamins are best for the human body"
}
```

---

# Example Debate Flow

```text
Motion:
Remote work is better than office work

Favor Agent:
Remote work improves flexibility and productivity.

Against Agent:
Office work improves collaboration and innovation.

Validation Agents:
Verify argument quality and factual accuracy.

Judge:
Evaluates the stronger position.

Sender:
Emails final decision.
```

---

# Core Components

## crew.py

Defines:

* agents
* tasks
* workflow orchestration
* tool integrations

Uses CrewAI sequential process execution.

---

## main.py

Application entry point.

Responsible for:

* passing debate motion
* starting crew execution
* printing final result

---

## web_search_tool.py

Provides real time web search capability using SerpAPI.

Capabilities:

* fetch latest information
* retrieve statistics
* gather supporting evidence

The file also contains:

* DuckDuckGo implementation
* caching architecture
* fallback search logic

These are currently commented but show future scalability planning.

---

## sendgrid_tool.py

Responsible for email delivery.

Features:

* SendGrid integration
* environment based configuration
* final debate result delivery

---

# Strengths of This Design

## Separation of Concerns

Each agent has a dedicated responsibility.

## Better Reasoning

Validation agents reduce hallucination risk.

## Extendability

Easy to add:

* memory
* moderation
* RAG
* analytics
* APIs
* human review

## Real World Architecture

Closer to production grade AI workflows than single prompt systems.

---

# Current Limitations

| Limitation            | Impact              |
| --------------------- | ------------------- |
| Sequential execution  | Higher latency      |
| No retry handling     | Failure sensitive   |
| No structured outputs | Harder integrations |
| No persistence layer  | No memory/history   |
| No async execution    | Lower scalability   |

---

# Future Enhancements

## Parallel Agent Execution

Run favor and against debaters simultaneously.

---

## Add Memory Layer

Use:

* Redis
* Vector DB
* PostgreSQL

For:

* debate history
* persistent memory
* learning context

---

## Add RAG Support

Enable agents to retrieve:

* PDFs
* research papers
* internal documents

---

## Add Structured Outputs

Use Pydantic models for machine readable responses.

---

## Add Observability

Track:

* execution metrics
* latency
* token usage
* traces
* failures

---

# Example Use Cases

* AI research assistant
* Policy analysis
* Legal debate simulation
* Education and learning
* Decision support systems
* Autonomous reasoning pipelines

---

# License

MIT License

---

# Author

Built using CrewAI and OpenAI based multi agent architecture.
