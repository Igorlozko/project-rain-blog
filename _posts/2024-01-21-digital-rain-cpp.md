---
layout: post
title: A Project in Modern C++
tags: cpp coding project
categories: demo
---
## Introduction

Digital rain is a visual effect of numbers and characters moving from top to bottom of the screen simulating a rainfall. I’ll discuss the development process, problem solving and technical conclusions that I came across during this project. The end goal of this project is to achieve a matrix effect of numbers and charracters falling down the console. Planning, design and technologies like algorithims will be used to achieve this effect.

### Project Demo
<img src="https://raw.githubusercontent.com/igorlozko/project-rain-blog/main/docs/assets/images/Picture1.png" width="800" height="400">

## Design and Test

### Planning 

I adopted an object-oriented approach to encapsulate the Digital Rain simulation's components, including the grid layout, raindrop behaviour, and rendering mechanism. I designed classes to represent the simulation and individual raindrops, ensuring modularity and extensibility. This involved defining clear interfaces and data structures to facilitate seamless interaction between components.
expand more on this 

### Project goals 
- Green characters and letters falling from top to bottom
- Charcters must be random and must change as they fall mimicing the rainfall droplets which dont stay the same chape as they fall as they are shaped by the wind.
- Using algorithims
- Clearing and rendering project

## Algorithm

### Algorithmic Approach
The core algorithm behind the Digital Rain simulation revolves around the management of raindrop descent and rendering. Raindrops are randomly generated at the top of the screen and gradually descend while leaving a trail of characters behind. The algorithm ensures smooth descent and prevents overlap between raindrops, resulting in a visually appealing effect.

<img src="https://raw.githubusercontent.com/igorlozko/project-rain-blog/main/docs/assets/images/Picture2.png" width="600" height="300">

### Object-Oriented Programming
Object-oriented programming (OOP) played a crucial role in structuring the Digital Rain simulation codebase. Classes such as Digital Rain and Raindrop were designed to encapsulate the simulation's logic and data. This modular approach enabled easier maintenance, extensibility, and code reuse. Each class has an interface, promoting clear communication between different components of the simulation.

## Sustainability

A key focus throughout the development process was sustainability. This involved writing clean, maintainable code that could withstand future changes and enhancements. Comments and documentation were added where necessary to improve code readability and understanding.

<img src="https://raw.githubusercontent.com/igorlozko/project-rain-blog/main/docs/assets/images/Picture3.png" width="900" height="200">

## New Technologies 

One of the new technologies I explored was the ANSI escape codes for terminal manipulation. This allowed me to control the cursor movement, text colour and formatting enhancing the visual aspect of digital rain. This can be seen below 

<img src="https://raw.githubusercontent.com/igorlozko/project-rain-blog/main/docs/assets/images/Picture4.png" width="900" height="200">

Multithreading with std:thread explored multithreading the std::thread library. It was employed to achieve a concurrent execution of the digital rain simulation alongside the main program flow, ensuring smooth animations rendering without blocking the user input or the operation.

## Problem Solving 

Several problem-solving initiatives were undertaken to overcome challenges encountered during development. Optimal raindrop rendering, preventing flickering and overlap, required innovative solutions. The introduction of vertical displacement tracking, and manipulation of ANSI escape codes played a pivotal role in achieving smooth raindrop descent.

Flashing of the console a flickering effect was solved by rendering

## Modern C++

## Code Explained 

### Digital Rain main file

<img src="https://raw.githubusercontent.com/igorlozko/project-rain-blog/main/docs/assets/images/Picture6.png" width="800" height="400">

I include the necessary header files iostream for input and output and DigitalRain header

Main initializes the parameters such as screenWidth, screenHeight, raindropFrequency, asciiRangeStart, asciiRangeEnd

Digital rain obkect line 14 instance of the digital rain class created with specific parametes 
responsible for generating and rendering the digital rain effect

start method runs indefinetly controlled byt he while(true) updating constantly 


### Digital Rain .h file

