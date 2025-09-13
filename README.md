# Digital Alarm Clock - Logisim FPGA Project

## 📌 Project Overview

This project implements a multifunctional digital alarm clock using Logisim-evolution v3.7.2 and FPGA synthesis on the TERASIC DE10-Lite board. The system combines traditional timekeeping with additional features including a timer, stopwatch, and musical alarms.

## ✨ Features

- **Digital Clock**: Real-time hour display with adjustable time settings
- **Alarm**: Programmable alarm with Harry Potter theme melody
- **Stopwatch**: Start/pause/reset functionality for time tracking
- **Timer**: Countdown timer with Beethoven's "Für Elise" melody
- **Display Options**: Invertible display for floor placement
- **Musical Alerts**: Two distinct melodies for different alarm types

## 🎮 Hardware Requirements

- TERASIC DE10-Lite FPGA Board
- USB connection cable
- Rotary encoder for navigation
- Push buttons (B1, B2)
- DIP switches
- 7-segment displays (6 units)
- LEDs for mode indication

## 🚀 Installation & Setup

1. **Connect the Hardware**
   - Connect the FPGA board to your computer via USB port
   - Launch FPGA synthesis to map the board with correct I/O configurations

2. **Initial Startup**
   - After mapping completion, all displays/LEDs will be off
   - Raise DIP Switch 4 to power on the device
   - "HELLO" message will display for 5 seconds
   - Clock will begin running automatically

3. **General Reset**
   - Press buttons B1 and B2 simultaneously (when DIP Switch 4 is activated)

## 📖 User Manual

### Navigation System
- **Rotary Encoder**: Navigate between modes
  - Rotate right: Increment mode
  - Rotate left: Decrement mode
  - Click: Validate/Enter selection

### Operating Modes

#### Mode I - Alarm ⏰
- LED 1 illuminated when selected
- Set alarm time using the Setting system
- Validate by clicking the encoder
- Stop alarm (Harry Potter theme) by pressing B2

#### Mode II - Stopwatch ⏱️
- LED 2 illuminated when selected
- **B1**: Start/Pause chronometer
- **B2**: Reset display for new timing session

#### Mode III - Timer ⏲️
- LED 3 illuminated when selected
- Set countdown time using the Setting system
- Validate by clicking the encoder
- Stop timer alarm (Für Elise) by pressing B2

#### Mode IV - Time Settings 🕐
- LED 4 illuminated when selected
- Adjust current time using the Setting system
- Validate by clicking the encoder
- Clock resumes with new parameters

#### Mode V - Clock Display 🕰️
- Simple time display with optional active alarm

### Special Features
- **DIP Switch 5**: Inverts display for floor placement
- **Musical Themes**:
  - Harry Potter theme by John Williams (Alarm)
  - Für Elise by Ludwig van Beethoven (Timer)

## 🔧 Technical Implementation

### Architecture
- **Main FSM**: 5-mode selector using 3-bit binary counter
- **Custom Counters**: 4-bit counters (0-9 and 0-5) with increment/decrement
- **Time Validation**: Prevents invalid time entries (>23:59:59)
- **Debouncing**: Filter implementation for encoder stability

### Key Components
- **State Machines**: Mode selection and time management
- **Memory Storage**: Parameter retention for timer, alarm, and time settings
- **Signal Processing**: Rising/falling edge detectors, one-tick converters
- **Gated Clock Prevention**: Proper clock domain management

### File Structure
```
project/
├── PROJET_FINI.circ     # Main Logisim circuit file
├── Rapport Systèmes Logiques.docx  # Technical documentation
└── README.md            # This file
```

## 🛠️ Technical Solutions

### Encoder Debouncing
- 4-stage D flip-flop filter chain
- SR-Latch network for stable signal output

### Time Constraint Management
- Dual FSM system for hours validation
- Prevents entries exceeding 23:59:59
- Dynamic limit adjustment based on tens/units interaction

### Clock Management
- Rising/falling edge detectors for signal synchronization
- One-tick converter for continuous-to-instantaneous signal conversion
- Proper gated clock avoidance techniques

## 📋 Known Issues & Solutions

1. **Encoder Bounce**: Resolved with custom filter implementation
2. **Invalid Time Entry**: Handled by interdependent FSM validation
3. **Gated Clock Issues**: Eliminated using edge detectors and one-tick converters

## 🎓 Learning Outcomes

This project provided valuable experience in:
- Memory management and storage organization
- Hierarchical task delegation in digital systems
- FPGA debugging without traditional compiler feedback
- State machine design and implementation
- Signal processing and timing constraints

## 📝 License

This is an educational project developed for Systems Logic course at EPFL.

---

**Note**: Ensure Logisim-evolution v3.7.2 is installed for circuit simulation and modification.
