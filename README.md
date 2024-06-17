In this ongoing software project to create a ride allocation system, I am currently working on refining the object-oriented design established in Stage 1. This stage focuses on developing the core classes necessary for the system's functionality.

The `Rides` class serves as the blueprint for individual rides, capturing crucial details such as starting and ending locations within the world grid (`rowOfStartInt`, `colOfStartInt`, `rowOfFinishInt`, `colOfFinishInt`), and time constraints (`earliestStart` and `latestFinish`). This ensures timely pickups and arrivals. The class includes a constructor for setting these attributes, getter methods for easy data access, and a `toString` method for a clear, space-separated overview of ride information. This structured approach is fundamental to developing a dynamic ride allocation system in later stages.

The `Cars` class represents each vehicle digitally. It tracks a car's capacity through the `numOfRides` attribute, indicating how many rides are assigned to it, and uses an `ArrayList` to store the unique IDs of these rides. The `getNumOfRides` method retrieves the number of rides assigned to a car, while the `getId` method returns a specific ride ID based on its index. The `toString` method provides a summary of the car's data, including the number of assigned rides and their IDs.

The `WorldAndRides` class stores details about the world (number of rows, columns, cars) and all requested rides. It reads data from a file and keeps track of everything in separate attributes and an `ArrayList` of `Rides` objects. This class offers methods to access specific details like the number of rides or the world's dimensions. 

The `Allocation` class designates rides to cars, reading files to determine which rides are assigned to each car. It uses an `ArrayList` named `cars` to store `Cars` objects, with each `Cars` object tracking the number of assigned rides (`numOfRides`) and the specific ride IDs stored in another `ArrayList` named `carID`. The `Allocation` class thus transforms allocation data into a structured format that connects the world information with car assignments.

To organise the ride allocations, I implemented the `Simulation` class, which acts as the conductor. It gathers world data (size, cars) and car assignments from files. For each car, it uses methods like `getNumOfRides` and `getId` from the `Allocation` class to access assigned rides. Methods from the `Rides` class are then used to calculate distances from starting points and check if the car can begin on time. Factors like wait time, ride length, and potential bonus points are considered using methods such as `getEarliestStart`. After simulating all cars and rides, the `Simulation` class calculates a final score.

In Stage 2, I am enhancing the `Allocation` class, focusing on assigning rides to cars. This involves creating separate lists (`carsList` and `ridesList`) to store `Cars` and `Rides` objects, respectively. Leveraging file-reading logic from Stage 1, I populate the `ridesList` with ride details and determine the total number of cars (`numOfCars`) from the file's first line. The `allocate` method iterates through both the car and ride lists, assigning rides to cars using methods like `giveRideToCar` from the `Cars` class. The `printAllocation` method, unchanged from Stage 1, prints the number of assigned rides and a list of ride IDs for each car.

Despite successfully passing all other tests, my program encountered an `IndexOutOfBoundsException` error, resulting in a zero score. This error occurred on line 21 of the `WorldAndRides.java` file within the `getRide` method. I am currently addressing this issue by reviewing the logic and calculations to ensure the index falls within the collection's bounds. Additionally, I am implementing proper checks and potential exception handling to manage errors.

Reflecting on my journey through this project, while I aced Stage 1, conquering file parsing and car data storage, Stage 2's car assignment logic has been the most challenging, particularly due to sorting algorithms. This hurdle ultimately prevented me from completing Stage 3. To tackle these challenges, I have been heavily relying on unit testing, crafting JUnit test cases to bolster my understanding of testing principles and ensure code quality.

---
