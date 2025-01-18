# Coin-Operated Drink Stand System

This project is a coin-operated drink stand system designed to accept Indonesian currency, calculate the total amount inserted, handle drink purchases, and dispense correct change. The system is implemented using ICs and logic gates in **Proteus** simulation software.

## Disclaimer
This system is designed and tested on **Proteus 8.11**. It utilizes a top-up system with coin sensors, a latch system for drink selection, a change system for correct coin dispensing, and displays to show the current token amount.

## Features

### 1. **Top-Up System**
- The system utilizes a **coin sensor** to detect coins based on size (100, 200, 500, and 1000 IDR).
- Coins are added to an **adder-register loop** that continuously adds the current token amount.

### 2. **Latch System**
- Once the top-up is complete, a **button** is pressed to transition to the purchasing state.
- The system offers 4 types of drinks with different prices:
  - Ice Cream: 1000 IDR/second
  - Milk: 200 IDR/second
  - Soda: 100 IDR/second
- A **subtractor-register system** performs subtraction to deduct the cost of the selected drink.
- Logic ensures that the current token amount cannot go below zero.
- **Multiplexer** is used to select the type of drink based on user input.

### 3. **Change System**
- A **decoder** converts the remaining balance into coins for change. For example, 800 IDR is converted into:
  - 1 x 500 IDR coin
  - 1 x 200 IDR coin
  - 1 x 100 IDR coin

### 4. **Additional Features**
- **Simulated Servos**: Emulates drink dispensing based on user selection.
- **7-Segment Displays**: Displays the current token balance.

## Components Used
- **Coin Sensor**: Detects coins based on size.
- **Adder and Subtractor Circuits**: For adding and subtracting coin values.
- **Register Loop**: Holds the current token value.
- **Multiplexer**: Selects the drink type.
- **Decoder**: Converts remaining balance into change coins.
- **Simulated Servos**: For drink dispensing.
- **7-Segment Displays**: Displays token value.

## States and Transitions

### 1. **Idle State**: 
- Initial state, waiting for user input.
  - **Transition**: Move to **Top-Up State** when a coin is detected.

### 2. **Top-Up State**: 
- Coins are being inserted and the total token value is being accumulated.
  - **Transition**: Move to **Purchase State** when the top-up is completed (button press).

### 3. **Purchase State**: 
- The user selects a drink, and the system checks if the available tokens are sufficient for the drink price.
  - **Transition**: Move to **Change Dispense State** if the purchase is successful (tokens are sufficient).
  - **Transition**: Return to **Top-Up State** if the tokens are insufficient (error state or user can top up more).

### 4. **Change Dispense State**: 
- The system calculates and dispenses the correct change, using a decoder to convert the remaining balance into coins.
  - **Transition**: Move to **Idle State** after change is dispensed.

## Software and Tools
- **Proteus 8.11**: For circuit design and simulation.

## Setup Instructions
1. Open the project in **Proteus 8.11**.
2. Load the provided **Proteus file**.
3. Simulate the circuit to test the system.
