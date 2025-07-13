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

## PALM GESTURE:       
<img width="954" height="573" alt="image" src="https://github.com/user-attachments/assets/d3359569-805f-4613-a1d3-8ee044c46daf" />
---
The palm gesture represents an open hand, with all fingers extended outward. It is typically used as the default state when no specific action is performed. The system interprets this as a neutral position, which is helpful in stabilizing gestures and avoiding unintentional actions. This gesture allows the system to detect transitions into other gestures while ensuring a smooth and accurate response. When no specific command is detected, the palm gesture maintains the status quo, preventing false triggers. It is particularly useful for resetting the system between actions. Users can rest their hands in this position when not interacting with the system. By being an open gesture, it minimizes noise from other finger movements. Its simplicity makes it an ideal "ready" state for gesture recognition. 
---

## LEFT CLICK(INDEX FINGER):
<img width="943" height="695" alt="image" src="https://github.com/user-attachments/assets/39262570-afed-4528-9a03-f962edf39b7a" />
---
The fist gesture is made by closing all fingers into the palm. In this system, it is primarily used for dragging objects on the screen, similar to holding down the left mouse button. Once recognized, it activates a "grab" mode, allowing users to move items across the screen by moving their hand. Releasing the fist disengages the action, akin to releasing the mouse button. This gesture is intuitive, as it mimics the natural action of holding an object. It’s also useful for tasks like drawing or dragging files and folders. The simplicity of the motion makes it reliable for consistent detection. By combining the fist gesture with cursor positioning, the system achieves precise control. This gesture offers a tactile and engaging way to interact with the interface

## RIGHT CLICK:
<img width="750" height="632" alt="image" src="https://github.com/user-attachments/assets/48233f6c-6b1c-4a87-8b35-b1324ad37983" />
---
The index gesture involves extending only the index finger while curling the rest. It triggers the right-click action on a virtual mouse, allowing users to access context menus or secondary actions. This gesture is mapped to a commonly used function, making it convenient for tasks like opening properties or accessing additional options. The system interprets this gesture only when performed distinctly to avoid accidental commands. It is especially helpful for navigating interfaces where right-clicking is frequently required. The gesture mimics a natural pointing action, enhancing its intuitiveness. Users find this gesture straightforward and easy to perform. By reducing the need for physical peripherals, it streamlines interaction. This implementation bridges the gap between physical mouse functionality and virtual gestures effectively.

## DRAG AND DROP:
<img width="689" height="634" alt="image" src="https://github.com/user-attachments/assets/ae10a884-5a84-45e6-a135-e36a9aec5936" />
---
Drag and drop is a gesture-based interaction that enables users to select and move objects within a digital interface intuitively. To initiate this action, the user typically performs a fist gesture, symbolizing a "grab." Once the system recognizes the gesture, the selected object adheres to the cursor's position, allowing it to be moved freely across the screen. This functionality is particularly useful for organizing files, arranging elements in design software, or manipulating items in gaming interfaces. The movement of the object is synchronized with the user’s hand motion, ensuring smooth and precise placement. Upon releasing the fist gesture, the system interprets this as a "drop" command, placing the object in the desired location. This method mimics real-world physical interactions, making it highly intuitive and easy to learn. By eliminating the need for a traditional mouse or keyboard, drag and drop enhances accessibility and flexibility. The system is designed to minimize detection errors, ensuring reliable performance even in dynamic environments. This feature adds a layer of convenience and efficiency, making digital interactions more engaging and user-friendly. 

## DOUBLE CLICK:
<img width="817" height="617" alt="image" src="https://github.com/user-attachments/assets/8eeb8aaa-f216-4050-8062-3fb190fcf202" />
---
In this gesture, the index and middle fingers are extended and brought close together while the rest remain curled. It simulates a double-click action, commonly used for opening files or applications. The system recognizes the gesture when the fingers are in proximity and detects the z-axis difference to ensure accuracy. This gesture enables rapid access to content without needing a physical mouse. It is particularly useful in environments requiring frequent opening of applications or documents. The closed position of the two fingers adds reliability by minimizing false positives. Its compact design makes it easy to transition into from other gestures. This gesture provides a fast and efficient way to navigate digital content intuitively.

## VOLUME/SCREEN BRIGHTNESS CONTROL:
<img width="995" height="600" alt="image" src="https://github.com/user-attachments/assets/e5e5ed4b-fa03-43de-b386-971cee9dd0b2" />
---
The pinch major gesture is performed by bringing the thumb and index finger of the dominant hand close together. It is used for adjusting system brightness and volume levels. Moving the pinch up or down modifies the brightness, while moving it sideways controls volume. This gesture leverages fine motor control for precise adjustments. The pinch action feels natural, as it mimics actions like turning a knob or pinching an object. By associating the gesture with two critical system functions, it enhances usability. It also provides visual feedback for real-time adjustments, making it intuitive. The system ensures accuracy by distinguishing between minor movements and deliberate actions. This gesture adds a layer of control and customization to the interaction.

## V GESTURE(MOVE MOUSE):
<img width="644" height="584" alt="image" src="https://github.com/user-attachments/assets/7246f1e9-4af8-4e41-9faa-c9bf0df9a543" />
---
The V gesture is performed by extending the index and middle fingers in a "V" shape while separating them slightly. It is used for moving the mouse cursor across the screen. Users can control the cursor position by moving their hand in the desired direction. The gesture offers precise control, essential for tasks like selecting text or clicking small buttons. Its distinct shape reduces detection errors, ensuring consistent performance. The natural pointing action of the fingers makes it intuitive and user-friendly. By combining this gesture with others, the system provides a complete suite of mouse functionalities. It is a versatile tool for navigating digital environments without physical peripherals. This gesture forms the backbone of cursor-based interactions.

## SCROLLING:
<img width="834" height="627" alt="image" src="https://github.com/user-attachments/assets/adc5a4a9-54b3-4cb1-8895-aac0029f3c1f" />
---
This gesture involves bringing the thumb and index finger of the non-dominant hand close together. It enables vertical and horizontal scrolling, replicating the functionality of a mouse wheel. Users can scroll through web pages, documents, or lists by moving their hand up, down, left, or right. The pinch action creates a tactile feel, improving user engagement. The system detects the gesture and applies smooth scrolling, providing a seamless experience. It eliminates the need for a physical scroll wheel, offering a more ergonomic alternative. By incorporating this gesture, the system adds flexibility for navigation. It is particularly useful for tasks involving extensive reading or browsing. The simplicity of the motion makes it easy to adopt.

## SCREENSHOT:
<img width="659" height="728" alt="image" src="https://github.com/user-attachments/assets/52cd1514-cb66-4813-afe4-05ed8d5ed9a4" />
---
The screenshot gesture is an intuitive, gesture-based command that allows users to capture the current screen with a simple hand movement. To activate the screenshot function, users perform a fist gesture with their left hand. Once detected, the system triggers a screenshot, capturing everything displayed on the screen at that moment. The process is seamless and eliminates the need for traditional keyboard shortcuts or mouse clicks. This gesture is particularly useful for hands-free interactions, providing a quicker alternative to manual screenshot methods. After the gesture is recognized, the screenshot is automatically saved with a timestamp in the filename, making it easy for users to identify and organize their captures. The gesture simplifies the process for users with mobility challenges or those who prefer gesture control over more traditional input devices. It also ensures that users can effortlessly capture images while interacting with other tasks on their computer. The screenshot gesture provides both convenience and efficiency, making it ideal for capturing important information, images, or errors during presentations and workflows. Overall, it offers a user-friendly, gesture-controlled alternative for digital screen capture






