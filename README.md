# 🏦 Bank Account Simulator (C++ OOP Project)

A console-based **Bank Account Simulator** developed in C++ to demonstrate core Object-Oriented Programming (OOP) principles. The system models real-world banking operations—including deposits, bonus deposits, withdrawals with account-specific rules, inter-account fund transfers, and monthly interest calculation—through a polymorphic class hierarchy.

---

## 📋 Table of Contents
- [Features](#-features)
- [OOP Concepts Demonstrated](#-oop-concepts-demonstrated)
- [Class Architecture](#-class-architecture)
- [Getting Started](#-getting-started)
- [Sample Output](#-sample-output)
- [Project Contributors](#-project-contributors)

---

## ✨ Features
- **Account Management:** Supports both **Savings** and **Checking** accounts with unique account numbers, holder names, and balances.
- **Flexible Deposits:** Perform standard deposits or promotional deposits with an added bonus amount.
- **Account-Specific Withdrawal Rules:**
  - **Savings Account:** Enforces a strict monthly limit of **3 withdrawals** and verifies sufficient balance.
  - **Checking Account:** Supports unlimited transactions with customizable **overdraft protection** (default: `$500.00`).
- **Interest Calculation:** Applies a static **11% monthly interest rate** to savings accounts and automatically resets the monthly withdrawal counter.
- **Fund Transfers:** Safely transfers money between any two accounts (e.g., Savings to Checking) using a `friend` function.
- **Operator Overloading:** Use intuitive syntax (`+`, `-`, `>`, `<`, `==`, `>>`, `<<`) for transactions, balance comparisons, and stream I/O.

---

## 🧠 OOP Concepts Demonstrated
| Concept | Implementation in Project |
| :--- | :--- |
| **Abstraction** | `Account` is an abstract base class defining pure virtual functions (`deposit`, `withdraw`, `display`). |
| **Inheritance** | `SavingsAccount` and `CheckingAccount` publicly inherit core attributes and behaviors from `Account`. |
| **Polymorphism** | Base class pointers (`Account*`) dynamically invoke overridden methods at runtime (late binding). |
| **Encapsulation** | Sensitive account data is protected using `protected` and `private` access specifiers with controlled getters. |
| **Function Overloading** | `deposit(double amount)` and `deposit(double amount, double bonus)` provide compile-time polymorphism. |
| **Operator Overloading** | Overloaded `+` (deposit), `-` (withdraw), `>`, `<`, `==` (balance comparison), and `<<` / `>>` (stream I/O). |
| **Friend Functions** | `transfer()`, `operator>>`, and `operator<<` access protected account members seamlessly. |
| **Static Members** | `withdrawalLimit` (`3`) and `interestRate` (`0.11`) are shared across all `SavingsAccount` instances. |

---

## 🏗️ Class Architecture

```text
                 ┌───────────────────────────┐
                 │     Account (Abstract)    │
                 ├───────────────────────────┤
                 │ # AccountNumber : int     │
                 │ # HolderName : string     │
                 │ # Balance : double        │
                 ├───────────────────────────┤
                 │ + deposit() = 0           │
                 │ + withdraw() = 0          │
                 │ + display() = 0           │
                 └─────────────┬─────────────┘
                               │
               ┌───────────────┴───────────────┐
               ▼                               ▼
┌─────────────────────────────┐ ┌─────────────────────────────┐
│       SavingsAccount        │ │       CheckingAccount       │
├─────────────────────────────┤ ├─────────────────────────────┤
│ - withdrawalCount : int     │ │ - overdraftLimit : double   │
│ - withdrawalLimit : static  │ ├─────────────────────────────┤
│ - interestRate : static     │ │ + deposit()                 │
├─────────────────────────────┤ │ + withdraw()                │
│ + deposit()                 │ │ + display()                 │
│ + withdraw()                │ └─────────────────────────────┘
│ + applyInterest()           │
│ + display()                 │
└─────────────────────────────┘
```

---

## 🚀 Getting Started

### Prerequisites
- A C++ compiler supporting C++11 or later (e.g., `g++`, `clang++`, or MSVC).

### Compilation & Execution
1. **Clone the repository:**
   ```bash
   git clone https://github.com/Tayyab-Yahya/OOP-Project-Back-Account-Simulator.git
   cd OOP-Project-Back-Account-Simulator
   ```

2. **Compile the source code:**
   ```bash
   g++ "OOP Final Project.cpp" -o BankSimulator
   ```

3. **Run the executable:**
   - **Windows:**
     ```bash
     BankSimulator.exe
     ```
   - **Linux / macOS:**
     ```bash
     ./BankSimulator
     ```

---

## 💻 Sample Output

```text
Savings Account: #1001
Account Holder Name: Jacob
Balance: $500.00
Withdrawal Count this month: 0

Deposited amount $100 to Savings Account #1001
Deposited Amount $100 and Bonus $100 to Savings Account #1001
Withdrew Amount $30 from Savings Account #1001
Amount $300 transferred from Account #1001 to Account #1003
Withdrawal Limit reached for Savings Account #1001

Savings Account: #1001
Account Holder Name: Jacob
Balance: $470.00
Withdrawal Count this month: 3

Interest of $51.70 applied to Savings Account #1001
```

---

## 👥 Project Contributors
**University of Management and Technology (UMT), Lahore**  
*Department of Computer Science — Object-Oriented Programming (Section V13)*

- **M. Tayyab Yahya** (`F2024266554`)
- **Saif Ur Rehman Hashmi** (`F2024266593`)
- **Naseem Khan** (`F2024266573`)

**Supervisor:** Sir Ammar Haider