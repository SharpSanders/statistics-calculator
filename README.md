# Statistics Calculator

A JavaScript-powered statistics calculator that processes a list of comma-separated numbers and computes key descriptive statistics in real time.

## Live Demo
https://sharpsanders.github.io/statistics-calculator/

<img src="/img/Screenshot-statistics-calculator.png" alt="Screenshot of the Statistics Calculator UI" />

---

## Overview

This project demonstrates data parsing, functional programming patterns, and mathematical computation using vanilla JavaScript.

Users can input a dataset and instantly calculate:

- Mean
- Median
- Mode
- Range
- Variance
- Standard Deviation

All calculations update dynamically without reloading the page.

---

## Features

- Accepts comma-separated numeric input
- Cleans and validates user data
- Handles datasets with duplicate values
- Gracefully returns no mode when appropriate
- Real-time DOM updates
- Clean, responsive dark UI

---

## Tech Stack

- **HTML5** – semantic structure and form controls  
- **CSS3** – custom dark theme styling  
- **JavaScript (ES6+)** – parsing, data processing, DOM updates  

No external libraries or frameworks used.

---

## Technical Highlights

### Input Parsing & Validation

- Splits input using regex to handle optional whitespace
- Converts values to numbers
- Filters out invalid entries (`NaN`)
- Prevents calculations on empty datasets

### Functional Programming Patterns

Uses:

- `map()` for number conversion  
- `filter()` for validation  
- `reduce()` for aggregation  
- `toSorted()` for non-mutating sorting  
- Object-based frequency counting for mode detection  

### Statistical Logic

- Median supports even/odd datasets
- Mode handles multimodal datasets
- Variance and standard deviation computed using reusable helper functions
- Separation between calculation logic and DOM rendering

---

## Project Structure

statistics-calculator/
index.html
styles.css
script.js
img/
Screenshot-statistics-calculator.png


---

## What I Practiced

- Writing reusable helper functions
- Implementing mathematical formulas in JavaScript
- Handling edge cases in user input
- Updating the DOM efficiently
- Keeping logic separate from UI concerns

---

## Potential Enhancements

- Toggle between population and sample variance
- Decimal precision formatting controls
- Visual chart representation (histogram)
- Input error messaging system

---

## Author

Built by Trevyn Sanders  
Better Endeavors LLC