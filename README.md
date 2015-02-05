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

* for_all = map function

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
add_health action(amount Number) {
 entity(hp = hp + amount)
}


for_all players add_health(1)

if player's hp < 10 then ...
```
