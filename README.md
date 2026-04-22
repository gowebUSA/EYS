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

```
  const loan = parseFloat(document.getElementById("loanAmount").value);
```

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

### 3. 🔁 Amortization loop (this is the core)

This part runs month by month:

```
  for (let i = 1; i <= months; i++) {
      let interest = balance * monthlyRate;
      let principal = payment - interest;
      balance -= principal;
  }
```

👉 What it’s doing:

- Calculates interest for the month
- Applies the rest to principal
- Reduces the balance
- Repeats

### 4. ⚡ Elimin8 logic (the secret sauce)

This is where the strategy kicks in:

```
  if (extraPayment > 0) {
      principal += extraPayment;
      balance -= extraPayment;
  }
```

👉 Translation:

- Inject extra money (cash flow / HELOC)
- Kill principal faster
- Reduce future interest

This is exactly the concept:
👉 principal-first acceleration instead of interest-heavy schedule

### 5. 📊 Updating the table

```
  tableHTML += `
  <tr>
    <td>${month}</td>
    <td>${interest}</td>
    <td>${principal}</td>
    <td>${balance}</td>
  </tr>
  `;
```

👉 This builds the amortization table dynamically.

### 6. 📈 Chart update

If you’re using Chart.js:

```
  chart.data.datasets[0].data = balances;
  chart.update();
```

👉 This redraws the graph when values change.

### 💡 Why this script is powerful (Elimin8 angle)

The script is not just a calculator.

It demonstrates:

- Why people stay in debt (interest front-loaded)
- How cash flow beats savings accounts
- How injecting principal flips the system

👉 That’s the whole message:

> “Money saved is money earned”

🔑 Simple way to explain it to clients

> “This script shows what the bank does to you… and what happens when you flip it.”





