# Ex06 BMI Calculator
## Date:2.05.2025

## AIM
To create a BMI calculator using React Router 

## ALGORITHM
### STEP 1 State Initialization
Manage the current page (Home or Calculator) using React Router.

### STEP 2 User Input
Accept weight and height inputs from the user.

### STEP 3 BMI Calculation
Calculate the BMI based on user input.

### STEP 4 Categorization
Classify the BMI result into categories (Underweight, Normal weight, Overweight, Obesity).

### STEP 5 Navigation
Navigate between pages using React Router.

## PROGRAM
Home.js
```
import React from 'react';
import { Link } from 'react-router-dom';

function Home() {
  return (
    <div>
      <h1>Welcome to BMI Calculator</h1>
      <Link to="/calculator">Go to Calculator</Link>
    </div>
  );
}

export default Home;
```
Calculator.js
```
import React, { useState } from 'react';

function Calculator() {
  const [height, setHeight] = useState('');
  const [weight, setWeight] = useState('');
  const [bmi, setBmi] = useState(null);
  const [category, setCategory] = useState('');

  const handleSubmit = (e) => {
    e.preventDefault();
    const calculatedBmi = weight / ((height / 100) ** 2);
    setBmi(calculatedBmi);
    categorizeBmi(calculatedBmi);
  };

  const categorizeBmi = (bmi) => {
    if (bmi < 18.5) {
      setCategory('Underweight');
    } else if (bmi >= 18.5 && bmi < 24.9) {
      setCategory('Normal weight');
    } else if (bmi >= 25 && bmi < 29.9) {
      setCategory('Overweight');
    } else {
      setCategory('Obesity');
    }
  };

  return (
    <div>
      <h2>BMI Calculator</h2>
      <form onSubmit={handleSubmit}>
        <input
          type="number"
          placeholder="Height (in cm)"
          value={height}
          onChange={(e) => setHeight(e.target.value)}
        />
        <input
          type="number"
          placeholder="Weight (in kg)"
          value={weight}
          onChange={(e) => setWeight(e.target.value)}
        />
        <button type="submit">Calculate</button>
      </form>
      {bmi && (
        <div>
          <h3>Your BMI: {bmi.toFixed(2)}</h3>
          <p>Category: {category}</p>
        </div>
      )}
    </div>
  );
}

export default Calculator;
```
App.js
```
import React from 'react';
import { BrowserRouter as Router, Route, Routes } from 'react-router-dom';
import Home from './Home';
import Calculator from './Calculator';

function App() {
  return (
    <Router>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/calculator" element={<Calculator />} />
      </Routes>
    </Router>
  );
}

export default App;
```

## OUTPUT
![image](https://github.com/user-attachments/assets/0daf463f-dbd3-4491-bfa3-b2a67fe9e941)
![image](https://github.com/user-attachments/assets/e6d6fe92-2ac5-47ef-af63-e16b86fbe108)


## RESULT
The program for creating BMI Calculator using React Router is executed successfully.
