# GSM-Based Two-Step Time-Limited Door Access System Using LPC2148

## 📌 Project Overview

The **GSM-Based Two-Step Time-Limited Door Access System** is an embedded security project designed to provide secure and controlled access to restricted areas using two-step authentication.

The system combines password-based authentication with GSM-based One-Time Password (OTP) verification to improve security and prevent unauthorized access.

The project is developed using the **LPC2148 ARM7 microcontroller**. A 4×4 matrix keypad is used to enter the password and OTP, while a GSM module sends the OTP to the registered mobile number.

After successful verification of both authentication steps, the microcontroller controls an L293D motor driver to operate a DC motor, which physically opens the door. After a predefined time duration, the motor rotates in the opposite direction to close the door.

The system integrates embedded C programming, UART communication, GSM technology, motor control, and time-based access management.

---

## 🎯 Project Objectives

- Implement two-step authentication for secure door access.
- Provide password-based authentication.
- Generate and verify OTPs through GSM communication.
- Send OTPs to a registered mobile number using a GSM module.
- Control door opening and closing using a DC motor.
- Implement motor direction control using the L293D motor driver.
- Provide time-limited door access.
- Automatically close the door after the predefined access duration.
- Display system status through an LCD.

---

## ✨ Key Features

- **Two-Step Authentication:** Password verification followed by GSM-based OTP verification.
- **GSM Communication:** Sends OTP through SMS to a registered mobile number.
- **OTP Verification:** Validates the OTP entered by the user.
- **Time-Limited Access:** Grants access for a predefined duration.
- **Automatic Door Operation:** Opens and closes the door using a DC motor.
- **Motor Direction Control:** Uses the L293D motor driver to control the motor.
- **LCD Interface:** Displays authentication messages and system status.
- **Keypad Interface:** Allows users to enter passwords and OTPs.
- **Buzzer Indication:** Provides audible alerts.
- **LED Indication:** Provides visual status information.
- **RTC Integration:** Supports real-time clock functionality for time-based operations.

---

## 🛠️ Hardware Requirements

| Component                    | Description                       |
| ---------------------------- | --------------------------------- |
| LPC2148 ARM7 Microcontroller | Main processing and control unit  |
| GSM Module (SIM800/SIM900)   | Sends OTP through SMS             |
| 4×4 Matrix Keypad            | Password and OTP input            |
| 16×2 LCD Display             | Displays system information       |
| L293D Motor Driver           | Controls DC motor direction       |
| DC Motor                     | Opens and closes the door         |
| RTC                          | Real-time clock and time tracking |
| Buzzer                       | Audio indication                  |
| LEDs                         | Visual status indication          |
| Power Supply                 | Provides power to the circuit     |

---

## 💻 Software Requirements

| Software / Language          | Purpose                          |
| ---------------------------- | -------------------------------- |
| Embedded C                   | Firmware development             |
| Keil µVision                 | Code development and compilation |
| Proteus Design Suite         | Circuit simulation               |
| UART                         | Communication with GSM module    |
| LPC2148 Peripheral Libraries | Hardware peripheral interfacing  |

---

## ⚙️ System Working Principle

The system follows a two-step authentication process to provide secure access.

1. **System Initialization:** The LPC2148 initializes the LCD, keypad, UART, GSM module, RTC, and motor driver.
2. **Password Entry:** The user enters the password using the 4×4 matrix keypad.
3. **Password Verification:** The microcontroller checks whether the entered password is correct.
4. **OTP Generation:** If the password is valid, the system generates a One-Time Password.
5. **OTP Transmission:** The GSM module sends the generated OTP to the registered mobile number through SMS.
6. **OTP Entry:** The user enters the received OTP using the keypad.
7. **OTP Verification:** The microcontroller validates the entered OTP.
8. **Access Authorization:** If both authentication steps are successful, the system grants access.
9. **Door Opening:** The LPC2148 sends control signals to the L293D motor driver, which operates the DC motor to open the door.
10. **Time-Limited Access:** The door remains open for the predefined duration.
11. **Automatic Door Closing:** After the access duration expires, the motor rotates in the opposite direction to close the door.
12. **System Reset:** The system returns to its secure state and waits for the next authentication request.

If either authentication step fails, access is denied.

---

## 🔐 Authentication Flow