<img src="https://raw.githubusercontent.com/igorlozko/project-rain-blog/main/docs/assets/images/Picture7.png" width="600" height="600">

   I include the necessary headers vector for using vector and other 

   Digital rain class holds the functionality of the digital rain effect
   Private memebrs: screenWidth: Holds the width of the screen.
                    screenHeight: Holds the height of the screen.
                    raindropFrequency: Determines the frequency of raindrops.
                    asciiRangeStart: Specifies the starting ASCII value for generating random characters.
                    asciiRangeEnd: Specifies the ending ASCII value for generating random characters.
                    grid: Represents the current state of the screen as a grid of characters.
                    nextGrid: Represents the next state of the screen after raindrops have fallen.
                    verticalDisplacement: Represents the vertical displacement of raindrops, which is currently unused in the provided code.
    Public methods: DigitalRain(int width, int height, int frequency, int start, int end): Constructor that initializes the DigitalRain object with the specified parameters.
                    start(): Method that starts the digital rain effect by continuously updating the state of the screen and rendering the raindrops


### Digital Rain cpp file

<img src="https://raw.githubusercontent.com/igorlozko/project-rain-blog/main/docs/assets/images/Picture5.png" width="600" height="600">

    Implemintation of the digital rain and definitions for the constructor and the start method.

    Constructor:

    The constructor initializes the DigitalRain object with the specified parameters:
        1. Width, height: Sets the screen dimensions.
        2. Frequency: Determines the frequency of raindrops.
        3. Start, end: Specifies the range of ASCII values for generating random characters.
        
    It initializes member variables:
        1. ScreenWidth, screenHeight: Set to the provided width and height.
        2. GaindropFrequency, asciiRangeStart, asciiRangeEnd: Set to the provided values.
        3. Grid: Initializes the grid vector with height rows and width columns, filled with spaces.
        4. NextGrid: Initializes the nextGrid vector with the same size as grid, filled with spaces.
        5. VerticalDisplacement: Initializes the verticalDisplacement vector with the same size as grid, filled with zeros.
        
    Additionally, it seeds the random number generator using the current time.

    Start Method:

    This method starts the digital rain effect by continuously updating the state of the screen and rendering the raindrops.
    It runs an infinite loop where each iteration represents a frame of the digital rain animation.
    Within the loop:
        It updates the nextGrid with new raindrops based on the specified frequency.
        Renders the raindrops on the screen without clearing it, allowing for the raindrops to accumulate over time.
        Swaps the grid and nextGrid.
        Moves raindrops down gradually and decreases their vertical displacement.
        Clears the top row of the nextGrid and resets the vertical displacement for the newly spawned raindrops.
        Sleeps for a short duration to control the speed of the rain animation.

    
    
    Algorithim used in digitalrain

    1. Initialization:

    The method starts with an infinite loop, representing continuous animation frames.
    In each iteration of the loop:
    The nextGrid is updated with new raindrops based on the specified frequency.
    Vertical displacement for each raindrop is reset.
    
    2. Rendering:

    The raindrops are rendered onto the screen without clearing it, allowing for accumulation over time.
    For each cell in the grid:
    If a raindrop is present (nextGrid[y][x] != ' '):
    The cursor is moved to the position (x, y + verticalDisplacement[y][x]) to ensure raindrops fall vertically.
    The raindrop character, preceded by spaces, is printed in green color using ANSI escape codes.
    The vertical displacement for the raindrop is incremented.

    3. Update:

    The grid and nextGrid are swapped, updating the raindrop positions.
    Raindrops are moved down gradually by copying them from grid to nextGrid and reducing their vertical displacement.
    The top row of nextGrid and associated vertical displacements are cleared to prepare for new raindrops.

    4. Animation Control:

    A short delay is introduced using std::this_thread::sleep_for to control the speed of the rain animation.

    Overall, this algorithm continuously updates and renders the raindrops, creating a digital rain effect where characters 
    fall from the top of the screen to the bottom, accumulating over time. The use of vertical displacement ensures that raindrops 
    fall vertically without overlapping, creating a visually appealing animation.
