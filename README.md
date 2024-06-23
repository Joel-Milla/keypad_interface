# Embedded Keypad Interaction System with STM32F407

## Overview
This project is developed to show STM32F407 connected with a matrix keypad. It configures specific pins to read inputs from the keypad and prints the pressed keys. 
## Key Features
- **Direct Port Access**: Directly manipulates hardware registers to control GPIO settings, to allow flow of data.
- **Keypad Scanning**: Implements a scanning algorithm to detect which keys are pressed on a matrix keypad.
- **Optimized Delay**: Uses manual delays to manage debouncing while printing the key pressed.
- **Character Mapping**: Converts keypad matrix positions to corresponding character outputs.

## Project Structure
- `main.c`: Contains the main logic for configuring GPIO ports and handling keypad input.

## Hardware and Tools
- **Microcontroller**: STM32F407
- **IDE**: STM32CubeIDE
- **Additional Components**:
  - Matrix Keypad
  - Jumping wires
  - Optional: Protoboard for easier wiring

## Setup and Run
1. Setup the STM32CubeIDE with the necessary project files.
2. Wire the matrix keypad to the STM32F407 according to the defined pin configurations (PD0-PD3 && PD8-PD11).
3. Compile the code onto the STM32F407 board.
4. Press keys on the keypad and observe the output on the console or debugger (Recomendation: Use SWV to see the printing statements).

## Detailed Operation
- **GPIO Configuration**: 
  - Outputs are set for rows (PD0-PD3).
  - Inputs are set for columns (PD8-PD11) with pull-up resistors activated to manage floating signal.
- **Key Detection**:
  - The program sets one row low at a time and checks column inputs for any low signal, indicating a button press.
  - Each button press is matched with a specific character based on the row and column detected, which is then printed.
- **Optimizations**:
  - Uses `volatile` keyword to ensure the compiler maintains code that interacts with hardware registers directly, preventing optimization-related issues.
  - Utilizes `const` to protect pointer addresses, ensuring they are not unintentionally altered after initial setup.

## Testing
- Test by pressing various keys on the keypad and verifying that the correct characters are displayed in the output console or debugger.

