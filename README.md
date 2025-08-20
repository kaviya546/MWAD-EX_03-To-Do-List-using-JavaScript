# MWAD-EX_03-To-Do-List-using-JavaScript
## Date:20.08.2025

## AIM
To create a To-do Application with all features using JavaScript.

## ALGORITHM
### STEP 1
Build the HTML structure (index.html).

### STEP 2
Style the App (style.css).

### STEP 3
Plan the features the To-Do App should have.

### STEP 4
Create a To-do application using Javascript.

### STEP 5
Add functionalities.

### STEP 6
Test the App.

### STEP 7
Open the HTML file in a browser to check layout and functionality.

### STEP 8
Fix styling issues and refine content placement.

### STEP 9
Deploy the website.

### STEP 10
Upload to GitHub Pages for free hosting.

## PROGRAM
## INDEX.HTML
```

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Todo App</title>
  <link rel="stylesheet" href="style.css" />
</head>
<body>

  <div class="todo-container">
    <h1>📝 My Todo List</h1>
    
    <div class="input-group">
      <input type="text" id="taskInput" placeholder="Add a new task..." />
      <button onclick="addTask()">Add</button>
    </div>

    <div class="filter-buttons">
      <button onclick="filterTasks('all')">All</button>
      <button onclick="filterTasks('active')">Active</button>
      <button onclick="filterTasks('completed')">Completed</button>
    </div>

    <ul id="taskList"></ul>
  </div>

  <script src="script.js"></script>
</body>
</html>

```
## STYLE.CSS
```
* {
    box-sizing: border-box;
  }
  
  body {
    font-family: 'Segoe UI', sans-serif;
    background: #f5f7fa;
    margin: 0;
    padding: 40px;
    display: flex;
    justify-content: center;
  }
  
  .todo-container {
    background: #fff;
    padding: 30px;
    border-radius: 12px;
    width: 100%;
    max-width: 500px;
    box-shadow: 0 4px 12px rgba(0,0,0,0.1);
  }
  
  h1 {
    text-align: center;
    color: #333;
    margin-bottom: 20px;
  }
  
  .input-group {
    display: flex;
    gap: 10px;
    margin-bottom: 20px;
  }
  
  .input-group input {
    flex: 1;
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 6px;
  }
  
  .input-group button {
    background: #4CAF50;
    color: white;
    border: none;
    padding: 10px 15px;
    border-radius: 6px;
    cursor: pointer;
    transition: background 0.3s;
  }
  
  .input-group button:hover {
    background: #45a049;
  }
  
  .filter-buttons {
    display: flex;
    justify-content: space-around;
    margin-bottom: 20px;
  }
  
  .filter-buttons button {
    padding: 6px 14px;
    border: none;
    background: #eee;
    border-radius: 6px;
    cursor: pointer;
    transition: background 0.3s;
  }
  
  .filter-buttons button:hover {
    background: #ccc;
  }
  
  #taskList {
    list-style: none;
    padding: 0;
    margin: 0;
  }
  
  .task-item {
    background: #fafafa;
    padding: 12px 15px;
    margin-bottom: 10px;
    border-radius: 8px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    border-left: 4px solid #4CAF50;
  }
  
  .task-item.completed {
    text-decoration: line-through;
    opacity: 0.6;
  }
  
  .task-text {
    flex: 1;
    margin-right: 10px;
  }
  
  .actions button {
    background: none;
    border: none;
    cursor: pointer;
    margin-left: 5px;
    color: #555;
    font-size: 16px;
  }
  
  .actions button:hover {
    color: #000;
  }
  ```
## SCRIPT.JS
```
let tasks = JSON.parse(localStorage.getItem("tasks")) || [];
let currentFilter = "all";

function saveTasks() {
  localStorage.setItem("tasks", JSON.stringify(tasks));
}

function renderTasks() {
  const list = document.getElementById("taskList");
  list.innerHTML = "";

  const filtered = tasks.filter(task => {
    if (currentFilter === "active") return !task.completed;
    if (currentFilter === "completed") return task.completed;
    return true;
  });

  filtered.forEach((task, index) => {
    const li = document.createElement("li");
    li.className = "task-item" + (task.completed ? " completed" : "");

    const span = document.createElement("span");
    span.className = "task-text";
    span.textContent = task.text;

    const actions = document.createElement("div");
    actions.className = "actions";

    const toggleBtn = document.createElement("button");
    toggleBtn.innerHTML = task.completed ? "✅" : "⬜";
    toggleBtn.onclick = () => toggleComplete(index);

    const editBtn = document.createElement("button");
    editBtn.innerHTML = "✏️";
    editBtn.onclick = () => editTask(index);

    const delBtn = document.createElement("button");
    delBtn.innerHTML = "🗑️";
    delBtn.onclick = () => deleteTask(index);

    actions.appendChild(toggleBtn);
    actions.appendChild(editBtn);
    actions.appendChild(delBtn);

    li.appendChild(span);
    li.appendChild(actions);
    list.appendChild(li);
  });
}

function addTask() {
  const input = document.getElementById("taskInput");
  const text = input.value.trim();
  if (text !== "") {
    tasks.push({ text, completed: false });
    input.value = "";
    saveTasks();
    renderTasks();
  }
}

function toggleComplete(index) {
  tasks[index].completed = !tasks[index].completed;
  saveTasks();
  renderTasks();
}

function deleteTask(index) {
  if (confirm("Delete this task?")) {
    tasks.splice(index, 1);
    saveTasks();
    renderTasks();
  }
}

function editTask(index) {
  const newText = prompt("Edit task:", tasks[index].text);
  if (newText !== null && newText.trim() !== "") {
    tasks[index].text = newText.trim();
    saveTasks();
    renderTasks();
  }
}

function filterTasks(filter) {
  currentFilter = filter;
  renderTasks();
}
renderTasks();
```

## OUTPUT

![WhatsApp Image 2025-08-20 at 21 46 21_5bab0774](https://github.com/user-attachments/assets/04daffac-c387-4ecc-b496-9d16cc3162d0)

![WhatsApp Image 2025-08-20 at 21 47 05_cca587e3](https://github.com/user-attachments/assets/0bf6afce-5a4a-47da-9471-7019d92ab58c)


![WhatsApp Image 2025-08-20 at 21 47 21_f7f2ae20](https://github.com/user-attachments/assets/7484da77-37df-40ab-8603-749c5dd9153f)

## RESULT
The program for creating To-do list using JavaScript is executed successfully.
