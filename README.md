# EduPortal - Student Admission & Course Selection

This project is a simple, front-end web application that simulates a student admission and course selection portal for a fictional institution. It demonstrates the use of HTML, CSS, and JavaScript to create a multi-page user flow, handle form submissions, and persist data locally using `localStorage`.

The application is structured using an HTML `<frameset>` to create a static navigation header and a dynamic main content area.

## Features

*   **Framed Layout:** Uses a top navigation frame and a main content frame for a persistent header.
*   **Student Admission Form:** A detailed form for students to enter personal and academic information.
*   **Client-Side Data Storage:** Utilizes the browser's `localStorage` to save form data and course selections, making it persistent across pages.
*   **Dynamic Course Catalog:** Course options are dynamically generated and displayed based on the user's stream selection (e.g., IT vs. Core Engineering).
*   **Final Summary Page:** Consolidates and displays all the user-entered information and their chosen course for a final review.
*   **Simple & Clean UI:** Styled with CSS for a clear and user-friendly interface.

## Technologies Used

*   HTML5
*   CSS3
*   JavaScript (ES6)

## How to Run

1.  Download all the project files into a single folder.
2.  Make sure you have an image named `images.png` in the same folder for the logo, or update the path in `navigation.html`.
3.  Open the `index.html` file in a modern web browser.

## A Note on `<frameset>`

This project uses the `<frameset>` tag for layout, primarily for educational and demonstration purposes. **The `<frameset>` tag is deprecated in HTML5** and is not recommended for modern web development. For new projects, consider using modern layout techniques like:

*   **CSS Flexbox or Grid** for layout.
*   **JavaScript (e.g., Fetch API or AJAX)** to dynamically load content into `<div>` elements.
*   **Server-Side Includes (SSI)** or a templating engine.

## Project Files & Code

<details>
<summary><code>index.html</code> (The main entry point with frameset)</summary>

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <title>EduPortal - Home</title>
</head>
<!--
  Note: The <frameset> tag is deprecated in HTML5.
  This implementation is for educational purposes to fulfill the request.
  For modern web development, consider using CSS for layout (like Flexbox or Grid)
  and JavaScript (e.g., Fetch API) to load content dynamically into a div,
  or use server-side includes.
-->
<frameset rows="160,*" border="0">
  <frame src="navigation.html" name="nav_frame" scrolling="no" noresize>
  <frame src="welcome.html" name="main_frame">
</frameset>
<noframes>
  <body>Your browser does not support frames.</body>
</noframes>
</html>
```

</details>

<details>
<summary><code>navigation.html</code> (Top navigation bar and header)</summary>

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Navigation</title>
  <style>
    body { font-family: Arial, sans-serif; margin: 0; background: #f4f4f4; overflow: hidden; }
    header {
      background-color: #5b2c6f;
      color: white;
      padding: 1rem 1.5rem;
      display: flex;
      align-items: center;
      gap: 1.5rem;
    }
    .logo {
      height: 60px;
      mix-blend-mode: hard-light;
      border-radius: 52%;
    }
    .header-text h1, .header-text p {
      margin: 0;
    }
    nav { background-color: #7d3c98; display: flex; justify-content: center; gap: 2rem; padding: 1rem; }
    nav a {
      color: white; text-decoration: none; font-weight: bold; font-size: 1rem;
    }
    nav a:hover { text-decoration: underline; }
  </style>
</head>
<body>

  <header>
    <!-- Make sure you have an image named 'images.png' in the same folder, or update the src path -->
    <img src="images.png" alt="Institute Logo" class="logo">
    <div class="header-text">
      <h1>Vignan Institute of Technology and Science </h1>
      <p>Welcome to vignanPortal - Course Selection System</p>
    </div>
  </header>

  <nav>
    <a href="login.html" target="main_frame">Login</a>
    <a href="cart.html" target="main_frame">Cart</a>
    <a href="final.html" target="main_frame">Final Summary</a>
  </nav>

</body>
</html>
```

</details>

