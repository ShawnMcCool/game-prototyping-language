# game-prototyping-language

Prototyping is not about making a finished product. It's about trying an idea. The goal of the language is to assist in this goal while preventing the user from being exposed to Java.

**Goals**

* 2D only
* Entity<->Component language
* Integrated and extensible collision detection
* Integrated spritemap support (jpg, png, bmp)
* Integrated tilemap support (tmx)
* Integrate audio support (mp3, wav)
* Integrate input device support (mouse, keyboard, gamepad)
* Basic ui / widget support

# Entity / Components

Toying with syntax...

```
entity Player {
  name Text = "Shawn"
  age Number = 33
}

addTo Player Sprite("dog.png")
Player.add(Sprite("dog.png"))
attach Sprite("dog.png") to Player
Player has Sprite("dog.png")
Player.has(Sprite("dog.png"))
```

