
# README for CalculatorApp

---

### Project: CalculatorApp  
**Created by:** Daulet Omarov 
**Date:** 28.09.2004 - 04.10.2024

---

## Overview

The **CalculatorApp** is a simple iOS calculator application built using **Swift** and **UIKit**. The app consists of a user interface with buttons for digits, operations (such as addition, subtraction, multiplication, and division), and functional buttons like **clear**, **backspace**, and **equals**. It allows users to perform basic arithmetic calculations and displays the result.

---

## Code Structure

### 1. **ViewController.swift**
This is the main view controller for the app, which handles all the button interactions and logic for the calculator.

### 2. **IBOutlets**
- **calculatorWorkings (UILabel):** Displays the current calculation being typed by the user.
- **calculatorResults (UILabel):** Displays the final result of the calculation after pressing the equals button.

### 3. **Variables**
- **workings (String):** A string that holds the current user input or expression. This is updated each time the user taps a button.

---

## Key Functions

### 1. **viewDidLoad()**
This method is called after the view controller has loaded its view hierarchy into memory. In this case, it simply calls the `clearAll()` method to reset the calculator when the app starts.

### 2. **clearAll()**
This function clears all user input and resets the calculator to an empty state. It sets both `workings` and the labels `calculatorWorkings` and `calculatorResults` to empty strings.

### 3. **equalsTap(_ sender: Any)**
This function is triggered when the equals button is pressed. It evaluates the mathematical expression in `workings` using the `NSExpression` class and displays the result in the `calculatorResults` label.
- The result is formatted using the `formatResult(result:)` method, which ensures that if the result is a whole number, it doesn't show decimal places, and if it's a decimal, it rounds to two decimal places.

### 4. **formatResult(result: Double) -> String**
This function formats the result of the calculation:
- If the result has no decimal part, it will return the number as an integer (e.g., `10`).
- If the result has decimals, it rounds to two decimal places (e.g., `10.56`).

### 5. **allClearTap(_ sender: Any)**
This function is linked to the "AC" button, which calls `clearAll()` to reset the calculator.

### 6. **backTap(_ sender: Any)**
This function handles the backspace operation. It removes the last character in the `workings` string and updates the `calculatorWorkings` label. It only performs the action if the `workings` string is not empty.

### 7. **addToWorkings(value: String)**
This helper function appends the input value (such as a digit or operation symbol) to the `workings` string and updates the `calculatorWorkings` label.

### 8. **Mathematical Operation Functions**
These functions handle the input for basic arithmetic operations. When a user taps any of these buttons, it appends the corresponding operation symbol to `workings`.
- **percentTap(_ sender: Any)** – Adds the percentage symbol `%`.
- **divideTap(_ sender: Any)** – Adds the division symbol `/`.
- **timesTap(_ sender: Any)** – Adds the multiplication symbol `*`.
- **minusTap(_ sender: Any)** – Adds the subtraction symbol `-`.
- **plusTap(_ sender: Any)** – Adds the addition symbol `+`.

### 9. **Digit and Decimal Input Functions**
These functions append their respective value to the `workings` string when tapped.
- **decimalTap(_ sender: Any)** – Adds the decimal point `.`.
- **zeroTap(_ sender: Any)** – Adds `0`.
- **oneTap(_ sender: Any)** – Adds `1`, and so on for the other digits up to 9.

---

## UI Interaction

Each button in the calculator is connected to a corresponding **@IBAction** in the `ViewController.swift` file. The user taps a button, which triggers the associated function, updating the `workings` string and the on-screen labels.

For example:
- Tapping `7` calls `sevenTap(_:)`, which appends `7` to the `workings` string.
- Tapping `+` calls `plusTap(_:)`, which appends `+` to the `workings` string.
- When the user finishes entering their expression and taps `=`, the `equalsTap(_:)` function evaluates the expression and displays the result.

---

## Error Handling

Currently, the app assumes that the user will always enter valid expressions. No error handling is implemented for cases like:
- Dividing by zero
- Inputting invalid expressions (e.g., multiple operators in a row like `++`)

---

## Future Enhancements

Potential improvements could include:
- **Error Handling:** Add checks for invalid expressions (e.g., multiple operators in a row, division by zero).
- **More Operations:** Add more advanced operations such as square roots, powers, or trigonometric functions.
- **Improved UI:** The UI can be enhanced for a more user-friendly and aesthetic experience.

---

## Conclusion

The **CalculatorApp** is a simple calculator implementation in Swift using UIKit. It demonstrates how to build a basic calculator with arithmetic operations and dynamic label updates. The app can be further improved with additional features and error handling.
