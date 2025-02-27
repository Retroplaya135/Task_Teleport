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

#Architectural Diagram 

```

                +----------------------+
                |     End User         |
                | (Browser/HTTP Client)|
                +----------------------+
                           |
                           v
                +----------------------+
                |    FastAPI Service   |
                |   (Uvicorn Server)   |
                +----------------------+
                           |
          +----------------+----------------+
          |                |                |
          v                v                v
+----------------+  +----------------+  +----------------+
|   NLP Module   |  | Scheduler      |  | Automation     |
|   (nlp.py)     |  | (scheduler.py) |  | (automation.py)|
+----------------+  +----------------+  +----------------+
                           |
                           v
                +----------------------+
                | JSON Response Output |
                +----------------------+
                           |
                           v
                +----------------------+
                |     End User         |
                | (Display Results)    |
                +----------------------+



```
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
# Workflow Diagram

```
+------------------------------+
|  User submits project        |
|  description via POST        |
|  /process endpoint           |
+--------------+---------------+
               |
               v
+------------------------------+
| FastAPI endpoint receives    |
| the request                  |
+--------------+---------------+
               |
               v
+------------------------------+
| NLP Module:                  |
| decompose_project()          |
| (Extract actionable tasks)   |
+--------------+---------------+
               |
               v
+------------------------------+
| Scheduler Module:            |
| schedule_tasks()             |
| (Assign priorities &         |
|  schedule times)             |
+--------------+---------------+
               |
               v
+------------------------------+
| Automation Module:           |
| identify_automatable_tasks() |
| (Flag tasks for automation)  |
+--------------+---------------+
               |
               v
+------------------------------+
| Aggregate results and create |
| JSON response                |
+--------------+---------------+
               |
               v
+------------------------------+
| Return JSON response to user |
+------------------------------+

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

The API will be available at http://127.0.0.1:8000. Visit http://127.0.0.1:8000/docs for the interactive Swagger UI.

API Endpoints

```
GET 
```

Returns a welcome message.

```
POST /process
```

Accepts a JSON payload with a description field (the project description) and returns:
decomposed_tasks: The list of tasks extracted.
scheduled_tasks: Each task with a scheduled time and priority.
automatable_tasks: The subset of tasks flagged as automatable.









# Future Enhancements

```
Calendar Integration:
```

Integrate with real calendar APIs (Google Calendar, Outlook) for dynamic scheduling.

```
Enhanced NLP:
```

Improve task decomposition with more advanced NLP techniques.

```
Interactive Front End:
```

Develop a web-based front end for interactive task management.

```
Advanced Automation Detection:
```
Expand automation detection using custom machine learning models.

# License

This project is licensed under the MIT License – see the LICENSE file for details.
