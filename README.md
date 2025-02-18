# Homespace Data Acquisition - Capstone for UMass Medical School

Welcome to my capstone project! I focused on creating a **personalized home monitoring system for sleep apnea patients**. Leveraging machine learning, hardware, and web development, I aim to improve treatment plans and enhance patient's quality of life through insightful data analysis.

## Table of Contents
1. [Overview](#overview)
    - [Problem Statement](#problem-statement)
    - [Objective Statement](#objective-statement)
2. [Solution](#solution)
3. [Sleep Apnea Detection System](#sleep-apnea-detection-system)
4. [File Navigation](#file-navigation)
5. [Installing Dependencies](#installing-dependencies)
    - [Arduino Nano 33 BLE Sense board](#arduino-nano-33-ble-sense-board)
    - [Raspberry Pi](#raspberry-pi)
    - [Installing Dependencies on Raspberry Pi](#installing-dependencies-on-raspberry-pi)
    - [Arduino Command Responder Code Structure](#arduino-command-responder-code-structure)
6. [Hardware Setup](#hardware-setup)
    - [Setting Up the Arduino Nano 33 BLE Sense Board](#setting-up-the-arduino-nano-33-ble-sense-board)
    - [Setting Up the Raspberry Pi](#setting-up-the-raspberry-pi)
7. [User Manual](#user-manual)
    - [Running the System](#running-the-system)
    - [Using the System](#using-the-system)
8. [License](#license)

## Overview

Welcome to my UML capstone project at [UMass Chan Medical School](https://www.umassmed.edu/), where I explore the intersection of machine learning, hardware, and web development to create a tailored home monitoring system for individuals affected by sleep apnea. This project's objective is to design a system capable of gathering data from an array of sensors within a custom device, using this data to understand a patient's daily movement patterns and detect sleep apnea episodes. By offering more accurate and personalized treatment plans, this technology enhances the patient's quality of life and provides healthcare professionals with comprehensive insights into the patient's condition. Through this endeavor, I aim to showcase the potential of IoT and TinyML in healthcare and their impact on people's lives. I will utilize a combination of hardware and software to develop a custom system that collects data from multiple sources and employs machine learning models to identify sleep apnea.


### Problem Statement:

There is a lack of objective and quantitative data with regard to homebound patients’ well-being, which results in many patients receiving inadequate support based on their needs. A system that establishes and tracks patterns in a patient’s movement in their home and detects the presence of sleep apnea is needed in order to help medical professionals make more informed decisions for their patients.

### Objective Statement:

The objective is to detect changes in the functional status of homebound patients with neurodegenerative disorders based on their movement around their homes. In addition, this system will detect if the patient suffers from sleep apnea by collecting daily breathing patterns, with the use of algorithms to make inferences based on data, by the end of April 2023.

## Solution

**Sleep Apnea Detection:** Utilizes an Arduino Nano 33 BLE Sense board and a Raspberry Pi as a central data collection hub for sleep detection. The system collects data from various sensors, including temperature, humidity, and color sensors, and analyzes the audio data to determine the number of breaths per minute. Embedded machine learning models, using TinyML technology on the Arduino, recognize specific keywords to control data collection. The Raspberry Pi processes the data and sends it to a MongoDB database for further analysis and storage.

<div align="center">
 
  <img src="https://user-images.githubusercontent.com/113388793/235320926-7c1fa5a8-1555-44fd-a874-1e4abb053c86.png" alt="IMG_9578" width="400">
 
</div>

<div align = 'center'>

 
Raspberry PI 3 Model B (left) and Arduino Nano 33 BLE Sense (right)
 
</div>

<div align="center">

<img src="https://user-images.githubusercontent.com/113388793/235321138-74b15155-ebe4-4229-9888-89c9ad9c4e1c.PNG" >

</div>

<div align = 'center'>

Flowchart for sleep apnea detection - ReDay Z.

</div>

**Machine Learning** (Keyword Spotting Model): The keyword spotting model used in this project is based on TensorFlow Lite Micro, which allows the Arduino to efficiently recognize specific keywords such as "learn" and "stop." The model works by converting the analog audio input into digital form and creating spectrograms using the Fourier transform. Spectrograms are visual representations of the audio frequencies, which are fed into the machine learning model for keyword recognition. The use of TinyML technology enables the model to run on resource-constrained devices like the Arduino Nano 33 BLE Sense, making it suitable for real-time, low-power applications. 

For a fun exercise, let's examine the spectrograms of my room's background noise as well as the spectrograms generated by two Harry Potter spell keywords: "aberto" and "silencio".

<div align="center">
  <table>
    <tr>
      <td align="center">
        <img src="https://user-images.githubusercontent.com/113388793/235321477-3c9f7046-fcac-4673-a856-37f952d52816.png" alt="Image 1" width="350"><br>
        <figcaption>Spectrogram of Background Noise</figcaption>
      </td>
      <td align="center">
        <img src="https://user-images.githubusercontent.com/113388793/235321513-eaaab921-492b-422e-8be6-8e90bd80b17e.png" alt="Image 2" width="350"><br>
        <figcaption>Spectrogram of "Aberto"</figcaption>
      </td>
      <td align="center">
        <img src="https://user-images.githubusercontent.com/113388793/235321536-e11d40a7-4c05-45de-a78c-49eac4bccac9.png" alt="Image 3" width="350"><br>
        <figcaption>Spectrogram of "Silencio"</figcaption>
      </td>
    </tr>
  </table>
</div>

# Sleep Apnea Detection System

This project utilizes an Arduino Nano 33 BLE Sense board to listen for specific voice commands and respond by collecting sensor data. The Arduino board is equipped with a microphone and various sensors, including temperature, humidity, and color sensors. The keyword spotting model is implemented using TensorFlow Lite Micro, which allows the board to recognize specific keywords like "learn" and "stop."

## File Navigation

1. Archive - included in this project serves as a repository for earlier ideas and attempts that, although did not lead to significant progress or success, contributed to the learning process and development of the final solution.

2. Collecting_Data - dedicated to the initial testing and validation of the sensors and other hardware components, ensuring that the project's goals are achievable. This folder contains various code snippets, scripts, and resources designed to test the functionality and reliability of the sensors, as well as to verify their compatibility with the chosen platform.

3. COMMANDER - houses the essential code and resources for the final Arduino hardware and the command responder. This folder serves as the core of the project's functionality, focusing on the integration of the Arduino Nano 33 BLE Sense board and the implementation of the command responder.

4. ML-KeywordSpotting - dedicated to the exploration and evaluation of various machine learning models and trials, with the goal of identifying the most efficient solution for the sleep apnea detection system. This folder contains an assortment of machine learning approaches, algorithms, and techniques that have been tested and refined throughout the project's development process. 

5. ML-LearnStopModel - contains the essential files for the final machine learning model used in the sleep apnea detection system. This folder serves as a streamlined repository for the key components needed to implement the chosen model, making it easy for the project team to integrate it with the rest of the system.

6. RASPBERRYPI - contains the final code for the Raspberry Pi component of the sleep apnea detection system. This folder is specifically dedicated to the data transfer and audio processing scripts required for the Raspberry Pi to effectively communicate with the Arduino and process the collected data. In addition to the core Python scripts for data transfer and audio processing, folder V also contains a README file that provides detailed instructions on how to configure the Raspberry Pi and set up the necessary dependencies for the system to function smoothly. 

## Installing Dependencies

#### Arduino Nano 33 BLE Sense board
- TensorFlow Lite Micro library
- Arduino_HTS221 library
- Arduino_APDS9960 library
- PDM library

#### Raspberry Pi
- Python
- NumPy
- SciPy
- MongoDB

### Installing Dependencies on Raspberry Pi

1. Update your Raspberry Pi's package list and installing the dependencies by running the following commands:

```bash
sudo apt update

sudo apt install python3 python3-pip

sudo apt install python3-numpy

sudo apt install python3-scipy

sudo apt install -y mongodb
```

### Arduino Command Responder Code Structure

The `arduino_command_responder.cpp` file contains the main code for the Arduino command responder, which consists of the following sections:

1. **Header includes**: The required libraries for the sensors, TensorFlow Lite Micro, and other necessary components are included at the beginning of the file.

2. **Global variables and functions**: Variables and functions are declared to handle data collection, sensor initialization, and data transmission.

3. **Command responder function**: The `RespondToCommand` function is responsible for processing the detected keywords, initializing sensors, and enabling/disabling data collection based on the voice command.

4. **Main setup and loop**: The main `setup()` and `loop()` functions are used to set up the hardware and call the TensorFlow Lite Micro library to listen for keywords and respond accordingly.

Remember to install the necessary libraries and set up the hardware according to the provided instructions to ensure the proper functioning of the Arduino command responder.

## Hardware Setup

### Setting Up the Arduino Nano 33 BLE Sense Board

1. Install the Arduino IDE from the official website: https://www.arduino.cc/en/software

2. Connect the Arduino Nano 33 BLE Sense board to your computer using a USB cable.

3. Open the Arduino IDE, and navigate to `Tools > Board > Boards Manager`. Search for "Arduino Mbed OS Nano Boards" and install the package.

4. Go to `Tools > Board` and select "Arduino Nano 33 BLE."

5. Install the required libraries:
    - TensorFlow Lite Micro library: Navigate to `Sketch > Include Library > Manage Libraries`, search for "TensorFlow Lite Micro" and install the latest version.
    - Arduino_HTS221 library: Search for "Arduino_HTS221" and install the latest version.
    - Arduino_APDS9960 library: Search for "Arduino_APDS9960" and install the latest version.
    - PDM library: Search for "PDM" and install the latest version.

6. Upload the `arduino_command_responder.cpp` file to the Arduino board by clicking the `Upload` button in the Arduino IDE.

### Setting Up the Raspberry Pi

1. Install Raspberry Pi OS on your Raspberry Pi and set up the necessary peripherals (keyboard, mouse, and monitor).

2. Connect the Raspberry Pi to the internet using an Ethernet cable or by configuring Wi-Fi.

3. Install Python and necessary libraries (such as NumPy, SciPy, and MongoDB) on the Raspberry Pi.

4. Connect the Arduino Nano 33 BLE Sense board to the Raspberry Pi using a USB cable.

5. Run the Python script on the Raspberry Pi to start collecting and processing data from the Arduino board.

## User Manual

### Running the System
#### Connect the Arduino to the Raspberry Pi
- Use a micro-USB cable to connect the Arduino Nano 33 BLE Sense to one of the Raspberry Pi's USB ports.
5.3. Log in to the Raspberry Pi
- Select the **Homespace Capstone user** to access the necessary content
- Log into the user account with the password: *homespace123*
#### Connect your Raspberry Pi to a Wi-Fi network
- Power on your Raspberry Pi and wait for it to boot into the Raspberry Pi OS desktop environment.
- In the top-right corner of the screen, you'll find the Wi-Fi icon (it looks like an antenna with radio waves). Click on the Wi-Fi icon to open the Wi-Fi menu.
- A list of available Wi-Fi networks will be displayed. Find your Wi-Fi network's SSID (name) in the list and click on it.
- A window will pop up asking for the Wi-Fi password. Enter the password for your Wi-Fi network and click on the "OK" button.
- Your Raspberry Pi will now attempt to connect to the Wi-Fi network. If the connection is successful, the Wi-Fi icon will change to indicate the connection strength, and you'll see a message saying that the connection has been established.
- To confirm that your Raspberry Pi is connected to the internet, you can open a terminal window and run the following command:
```
ping -c 4 google.com
```
- This command will send four packets to Google's server. If the connection is successful, you'll see responses from the server, indicating that your Raspberry Pi is connected to the internet.
- If you want to view the IP address assigned to your Raspberry Pi on the Wi-Fi network, you can run the following command in the terminal:
```
ifconfig wlan0
```
- Look for the "inet" line, and you'll see the IP address next to it.
#### Start the Python script
- Open a terminal window on the Raspberry Pi and navigate to the directory containing the Python script (e.g., the desktop).
- Run the Python script using the following command:
  ```
  python3 run.py
  ```
### Using the System
- With the Python script running on the Raspberry Pi, the system is now listening for the keywords "learn" and "stop."
- Say the keyword "learn" to start data collection. The Arduino will collect data from the temperature, humidity, color sensors, and the microphone.
- The Raspberry Pi processes the data, including analyzing the audio to determine breaths per minute, and stores the data in a MongoDB database.
- Say the keyword "stop" to stop data collection.

## License
I have cited open source code to their authors. The following sections of this project are my own, but free to use under the [MIT license](https://github.com/redayzarra/sleep-apnea-detection/blob/master/LICENSE).

1. Machine Learning Models 
2. Arduino command responder
3. Raspberry PI data transfer code
4. Raspberry PI and MongoDB connection code
5. Breath Detection code (Raspberry PI script)
