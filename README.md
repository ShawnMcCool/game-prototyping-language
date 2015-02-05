# game-prototyping-language

**Goals**

* 2D only
* Entity<->Component language
* Integrated and extensible collision detection
* Integrated spritemap support (jpg, png, bmp)
* Integrated tilemap support (tmx)
* Integrate audio support (mp3, wav)
* Integrate input device support (mouse, keyboard, gamepad)

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

