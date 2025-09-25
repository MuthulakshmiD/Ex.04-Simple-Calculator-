# Ex04 Simple Calculator - React Project
## Date:

## AIM
To  develop a Simple Calculator using React.js with clean and responsive design, ensuring a smooth user experience across different screen sizes.

## ALGORITHM
### STEP 1
Create a React App.

### STEP 2
Open a terminal and run:
  <ul><li>npx create-react-app simple-calculator</li>
  <li>cd simple-calculator</li>
  <li>npm start</li></ul>

### STEP 3
Inside the src/ folder, create a new file Calculator.js and define the basic structure.

### STEP 4
Plan the UI: Display screen, number buttons (0-9), operators (+, -, *, /), clear (C), and equal (=).

### STEP 5
Create a new file Calculator.css in src/ and add the styling.

### STEP 6
Open src/App.js and modify it.

### STEP 7
Start the development server.
  npm start

### STEP 8
Open http://localhost:3000/ in the browser.

### STEP 9
Test the calculator by entering numbers and operations.

### STEP 10
Fix styling issues and refine content placement.

### STEP 11
Deploy the website.

### STEP 12
Upload to GitHub Pages for free hosting.

## PROGRAM
App.jsx
```
import React, { useState } from "react";
import "./App.css";

function App() {
  const [expression, setExpression] = useState("");
  const [result, setResult] = useState("");

  const handleClick = (value) => {
    if (value === "C") {
      setExpression("");
      setResult("");
    } else if (value === "⌫") {
      setExpression((prev) => prev.slice(0, -1));
    } else if (value === "=") {
      try {
        // Replace √ with Math.sqrt(), ^ with **
        let exp = expression
          .replace(/√(\d+(\.\d+)?)/g, "Math.sqrt($1)") 
          .replace(/√\(/g, "Math.sqrt(")               
          .replace(/\^/g, "**");                      

        const res = new Function("return " + exp)();
        setResult(res);
      } catch {
        setResult("Error");
      }
    } else {
      setExpression((prev) => prev + value);
    }
  };

  const buttons = [
    "7", "8", "9", "/",
    "4", "5", "6", "*",
    "1", "2", "3", "-",
    "0", ".", "√", "+",
    "C", "^", "=", "⌫"
  ];

  return (
    <div className="calculator-wrapper">
      <div className="calculator">
        {/* Calculator Name */}
        <h2 className="calc-name">React Calculator</h2>

        {/* Display */}
        <div className="display">
          <div>{expression || "0"}</div>
          <div className="result">{result !== "" ? "= " + result : ""}</div>
        </div>

        {/* Buttons */}
        <div className="buttons">
          {buttons.map((btn) => (
            <button key={btn} onClick={() => handleClick(btn)}>
              {btn}
            </button>
          ))}
        </div>

        {/* Footer */}
        <footer className="footer">
          <p>Developed by: <strong>Muthulakshmi D</strong></p>
          <p>Register No: <strong>212223040122</strong></p>
        </footer>
      </div>
    </div>
  );
}

export default App;

```
App.css
```
/* Full-screen centering */
.calculator-wrapper {
  width: 100vw;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  background: linear-gradient(135deg, #b9e9e9, #f2b5e1);
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  overflow: hidden;
}

/* Watermark background */
body::before {
  content: "React Calculator React Calculator React Calculator ";
  position: fixed;
  top: -50%;
  left: -50%;
  width: 200%;
  height: 200%;
  font-size: 3rem;
  font-weight: bold;
  color: rgba(255, 255, 255, 0.05);
  transform: rotate(-25deg);
  white-space: pre-wrap;
  z-index: 0;
  pointer-events: none;
}

/* Calculator container */
.calculator {
  background: rgba(255, 255, 255, 0.15);
  backdrop-filter: blur(12px);
  padding: 25px;
  border-radius: 20px;
  box-shadow: 0 8px 25px rgba(0, 0, 0, 0.3);
  width: 350px;
  text-align: center;
  z-index: 1;
}

/* Heading */
.calc-name {
  font-size: 1.8rem;
  font-weight: bold;
  color: #3e3a3d;
  margin-bottom: 15px;
}

/* Display */
.display {
  background: rgb(24, 22, 22);
  color: lavender;
  font-size: 1.6rem;
  font-weight: bold;
  text-align: right;
  padding: 15px;
  border-radius: 10px;
  margin-bottom: 15px;
  overflow-x: auto;
  box-shadow: inset 0 0 10px rgba(202, 187, 187, 0.4);
}

.result {
  color: lavender;
  font-size: 1.3rem;
  font-weight: bold;
  margin-top: 5px;
}

/* Buttons grid */
.buttons {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 12px;
}

/* Buttons */
button {
  font-size: 1.2rem;
  padding: 15px;
  border: none;
  border-radius: 12px;
  background: #ffffff;
  color: #333;
  font-weight: bold;
  cursor: pointer;
  transition: transform 0.15s, background 0.3s;
  box-shadow: 0 4px 10px rgba(0,0,0,0.2);
}

button:hover {
  background: #f2b5e1;
  color: #111;
  transform: translateY(-2px);
}

button:active {
  background: #f2b5e1;
  color: #f2b5e1;
  transform: scale(0.95);
}

/* Footer */
.footer {
  margin-top: 20px;
  text-align: center;
  font-size: 14px;
  color: #342d2d;
}
```

## OUTPUT
<img width="1919" height="929" alt="image" src="https://github.com/user-attachments/assets/c95952b0-6948-4c63-b335-1ed63ecdda69" />


## RESULT
The program for developing a simple calculator in React.js is executed successfully.
