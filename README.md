To-Do List App
A simple, user-friendly to-do list web application built with HTML, CSS, and JavaScript. Features include adding tasks, marking them as complete with a strike-through effect, and deleting tasks. Completed tasks automatically remove after a short delay. Stylish design with smooth transitions and rounded buttons for an enhanced user experience.







<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>To-Do List App</title>
    <style>
        body {
    font-family: Arial, sans-serif;
    background-color: #f0f0f0;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    margin: 0;
}

.container {
    background-color: #fff;
    padding: 20px;
    border-radius: 5px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    width: 300px;
}

h1 {
    text-align: center;
    color: #333;
}

form {
    display: flex;
    margin-bottom: 10px;
}

input[type="text"] {
    flex: 1;
    padding: 8px;
    font-size: 16px;
}li {
    padding: 10px;
    border-bottom: 1px solid #ddd;
    display: flex;
    justify-content: space-between; /* Align items and buttons */
    align-items: center; /* Center items and buttons */
}

button {
    padding: 8px 16px;
    background-color: #4caf50;
    color: white;
    border: none;
    cursor: pointer;
    font-size: 16px;
    border-radius: 5px; /* Rounded corners for rectangular buttons */
    transition: background-color 0.3s ease; /* Smooth transition for hover effect */
}

button:hover {
    background-color: #45a049; /* Change color on hover */
}

.strike {
    text-decoration: line-through;
    opacity: 0.5; /* Reduce opacity for completed tasks */
}

    </style>
</head>

<body>
    <div class="container">
        <h1>To-Do List</h1>
        <form id="task-form">
            <input type="text" id="task-input" placeholder="Add a new task...">
            <button type="submit">Add Task</button>
        </form>
        <ul id="task-list"></ul>
    </div>
    
    <script>// Selectors
        const form = document.getElementById('task-form');
        const taskInput = document.getElementById('task-input');
        const taskList = document.getElementById('task-list');
        
        // Event listener for form submission
        form.addEventListener('submit', function(e) {
            e.preventDefault();
            const taskText = taskInput.value.trim();
            if (taskText !== '') {
                addTask(taskText);
                taskInput.value = '';
            }
        });
        
        // Function to add a new task
        function addTask(taskText) {
            const li = document.createElement('li');
            
            // Create a span element for the task text
            const taskSpan = document.createElement('span');
            taskSpan.innerText = taskText;
            
            // Append the span to the list item
            li.appendChild(taskSpan);
            
            const deleteButton = document.createElement('button');
            deleteButton.innerText = 'Delete';
            deleteButton.className = 'delete-btn';
            deleteButton.addEventListener('click', function() {
                li.remove();
            });
            
            const completeButton = document.createElement('button');
            completeButton.innerText = 'Complete';
            completeButton.className = 'complete-btn';
            completeButton.addEventListener('click', function() {
                li.classList.toggle('completed');
                taskSpan.classList.toggle('strike'); // Toggle strike-through effect
                setTimeout(function() {
                    li.remove(); // Remove the task after a short delay
                }, 500); // Adjust the delay time as needed (500ms in this example)
            });
            
            li.appendChild(completeButton);
            li.appendChild(deleteButton);
            
            taskList.appendChild(li);
        }
        </script>
</body>
</html>
