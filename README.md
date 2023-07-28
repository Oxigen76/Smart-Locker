# Smart-Locker
This project involves building a secure, password-protected locker system.


## Overview

This project involves assembling a secure locker system using various components. The locker opens when a password is correctly entered on the keypad. If the password matches the one stored in the system, a servo motor rotates 90 degrees to unlock the locker and reverts back to its original position after a set duration.

## System Design

### Hardware Components

The primary components required for this project include a keypad for password entry, a servo motor to control the lock mechanism, and an Arduino board to process input and control the servo motor.

Below are diagrams and tables that detail the components used in our system and their connections.

#### Figure 2: Components used in our system 
![Components](Insert-Figure-2-URL-here)

#### Figure 3: Component List
![Component List](Insert-Figure-3-URL-here)

#### Figure 4: Wired connection on our system 
![Wired connection](Insert-Figure-4-URL-here)

#### Figure 5: Schematic view of our system 
![Schematic view](Insert-Figure-5-URL-here)

#### Figure 6: Connection details for our system 
![Connection details](Insert-Figure-6-URL-here)

#### Table 2: Component connection to Arduino Board

| Component | Pin Arduino Board |
| --- | --- |
| Keypad Row | 13, 12, 11, 10 |
| Keypad Column | 9, 8, 7, 6 |
| Servo1 PWR | +5V |
| Servo1 SIG | 5 |
| Servo1 GND | GND |

### Software

The system's functionality is driven by Arduino code that captures and validates keypad inputs, controls the servo motor, and manages password storage and handling.

#### Code Overview

Below are some snippets of our Arduino code with explanations.

##### Figure 7: Activating the keypad and entering the password 
![Code lines](Insert-Figure-7-URL-here)

A 4-digit password is input on the keypad, followed by the '#' key to validate the entry.

##### Figure 8: System reset if '#' is not pressed
![System Reset](Insert-Figure-8-URL-here)

The system stores one master password and two guest passwords.

##### Figure 9: Code lines for passwords 
![Password Code](Insert-Figure-9-URL-here)

The system logs the time when a password is entered. If the passwords match those stored, it will not display them, but only the locker's opening and the event timestamp.

##### Figure 10: Serial Monitor after Master password is entered 
![Master Password](Insert-Figure-10-URL-here)

An event showing the incorrect password and timestamp is created if a wrong password is entered.

##### Figure 11: Code line for Incorrect password 
![Incorrect Password Code](Insert-Figure-11-URL-here)

##### Figure 12: Incorrect password with timestamp
![Incorrect Password](Insert-Figure-12-URL-here)

##### Code Snippets:

###### Figure 13: Inserting Arduino Libraries
![Arduino Libraries](Insert-Figure-13-URL-here)

###### Figure 14: Adding necessary Libraries
![Additional Libraries](Insert-Figure-14-URL-here)

###### Figure 15: Setting up passwords, Keypad, and Servo Motor
![Setup Code](Insert-Figure-15-URL-here)

###### Figure 16: Code for main program loop and password processing function
![Main Program Code](Insert-Figure-16-URL-here)

###### Figure 17: Messages printed on Serial Monitor
![Serial Monitor Messages](Insert-Figure-17-URL-here)

##### System Operation

###### Figure 18: System closed
![System Closed](Insert-Figure-18-URL-here)

###### Figure 19: System opening
![System Opening](Insert-Figure-19-URL-here)


## Testing system

### Integration test:

1. Test the system: 
    - Enter the Master password: Press '*' followed by "1234", then press '#'. The servo motor should move to the open position, unlocking the door. After 5 seconds, the servo motor should return to the closed position, locking the door again.
        ![Test Master password](Insert-Figure-28-URL-here)
    - Enter the Guest1 password: Press '*' followed by "5678", and then press '#'. The servo motor should move to the open position, unlocking the door. After 5 seconds, the servo motor should return to the closed position, locking the door again.
        ![Test Guest 1 password](Insert-Figure-29-URL-here)
    - Enter the Guest2 password: Press '*' followed by "9012", then press '#'. The servo motor should move to the open position, unlocking the door. After 5 seconds, the servo motor should return to the closed position, locking the door again.
        ![Test Guest 2 password](Insert-Figure-30-URL-here)
    - Enter an incorrect password: Press '*' followed by an incorrect password (e.g., "1111"), then press '#'. The servo motor should not move, and the door should remain locked.
        ![Test incorrect password](Insert-Figure-31-URL-here)
2. Observe the Arduino Serial Monitor to view the output messages for each password attempt, including the time of the attempt and whether the password was correct or incorrect.
3. Test the timeout functionality: Press '*' and enter part of a password (e.g., "12"), but do not press '#' within 2 seconds. The system should display a timeout message on the Serial Monitor, and the door should remain locked.
    ![Test timeout function](Insert-Figure-32-URL-here)

### Functionality Test

