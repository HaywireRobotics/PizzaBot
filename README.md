# PizzaBot
This is the template for Haywire Robotics' PizzaBot design. It will get a minimum viable product chassis up and running. At the moment it also contains some features for limelights and AprilTags, although those aren't working very well.

The codebase is designed to work with the following components:
- [MK4 Swerve Modules](https://www.swervedrivespecialties.com/products/mk4-swerve-module?variant=39376675012721) from Swerve Drive Specialties.
- [NEO Brushless Motors](https://www.revrobotics.com/rev-21-1650/) from REV Robotics.
- [CTRE CANCoders](https://store.ctr-electronics.com/cancoder/) from CTR Electronics.

If your bot uses different types of components, then the code will need to be modified.

## Getting Set Up
Adapting the code to work with your robot is relatively simple.
### 1. Set width and length
The variables for the drivetrain's width and length need to be set to your robots dimensions, and can be found in `Constants.java`. Measure from the center of each swerve module.
```java
public static final double DRIVETRAIN_TRACKWIDTH_METERS = 0.475;
public static final double DRIVETRAIN_TRACKLENGTH_METERS = 0.475;
```
### 2. Configure IDs
All of the IDs for the motors and encoders need to be configured in `Constants.java`. Be sure that you have accurately identified which modules you want to be the front left, front right, back left, and back right.
```java
public static final int FRONT_LEFT_MODULE_DRIVE_MOTOR = 2;
public static final int FRONT_LEFT_MODULE_STEER_MOTOR = 1;
public static final int FRONT_LEFT_MODULE_STEER_ENCODER = 12; 
```
### 3. Calibrate encoder offsets
CTRE CANCoders come with various preconfigured absolute values that can differ depending on how you assembled the modules. To deal with this, PizzaBot has encoder offset values that you can configure. To do so, turn on the bot and monitor what values each of the CANCoders are giving. Rotate by hand each module to what you wish to be its zeroed position (do this while the bot is disabled). Then, plug the absolute angle values recieved by each encoder into `Constants.java`.
```java
public static final double FRONT_LEFT_MODULE_STEER_OFFSET = 169;
```
If some modules seem reversed from what they ought to be, you can correct that with the reverse drive variables.
```java
public static final boolean FRONT_LEFT_REVERSE_DRIVE = true;
```
### 4. Change `MAX_SPEED`
Configure the maximum motor speed to something reasonable for your purposes. The codebase may have it set low for testing reasons.
```java
public static final int MAX_SPEED = 1000;
```