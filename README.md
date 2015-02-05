# Game Prototyping Language

Prototyping is not about making a finished product. It's about trying an idea. The goal of the language is to assist in this goal while preventing the user from being exposed to Java or JavaScript.

**Goals**

* 2D only
* Entity<->Component language
* Integrated collision detection
* Integrated spritemap support (jpg, png, bmp)
* Integrated tilemap support (tmx)
* Integrate audio support (mp3, wav)
* Integrate input device support (mouse, keyboard, gamepad)

**Willful Omissions**

* Scene management
* UI

# Structures

* actor - entities which have behaviors
* behavior - entity components
* action - function

# Control Structures 

* to_all = infix map function

# Entity / Behaviors

Toying with syntax...

```
has_health behavior {
  hp Number = 100
}

moves_randomly behavior {
  speed Number = 10
  
  ...
}
```

```
player actor = has_health(hp = 150) + moves_randomly
```

# Basic Control

```
add_health action(amountToAdd Number) {
 actor's hp = hp + amountToAdd
}


add_health(1) to_all players

if player's hp < 10 then ...
```

# Example Application

```
paddle_one actor = can_move(controller = input_device(1))
paddle_two actor = can_move(controller = input_device(2))

group paddles = poddle_one + paddle_two

move_up action(speed Number) {
  actor's y_position = actor's y_position - speed
}

move_down action(speed Number) {
  actor's y_position = actor's y_position + speed
}

can_move behavior {
  if controller's up_is_pressed then move_up(speed) actor
  if controller's down_is_pressed then move_down(speed) actor
}
```
