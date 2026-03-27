<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Intermediate HTML CSS JS Project</title>
  <style>
    /* RESET */
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: Arial, sans-serif;
    }

    body {
      background: #f4f4f4;
      padding: 20px;
    }

    /* GRID LAYOUT */
    .container {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 20px;
    }

    /* CARD STYLE */
    .card {
      background: #fff;
      padding: 20px;
      border-radius: 10px;
      box-shadow: 0 2px 8px rgba(0,0,0,0.1);
    }

    h2 {
      margin-bottom: 15px;
      color: teal;
    }

    /* FORM */
    form {
      display: flex;
      flex-direction: column;
    }

    input, button {
      padding: 10px;
      margin-bottom: 10px;
      border-radius: 5px;
      border: 1px solid #ccc;
    }

    button {
      background: teal;
      color: white;
      cursor: pointer;
      border: none;
    }

    button:hover {
      background: darkcyan;
    }

    .error {
      color: red;
      font-size: 14px;
    }

    /* TODO LIST */
    .todo-container {
      display: flex;
      flex-direction: column;
    }

    .todo-input {
      display: flex;
      gap: 10px;
    }

    ul {
      list-style: none;
      margin-top: 10px;
    }

    li {
      background: #e3f2f2;
      padding: 10px;
      margin-bottom: 5px;
      display: flex;
      justify-content: space-between;
      border-radius: 5px;
    }

    .delete-btn {
      background: red;
      border: none;
      color: white;
      padding: 5px 10px;
      cursor: pointer;
      border-radius: 5px;
    }

    /* RESPONSIVE */
    @media(max-width: 768px) {
      .container {
        grid-template-columns: 1fr;
      }
    }
  </style>
</head>
<body>

  <h1>Intermediate Web Project</h1>

  <div class="container">

    <!-- CONTACT FORM -->
    <div class="card">
      <h2>Contact Form</h2>
      <form id="contactForm">
        <input type="text" id="name" placeholder="Enter Name">
        <input type="email" id="email" placeholder="Enter Email">
        <button type="submit">Submit</button>
        <p id="formError" class="error"></p>
      </form>
    </div>

    <!-- TODO LIST -->
    <div class="card">
      <h2>To-Do List</h2>
      <div class="todo-container">
        <div class="todo-input">
          <input type="text" id="taskInput" placeholder="Enter task">
          <button onclick="addTask()">Add</button>
        </div>
        <ul id="taskList"></ul>
      </div>
    </div>

  </div>

  <script>
    // FORM VALIDATION
    document.getElementById("contactForm").addEventListener("submit", function(e) {
      e.preventDefault();

      let name = document.getElementById("name").value.trim();
      let email = document.getElementById("email").value.trim();
      let error = document.getElementById("formError");

      if (name === "" || email === "") {
        error.textContent = "All fields are required!";
        return;
      }

      let emailPattern = /^[^ ]+@[^ ]+\.[a-z]{2,3}$/;
      if (!email.match(emailPattern)) {
        error.textContent = "Invalid email format!";
        return;
      }

      error.style.color = "green";
      error.textContent = "Form submitted successfully!";
    });

    // TODO LIST FUNCTIONALITY
    function addTask() {
      let input = document.getElementById("taskInput");
      let task = input.value.trim();

      if (task === "") return;

      let li = document.createElement("li");
      li.textContent = task;

      let delBtn = document.createElement("button");
      delBtn.textContent = "Delete";
      delBtn.classList.add("delete-btn");

      delBtn.onclick = function() {
        li.remove();
      };

      li.appendChild(delBtn);
      document.getElementById("taskList").appendChild(li);

      input.value = "";
    }
  </script>

</body>
</html>

