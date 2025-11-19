# Statistics Calculator

A simple JavaScript-powered statistics calculator that takes a list of **comma-separated numbers** and computes:

- Mean
- Median
- Mode
- Range
- Variance
- Standard Deviation

Built to practice array methods, functional helpers, and basic statistics formulas in vanilla JS.

---

## How It Works

1. Enter a list of numbers separated by commas, for example:

   ```text
   1, 2, 2, 3, 4, 7
Click Calculate.

The page updates and shows:

Mean

Median

Mode (or nothing if there is no mode)

Range

Variance

Standard Deviation

Each result is shown under its own short explanation of the concept.

Tech Stack
HTML – form, labels, and results area.

CSS – dark theme styling + typography.

JavaScript – parsing input, computing statistics, updating the DOM.

JavaScript Breakdown
All logic lives in script.js.

Parsing the Input
js
Copy code
const value = document.querySelector("#numbers").value;
const array = value.split(/,\s*/g);
const numbers = array.map(el => Number(el)).filter(el => !isNaN(el));
Splits on commas (optionally followed by spaces).

Converts each entry to a Number.

Filters out anything that isn’t a valid number.

You should enter at least one valid number for meaningful results.

Helper Functions
Mean

js
Copy code
const getMean = (array) =>
  array.reduce((acc, el) => acc + el, 0) / array.length;
Median

js
Copy code
const getMedian = (array) => {
  const sorted = array.toSorted((a, b) => a - b);
  return sorted.length % 2 === 0
    ? getMean([sorted[sorted.length / 2], sorted[sorted.length / 2 - 1]])
    : sorted[Math.floor(sorted.length / 2)];
};
Mode

js
Copy code
const getMode = (array) => {
  const counts = {};
  array.forEach(el => counts[el] = counts[el] ? counts[el] + 1 : 1);

  if (new Set(Object.values(counts)).size === 1) {
    return null; // no mode if all counts equal
  }

  const highest = Object.keys(counts).sort(
    (a, b) => counts[b] - counts[a]
  )[0];

  const mode = Object.keys(counts).filter(
    (el) => counts[el] === counts[highest]
  );

  return mode.join(", ");
};
Range

js
Copy code
const getRange = (array) => Math.max(...array) - Math.min(...array);
Variance

js
Copy code
const getVariance = (array) => {
  const mean = getMean(array);
  return array.reduce((acc, el) => {
    const diff = el - mean;
    return acc + diff ** 2;
  }, 0) / array.length;
};
Standard Deviation

js
Copy code
const getStandardDeviation = (array) =>
  Math.sqrt(getVariance(array));
Updating the UI
js
Copy code
const calculate = () => {
  // parse numbers...
  const mean = getMean(numbers);
  const median = getMedian(numbers);
  const mode = getMode(numbers);
  const range = getRange(numbers);
  const variance = getVariance(numbers);
  const standardDeviation = getStandardDeviation(numbers);

  document.querySelector("#mean").textContent = mean;
  document.querySelector("#median").textContent = median;
  document.querySelector("#mode").textContent = mode;
  document.querySelector("#range").textContent = range;
  document.querySelector("#variance").textContent = variance;
  document.querySelector("#standardDeviation").textContent = standardDeviation;
};
The <form> calls calculate(); return false; on submit, so the page doesn’t reload.

Project Structure
text
Copy code
statistics-calculator/
├── index.html   # Form + explanations + result placeholders
├── styles.css   # Dark theme styling and layout
└── script.js    # Parsing, stats helpers, and DOM updates
What I Practiced
Parsing and validating user input from a text field.

Using array methods (map, reduce, filter, toSorted).

Implementing basic statistics formulas in JavaScript.

Separating logic into small, reusable helper functions.

Updating the DOM with calculated values.

Future Improvements
Show validation errors if no valid numbers are entered.

Allow users to choose population vs sample variance/standard deviation.

Format results to a fixed number of decimal places.

Add charts or visualizations (e.g., histogram) for the dataset.

Author
Created by Trevyn Sanders.