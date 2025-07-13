# AI-Mouse

---

#  Gesture-Controlled System Interface

## Overview

This project implements a real-time hand gesture recognition system using a webcam to control system functionalities such as:

* Mouse movement and clicks
* Volume and brightness control
* Scrolling (horizontal/vertical)
* Screenshot capture

The system uses **MediaPipe**, **OpenCV**, **PyAutoGUI**, **PyCaw**, and other libraries for gesture detection, hand tracking, and interacting with the system hardware (audio, brightness, mouse, etc.).

---

##  Features

* 🖱 **Mouse Control**:

  * Move cursor with "V" gesture
  * Left-click using "Mid" gesture
  * Right-click with "Index" gesture
  * Double-click with "Two Finger Closed"
  * Drag with "Fist" gesture

*  **System Volume & Brightness Control**:

  * Use **"Pinch Major"** gesture to increase/decrease volume or screen brightness depending on gesture direction.

*  **Scrolling**:

  * Use **"Pinch Minor"** gesture to scroll horizontally or vertically.

*  **Screenshot Functionality**:

  * Show a "Fist" gesture with your **non-dominant hand** to instantly take a screenshot.

---

##  Tech Stack

| Component                     | Purpose                              |
| ----------------------------- | ------------------------------------ |
| **Python**                    | Programming language                 |
| **MediaPipe**                 | Hand detection and tracking          |
| **OpenCV**                    | Camera and image processing          |
| **PyAutoGUI**                 | GUI automation (mouse & keyboard)    |
| **PyCaw**                     | System volume control                |
| **screen-brightness-control** | Screen brightness adjustment         |
| **Google Protobuf**           | Handling Mediapipe’s landmark output |
-
##  How It Works

* Opens the webcam feed and detects hands using **MediaPipe**.
* Classifies hand gestures (e.g., V, Fist, Index, Pinch).
* Executes mapped system commands based on gesture:

  * Cursor movement with velocity dampening.
  * Dynamic scrolling.
  * Brightness/volume change with pinch distance.
  * Screenshot naming using timestamp.

Each gesture is mapped with logic for gesture recognition robustness and smoothness.

---

##  Gesture Mapping Summary

| Gesture             | Action                              |
| ------------------- | ----------------------------------- |
| V (First 2 Fingers) | Mouse movement                      |
| Fist                | Mouse drag / Screenshot (left hand) |
| Mid Finger          | Left click                          |
| Index Finger        | Right click                         |
| Two Fingers Closed  | Double click                        |
| Pinch Major         | Volume / Brightness control         |
| Pinch Minor         | Scrolling                           |
| Palm                | Neutral (Idle)                      |

---


##  Demo



|  **Gesture**                       |  **Image**             | **Description**                                                                                                                                                                                                                                                                            |
| ------------------------------------ | ------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Palm (Neutral Gesture)**           |  <img width="954" height="573" alt="image" src="https://github.com/user-attachments/assets/d3359569-805f-4613-a1d3-8ee044c46daf" />     | The palm gesture represents an open hand, with all fingers extended outward. It is the default "neutral" state, used to prevent false triggers and stabilize transitions between other gestures. It helps reset the system and allows the user to rest their hand without unintended actions. |
| **Left Click (Mid Gesture)**         |<img width="943" height="695" alt="image" src="https://github.com/user-attachments/assets/39262570-afed-4528-9a03-f962edf39b7a" />    | Extend the middle finger while keeping others curled. Triggers a **left mouse click**. Recognized only when a cursor movement (V Gesture) precedes it to avoid misfires.                                                                                                                      |
| **Right Click (Index Gesture)**      | <img width="750" height="632" alt="image" src="https://github.com/user-attachments/assets/48233f6c-6b1c-4a87-8b35-b1324ad37983" />      | Extend only the index finger while curling the rest. Triggers a **right-click** action, useful for opening context menus or secondary options. Mimics natural pointing.                                                                                                                       |
| **Drag and Drop (Fist Gesture)**     | <img width="689" height="634" alt="image" src="https://github.com/user-attachments/assets/ae10a884-5a84-45e6-a135-e36a9aec5936" />    | Close all fingers into a fist to simulate **click-and-hold**. Move your hand to drag items. Releasing the fist drops the item. Ideal for file movement or drawing interactions.                                                                                                               |
| **Double Click (Two Finger Closed)** | <img width="817" height="617" alt="image" src="https://github.com/user-attachments/assets/8eeb8aaa-f216-4050-8062-3fb190fcf202" />  | Extend the index and middle fingers close together. Simulates a **double click**—commonly used for opening apps/files. The gesture ensures proximity (Z-axis) for accuracy.                                                                                                                   |
| **V Gesture (Mouse Movement)**       | <img width="644" height="584" alt="image" src="https://github.com/user-attachments/assets/7246f1e9-4af8-4e41-9faa-c9bf0df9a543" />        | Extend the index and middle fingers in a "V" shape. Moves the **mouse cursor** across the screen based on your hand motion. It offers high accuracy and smooth control.                                                                                                                       |
| **Scroll (Pinch Minor)**             |<img width="834" height="627" alt="image" src="https://github.com/user-attachments/assets/adc5a4a9-54b3-4cb1-8895-aac0029f3c1f" />      | Pinch the thumb and index finger of the **non-dominant hand**. Move your hand vertically or horizontally to simulate **scrolling** like a mouse wheel. Great for documents/webpages.                                                                                                          |
| **Volume/Brightness (Pinch Major)**  | <img width="834" height="627" alt="image" src="https://github.com/user-attachments/assets/adc5a4a9-54b3-4cb1-8895-aac0029f3c1f" />       | Pinch thumb and index finger of the **dominant hand**. Move **up/down** to control **brightness**, and **left/right** for **volume**. Intuitive gesture that mimics knob turning.                                                                                                             |
| **Screenshot (Left-Hand Fist)**      |<img width="659" height="728" alt="image" src="https://github.com/user-attachments/assets/52cd1514-cb66-4813-afe4-05ed8d5ed9a4" /> | Make a **fist with your left hand**. Instantly captures a screenshot of the screen and saves it with a timestamp. Fast, accessible, and useful for hands-free capturing.                                                                                                                      |






