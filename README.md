# Renton Technical College CSI-244
<br />    

<div align="center">  
    <img src="logo.jpg" alt="Logo">
    <h3 align="center">Guided Activity 3</h3>
</div>

This repository is a part of CSI-244 at Renton Technical College.

## Guided Activity Part 3 Bootstrap and Formdata
1. Clone this repository to your machine.
2. Open the repository in Visual Studio code and follow the instructions below.

#### Step 1: Project Setup

##### Creating Your Project
- **Action:** Start a new Node.js project and install Express.
  - Open your terminal or command prompt.
  - Run the following command to initialize your project:
    ```powershell
    npm init
    ```
  - Follow the prompts to create your project, setting `server.js` as the entry point.

##### Installing Express
- **Action:** Install Express.
  - In the terminal, run:
    ```powershell
    npm install express
    ```

##### Installing nodemon
- **Action:** Install Nodemon, but only as a development dependency.
  - In the terminal, run:
    ```powershell
    npm install nodemon --save-dev
    ```

##### Verifying package.json
- You should now have a package.json created in the current folder. Edit the "scripts" collection to match the following.  
    ```json
  "scripts": {
    "start": "node server.js",
    "dev": "nodemon server.js"
      },

    ```
- You do not need to change anything else in package.json except for the "scripts" collection.

##### Creating the Server File
- **Action:** Create the main server file.
  - In your project directory, create a file named `server.js`.

#### Step 2: Setting Up the Express Server

##### Writing the Server Code
- **Setting Up Express:**
  - Open `server.js` in a text editor.
  - Write the following code to import necessary modules and set up the Express app:
    ```javascript
    const express = require("express");
    const path = require("path");
    const fs = require("fs");
    const app = express();
    ```

- **Serving HTML Pages:**
  - Define routes to serve your `index.html` and `support.html` pages using `res.sendFile`. For example:
    ```javascript
    // Serve index.html on the root path
    app.get("/", (req, res) => {
      res.sendFile(path.join(__dirname, "public", "index.html"));
    });

    // Serve support.html on the '/support' path
    app.get("/support", (req, res) => {
      res.sendFile(path.join(__dirname, "public", "support.html"));
    });
    ```

- **Starting the Server:**
  - Make the server listen on a port (e.g., 3000) for incoming connections:
    ```javascript
    const PORT = 3000;
    app.listen(PORT, () => {
      console.log(`Server running on port ${PORT}`);
    });
    ```

#### Step 3: Creating HTML Pages

#### Creating the `public` Directory and `index.html` File

- **Creating the `public` Directory:**
   - The `public` directory will hold all your static files like HTML, CSS, and JavaScript.
   - In your project's root directory, create the `public` directory:
     ```bash
     mkdir public
     ```
   - This command creates a new directory named `public`.

- **Navigate to the `public` Directory:**
   - Change into the `public` directory:
     ```bash
     cd public
     ```

- **Creating `index.html`:**
   - Within the `public` directory, create a file named `index.html`.
   - You can use a text editor or the following terminal command:
     ```bash
     new-item index.html
     ```

#### Adding Content to `index.html`

- **Setting Up the HTML Structure:**
   - Start with the basic HTML5 document structure. Include two `DOCTYPE` declarations for HTML5, the opening `<html>` tag with language attribute, `<head>`, and `<body>` sections.
   - In the `<head>` section, add a title for your page and include the Bootstrap CSS link. This link connects your HTML file to the Bootstrap framework, enabling you to use its pre-designed components and styles.
     ```html
     <!DOCTYPE html>
     <!DOCTYPE html>
     <html lang="en">
       <head>
         <meta charset="UTF-8" />
         <meta name="viewport" content="width=device-width, initial-scale=1.0" />
         <title>Bootstrap Tutorial</title>
         <!-- Link Bootstrap CSS -->
         <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css" rel="stylesheet" />
       </head>
       <body>
       ...
       </body>
     </html>
     ```

