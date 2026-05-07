# STM32 RTOS Event-Driven Control System

An event-driven embedded control system built on STM32 using FreeRTOS/CMSIS-RTOS v2.

This project demonstrates:

- RTOS task management
- State machine architecture
- UART command handling
- ADC monitoring
- Event flags
- Message queues
- Mutex synchronization
- Interrupt-driven communication

---

# Features

## State Machine

The system operates using three states:

| State | Description |
|---|---|
| STATE_RUN | Normal operation |
| STATE_ERROR | Warning condition detected |
| STATE_STOP | Unsafe condition / emergency stop |

---

## UART Commands

Commands are received through UART interrupt mode.

| Command | Action |
|---|---|
| r | Start system |
| s | Stop system |

---

## ADC Monitoring

ADC continuously monitors sensor values and classifies them into:

| ADC State | Condition |
|---|---|
| ADC_NORMAL | Safe |
| ADC_WARNING | High temperature |
| ADC_DANGER | Unsafe condition |

---

## RTOS Objects Used

- Threads (Tasks)
- Message Queues
- Event Flags
- Mutex
- Software Timer

---

# Software Architecture

## Tasks

### ControlTask
- Main system controller
- Handles state transitions
- Processes commands and events

### uartTask
- Processes UART input
- Sends commands to queue

### ADCTask
- Reads ADC values periodically
- Updates ADC state

---

# Peripheral Usage

| Peripheral | Usage |
|---|---|
| UART2 | Serial communication |
| ADC1 | Sensor monitoring |
| GPIO | LED indicators |
| EXTI | Emergency stop button |

---

# LED Indication

| LED | Meaning |
|---|---|
| Green | RUN |
| Yellow | ERROR/WARNING |
| Red | STOP |

---

# Synchronization

UART printing is protected using a mutex to avoid corrupted output from multiple tasks.

---

# Example Serial Output

text [WARN] : High Temperature! [STATE] : ERROR  [ERROR] : Unsafe Condition! [STATE] : STOP  [STATE] : RUN 

---

# Tools & Frameworks

- STM32CubeIDE
- STM32 HAL
- CMSIS-RTOS v2
- FreeRTOS

---

# Project Structure

text Core/ ├── Inc/ ├── Src/ │   └── main.c 

---

# Future Improvements

- PWM motor control
- LCD/OLED interface
- DMA-based UART
- Sensor filtering
- Fault logging
- Low power mode

---

# Author

Embedded Systems / STM32 RTOS Practice Project