<details>
<summary><code>welcome.html</code> (Initial landing page content)</summary>

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Welcome</title>
  <style>
    body { font-family: Arial, sans-serif; margin: 0; background: #f4f4f4; }
    main { text-align: center; padding: 3rem 1rem; }
    h2 { color: #5b2c6f; }
  </style>
</head>
<body>
  <main>
    <h2>Start Your Academic Journey</h2>
    <p>Please begin by logging in and submitting your admission details.</p>
  </main>
</body>
</html>
```

</details>

<details>
<summary><code>login.html</code> (Student admission form)</summary>

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>EduPortal - Admission Form</title>
  <style>
    body {
      font-family: Arial; background: #ecf0f1;
      display: flex; justify-content: center; align-items: center;
      height: 100vh; margin: 0;
    }
    .form-container {
      background: white; padding: 2rem; border-radius: 10px;
      box-shadow: 0 2px 10px rgba(0,0,0,0.1); width: 400px;
    }
    h2 { color: #5b2c6f; text-align: center; }
    label {
      display: block; margin-top: 1rem; margin-bottom: 0.3rem;
      font-weight: bold; color: #5b2c6f;
    }
    input, textarea {
      width: 100%; padding: 0.5rem;
      border: 1px solid #ccc; border-radius: 5px;
    }
    input[type="text"], input[type="email"], input[type="tel"] {
      appearance: none; -moz-appearance: textfield;
    }
    input::-webkit-outer-spin-button,
    input::-webkit-inner-spin-button {
      -webkit-appearance: none; margin: 0;
    }
    button {
      width: 100%; padding: 0.6rem; margin-top: 1rem;
      background: #8e44ad; color: white;
      border: none; border-radius: 5px;
      font-weight: bold; cursor: pointer;
    }
    button:hover { background: #7d3c98; }
    .message {
      margin-top: 1rem; color: #5b2c6f; font-weight: bold; text-align: center; display: none;
    }
  </style>
  <script>
    function handleSubmit(event) {
      event.preventDefault();
      localStorage.setItem("studentName", document.getElementById("name").value);
      localStorage.setItem("studentEmail", document.getElementById("email").value);
      localStorage.setItem("studentPhone", document.getElementById("phone").value);
      localStorage.setItem("interPercent", document.getElementById("inter").value);
      localStorage.setItem("jeePercent", document.getElementById("jee").value);
      localStorage.setItem("studentInfo", document.getElementById("info").value);
      localStorage.setItem("studentExpectation", document.getElementById("expect").value);

      document.getElementById("message").style.display = "block";

      setTimeout(() => {
        // When using frames, we need to target the parent to change the 'main_frame' content
        if (window.parent && window.parent.main_frame) {
          window.parent.main_frame.location.href = "cart.html";
        } else { // Fallback for opening the page directly
          window.location.href = "cart.html";
        }
      }, 2000);
    }
  </script>
</head>
<body>

  <div class="form-container">
    <h2>Student Admission Form</h2>
    <form onsubmit="handleSubmit(event)">
      <label for="name">Full Name</label>
      <input type="text" id="name" required />

      <label for="email">Gmail ID</label>
      <input type="email" id="email" required />

      <label for="phone">Phone Number</label>
      <input type="tel" id="phone" required />

      <label for="inter">Intermediate Percentage</label>
      <input type="text" id="inter" inputmode="decimal" required />

      <label for="jee">JEE Mains Percentage</label>
      <input type="text" id="jee" inputmode="decimal" required />

      <label for="info">Achievements or Interests (e.g. Dance, Coding, etc.)</label>
      <textarea id="info" rows="3" required></textarea>

      <label for="expect">What are you expecting from our institution?</label>
      <textarea id="expect" rows="3" required></textarea>

      <button type="submit">Submit</button>
    </form>
    <div class="message" id="message">✅ Details submitted! Redirecting to course selection...</div>
  </div>

</body>
</html>
```

</details>

<details>
<summary><code>cart.html</code> (Course/Branch selection page)</summary>

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>EduPortal - Choose Your Stream</title>
  <style>
    body { font-family: Arial, sans-serif; margin: 0; background: #f4f4f4; }
    header {
      background-color: #5b2c6f; color: white; text-align: center;
      padding: 1.5rem;
    }
    footer{
      background-color: #5b2c6f; color: white; text-align: center;
      padding: 1.5rem;
      position: absolute;
      bottom: 0;
      width: 97%;
    }
    main { padding: 2rem; max-width: 1000px; margin: auto; }
    h2, h3 { color: #5b2c6f; }
    .stream-selection {
      display: flex; justify-content: center; gap: 2rem; margin-bottom: 2rem;
    }
    .stream-selection button {
      padding: 1rem 2rem; font-size: 1rem; font-weight: bold;
      background: #8e44ad; color: white; border: none; border-radius: 6px;
      cursor: pointer;
    }
    .stream-selection button:hover { background: #7d3c98; }
    .branch-card {
      background: white; padding: 1rem; border-radius: 8px; box-shadow: 0 2px 6px rgba(0,0,0,0.1);
      margin-bottom: 1.5rem;
    }
    .branch-card h4 { margin: 0.5rem 0; }
    .branch-card ul { padding-left: 1.5rem; }
    .branch-card button {
      margin-top: 1rem; padding: 0.5rem 1rem; background: #8e44ad;
      color: white; border: none; border-radius: 4px; font-weight: bold; cursor: pointer;
    }
    .branch-card button:hover { background: #7d3c98; }
  </style>
  <script>
    const branches = {
      Tech: [
        {
          name: "Computer Science & Engineering (CSE)",
          duration: "4 Years",
          fee: "INR 3.2 Lakhs",
          highlights: ["Strong programming foundation", "Industry-aligned curriculum", "Internship & placement support"],
          outcome: "Software Developer, AI/ML Engineer, Backend Engineer"
        },
        {
          name: "Artificial Intelligence & Machine Learning (AIML)",
          duration: "4 Years",
          fee: "INR 3.3 Lakhs",
          highlights: ["Neural networks & AI labs", "Project-based learning", "Modern tools & platforms"],
          outcome: "AI Developer, ML Engineer, Data Scientist"
        },
        {
          name: "CSE with Data Science",
          duration: "4 Years",
          fee: "INR 3.4 Lakhs",
          highlights: ["Data handling & analysis", "Big Data tools", "Python, R & SQL mastery"],
          outcome: "Data Analyst, Business Intelligence Analyst"
        },
        {
          name: "Information Technology (IT)",
          duration: "4 Years",
          fee: "INR 3.0 Lakhs",
          highlights: ["Web & App development", "IT Security basics", "Database & Cloud training"],
          outcome: "Web Developer, IT Consultant, DevOps Engineer"
        }
      ],
      Core: [
        {
          name: "Electronics & Communication Engineering (ECE)",
          duration: "4 Years",
          fee: "INR 3.1 Lakhs",
          highlights: ["Digital Systems & VLSI", "Robotics & IoT Labs", "Research-oriented curriculum"],
          outcome: "Embedded Engineer, Circuit Designer, IoT Specialist"
        },
        {
          name: "Electrical & Electronics Engineering (EEE)",
          duration: "4 Years",
          fee: "INR 3.0 Lakhs",
          highlights: ["Power systems & drives", "Control & Automation", "Renewable energy modules"],
          outcome: "Electrical Engineer, Control Engineer"
        },
        {
          name: "Mechanical Engineering",
          duration: "4 Years",
          fee: "INR 3.2 Lakhs",
          highlights: ["Thermodynamics & Machines", "CAD/CAM/CAE", "Industrial automation"],
          outcome: "Mechanical Design Engineer, Thermal Analyst"
        },
        {
          name: "Civil Engineering",
          duration: "4 Years",
          fee: "INR 2.8 Lakhs",
          highlights: ["Structural Design & Surveying", "AutoCAD & STAADPro training", "Site project internships"],
          outcome: "Site Engineer, Structural Analyst"
        }
      ]
    };

    function displayBranches(streamType) {
      const container = document.getElementById("branches");
      container.innerHTML = "";
      branches[streamType].forEach(branch => {
        const div = document.createElement("div");
        div.className = "branch-card";
        div.innerHTML = `
          <h3>${branch.name}</h3>
          <p><strong>Duration:</strong> ${branch.duration}</p>
          <p><strong>Fee:</strong> ${branch.fee}</p>
          <p><strong>Highlights:</strong></p>
          <ul>${branch.highlights.map(h => `<li>${h}</li>`).join('')}</ul>
          <p><strong>After Completion:</strong> ${branch.outcome}</p>
          <button onclick='selectBranch(${JSON.stringify(branch)})'>Select This Branch</button>
        `;
        container.appendChild(div);
      });
    }

    function selectBranch(branch) {
      localStorage.setItem("selectedBranch", JSON.stringify(branch));
      // When using frames, we need to target the parent to change the 'main_frame' content
      if (window.parent && window.parent.main_frame) {
        window.parent.main_frame.location.href = "final.html";
      } else { // Fallback for opening the page directly
        window.location.href = "final.html";
      }
    }
  </script>
</head>
<body>
  <header>
    <h1>Choose Your Program Stream</h1>
    <p>Select a path that aligns with your interest and career goals</p>
  </header>

  <main>
    <div class="stream-selection">
      <button onclick="displayBranches('Tech')">IT & Computer Streams</button>
      <button onclick="displayBranches('Core')">Core Engineering Streams</button>
    </div>
    <div id="branches"></div>
  </main>

  <footer>
    <p>&copy; 2025 EduPortal. All rights reserved.</p>
  </footer>
</body>
</html>
```

</details>

<details>
<summary><code>final.html</code> (Final summary page)</summary>

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>EduPortal - Final Summary</title>
  <style>
    body {
      font-family: Arial, sans-serif; margin: 0; background: #f4f4f4;
      /* Add padding to prevent content from being hidden by the fixed footer */
      padding-bottom: 5rem;
    }
    header {
      background-color: #5b2c6f; color: white;
      text-align: center; padding: 1.5rem;
    }
    footer {
      background-color: #5b2c6f; color: white;
      text-align: center; padding: 1.5rem;
      position: fixed; bottom: 0; width: 100%;
      box-sizing: border-box;
    }
    main {
      padding: 2rem; max-width: 900px; margin: auto;
    }
    h2 { color: #5b2c6f; }
    .section {
      background: white; padding: 1.5rem; border-radius: 8px;
      box-shadow: 0 2px 6px rgba(0,0,0,0.1); margin-bottom: 2rem;
    }
    p { margin: 0.5rem 0; }
    ul { padding-left: 1.5rem; }
  </style>
  <script>
    function loadSummary() {
      document.getElementById("name").textContent = localStorage.getItem("studentName") || '-';
      document.getElementById("email").textContent = localStorage.getItem("studentEmail") || '-';
      document.getElementById("phone").textContent = localStorage.getItem("studentPhone") || '-';
      document.getElementById("inter").textContent = localStorage.getItem("interPercent") || '-';
      document.getElementById("jee").textContent = localStorage.getItem("jeePercent") || '-';
      document.getElementById("info").textContent = localStorage.getItem("studentInfo") || '-';
      document.getElementById("expect").textContent = localStorage.getItem("studentExpectation") || '-';

      const branch = JSON.parse(localStorage.getItem("selectedBranch"));
      if (branch) {
        document.getElementById("branchName").textContent = branch.name;
        document.getElementById("branchDuration").textContent = branch.duration;
        document.getElementById("branchFee").textContent = branch.fee;
        document.getElementById("branchOutcome").textContent = branch.outcome;
        document.getElementById("branchHighlights").innerHTML = branch.highlights.map(h => `<li>${h}</li>`).join('');
      } else {
        document.getElementById("branchDetails").innerHTML = '<p>No branch selected.</p>';
      }
    }

    window.onload = loadSummary;
  </script>
</head>
<body>
  <header>
    <h1>Final Submission Summary</h1>
    <p>Review all details before final admission submission</p>
  </header>

  <main>
    <div class="section">
      <h2>Student Information</h2>
      <p><strong>Name:</strong> <span id="name"></span></p>
      <p><strong>Email:</strong> <span id="email"></span></p>
      <p><strong>Phone Number:</strong> <span id="phone"></span></p>
      <p><strong>Intermediate Percentage:</strong> <span id="inter"></span></p>
      <p><strong>JEE Mains Percentage:</strong> <span id="jee"></span></p>
      <p><strong>Achievements / Interests:</strong> <span id="info"></span></p>
      <p><strong>Expectations from Institution:</strong> <span id="expect"></span></p>
    </div>

    <div class="section" id="branchDetails">
      <h2>Selected Branch Details</h2>
      <p><strong>Branch:</strong> <span id="branchName"></span></p>
      <p><strong>Duration:</strong> <span id="branchDuration"></span></p>
      <p><strong>Fee:</strong> <span id="branchFee"></span></p>
      <p><strong>Highlights:</strong></p>
      <ul id="branchHighlights"></ul>
      <p><strong>After Completion:</strong> <span id="branchOutcome"></span></p>
    </div>
  </main>

  <footer>
    <p>&copy; 2025 EduPortal. All rights reserved.</p>
  </footer>
</body>
</html>
```

</details>