- **Bootstrap Navbar:**
   - Inside the `<body>`, start with a Bootstrap navbar. This navbar includes a brand label, a collapsible hamburger menu for smaller screens, and navigation links.
   - The `navbar-expand-sm` class makes the navbar collapsible on screens smaller than the 'sm' breakpoint. The `navbar-light` and `bg-light` classes style it with a light color theme.
    ```html
        <!-- Bootstrap Navbar -->
    <nav class="navbar navbar-expand-sm navbar-light bg-light">
      <a class="navbar-brand" href="#">Navbar</a>
      <!-- This is the button that only appears when the on a small screen  -->
      <button
        class="navbar-toggler"
        type="button"
        data-toggle="collapse"
        data-target="#navbarNav"
        aria-controls="navbarNav"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>
      <!-- These links will hide on a small screen but be present on a large one -->
      <div class="collapse navbar-collapse" id="navbarNav">
        <ul class="navbar-nav">
          <li class="nav-item active">
            <a class="nav-link" href="#">Home</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#">About</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#">Contact</a>
          </li>
        </ul>
      </div>
    </nav>
    ```
- **Bootstrap Grid System:**
   - Utilize Bootstrap's grid system to structure your page content. Start with a `container` class, which centers your content and adds margins.
   - Inside the container, use `row` to create a horizontal grouping of columns.
   - Then, add `col-12`, `col-sm-6`, and `col-md-4` classes to create responsive columns. The numbers indicate how many grid columns the element should span. For instance, `col-md-4` takes up 4 out of 12 columns on medium-sized screens and larger.
    ```html
            <!-- To use grid you create a div with a class of container -->
    <div class="container">
      <!-- Next we create a row -->
      <div class="row">
        <!-- Place elements in the row and specify how many columns they should occupy -->
        <!-- There are 12 columns available -->
        <div class="col-12">
          <h1>Bootstrap Tutorial</h1>
          <p>This is a hands-on tutorial for Bootstrap.</p>
        </div>
      </div>
      <div class="row bg-light">
        <div class="col-sm-6">
          <h2>Bootstrap Grid System</h2>
          <p>
            Bootstrap's grid system allows up to 12 columns across the page. If
            you take up 6 columns, you have 6 left. If you take up 3 columns,
            you have 9 left.
          </p>
        </div>
        <div class="col-sm-6">
          <h2>Grid helps position elements</h2>
          <p>
            Here we have elements that take up 6 columns each next to each other
            on a larger screen. If the screen is smaller, they stack on top of
            each other. The sm controls when the elements will stack.
          </p>
        </div>
      </div>
      <!-- since md was used here these will stack at a larger size than sm -->
      <div class="row">
        <div class="col-md-4">
          <h2>Column 1</h2>
          <p>This is the content of column 1.</p>
        </div>
        <div class="col-md-4">
          <h2>Column 2</h2>
          <p>This is the content of column 2.</p>
        </div>
        <div class="col-md-4">
          <h2>Column 3</h2>
          <p>This is the content of column 3.</p>
        </div>
      </div>
    ```

- **Bootstrap Components - Buttons and Alert:**
   - Add different styled buttons using `btn` classes like `btn-primary`, `btn-secondary`, and `btn-outline-primary`.
   - Include an alert box using the `alert` and `alert-success` classes for a success message.
    ```html
              <!-- Bootstrap Buttons -->
      <button class="btn btn-primary">Primary Button</button>
      <button class="btn btn-secondary">Secondary Button</button>
      <button class="btn btn-outline-primary">Outline Success</button>

      <!-- Bootstrap Alert -->
      <div class="alert alert-success" role="alert">
        This is a success alert.
      </div>
    </div>
    ```
- **Linking Bootstrap JavaScript:**
   - At the end of your `<body>`, include the Bootstrap JavaScript bundle. This script is necessary for interactive components like the collapsible navbar to function properly.
     ```html
     <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/js/bootstrap.bundle.min.js"></script>
     ```

##### Creating `support.html`

- **Creating `support.html`:**
   - Inside the `public` directory, you'll create a file named `support.html`.
   - Use a text editor or the command line to create this file:
     ```bash
     new-item support.html
     ```

#### Adding Content to `support.html`

- **Basic HTML Structure:**
   - Begin with the standard HTML5 structure. Include `DOCTYPE`, the opening `<html>` tag with language attribute, `<head>`, and `<body>` sections.
   - In the `<head>` section, add a title for your page and link Bootstrap’s CSS for styling.
     ```html
     <!DOCTYPE html>
     <html lang="en">
       <head>
         <meta charset="UTF-8" />
         <meta name="viewport" content="width=device-width, initial-scale=1.0" />
         <title>Support Form</title>
         <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css" rel="stylesheet" />
       </head>
       <body>
       <!-- code for next step goes here -->
       </body>
     </html>
     ```

