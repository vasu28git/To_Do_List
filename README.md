# Ex03 To-Do List using JavaScript
## Date: 11-02-2026

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
### index.html

```
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Smart To-Do</title>
<link rel="stylesheet" href="style.css">
</head>

<body>

<div class="container">
    <h1>Smart To-Do List</h1>

    <div class="input-area">
        <input type="text" id="taskInput" placeholder="Add a task...">
        <button id="addTask">+</button>
    </div>

    <ul id="taskList"></ul>
</div>

<script src="script.js"></script>
</body>
</html>
```
### style.css

```
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    font-family: Arial;
    background: linear-gradient(135deg, #667eea, #764ba2);
    height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
}

.container {
    width: 350px;
    background: white;
    padding: 20px;
    border-radius: 12px;
    box-shadow: 0 10px 25px rgba(0,0,0,0.2);
}

h1 {
    text-align: center;
    margin-bottom: 15px;
}

.input-area {
    display: flex;
    margin-bottom: 15px;
}

.input-area input {
    flex: 1;
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 6px 0 0 6px;
}

.input-area button {
    padding: 10px 15px;
    border: none;
    background: #667eea;
    color: white;
    font-size: 18px;
    border-radius: 0 6px 6px 0;
    cursor: pointer;
}

ul {
    list-style: none;
}

li {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 10px;
    margin-top: 10px;
    background: #f5f5f5;
    border-radius: 6px;
}

.completed span {
    text-decoration: line-through;
    color: gray;
}

.actions {
    display: flex;
    gap: 5px;
}

.delete-btn {
    background: red;
    color: white;
    border: none;
    padding: 5px 8px;
    border-radius: 4px;
    cursor: pointer;
}

.check-btn {
    background: green;
    color: white;
    border: none;
    padding: 5px 8px;
    border-radius: 4px;
    cursor: pointer;
}
```
### script.js
```
document.addEventListener("DOMContentLoaded", () => {
    const input = document.getElementById("taskInput");
    const addBtn = document.getElementById("addTask");
    const list = document.getElementById("taskList");

    loadTasks();

    addBtn.addEventListener("click", () => {
        if (input.value.trim() !== "") {
            createTask(input.value);
            saveTasks();
            input.value = "";
        }
    });

    input.addEventListener("keypress", (e) => {
        if (e.key === "Enter") addBtn.click();
    });

    function createTask(text, completed = false) {
        const li = document.createElement("li");

        if (completed) li.classList.add("completed");

        li.innerHTML = `
            <span>${text}</span>
            <div class="actions">
                <button class="check-btn">✔</button>
                <button class="delete-btn">X</button>
            </div>
        `;

        li.querySelector(".check-btn").onclick = () => {
            li.classList.toggle("completed");
            saveTasks();
        };

        li.querySelector(".delete-btn").onclick = () => {
            li.remove();
            saveTasks();
        };

        list.appendChild(li);
    }

    function saveTasks() {
        const tasks = [];
        document.querySelectorAll("li").forEach(li => {
            tasks.push({
                text: li.querySelector("span").innerText,
                completed: li.classList.contains("completed")
            });
        });
        localStorage.setItem("tasks", JSON.stringify(tasks));
    }

    function loadTasks() {
        const data = JSON.parse(localStorage.getItem("tasks")) || [];
        data.forEach(task => createTask(task.text, task.completed));
    }
});
```
## OUTPUT
<img width="1555" height="869" alt="image" src="https://github.com/user-attachments/assets/30c93fb9-a797-4fec-939d-d8299ae1665a" />

<img width="1262" height="793" alt="image" src="https://github.com/user-attachments/assets/d4e91c43-7b0a-4ee9-82bd-d54c4c834bee" />

## RESULT
The program for creating To-do list using JavaScript is executed successfully.
