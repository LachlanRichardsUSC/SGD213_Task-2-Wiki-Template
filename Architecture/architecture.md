# Architecture 

![alt text](https://github.com/LachlanRichardsUSC/SGD213_Task-2-Wiki-Template/blob/86ababcff6ff7a025c025380860e2f65277403e1/Media/UML%20Diagrams/ClassDiagramVer2.png?raw=true)

## Justification

For our architecture, we have chosen option 2 for modularity with Game Objects that have shared behaviour. This is done through using interfaces, which is logical since many objects in the game will feature shared movement. Each object with these shared behaviours will inherent both direction and speed from this interface.

In retrospect, the provided image is initially hard to follow, although the intent of this UML class diagram is to demonstate how each of the Game Objects interact with eachother, as well as what classes they inherent for shared functionality between Game Objects.
