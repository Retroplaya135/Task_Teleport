# Task Teleport - Intelligent Workflow Decomposer

Task Teleport is an AI-powered service that decomposes a high-level project description into actionable tasks, schedules them based on a simple heuristic, and identifies tasks that may be automated.

This service is implemented as a FastAPI application and is designed to be deployable as a SaaS solution. It is built with extensibility in mind, allowing for future integration with calendar APIs, more advanced NLP models, and additional automation features.

---

## Features

- **NLP Decomposition:**  
  Uses spaCy to break down a project description into individual, actionable tasks.

- **Task Scheduling:**  
  Assigns dummy priorities and scheduled times (starting at 9:00 AM) to each task.

- **Automation Identification:**  
  Flags tasks that contain keywords (e.g., "email", "update", "notification") as potentially automatable.

---

## Repository Structure

```
TaskTeleport/ 
├── README.md 
├── requirements.txt 
├── LICENSE 
  └── task_teleport/ 
  ├── init.py 
  ├── main.py 
  ├── nlp.py 
  ├── scheduler.py 
  └── automation.py
```


---

## Getting Started

### Prerequisites

- Python 3.7+
- [spaCy](https://spacy.io/) (with the English model)

### Installation

1. **Clone the repository:**
   ```bash
   git clone https://github.com/yourusername/TaskTeleport.git
   cd TaskTeleport

2. Create and activate a virtual environment:
   ```bash
   python -m venv venv
   source venv/bin/activate   # On Windows: venv\Scripts\activate

3. Install dependencies:
```
   pip install -r requirements.txt
```

4. Download the spaCy English model:
```
python -m spacy download en_core_web_sm
```

# Running the Service

Run the FastAPI application with Uvicorn:

```
uvicorn task_teleport.main:app --reload
```
