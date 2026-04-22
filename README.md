# EYS
Estimate Your Savings Calculator

Converted Excel to HTML using JavaScript.

## 🧠 What the <script> does (big picture)

Your `<script>` is the brain of the calculator.

It:

- Takes user inputs (loan, rate, payment, etc.)
- Runs the math (amortization logic)
- Updates the table + chart
- Simulates your Elimin8 strategy (accelerated payoff)

👉 “reallocates available cash flow to reduce the principal balance more aggressively.”

## 🔍 Key Parts of the Script (explained)
### 1. 📥 Getting user input

You’ll see stuff like:

`const loan = parseFloat(document.getElementById("loanAmount").value);`

👉 This means:

- Go to the input box
- Grab the value
- Convert it into a number

### 2. 🧮 Monthly payment calculation

Usually something like:

```
  let monthlyRate = annualRate / 12;
  let payment = loan * (monthlyRate / (1 - Math.pow(1 + monthlyRate, -months)));
```

👉 This is standard mortgage math:

- Interest is calculated monthly
- Payment is fixed
- Early payments = mostly interest







