Perfect choice of project 🚀 — a Task Tracker CLI is a solid way to practice file handling, JSON manipulation, and CLI argument parsing. Since you’d like to push the solution to GitHub with a proper **README**, let’s plan step by step. I’ll draft the **project structure**, **main Python implementation**, and a **README.md** for your repo.

---

## 📂 Project Structure

```bash
Task-Tracker/
├── task_cli.py       # Main CLI app
├── tasks.json        # Stores tasks (auto-created if missing)
└── README.md         # Documentation
```

---

## 🐍 Python Implementation (`task_cli.py`)

Here’s a clean Python version that meets your requirements:

```python
#!/usr/bin/env python3
import sys
import json
import os
from datetime import datetime

TASKS_FILE = "tasks.json"

def load_tasks():
    if not os.path.exists(TASKS_FILE):
        return []
    with open(TASKS_FILE, "r") as f:
        try:
            return json.load(f)
        except json.JSONDecodeError:
            return []

def save_tasks(tasks):
    with open(TASKS_FILE, "w") as f:
        json.dump(tasks, f, indent=4)

def generate_id(tasks):
    return max([task["id"] for task in tasks], default=0) + 1

def add_task(description):
    tasks = load_tasks()
    task = {
        "id": generate_id(tasks),
        "description": description,
        "status": "todo",
        "createdAt": datetime.now().isoformat(),
        "updatedAt": datetime.now().isoformat(),
    }
    tasks.append(task)
    save_tasks(tasks)
    print(f"Task added successfully (ID: {task['id']})")

def update_task(task_id, description):
    tasks = load_tasks()
    for task in tasks:
        if task["id"] == task_id:
            task["description"] = description
            task["updatedAt"] = datetime.now().isoformat()
            save_tasks(tasks)
            print("Task updated successfully")
            return
    print("Task not found")

def delete_task(task_id):
    tasks = load_tasks()
    new_tasks = [task for task in tasks if task["id"] != task_id]
    if len(tasks) == len(new_tasks):
        print("Task not found")
    else:
        save_tasks(new_tasks)
        print("Task deleted successfully")

def mark_status(task_id, status):
    tasks = load_tasks()
    for task in tasks:
        if task["id"] == task_id:
            task["status"] = status
            task["updatedAt"] = datetime.now().isoformat()
            save_tasks(tasks)
            print(f"Task marked as {status}")
            return
    print("Task not found")

def list_tasks(filter_status=None):
    tasks = load_tasks()
    if filter_status:
        tasks = [task for task in tasks if task["status"] == filter_status]

    if not tasks:
        print("No tasks found")
        return

    for task in tasks:
        print(f"[{task['id']}] {task['description']} - {task['status']}")

def main():
    if len(sys.argv) < 2:
        print("Usage: task-cli <command> [arguments]")
        return

    command = sys.argv[1]

    if command == "add":
        if len(sys.argv) < 3:
            print("Usage: task-cli add <description>")
            return
        add_task(" ".join(sys.argv[2:]))

    elif command == "update":
        if len(sys.argv) < 4:
            print("Usage: task-cli update <id> <description>")
            return
        update_task(int(sys.argv[2]), " ".join(sys.argv[3:]))

    elif command == "delete":
        if len(sys.argv) < 3:
            print("Usage: task-cli delete <id>")
            return
        delete_task(int(sys.argv[2]))

    elif command == "mark-in-progress":
        if len(sys.argv) < 3:
            print("Usage: task-cli mark-in-progress <id>")
            return
        mark_status(int(sys.argv[2]), "in-progress")

    elif command == "mark-done":
        if len(sys.argv) < 3:
            print("Usage: task-cli mark-done <id>")
            return
        mark_status(int(sys.argv[2]), "done")

    elif command == "list":
        if len(sys.argv) == 2:
            list_tasks()
        else:
            status = sys.argv[2]
            if status not in ["todo", "in-progress", "done"]:
                print("Invalid status. Use: todo, in-progress, or done")
            else:
                list_tasks(status)

    else:
        print("Unknown command")

if __name__ == "__main__":
    main()
```

Make it executable:

```bash
chmod +x task_cli.py
```

Then run:

```bash
./task_cli.py add "Buy groceries"
./task_cli.py list
```

---

## 📘 README.md

Here’s a professional `README.md` for your GitHub:

```markdown
# 📝 Task Tracker CLI

A simple **Command Line Interface (CLI)** to manage tasks.  
This project helps practice **file handling, JSON storage, and CLI argument parsing**.

## 🚀 Features
- Add, update, and delete tasks
- Mark tasks as `todo`, `in-progress`, or `done`
- List tasks by status or all at once
- Persistent storage in `tasks.json`

## 📂 Project Structure
```

Task-Tracker/
├── task\_cli.py       # Main CLI app
├── tasks.json        # Stores tasks (auto-created if missing)
└── README.md         # Documentation

````

## ⚙️ Installation
Clone the repository:
```bash
git clone https://github.com/GeigerJR/Task-Tracker.git
cd Task-Tracker
````

Make the CLI script executable:

```bash
chmod +x task_cli.py
```

## 🖥️ Usage

### Add a new task

```bash
./task_cli.py add "Buy groceries"
# Output: Task added successfully (ID: 1)
```

### Update a task

```bash
./task_cli.py update 1 "Buy groceries and cook dinner"
```

### Delete a task

```bash
./task_cli.py delete 1
```

### Mark a task

```bash
./task_cli.py mark-in-progress 1
./task_cli.py mark-done 1
```

### List tasks

```bash
./task_cli.py list
./task_cli.py list todo
./task_cli.py list in-progress
./task_cli.py list done
```

## 🛠️ Tech Stack

* **Python 3**
* **JSON for storage**

## 📌 Future Improvements

* Add priority levels (Low, Medium, High)
* Add deadlines/reminders
* Export tasks to CSV/Markdown

---

💡 Contributions are welcome! Fork the repo, make changes, and submit a PR.

```

---

👉 Next step: Do you want me to also prepare the **Git commands** to push this into your repo (`https://github.com/GeigerJR/Task-Tracker.git`) so you can copy-paste them directly?
```
