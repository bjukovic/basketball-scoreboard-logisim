# Basketball Scoreboard Simulation

A digital basketball scoreboard simulation developed in **Logisim** as a practical implementation of digital logic design principles. The system reproduces the core functionality of a basketball scoreboard, including team scoring, foul tracking, game timing, period management, shot clock control, buzzer alerts, and possession indication.

## Overview

The project was developed to demonstrate how fundamental digital logic components can be integrated into a complete, interactive system.

The scoreboard consists of several interconnected subsystems that operate together to simulate essential game-management functions. User inputs are processed through combinational and sequential logic circuits, while counters and seven-segment displays provide real-time feedback.

The project was designed with an emphasis on **functional correctness, modularity, and organized circuit design**.

## Features

### Score Management

The system provides independent score tracking for the Home and Guest teams.

* Add 1, 2, or 3 points
* Subtract 1 point to correct scoring errors
* Reset individual team scores
* Display scores using seven-segment displays
* Multiplexer-based selection of scoring operations
* Binary-to-BCD and BCD-to-seven-segment conversion

### Foul Management

Each team has an independent foul counter.

* Increment team fouls
* Reset foul count
* Automatically detect five fouls
* Activate a bonus LED when the foul count reaches five
* Comparator-based foul-limit detection

### Game Timer

The game timer simulates a **10-minute period**.

* Minute and second countdown
* Period counter
* Start/stop control
* Reset functionality
* Automatic transition between periods
* Buzzer activation when the period ends
* Seven-segment display for time and period information

### Shot Clock

The scoreboard includes a **24-second shot clock**.

* 24-second countdown
* Dedicated reset control
* Warning LED at 1 second remaining
* Buzzer warning before expiration
* Possession change when the timer reaches zero
* Possession state implemented using a T Flip-Flop

## System Architecture

The project is divided into four primary subsystems:

```text
                    BASKETBALL SCOREBOARD
                              │
          ┌───────────────────┼───────────────────┐
          │                   │                   │
          ▼                   ▼                   ▼
    Score System         Foul System         Game Timer
   Home / Guest         Home / Guest        10 min / Period
                                                  │
                                                  ▼
                                            Shot Clock
                                              24 sec
```

Each subsystem is implemented using dedicated digital logic components and is integrated into the final scoreboard interface.

## Digital Logic Implementation

### Score Counters

Each team has an independent score counter. User input buttons determine the desired scoring operation.

A multiplexer selects between four possible values:

| Input | Operation |
| ----- | --------- |
| `00`  | +1        |
| `01`  | +2        |
| `10`  | +3        |
| `11`  | -1        |

The selected value is processed by an adder and combined with the team's current score.

A custom `PLUS123_1` circuit generates the multiplexer selection signals and enables the corresponding scoring operation. A negator is used to generate the negative value required for score correction.

### Foul Counters

The foul subsystem uses independent counters for the Home and Guest teams.

Each foul input increments the corresponding counter by one. A comparator continuously checks the counter against the value `5`. When five fouls are reached, the corresponding bonus LED is activated.

### Game Timer

The game timer uses separate counters for minutes, seconds, and periods.

The seconds counter is driven by the clock signal. When the seconds counter reaches zero, the minutes counter is updated. Once both minutes and seconds reach zero, the period counter advances.

Two comparator outputs are combined using an AND gate to detect the end of the period and activate the buzzer.

### Shot Clock

The shot clock implements a 24-second countdown.

When the counter reaches `1`, a warning LED and buzzer are activated. When the counter reaches `0`, the possession state changes.

The possession mechanism is implemented using a **T Flip-Flop** combined with a NOT gate, allowing the possession indicator to alternate between the two teams.

## Components Used

The circuit makes use of the following digital logic components:

* Counters
* Adders
* Multiplexers
* Comparators
* Negators
* AND gates
* NOT gates
* T Flip-Flop
* Binary-to-BCD converters
* BCD-to-seven-segment converters
* Seven-segment displays
* LEDs
* Push buttons
* Clock signals
* Buzzers
* Tunnels

## Interface Design

The final circuit is organized to resemble a physical basketball scoreboard.

The scoreboard display is positioned at the center of the design, while the control interfaces are arranged below it. Controls for the Home team are placed on the left and controls for the Guest team on the right.

Central controls provide access to:

* Game timer start/stop
* Game timer reset
* Shot clock reset

Tunnels are used extensively to organize signal connections and reduce unnecessary wiring across the circuit, resulting in a cleaner and more maintainable design.

## Results

The completed simulation successfully implements the intended scoreboard functionality.

Testing confirmed the correct operation of:

* Home and Guest score tracking
* 1-, 2-, and 3-point scoring
* Score correction
* Team foul counters
* Five-foul bonus indication
* Game countdown timer
* Period management
* Period-end buzzer
* 24-second shot clock
* Shot-clock warning
* Possession switching

The integrated system provides an interactive representation of the main functions required for basketball scorekeeping while demonstrating the practical application of digital logic design.

## Technologies

**Software**

* Logisim

**Concepts**

* Digital Logic Design
* Combinational Logic
* Sequential Logic
* Counters
* Multiplexers
* Adders
* Comparators
* Flip-Flops
* Seven-Segment Displays
* Clock-Based Timing

## Repository Structure

```text
Basketball-Scoreboard/
│
├── BasketballScoreboard.circ
└── README.md
```

### Files

**`BasketballScoreboard.circ`**
Complete Logisim circuit containing the basketball scoreboard implementation.

**`README.md`**
Project documentation and system overview.

## Getting Started

### Prerequisites

* Logisim or a compatible Logisim-based digital circuit simulator

### Running the Simulation

1. Clone the repository.
2. Open `BasketballScoreboard.circ` in Logisim.
3. Start the circuit simulation.
4. Use the provided control buttons to operate the scoreboard.

## Project Objectives

The primary objectives of the project were to:

1. Design a functional digital basketball scoreboard.
2. Apply digital logic concepts to a practical application.
3. Implement independent scoring and foul-management systems.
4. Develop clock-based countdown and period-management circuits.
5. Implement a 24-second shot clock with possession control.
6. Integrate multiple digital subsystems into a single functional circuit.
7. Maintain an organized and understandable circuit architecture.

## Academic Context

This project was developed as a practical application of **Digital Logic Design**, demonstrating the integration of fundamental logic components into a larger real-world system.

## Author

**Berina Juković**
Computer Science & Engineering
