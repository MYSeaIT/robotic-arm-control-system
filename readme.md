# Project Name: Robotic Arm Control System

# About

The Robotic Arm Control System project focuses on creating a Python-based control interface for a robotic arm using a Raspberry Pi. The software, `arm.py`, provides a class `Joint` to represent each moveable segment of the robot arm and a class `Arm` to control multiple `Joint` instances simultaneously. 

Key features include:
- Individual joint control with positional feedback.
- Limit setting for preventing mechanical overextension.
- Emergency stop functionality to halt all movements instantly.
- Concurrent joint manipulation allowing for complex, coordinated movements.

The control system is intended to be integrated into applications requiring precise and multi-joint robotic arm control. It can be adapted to various robotic arm models with varying degrees of complexity.

This document serves as a detailed guide for developers working with `arm.py` and outlines the encountered difficulties, bugs, and the measures taken to resolve them during the development process. Our aim is to provide transparency and aid future development and debugging efforts.


## Development Procedure

### Errors Encountered and Solutions Applied

#### Issue 1: GPIO.cleanup() not called after controlling the robotic arm

Cause: Failure to clean up GPIO resources can lead to potential issues with pin management and usage.

Solution: Added GPIO.cleanup() in the main function to ensure proper release of GPIO resources.

#### Issue 2: KeyboardInterrupt exception not properly handled during joint movement.

Cause: Failure to catch and handle the KeyboardInterrupt exception can result in unexpected termination of the program.

Solution: Implemented try-except block to catch KeyboardInterrupt exception and handle the motor movement interruption.

#### Issue 3: Lack of clear direction on how to set up the remote control system.

Cause: Remote control system setup was not clearly documented, leading to confusion in the development process.

Solution: Updated README with clear instructions on setting up the remote control system using Flask-SocketIO.

## Functions Related Errors

1. **Joint Movement**:
   - Issue: Inconsistent movement of joints during concurrent operations.
   - Cause: Synchronization issues in the concurrent_movement() function.
   - Solution: Implemented ThreadPoolExecutor for better synchronization of joint movements.

2. **Motor Limit Handling**:
   - Issue: Unreliable handling of motor limits during joint movement.
   - Cause: Improper validation of motor limits in the go() function.
   - Solution: Added conditional checks to ensure accurate motor limit handling.

3. **E-STOP Functionality**:
   - Issue: E-STOP functionality not fully implemented.
   - Cause: Incomplete integration of E-STOP handling in the Arm class.
   - Solution: Enhanced Arm class to include explicit E-STOP functionality for joint movements.
