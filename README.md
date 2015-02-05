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
player actor = has_health(hp = 150) and moves_randomly
```

# Basic Control

```
add_health action(amountToAdd Number) {
 actor's hp = hp + amountToAdd
}


add_health(1) to_all players

if player's hp < 10 have ...
```

# Example Application

```
# paddles
paddle_one actor = position(x = 10,  y = 100) and is_controlled_by(controller = input_device(1))
paddle_two actor = position(x = 190, y = 100) and is_controlled_by(controller = input_device(2))

group paddles = paddle_one + paddle_two

# ball
ball actor = position(x = 100, y = 100, angle = 97) and moves_linearly and bounces_off_paddles

# behaviors

start_at behavior {
  actor's position's x = x
  actor's position's y = y
}

moves_linearly behavior { 
  speed Number = 9
  actor's position = actor's position's forward(speed)
}

is_controlled_by behavior {
  speed Number = 10
  if controller's up_is_pressed have actor move_up(speed)
  if controller's down_is_pressed have actor move_down(speed)
}

bounces_off_paddles behavior {
  if actor collides_with paddles have actor's position's angle flip_horizontally
}

# actions

move_up action(speed Number) {
  actor's position's y = actor's position's y - speed
}

move_down action(speed Number) {
  actor's position's y = actor's position's y + speed
}
```
