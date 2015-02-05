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
# paddles
paddle_one actor = start_at(x = 10,  y = 100) + can_move(controller = input_device(1))
paddle_two actor = start_at(x = 190, y = 100) + can_move(controller = input_device(2))

group paddles = paddle_one + paddle_two

# ball
ball actor = start_at(x = 100, y = 100) + moves_linearly + bounces_off_paddles

# behaviors

start_at behavior {
  actor's position's x = x
  actor's position's y = y
}

moves_linearly behavior { 
  speed Number = 9
  angle Number = 97
  actor's position = actor's position's forward(speed)
}

can_move behavior {
  speed Number = 10
  if controller's up_is_pressed then make actor move_up(speed)
  if controller's down_is_pressed then make actor move_down(speed)
}

# actions

move_up action(speed Number) {
  actor's position's y = actor's position's y - speed
}

move_down action(speed Number) {
  actor's position's y = actor's position's y + speed
}
```
