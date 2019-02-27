# DTWSpells-ShawnPolson
Minimal code pieces to call an elevator with a "magic wand."

## Creator:
Shawn Polson

## Goal:
The idea behind this mini-project was to prepare for the larger "Wonkavator" project. The goal here was to create a Wekinator project that takes as input the X, Y, Z data from a Microbit that is attatched to a "wand", and uses dynamic time warping to recognize "up" and "down" gestures from those inputs. Once Wekinator can reliably recognize "up" and "down" gestures performed with the wand, the only extra step needed to call an elevator would be to send the Wekinator output to some solenoid switches (not done here). 

## Approach Used:
### Sensors:
This mini-project uses two Microbit sensors for inputs. One Microbit is wirelessly attached to the "wand" (a spatula, in this case) and transmits its X, Y, Z data. The second Microbit is connected to the computer via a USB port and it recieves the data transmitted from the wand (and then feeds the data into Wekinator).

### Feature Extractor Approaches:
For feature extraction, what I've done is disable the "Y" inupt so that Wekinator only recieves X and Z inputs from the wand. In my experimentation, this improved the gesture recognition roughly 3 fold (shown in the Experiments table below)

### ML Model Structure:
 - Dynamic Time Warping
 - Matching computed continuously while running
 - Downsample so examples have max length of 10
 - Countinuous matches use a minimum length of 5
 - Match width: 5
 - Match hop size: 1
 
This structure remained constant during my experimentation because my feature extraction gave me a good enough accuracy boost.

#### Experiments
|Inputs | # Up gestures performed | # Down gestures performed | # Up gestures recognized | # Down gestures recognized 
|-------| :---------------------: |:-------------------------:| :-----------------------:|:-------------------------:
| X,Y,Z | 10                      | 10                        |  3                       | 2                         
| X, Y  | 10                      | 10                        |  4                       | 5
| X, Z  | 10                      | 10                        | 9                        | 8


## Demo Video:
https://youtu.be/kumwyzGUf74
