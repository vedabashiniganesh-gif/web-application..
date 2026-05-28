<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>To-Do App</title>
<style>
    body {
        font-family: Arial, sans-serif;
        background: #f4f4f4;
        display: flex;
        justify-content: center;
        margin-top: 50px;
    }

    .container {
        background: white;
        padding: 20px;
        width: 400px;
        border-radius: 10px;
        box-shadow: 0 0 10px gray;
    }

    h2 {
        text-align: center;
    }

    input, button {
        padding: 10px;
        margin: 5px 0;
        width: 100%;
        box-sizing: border-box;
    }

    ul {
        list-style: none;
        padding: 0;
    }

    li {
        background: #eee;
        padding: 10px;
        margin-top: 10px;
        border-radius: 5px;
    }

    .completed {
        text-decoration: line-through;
        color: gray;
    }

    .btn-group button {
        width: 30%;
        margin-right: 5px;
    }
</style>
</head>
<body>

<div class="container">
    <h2>To-Do App</h2>

    <input type="text" id="taskInput" placeholder="Enter task">
    <input type="datetime-local" id="taskDate">

    <button onclick="addTask()">Add Task</button>

    <ul id="taskList"></ul>
</div>

<script>
function addTask() {
    let taskText = document.getElementById("taskInput").value;
    let taskDate = document.getElementById("taskDate").value;

    if (taskText === "") {
        alert("Please enter a task!");
        return;
    }

    let li = document.createElement("li");

    li.innerHTML = `
        <span>${taskText} <br><small>${taskDate}</small></span>
        <div class="btn-group">
            <button onclick="completeTask(this)">✓</button>
            <button onclick="editTask(this)">Edit</button>
            <button onclick="deleteTask(this)">X</button>
        </div>
    `;

    document.getElementById("taskList").appendChild(li);

    document.getElementById("taskInput").value = "";
    document.getElementById("taskDate").value = "";
}

function completeTask(button) {
    let task = button.parentElement.parentElement.querySelector("span");
    task.classList.toggle("completed");
}

function editTask(button) {
    let task = button.parentElement.parentElement.querySelector("span");
    let newTask = prompt("Edit task:", task.firstChild.textContent);

    if (newTask) {
        task.firstChild.textContent = newTask + " ";
    }
}

function deleteTask(button) {
    button.parentElement.parentElement.remove();
}
</script>

</body>
</html># web-application..
