# Options

Below are three different options that were formulated by our group in order to determine our architectural strategy for developing the client specification. Additional context is provided further down below for the methods used to adhere to our Architecture Options.

## Option 1
- The PlayerCharacter is inherent of PlayerController.
- The PlayerCharacter is also inherent of an interface called IMovable to control shared movement between enemies, projectiles and itself.
- Using a proximity circle, enemies will become aggressive towards the player when nearby.
- There are pickups scattered throughout the level which enable the player to collect various powerups in the form of weapons.
- These weapons inherent from a WeaponBase class.
- The weapons, when activated, instantiate Bullet objects that are collected in an ObjectPool as a form of memory management.
- These Bullets move in a fixed direction until they collide with a wall or a player.
- The Collision checks the tag associated with the object it strikes, and the collision behaviour is determined by their tag.
- An interface for health called IHealth is used for attributes such as damage dealt, max and current health, healing, etc...

## Option 2
- The PlayerCharacter is controlled via the PlayerController.
- The PlayerCharacter is inherent of an interfacee called IMovement to handle shared movemenet with objects such as projectiles, falling obstacles and itself.
- Enemies are controlled via collisions using RigidBody, their direction of moveemnt changes when they collide with a wall.
- There are pickups scattered throughout the level which enable the player to collect varous powerups in the form of weapons.
- These weapons are inherent of a WeaponBase class.
- The weapons, when activated, instantiated Bullet objects that are collected in an ObjectPool as a form of memory management.
- Bullets move in a fixed direction and their collision behaviour is determined by tags.
- An interface for health called IHealth is used for attributes such as damage dealt, max and current health, healing, etc...

## Option 3
- The PlayerCharacter and Enemy objects use the RigidBody component to handle the movement by adding force to the object upon an input.
- The bullets may also use the RigidBody component for movement, also utilising tags to determine their collision behaviours.
- interfaces such as IMovement are not used here.
- instantiated Bullet objects that are collected in an ObjectPool as a form of memory management.
- An interface for health called IHealth is used for attributes such as damage dealt, max and current health, healing, etc...

## Inheritence

Inheritance is a fundamental concept in object-oriented programming that allows a class to inherit properties and behaviors (methods) from another class. In Unity, this is commonly used to create a hierarchical relationship between classes, enabling more specific classes to adopt and possibly modify functionalities of more generic classes. For example, you might have a base class Enemy that handles basic behaviors like movement and health, and specific enemy types like the star enemy or forest dwelling enemy that inherit from Enemy and add unique behaviors or properties.

An example of Inheritence is as follows:

Enemy (Base Class)         |  Weapon (Base Class)
:-------------------------:|:-------------------------:
 Star Enemy (Derived)      | Laser Weapon (Derived)  
Tree Enemy (Derived)       |Pulse Weapon (Derived)

Below are some key reasons to utilise Inheritence in your projects:
### Code Reusability 
- Inheritance allows developers to create a base class with generic functionality that can be extended by other classes. This promotes code reuse, as common methods and properties do not need to be rewritten for each new subclass.
### Simplified Maintenance
- Changes to shared functionality need only be made in the base class, which then automatically propagate to all derived classes. This simplifies maintenance and updates across the codebase.
### Organizational Clarity
- Inheritance establishes a clear hierarchy of classes, which can make the structure of the code easier to understand, especially in large projects where relationships between objects are complex.


## Interfaces

Interfaces define a contract for classes without providing a concrete implementation of the methods they declare. This is useful in Unity for creating systems that expect certain behaviors from a variety of objects without needing to know the specific type of the object. For example, an IDamageable interface might declare a method TakeDamage. Any class that implements this interface is then required to define this method, ensuring that any object treated as IDamageable can be damaged, whether it's a player, an enemy, or a destructible piece of the environment.

Interfaces are great for the following reasons:

### Flexibility in Implementation
- Interfaces allow for defining a common protocol without committing to a particular implementation. This enables different classes to implement the same interface in diverse ways, providing flexibility in how objects fulfill their roles.
### Enhanced Modularity
- By coding to an interface rather than a specific class, systems can remain decoupled and more modular. Components can be easily swapped as long as they adhere to the interface, facilitating easier updates and extensions.
### Support for Polymorphism
- Interfaces enable polymorphic behavior without the constraints of inheritance hierarchies, allowing objects of different classes to be treated the same way if they implement the same interface.

## Unity Component Pattern

The Unity Component Pattern is a core architectural pattern in Unity that emphasizes composition over inheritance. Instead of creating complex hierarchies of objects, you build functionality through the composition of various independent components. Each component is a script or built-in Unity module that controls certain aspects of what an object can do. For instance, a game object might have a Rigidbody for physics, a Renderer for visuals, and custom scripts for specific behaviors. This approach offers flexibility and reusability, as components can be mixed and matched to create diverse functionalities without the rigid structures imposed by inheritance.

Below is an example of the component pattern for two objects, the player object and the enemy object, demonstrated using a table, with the columns reperesenting the individual component that is attached to the game object.

PlayerObject         |  EnemyObject
:-------------------------:|:-------------------------:
 Move Component     | Move Component
Weapon Component      |Weapon Component
RigidBody            | RigidBody
PlayerInput          | EnemyAI
Render Component      | Render Component

Some key advantages to the component pattern include:

### High Modularity
- Components are modular and encapsulated, making it easy to mix and match functionalities. Developers can add or remove features from game objects on the fly without affecting unrelated systems.
### Ease of Iteration
- The component-based system simplifies iterative design and testing. New behaviors can be added to objects without altering existing code, allowing for rapid prototyping and adjustments based on testing feedback.
### Reusability Across Projects
- Components can be designed to be generic and reusable across different projects. A well-designed component can be used in multiple game objects or even different games, maximizing code reuse.

## Data Hiding

Data hiding is a principle of encapsulation in software design that restricts access to the internal state of an object. This is critical in game development for maintaining control over how game elements are manipulated, thereby protecting the integrity of the data and preventing misuse. In Unity, this can be implemented using access modifiers like private or protected, ensuring that variables and functions are not accessible from other scripts unless explicitly allowed. For instance, a player's health might be declared as a private variable with public methods to modify it, like TakeDamage or Heal, controlling how these values are changed and preventing direct access from other classes.

Key advantages of Data Hiding include:

### Improved Security
- By restricting access to internal states, data hiding prevents external entities from making unauthorized changes. This protects the integrity of the data and ensures that objects are used only through their intended interfaces.
### Simplified Debugging and Maintenance
- Encapsulated code is generally easier to debug and maintain because interactions with internal data are controlled and predictable. This containment reduces the chances of bugs related to unexpected data manipulations.
### Ease of Refactoring:
- When data is hidden and accessed via methods, refactoring the internals of a class does not affect other parts of the code that use it. This means developers can improve or optimize the internals without worrying about breaking other dependencies.

In short, these architectural concepts provide a robust framework for designing and managing complex interactions in game development, ensuring a scalable, maintainable, and efficient project.

