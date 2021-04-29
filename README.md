# Elevator Control
## ITI8531 Software Synthesis and Verification
### Mike Camara

# Introduction

I have created an elevator control system with an elevator manager orchestrating the different operational and functional components except for the user interactions. For simplicity, we restrict our analysis to 4 floors. 

# Functional Requirements

**✅  The Elevator Manager has the following elevator states {inService, floorStop, noOperations, inMaintenance}.**

**✅  When a elevatorCall or floorCall is requested it should be registered in the service queue.**

**✅  Impose priority to call requests.**

**✅  When the call is received, assign a direction (forward or reverse) and service the call in the queue.** 

**✅  The lift should not operate if the user selects the same floor.** 

**✅  Execute the task queue and provide the service to the floor.**

**✅  The motor control should latch the Direction and Enable the operation.**  

**✅  The sensor inputs should cut out the queue when the elevator reaches the floor and load the queue with a new value. It should service the requests coming in descending and ascending order while moving up and down, i.e., if there is a request from floor 2 after floor 3, still floor 2 service requests can be handled while going up.**

**✅  The above task should be repeated for Elevator Control command as well.**  

**✅  PickUp and dropOff operations, de-register the current floor from the queue, set the operating mode to be Idle and doorOpen status to be 1.**  

**✅  Update the elevator status after this operation and continue with the service queue.** 

# Safety Requirements

**✅  During dropping and picking operations keep the elevator stopped.**

**✅  For servicing any floor control, the elevator door needs to be closed, the floor button is depressed, no overload or any other stopping operations initiated. Once the door opens the status of the lift should be brought to floor-stop.**

**✅  Door closing is achieved after this either by depressing the door close button or when the user selects the floor (a timing will be included later here) and there are no warnings of users coming in from a motion detector sensor.**  

# Comfort Requirements

**✅  Floor panel should have the following up and down button is depressed by the user, the up or down LED should glow. They can both glow together and the complimentary operations should be cut-out on reaching the floor.** 

**✅  In the elevatorPanel the floorNumber should be displayed.** 

**✅  Update the car-display on the floor when a button is depressed.** 

**✅  Based on the assigned direction show the Up and Down display in the elevatorDisplay and floorDisplay.** 


# Verification
I used the Verification server to simulate the internal behavior of components (states, transitions, transition conditions, and updates)  and verify them against the requirements.

<img width="471" alt="verificationsScreenshot" src="https://user-images.githubusercontent.com/8085864/116611124-af5b6100-a93e-11eb-8937-757c7474d089.PNG">

# Architecture design
First I extracted the components from requirements and then I distinguished them into active and passive components.
The active components such as Elevator, Door, Buttons, and Elevator Managers have their own behavior.
Using the UPPAAL Graphical user interface I have specified the internal behavior of components and interfaces including the synchronization and data links between components and adding timing specification to the behavior (timed automata). 


# System Screenshots

<img width="524" alt="buttonsScreenshot" src="https://user-images.githubusercontent.com/8085864/116611107-abc7da00-a93e-11eb-9eb0-7c6b5550e2ea.PNG">
<img width="459" alt="dataScreenshot" src="https://user-images.githubusercontent.com/8085864/116611118-ad919d80-a93e-11eb-85aa-6d3daa8059ed.png">
<img width="515" alt="doorElevatorScreenshot" src="https://user-images.githubusercontent.com/8085864/116611121-aec2ca80-a93e-11eb-8f20-77ce87459e3b.PNG">




