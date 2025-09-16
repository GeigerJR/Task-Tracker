---

## 📘 README.md

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

### 💡 https://roadmap.sh/projects/task-tracker

```
