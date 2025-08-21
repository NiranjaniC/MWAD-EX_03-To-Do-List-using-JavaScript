# MWAD-EX_03-To-Do-List-using-JavaScript
## Date: 21/08/2025

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
  <title>Dark To-Do App</title>
  <link rel="stylesheet" href="style.css" />
</head>
<body>
  <div class="app">
    <h1>📝 My To-Do List</h1>
    <div class="todo-input">
      <input type="text" id="taskInput" placeholder="Add a new task...">
      <button id="addTaskBtn">Add</button>
    </div>
    <ul id="taskList"></ul>
    <div class="footer">
      <button id="clearAll">Clear All</button>
      <button id="toggleTheme">🌙 Theme</button>
    </div>
  </div>
  <script src="script.js"></script>
</body>
</html>
```
## INDEX.CSS
```
/* Dark theme base */
body {
  font-family: 'Segoe UI', sans-serif;
  background-color: #121212;
  color: #f0f0f0;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  margin: 0;
}

.app {
  background: #1e1e1e;
  padding: 20px;
  border-radius: 16px;
  width: 350px;
  box-shadow: 0 0 20px rgba(0,0,0,0.6);
}

h1 {
  text-align: center;
  color: #ffcc00;
  margin-bottom: 20px;
}

.todo-input {
  display: flex;
  gap: 10px;
}

.todo-input input {
  flex: 1;
  padding: 10px;
  border: none;
  border-radius: 8px;
  background: #2a2a2a;
  color: #fff;
}

.todo-input button {
  padding: 10px 15px;
  border: none;
  border-radius: 8px;
  background: #ffcc00;
  cursor: pointer;
  font-weight: bold;
}

ul {
  list-style: none;
  padding: 0;
  margin-top: 20px;
  max-height: 300px;
  overflow-y: auto;
}

li {
  background: #2a2a2a;
  margin: 8px 0;
  padding: 10px;
  border-radius: 8px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

li.completed {
  text-decoration: line-through;
  opacity: 0.6;
}

li button {
  margin-left: 5px;
  background: transparent;
  border: none;
  cursor: pointer;
  color: #ffcc00;
}

.footer {
  margin-top: 20px;
  display: flex;
  justify-content: space-between;
}
```
##INDEX.JS
```
// Select DOM elements
const taskInput = document.getElementById("taskInput");
const addTaskBtn = document.getElementById("addTaskBtn");
const taskList = document.getElementById("taskList");
const clearAllBtn = document.getElementById("clearAll");
const toggleThemeBtn = document.getElementById("toggleTheme");

// Load tasks from localStorage
let tasks = JSON.parse(localStorage.getItem("tasks")) || [];

// Render tasks
function renderTasks() {
  taskList.innerHTML = "";
  tasks.forEach((task, index) => {
    const li = document.createElement("li");
    li.className = task.completed ? "completed" : "";
    li.innerHTML = `
      <span onclick="toggleTask(${index})">${task.text}</span>
      <div>
        <button onclick="editTask(${index})">✏️</button>
        <button onclick="deleteTask(${index})">🗑️</button>
      </div>
    `;
    taskList.appendChild(li);
  });
  localStorage.setItem("tasks", JSON.stringify(tasks));
}

// Add Task
addTaskBtn.addEventListener("click", () => {
  const text = taskInput.value.trim();
  if (text !== "") {
    tasks.push({ text, completed: false });
    taskInput.value = "";
    renderTasks();
  }
});

// Toggle Task Completion
function toggleTask(index) {
  tasks[index].completed = !tasks[index].completed;
  renderTasks();
}

// Edit Task
function editTask(index) {
  const newTask = prompt("Edit your task:", tasks[index].text);
  if (newTask !== null && newTask.trim() !== "") {
    tasks[index].text = newTask.trim();
    renderTasks();
  }
}

// Delete Task
function deleteTask(index) {
  tasks.splice(index, 1);
  renderTasks();
}

// Clear All Tasks
clearAllBtn.addEventListener("click", () => {
  if (confirm("Delete all tasks?")) {
    tasks = [];
    renderTasks();
  }
});

// Theme Toggle (Dark/Light)
toggleThemeBtn.addEventListener("click", () => {
  document.body.classList.toggle("light-mode");
});

// Add light mode styles
const style = document.createElement("style");
style.innerHTML = `
  body.light-mode {
    background: #f5f5f5;
    color: #111;
  }
  body.light-mode .app {
    background: #fff;
    color: #111;
  }
  body.light-mode li {
    background: #eee;
    color: #111;
  }
`;
document.head.appendChild(style);

// Initialize
renderTasks();
```
## OUTPUT

<img width="1915" height="1015" alt="image" src="https://github.com/user-attachments/assets/ef127709-6830-40a3-982f-3c3fac568ae2" />

<img width="1919" height="968" alt="image" src="https://github.com/user-attachments/assets/1aefa3e3-73e5-47fe-b590-387774607603" />

<img width="1916" height="1006" alt="image" src="https://github.com/user-attachments/assets/b47d84a7-8642-496c-bfbd-6677a5e2ef49" />




## RESULT
The program for creating To-do list using JavaScript is executed successfully.
