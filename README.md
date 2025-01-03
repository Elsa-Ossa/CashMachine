# Cash Machine Project

## Overview
The Cash Machine Project is a web-based application simulating basic ATM functionalities, including balance checking, deposits, withdrawals, and transaction history management. It uses HTML, CSS, and JavaScript to provide an interactive and secure user experience.

---

## Features
1. **PIN Validation**:
   - Users must enter a PIN to access the application.
   - Limited to 3 incorrect attempts before locking access.

2. **Account Operations**:
   - **Check Balance**: View the current account balance.
   - **Deposit Money**: Add money to the account after validation.
   - **Withdraw Money**: Subtract money, ensuring sufficient funds.
   - **Transaction History**: View the last 5 transactions.

3. **Error Handling**:
   - Prevents invalid inputs (e.g., negative or non-numeric values).
   - Displays appropriate messages for insufficient funds or incorrect PIN attempts.

4. **User-Friendly Interface**:
   - Responsive design for smooth interaction.
   - Dynamic content updates without page reloads.

---

## Technology Stack
- **HTML**: Structures the interface.
- **CSS**: Styles the application for readability and user experience.
- **JavaScript**: Implements application logic and interactivity.

---

## Installation
1. **Prerequisites**:
   - Install [Visual Studio Code](https://code.visualstudio.com/).
   - Install the **Live Server** extension in Visual Studio Code.

2. **Setup**:
   - Clone or download the project files into a folder, e.g., `CashMachineProject`.
   - Ensure the project contains:
     - `index.html`: The main HTML file.
     - `cashMachine.js`: The JavaScript file.
     - `style.css` (optional): Any custom styles.

3. **Run the Application**:
   - Open the `index.html` file in Visual Studio Code.
   - Right-click the file and select **Open with Live Server**.
   - The application will launch in your default browser.

---

## Usage Instructions
1. Open the application in your browser.
2. Enter the **PIN** to log in (default PIN: `1234`).
   - You have 3 attempts to enter the correct PIN.
3. Use the menu options to perform actions:
   - **Check Balance**: Displays the current balance.
   - **Deposit Money**: Prompts for an amount to deposit.
   - **Withdraw Money**: Prompts for an amount to withdraw. Ensures sufficient funds.
   - **View Transactions**: Shows the last 5 transactions.
4. Exit the application by clicking the **Exit** button.

---

## File Structure
```
CashMachineProject/
├── index.html         # Main HTML file
├── cashMachine.js     # JavaScript logic
├── style.css          # Optional CSS file for styling
```

---

## Code Example
### HTML (index.html):
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cash Machine</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <div id="app">
        <h2>Cash Machine</h2>
        <div id="login">
            <p>Enter PIN:</p>
            <input type="password" id="pin" maxlength="4">
            <button onclick="checkPIN()">Submit</button>
        </div>
        <div id="menu" class="hidden">
            <button onclick="checkBalance()">Check Balance</button>
            <button onclick="depositMoney()">Deposit Money</button>
            <button onclick="withdrawMoney()">Withdraw Money</button>
            <button onclick="viewTransactions()">View Transactions</button>
            <button onclick="exitApp()">Exit</button>
        </div>
        <div id="action" class="hidden">
            <p id="action-message"></p>
            <input type="number" id="amount" class="hidden">
            <button id="confirm" class="hidden" onclick="performAction()">Confirm</button>
        </div>
        <div id="transactions" class="hidden">
            <h3>Transaction History</h3>
            <ul id="transaction-list"></ul>
        </div>
    </div>
    <script src="cashMachine.js"></script>
</body>
</html>
```

### JavaScript (cashMachine.js):
```javascript
let balance = 1000;
const pin = '1234';
let attempts = 3;
const transactions = [];

function checkPIN() {
    const inputPIN = document.getElementById('pin').value;
    if (inputPIN === pin) {
        document.getElementById('login').classList.add('hidden');
        document.getElementById('menu').classList.remove('hidden');
    } else {
        attempts--;
        if (attempts === 0) {
            alert("Too many incorrect attempts. Access locked.");
        } else {
            alert(`Incorrect PIN. ${attempts} attempts left.`);
        }
    }
}

function checkBalance() {
    alert(`Your balance is £${balance}`);
}

function depositMoney() {
    const amount = parseFloat(prompt("Enter amount to deposit:"));
    if (!isNaN(amount) && amount > 0) {
        balance += amount;
        transactions.push(`Deposit: £${amount}`);
        alert(`New balance: £${balance}`);
    } else {
        alert("Invalid amount. Please try again.");
    }
}

function withdrawMoney() {
    const amount = parseFloat(prompt("Enter amount to withdraw:"));
    if (!isNaN(amount) && amount > 0 && amount <= balance) {
        balance -= amount;
        transactions.push(`Withdrawal: £${amount}`);
        alert(`New balance: £${balance}`);
    } else if (amount > balance) {
        alert("Insufficient funds.");
    } else {
        alert("Invalid amount. Please try again.");
    }
}

function viewTransactions() {
    if (transactions.length === 0) {
        alert("No transactions yet.");
    } else {
        alert(transactions.join('\n'));
    }
}

function exitApp() {
    alert("Goodbye!");
}
```

---

## Future Enhancements
1. **User Authentication**:
   - Add multiple user accounts with unique PINs.
2. **Data Persistence**:
   - Save user data and transaction history using localStorage or a database.
3. **Advanced Features**:
   - Implement a logout feature.
   - Add support for multiple currencies.
4. **Improved Styling**:
   - Enhance design with animations and transitions.

---

## License
This project is open-source and available for use under the [MIT License](LICENSE).

---

## Acknowledgments
This project was developed as a learning exercise for mastering core web development concepts, including:
- DOM manipulation
- Responsive design
- JavaScript event handling.




