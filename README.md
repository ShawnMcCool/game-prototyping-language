# Game Prototyping Language

Prototyping is not about making a finished product. It's about trying an idea. The goal of the language is to assist in this goal while preventing the user from being exposed to Java or JavaScript.

**Goals**

* 2D only
* Entity<->Component language
* Integrated and extensible collision detection
* Integrated spritemap support (jpg, png, bmp)
* Integrated tilemap support (tmx)
* Integrate audio support (mp3, wav)
* Integrate input device support (mouse, keyboard, gamepad)
* Basic ui / widget support

**Willful Omissions**

* Scene management
* UI

# Entity / Components

Toying with syntax...

```
health component {
  hp Number = 100
}

moves_randomly component {
  speed Number = 10
  
  ...
}
```

```
player entity = health(hp = 150) + moves_randomly
```

# Basic Control

```
add_health transformation(amount Number) {
 entity(hp = hp + amount)
}


for_each players add_health(1)
```

