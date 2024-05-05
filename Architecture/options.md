# TOP HEADING

You should consider 3 different architecture options in here.

You **don't** need UML in here.

You should also justify your thinking.

Hot tip: use our text book for guidance.

## Option 1
The PlayerCharacter inherents from PlayerController. The PlayerCharacter also inherents from an interface called IMovable to control shared movement between enemies, projectiles and itself. Using a proximity circle, enemies will become aggressive towards the player when nearby. There are pickups scattered throughout the level which enable the player to collect varous powerups in the form of weapons. These weapons inherent from a WeaponBase class. The weapons, when activated, instantiated Bullet objects that are collected in an ObjectPool as a form of memory management. These bullets move in a fixed direction until they collide with a wall or a player. The Collision checks the tag associated with the object it strikes, and the collision behaviour is determined by their tag. an interface for health called IHealth is used for attributes such as damage dealt, max and current health, healing, etc...

## Option 2
The PlayerCharacter is controlled via the PlayerController. The PlayerCharacter inherents from an interfacee called IMovement to handle shared movemenet with objects such as projectiles, falling obstacles and itself. Enemies are controlled via collisions using RigidBody, their direction of moveemnt changes when they collide with a wall. There are pickups scattered throughout the level which enable the player to collect varous powerups in the form of weapons. These weapons inherent from a WeaponBase class. The weapons, when activated, instantiated Bullet objects that are collected in an ObjectPool as a form of memory management. Bullets move in a fixed direction and their collision behaviour is determined by tags. an interface for health called IHealth is used for attributes such as damage dealt, max and current health, healing, etc...

## Option 3
The PlayerCharacter and Enemy objects use the RigidBody component to handle the movement by adding force to the object upon an input. The bullets may also use the RigidBody component for movement, also utilising tags to determine their collision behaviours. interfaces such as IMovement are not used here. instantiated Bullet objects that are collected in an ObjectPool as a form of memory management.  An interface for health called IHealth is used for attributes such as damage dealt, max and current health, healing, etc...