![Functionality test](Insert-Table-6-URL-here)
| Tinkercad Test | Real-World Test |
|----------------|-----------------|
| Prepare the test environment: Ensure the electronic lock system is assembled correctly and connected, load the required software onto the microcontroller, and connect the microcontroller to a computer to monitor the Serial output. | Prepare the test environment: Install the electronic lock system on the meeting room door, load the required software onto the microcontroller, and connect the microcontroller to a computer to monitor the Serial output. |
| Test the password input: Enter various passwords using the keypad and observe if the system accepts the input correctly. Test for correct processing by entering invalid symbols or incomplete passwords. To test the timeout functionality, input a password without pressing '#' within 2 seconds and verify if the system cancels the input. | Test the password input: Have different employees try to input their passwords using the keypad and observe if the system accepts the input correctly. Test for correct processing by entering invalid symbols or incomplete passwords. To test the timeout functionality, input a password without pressing '#' within 2 seconds and verify if the system cancels the input. |
| Test the password validation: Enter valid Master, Guest1, and Guest2 passwords to see if the system accepts them. Input incorrect passwords to check if the system rejects them. | Test the password validation: Have authorised employees enter their valid passwords to see if the system grants them access. Have unauthorised employees attempt to input random or guessed passwords to check if the system rejects them. |
| Test the servo motor control: With valid passwords entered, observe if the servo motor unlocks the door. Check if the servo motor returns to the locked position after 5 seconds. Verify that the servo motor remains stationary when someone enters an incorrect password. | Test the servo motor control: With valid passwords entered, observe if the servo motor unlocks the meeting room door. Check if the servo motor returns to the locked position after 5 seconds. Verify that the servo motor remains stationary when someone enters an incorrect password. |
| Test the Serial Monitor output: Observe the Serial Monitor for each password attempt. Check the time of the attempt to ensure the system logs it correctly. Verify if the system identifies and logs whether the password is correct or incorrect. | Test the Serial Monitor output: Observe the Serial Monitor for each password attempt. Check the time of the attempt to ensure the system logs it correctly. Verify if the system identifies and logs whether the password is correct or incorrect. |
| Test reliability and robustness: Repeat the tests multiple times to ensure consistent performance. Enter passwords quickly and in rapid succession to test the system's ability to handle such situations without errors. | Test reliability and robustness: Repeat the tests multiple times over a few days to ensure consistent performance. During peak hours, have employees enter their passwords rapidly to test the system's ability to handle such situations without errors. |
| Document the test results: Record the results of each test, noting any discrepancies or issues. Then, analyse the results to determine if the system meets the requirements. If you discover any problems, address them and retest the system. | Test the impact of environmental factors: Test the electronic lock system in various lighting conditions (natural, artificial, low light) to ensure the keypad remains functional. Test the system during temperature fluctuations (e.g., hot afternoons or cold mornings) to ensure the components work consistently. Then, document the test results: Record the results of each test, noting any discrepancies or issues. Then, analyse the results to determine if the system meets the requirements for the office environment. If you discover any problems, address them and retest the system. |

### Documenting Test Results for the Smart Locker System

| Test ID | Test Description                           | Expected Result                           | Actual Result                           | Status                                                | Issue / Discrepancy |
|---------|--------------------------------------------|-------------------------------------------|-----------------------------------------|--------------------------------------------------------|---------------------|
| T01     | Initialize Smart Locker System             | System initializes successfully           | System initializes successfully         | ![Pass](https://img.shields.io/badge/Status-Pass-green) |                     |
| T02     | Connect to camera                          | Camera connection established             | Camera connection established           | ![Pass](https://img.shields.io/badge/Status-Pass-green) |                     |
| T03     | Test camera focus and zoom                 | Focus and zoom adjust correctly           | Focus and zoom adjust correctly         | ![Pass](https://img.shields.io/badge/Status-Pass-green) |                     |
| T04     | Test servo motor movement                  | Servo motor moves accurately and smoothly | Servo motor moves accurately, not smoothly | ![Fail](https://img.shields.io/badge/Status-Fail-red) | Motor stutter       |
| T05     | Test object detection                      | System detects and identifies objects successfully | System detects and identifies objects successfully | ![Pass](https://img.shields.io/badge/Status-Pass-green) |                     |
| T06     | Test object tracking                       | System tracks object movements accurately | System tracks object movements with some lag | ![Fail](https://img.shields.io/badge/Status-Fail-red) | Tracking lag        |
| T07     | Test system response time                  | System responds within specified time     | System responds within specified time   | ![Pass](https://img.shields.io/badge/Status-Pass-green) |                     |
| T08     | Test system accuracy                       | System accurately identifies and locates objects | System accurately identifies and locates objects | ![Pass](https://img.shields.io/badge/Status-Pass-green) |                     |



### Unit Testing

1. First, let's create a helper function to simulate user input and set the servo state:
    ![Unit test change code 1](Insert-Figure-33-URL-here)
2. Next, we will create the test_password() function to test each case:
    ![Unit test change code 2](Insert-Figure-34-URL-here)
3. Modify the process_password() function to return the result instead of printing it:
    ![Unit test change code 3](Insert-Figure-35-URL-here)
4. Finally, add a test function to run all the test cases:
    ![Unit test change code 4](Insert-Figure-36-URL-here)
5. Call the run_tests() function in the setup() function before starting the main loop:
    ![Unit test change code 5](Insert-Figure-37-URL-here)





