# ViajaMas™

## Introduction

ViajeMas™ is a system that allows users of the Metro in Madrid to avoid crowded compartments through directions to the less crowded wagon.

The train has been divided into different subsections that will be referred to as “doors”. These doors stand for the space of the wagon that surrounds each door of each wagon. Therefore, we will divide the people into as many groups as different doors exist in the train itself.

The nature of the train will vary depending on the line and the model.

DISCLAIMER: this program is a virtual simulation of the actual system

## Installation

In order to implement this system, Python needs to be installed (any version above ). Once Python is installed, the program is ready to be run.

The complexity of our proposal comes from the usage of heat cameras (one heat camera per door). Each camera outputs a reading and these readings are inputted as a series of comma-separated values on a txt file. Therefore, there will be one reading per heat camera installed in the train.

Taking this into account, we have used a training file to simulate the readings, which will need to be inputted into the interpreter of choice along with the program so the latter can be run*:

* nevertheless, any txt file with the specified characteristics would serve the same purpose
heat_map.txt - training data
In terms of the interpreter, the program has been designed to run on Google Collaboratory. To do so, WHAGAG.ipyb need to be downloaded.

## Usage

### User experience

Once the code is run, the simulation will ask the user to click the key A to receive the door with the most available spots.

After, the user will be given an answer in the shape of “Go to door X” where X stands for the door with the least number of people.

Program input: key A
Program output: door with least amount of passengers

### Underlying code:

Before the user inputs, the program will read in the txt file into a list. Each element of the list will be a value of the comma-separated list of heat map readings.

Afterwards, the values inside this list will be reformatted into instances of the class Door. The class Door is defined inside the class Train and it has two attributes: the number of the door and the available spots. Each reading is reformatted from number of people in each door to the number of available spots (capacity of the door minus the number of passengers).

This new list will work as a more flexible hash table.

In order to reformat the list, an instance of the class Train needs to be created first, that will specify the conditions of the train: the total number of doors in each wagon, the total number of wagons and the capacity of each door (all inherited by the Door class).

By the simulation’s default, the train created will be “coche serie 7000”, used in the line 10. The adjustment of these parameters will be part of the instalment proceed of the system in real life.

Once these two procedures are done (summarised into two functions), the user’s input will be asked.

If the correct input is received, an infinite loop will start that will jump onto the next step. If the input is not correct, then the loop will be broken and the program will be exited.

The next step will take the class instances’ list and apply a quicksort specialised algorithm on it. This quicksort algorithm takes in as input a list of Door instances and sorts the items recursively into two categories, higher and lower than the pivot. The parameter used to test whether an item is higher or lower is the “available spots” attribute of the item, that is, quicksort will be applied on the items in terms of their available spots, so the list will be sorted from door with least spots to door with most spots.

Then, the quicksorted list will rewrite the original list and the top pick will be defined as the door instance on the last position of the list. The final output will be presented to the user in the form of “Go to door X”, as it has been previously stated. The program will print the text and add as “door” the attribute “door” (which stands for the door number) of the top pick Door instance.

After the output is presented, the number of spots available on the top pick door will be reduced by one unit, so the next iteration of the loop takes into account the previous passenger (that will take one available spot in said door).
In order to summarise the techniques used, we have used the following data structures and algorithms:

#### Data structures:

- Class: to store the information on the train (Train class) and the information on each door (Door class)
- Lists: to save the readings, to reformat them and sort the door instances

#### Algorithms:

- Quicksort: to sort the door instances’ list by available spots

## Credits

The contributors of this project are:

- Hiba Laziri
- Marya Mufti
- Laura Moya
- Fabian Perez
- Rayna Solanki 
- Alicia Vera Peña