```text
             SYSTEM START
                  |
                  v
          Initialize LPC2148
                  |
                  v
             Enter Password
                  |
                  v
          Verify Password
                  |
           +------+------+
           |             |
         Invalid        Valid
           |             |
           v             v
      Access Denied   Generate OTP
                         |
                         v
                    Send OTP via GSM
                         |
                         v
                      Enter OTP
                         |
                         v
                    Verify OTP
                         |
                  +------+------+
                  |             |
                Invalid        Valid
                  |             |
                  v             v
             Access Denied  Access Granted
                                |
                                v
                          Open Door Motor
                                |
                                v
                         Start Access Timer
                                |
                                v
                         Access Time Expires
                                |
                                v
                         Close Door Motor
                                |
                                v
                          Secure State
```

---

## 🔌 Hardware Interfacing

### 1. LPC2148 Microcontroller

The LPC2148 ARM7 microcontroller acts as the main controller. It manages keypad input, LCD output, GSM communication, OTP verification, RTC operations, and motor control.

### 2. GSM Module

The GSM module communicates with the LPC2148 through UART.

AT commands are used to configure the GSM module and send SMS messages containing the generated OTP.

### 3. 4×4 Matrix Keypad

The keypad is used for entering the password and OTP. The microcontroller scans the keypad to identify the pressed keys.

### 4. LCD Display

The 16×2 LCD displays messages such as:

- Enter Password
- Invalid Password
- Sending OTP
- Enter OTP
- Invalid OTP
- Access Granted
- Access Denied
- Door Opening
- Door Closing

### 5. L293D Motor Driver and DC Motor

The L293D motor driver is used to control the direction of rotation of the DC motor.

The LPC2148 sends GPIO control signals to the L293D, which drives the motor to open and close the door.

| L293D Control Inputs   | Motor Operation    |
| ---------------------- | ------------------ |
| IN1 = HIGH, IN2 = LOW  | Forward rotation   |
| IN1 = LOW, IN2 = HIGH  | Reverse rotation   |
| IN1 = LOW, IN2 = LOW   | Motor stops/coasts |
| IN1 = HIGH, IN2 = HIGH | Motor stops/brakes |

The motor direction is reversed after the predefined access duration to close the door.

### 6. RTC

The RTC provides real-time information and can be used for time-based operations within the access control system.

---

## 📚 Embedded Systems Concepts Used

- ARM7 LPC2148 Architecture
- Embedded C Programming
- GPIO Interfacing
- UART Communication
- GSM Communication
- AT Commands
- LCD Interfacing
- Matrix Keypad Interfacing
- DC Motor Interfacing
- L293D Motor Driver
- RTC Interfacing
- OTP Generation and Verification
- Time-Based Access Control

---

## 📂 Project Directory Structure

```text
GSM-Based-Two-Step-Door-Access-System/
│
├── README.md
│
├── Source/
│   ├── main.c
│   ├── gpio.c
│   ├── uart.c
│   ├── lcd.c
│   ├── keypad.c
│   ├── gsm.c
│   ├── motor.c
│   └── timer.c
│
├── Header/
│   ├── types.h
│   ├── defines.h
│   ├── lcd.h
│   ├── keypad.h
│   ├── uart.h
│   ├── gsm.h
```

---

## 🚀 Applications

- Residential security systems
- Office access control
- Laboratory security systems
- Restricted-area access management
- Educational institutions
- Small-scale industrial security systems

---

## 🔮 Future Enhancements

- Fingerprint-based authentication.
- RFID-based access control.
- Mobile application integration.
- Cloud-based access monitoring.
- Multiple-user authentication.
- Failed login attempt detection.
- Real-time access logging.
- Door position detection using limit switches.
- Improved OTP security with expiration and retry limits.

---

## 👨‍💻 Project Information

| Category                | Details                                            |
| ----------------------- | -------------------------------------------------- |
| Project Title           | GSM-Based Two-Step Time-Limited Door Access System |
| Domain                  | Embedded Systems                                   |
| Microcontroller         | LPC2148 ARM7                                       |
| Programming Language    | Embedded C                                         |
| Communication Protocol  | UART                                               |
| GSM Communication       | SMS using AT Commands                              |
| Motor Driver            | L293D                                              |
| Motor                   | DC Motor                                           |
| Development Environment | Keil µVision                                       |
| Simulation Tool         | Proteus Design Suite                               |

---

## 📌 Conclusion

The GSM-Based Two-Step Time-Limited Door Access System provides an additional layer of security by combining password-based authentication with GSM-based OTP verification.

The integration of the LPC2148 ARM7 microcontroller, GSM communication, keypad, LCD, RTC, L293D motor driver, and DC motor demonstrates the practical implementation of embedded systems in security and automation applications.

The project provides controlled door access through two-step authentication and time-limited motor operation. It can be further enhanced by integrating biometric authentication, remote monitoring, and door position detection to develop a more advanced security system.

---