- **Bootstrap Container:**
   - Use a `container` class to center your form on the page. Bootstrap's `container` class provides margins and proper alignment.
     ```html
     <div class="container">
       <h2>Support Form</h2>
      <!-- code for the nex step goes here -->
     </div>
     ```

- **Creating the Form:**
   - The `form` tag defines how data will be sent. In this case, it’s using the `GET` method to `/submitform`.
   - Comments in the HTML explain that the data is sent via URL (not secure for sensitive data), and the `name` attribute in form elements corresponds to the data keys.
     ```html
     <form action="/submitform" method="get">
        <div class="form-group">
          <label for="name">Name</label>
          <input
            type="text"
            class="form-control"
            id="name"
            name="name"
            placeholder="Enter your name"
          />
        </div>
        <div class="form-group">
          <label for="email">Email</label>
          <input
            type="email"
            class="form-control"
            id="email"
            name="email"
            placeholder="Enter your email"
          />
        </div>
        <div class="form-group">
          <label for="message">Message</label>
          <textarea
            class="form-control"
            id="message"
            rows="3"
            placeholder="Enter your message"
            name="message"
          ></textarea>
        </div>
        <div class="form-group">
          <label for="date">Date</label>
          <input
            type="date"
            class="form-control"
            id="date"
            name="date"
            placeholder="Select a date"
          />
        </div>
        <div class="form-group">
          <label for="urgency">Urgency</label>
          <select class="form-control" id="urgency" name="urgency">
            <option value="low">Low</option>
            <option value="medium">Medium</option>
            <option value="high">High</option>
          </select>
        </div>
        <button type="submit" class="btn btn-primary">Submit</button>
      </form>
     ```

- **Form Input Elements:**
   - Notice the use Bootstrap’s `form-group` and `form-control` classes to style your input fields.
   - Each input field (like `text`, `email`, `textarea`, `date`, and `select`) is wrapped in a `div` with the class `form-group` for proper spacing and layout.
   - The `class="form-control"` on each input element gives a consistent and attractive styling.
   - The `name` attribute will determine the name of the property where the data will be sent. 

- **Submit Button:**
   - A submit button is included at the end of the form. The `btn` and `btn-primary` classes style it as a primary Bootstrap button.

#### Step 4: Handling Form Submissions

#### Setting Up Route for Form Submission
- **Action:** Create a route to process form submissions.
  - In `server.js`, add a route for form submission. Use the HTTP `GET` method to capture data from the query string.
    ```javascript
    app.get("/submitform", (req, res) => {
      // Code to process form data
      console.log(req.query);
    });
    ```
  
- **Action:** Get the data from the form and save it in a file.
  - Use the `fs` (File System) module to write form data to a file.
  - Implement error handling to manage file write operations.
  - Send a response back to the user upon successful data handling.

  Here is the expanded code for the `/submitform` endpoint:
  ```javascript
  const fs = require('fs');

  app.get("/submitform", (req, res) => {
    // Notice that the data from the form is in the request query object.
    // The information is in the form of key-value pairs with the key
    // being the name of the input field and the value being the value of the input field.
    console.log(req.query);

    // Let's save these values to a file and then send a response to the user.
    fs.appendFile("formdata.txt", JSON.stringify(req.query) + '\n', (err) => {
      if (err) {
        console.error("Error writing to file", err);
        res.status(500).send("An error occurred while processing your form.");
        return;
      }
      console.log("The data was appended to file!");

      // Send a response back to the user.
      res.send("Thank you for submitting the form");
    });
  });
  ```

#### Understanding the Code:
- `fs.appendFile`: This method is used to append the form data to a file named `formdata.txt`. If the file doesn't exist, it will be created.
- `JSON.stringify(req.query)`: Converts the query object into a string format for easy storage.
- `res.send`: Sends a response back to the client.


#### Step 5: Testing the Application

- **Run Your Server:**
   - Before you can run your server make sure that you are in the same director as server.cs
            ```powershell
                cd ..
            ```
   - Use the command `npm run dev` to start your server.

2. **Test the Pages and Form:**
   - Visit `http://localhost:3000` in a browser to view the `index.html` page.
   - Go to `http://localhost:3000/support` to access the support form.
   - Fill out the form with information and click submit.
   - A `formdata.txt` file should have been created containing the information from the form.

3. **Debugging:**
   - Troubleshoot any issues by checking the server console and ensuring all routes are correctly set up.


Create a new commit with the message Guided Activity 3 Complete and push the changes to GitHub


If you have any questions about this assignment please reach out to myself or our TA for this course.
