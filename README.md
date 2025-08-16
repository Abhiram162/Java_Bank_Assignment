# Banking Management System

A Java-based Banking Management System that simulates basic banking operations through a command-line interface with a simple GUI element for the exit message.

## Features

- Create multiple bank accounts
- Secure PIN-based authentication
- Account operations:
  - Deposit money
  - Withdraw money (regular and denomination-based)
  - Transfer money between accounts
  - Check balance
  - View account details
  - Close account

## Technical Details

- Written in Java
- Uses Object-Oriented Programming concepts:
  - Abstraction
  - Interfaces
  - Inheritance
  - Encapsulation
- Implements exception handling for input validation
- Uses Java Swing for basic GUI elements

## Getting Started

### Prerequisites

- Java Development Kit (JDK) installed on your system
- Any Java IDE (optional)

### Running the Application

1. Compile the Java files:
   ```bash
   javac BankingManagement.java
   ```

2. Run the program:
   ```bash
   java BankingManagement
   ```

## Usage

1. First, specify the number of accounts you want to create
2. For each account, provide:
   - Account holder's name
   - Account type
   - 4-digit PIN
   - Initial deposit (minimum Rs.1000)
3. Use the generated account number and PIN to access account features
4. Choose from the available operations:
   - Deposit
   - Withdrawal
   - Denomination-based withdrawal
   - Transfer to another account
   - Balance inquiry
   - Account details
   - Close account

## Security Features

- PIN-based authentication
- Minimum balance requirement
- Input validation
- Secure fund transfer between accounts

## Note

This is a demonstration project and should not be used for actual banking operations.
