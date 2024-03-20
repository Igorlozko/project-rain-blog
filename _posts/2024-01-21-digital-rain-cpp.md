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

### Design Overview

The DigitalRain class is designed to simulate a digital rain effect similar to the one seen in "The Matrix" movie. It utilizes a grid-based approach to represent the characters falling down the screen. The design includes the following key components:

**Grid Representation:** The rain effect is modeled using a grid, where each cell corresponds to a character position on the screen. The grid is represented using a two-dimensional vector of characters.

**Random Raindrops Generation:** Raindrops are randomly generated at the top of the screen with a specified frequency. When a raindrop is generated, a random character from a specified ASCII range is assigned to it.

**Vertical Displacement:** Each raindrop has a vertical displacement value, which determines how far down the screen it has moved. This allows for the simulation of raindrops falling at different speeds.

**Rendering and Animation:** The raindrops are rendered on the screen using ANSI escape codes to control the cursor position and color. The animation is achieved by continuously updating the grid and shifting characters downward.

### Planning 

I adopted an object-oriented approach to encapsulate the Digital Rain simulation's components, including the grid layout, raindrop behaviour, and rendering mechanism. I designed classes to represent the simulation and individual raindrops, ensuring modularity and extensibility. This involved defining clear interfaces and data structures to facilitate seamless interaction between components.

### Project goals 
- Green characters and letters falling from top to bottom
- Charcters must be random and must change as they fall mimicing the rainfall droplets which dont stay the same chape as they fall as they are shaped by the wind.
- Using algorithims
- Clearing and rendering project

## Algorithm

### Algorithmic Approach
The core algorithm behind the Digital Rain simulation revolves around the management of raindrop descent and rendering. Raindrops are randomly generated at the top of the screen and gradually descend while leaving a trail of characters behind. The algorithm ensures smooth descent and prevents overlap between raindrops, resulting in a visually appealing effect.

**The DigitalRain class employs several algorithms to achieve the desired digital rain effect:**

**Random Raindrop Generation:** The algorithm generates raindrops randomly at the top of the screen with a specified frequency. It uses the rand() function to generate random numbers and assigns a random character from the specified ASCII range to each raindrop.

**Grid Update:** The algorithm updates the grid to move raindrops downward and clear the top row. It shifts characters downward in the grid, updates the vertical displacement values, and clears the top row to simulate new raindrops entering the screen.

**Rendering and Animation:** The algorithm renders the raindrops on the screen using ANSI escape codes to control cursor position and color. It iterates over the grid, adjusts the cursor position based on the vertical displacement of each raindrop, and prints characters with appropriate color codes.

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

**The DigitalRain class addresses several challenges to achieve the digital rain effect:**

**Efficient Raindrop Generation:** To generate raindrops randomly at the top of the screen, the class must efficiently select random positions and characters. The algorithm uses the rand() function and appropriate logic to achieve this while maintaining performance.

**Smooth Animation:** The class must ensure that the animation remains smooth even when simulating a large number of raindrops falling simultaneously. This requires careful management of grid updates and rendering to minimize flickering and lag.

**Correct Rendering:** The class must accurately render raindrops on the screen and handle cases where raindrops overlap or characters collide. This requires precise control over cursor position and character colors to produce a visually appealing effect.

Flashing of the console a flickering effect was solved by rendering

## Modern C++

Modern C++" encapsulates a contemporary approach to software development using the C++ programming language. Embracing the evolution of the language, Modern C++ emphasizes leveraging the latest features and best practices introduced in newer standards, such as C++11 and beyond. 

This approach advocates for writing code that is not only efficient and performant but also expressive, readable, and maintainable. By incorporating features like smart pointers, lambda expressions, range-based loops, and type inference, we can streamline their codebase while enhancing its clarity and robustness. 

In this project solutions that efficiently manage memory, utilize object-oriented design principles, and potentially exploit concurrency for optimal performance. 

**The DigitalRain class leverages modern C++ features and techniques to enhance its functionality and readability:**

**Smart Pointers:** While the code doesn't explicitly use smart pointers, they could be employed to manage memory more efficiently, especially if dynamic memory allocation is involved.

**Standard Library:** The class utilizes standard C++ library components such as vectors, time functions, and threading utilities to implement its functionality.

**Concurrency:** Although not utilized in this specific implementation, modern C++ concurrency features such as std::thread could be employed to improve performance, especially in systems with multiple cores.

**RAII:** Resource Acquisition Is Initialization (RAII) is implicitly used in the class through the initialization of member variables and automatic resource cleanup upon object destruction.

**Type Inference:** The code utilizes explicit type declarations for variables and parameters, but type inference (e.g., auto) could be used to improve code readability in certain contexts.

## Code Explained 

### Digital Rain main file

<img src="https://raw.githubusercontent.com/igorlozko/project-rain-blog/main/docs/assets/images/Picture6.png" width="800" height="400">

I include the necessary header files iostream for input and output and DigitalRain header

Main initializes the parameters such as screenWidth, screenHeight, raindropFrequency, asciiRangeStart, asciiRangeEnd

Digital rain object instance of the digital rain class created with specific parametes 
responsible for generating and rendering the digital rain effect

start method runs indefinetly controlled by the while(true) updating constantly.


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
