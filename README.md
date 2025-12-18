# Build a beginner "dodge" game

## Introduction @unplugged

In this tutorial, you'll create a fun dodge game where you control a character that must avoid falling objects. If you get hit, you lose a life!

## Step 1 - Set the background

First, let's set a background color for our game. Drag the ``||scene:set background color||`` block into the ``||loops:on start||`` block and pick a color you like.

```blocks
scene.setBackgroundColor(9)
```

## Step 2 - Create your player sprite

Now let's create the main character! Drag ``||sprites:set mySprite to sprite of kind Player||`` into ``||loops:on start||``. Click on the grey box to open the image editor and draw your character (or use the one shown).

```blocks
scene.setBackgroundColor(9)
let mySprite = sprites.create(img`
    . . . . f f f f f . . . . . . . 
    . . . f e e e e e f . . . . . . 
    . . f d d d d e e e f . . . . . 
    . c d f d d f d e e f f . . . . 
    . c d f d d f d e e d d f . . . 
    c d e e d d d d e e b d c . . . 
    c d d d d c d d e e b d c . f f 
    c c c c c d d d e e f c . f e f 
    . f d d d d d e e f f . . f e f 
    . . f f f f f e e e e f . f e f 
    . . . . f e e e e e e e f f e f 
    . . . f e f f e f e e e e f f . 
    . . . f e f f e f e e e e f . . 
    . . . f d b f d b f f e f . . . 
    . . . f d d c d d b b d f . . . 
    . . . . f f f f f f f f f . . . 
    `, SpriteKind.Player)
```

## Step 3 - Add player movement

Let's make the player move left and right using the controller. Drag ``||controller:move mySprite with buttons||`` into ``||loops:on start||``. Click on the + sign and set **vx** to `100` and **vy** to `0` so the player only moves horizontally.

```blocks
scene.setBackgroundColor(9)
let mySprite = sprites.create(img`
    . . . . f f f f f . . . . . . . 
    . . . f e e e e e f . . . . . . 
    . . f d d d d e e e f . . . . . 
    . c d f d d f d e e f f . . . . 
    . c d f d d f d e e d d f . . . 
    c d e e d d d d e e b d c . . . 
    c d d d d c d d e e b d c . f f 
    c c c c c d d d e e f c . f e f 
    . f d d d d d e e f f . . f e f 
    . . f f f f f e e e e f . f e f 
    . . . . f e e e e e e e f f e f 
    . . . f e f f e f e e e e f f . 
    . . . f e f f e f e e e e f . . 
    . . . f d b f d b f f e f . . . 
    . . . f d d c d d b b d f . . . 
    . . . . f f f f f f f f f . . . 
    `, SpriteKind.Player)
controller.moveSprite(mySprite, 100, 0)
```

## Step 4 - Keep player on screen

We don't want the player to leave the screen! Add ``||sprites:set mySprite stay in screen||`` and set it to **ON**.

```blocks
scene.setBackgroundColor(9)
let mySprite = sprites.create(img`
    . . . . f f f f f . . . . . . . 
    . . . f e e e e e f . . . . . . 
    . . f d d d d e e e f . . . . . 
    . c d f d d f d e e f f . . . . 
    . c d f d d f d e e d d f . . . 
    c d e e d d d d e e b d c . . . 
    c d d d d c d d e e b d c . f f 
    c c c c c d d d e e f c . f e f 
    . f d d d d d e e f f . . f e f 
    . . f f f f f e e e e f . f e f 
    . . . . f e e e e e e e f f e f 
    . . . f e f f e f e e e e f f . 
    . . . f e f f e f e e e e f . . 
    . . . f d b f d b f f e f . . . 
    . . . f d d c d d b b d f . . . 
    . . . . f f f f f f f f f . . . 
    `, SpriteKind.Player)
controller.moveSprite(mySprite, 100, 0)
mySprite.setStayInScreen(true)
```

## Step 5 - Position the player

Let's place the player near the bottom of the screen. Add ``||sprites:set mySprite position||`` and set **x** to `80` and **y** to `101`.

```blocks
scene.setBackgroundColor(9)
let mySprite = sprites.create(img`
    . . . . f f f f f . . . . . . . 
    . . . f e e e e e f . . . . . . 
    . . f d d d d e e e f . . . . . 
    . c d f d d f d e e f f . . . . 
    . c d f d d f d e e d d f . . . 
    c d e e d d d d e e b d c . . . 
    c d d d d c d d e e b d c . f f 
    c c c c c d d d e e f c . f e f 
    . f d d d d d e e f f . . f e f 
    . . f f f f f e e e e f . f e f 
    . . . . f e e e e e e e f f e f 
    . . . f e f f e f e e e e f f . 
    . . . f e f f e f e e e e f . . 
    . . . f d b f d b f f e f . . . 
    . . . f d d c d d b b d f . . . 
    . . . . f f f f f f f f f . . . 
    `, SpriteKind.Player)
controller.moveSprite(mySprite, 100, 0)
mySprite.setStayInScreen(true)
mySprite.setPosition(80, 101)
```

## Step 6 - Add lives

The player needs lives! Add ``||info:set life to||`` and set it to `3`.

```blocks
scene.setBackgroundColor(9)
let mySprite = sprites.create(img`
    . . . . f f f f f . . . . . . . 
    . . . f e e e e e f . . . . . . 
    . . f d d d d e e e f . . . . . 
    . c d f d d f d e e f f . . . . 
    . c d f d d f d e e d d f . . . 
    c d e e d d d d e e b d c . . . 
    c d d d d c d d e e b d c . f f 
    c c c c c d d d e e f c . f e f 
    . f d d d d d e e f f . . f e f 
    . . f f f f f e e e e f . f e f 
    . . . . f e e e e e e e f f e f 
    . . . f e f f e f e e e e f f . 
    . . . f e f f e f e e e e f . . 
    . . . f d b f d b f f e f . . . 
    . . . f d d c d d b b d f . . . 
    . . . . f f f f f f f f f . . . 
    `, SpriteKind.Player)
controller.moveSprite(mySprite, 100, 0)
mySprite.setStayInScreen(true)
mySprite.setPosition(80, 101)
info.setLife(3)
```

## Step 7 - Create falling enemies

Now let's spawn enemies that fall from the top! Drag ``||game:on game update every||`` from ``||game:Game||`` and set the interval to `500` ms.

```blocks
game.onUpdateInterval(500, function () {
    
})
```

## Step 8 - Add the enemy sprite

Inside the ``||game:on game update every||`` block, create an enemy sprite. Use ``||sprites:set mySprite2 to sprite of kind Enemy||`` and draw something to dodge!

```blocks
let mySprite2: Sprite = null
game.onUpdateInterval(500, function () {
    mySprite2 = sprites.create(img`
        . . . . . . . . . . . . . . . . 
        . . . . . . . . . . . . . . . . 
        . . . . . . . . . . . . . . . . 
        . . . . . . c c . . . . . . . . 
        . . . . c a f b c . . . . . . . 
        . . . . b f f b c c . . . . . . 
        . . . a a f b a b a c . . . . . 
        . . . c a c b b f f b . . . . . 
        . . . . b f f b f a b . . . . . 
        . . . . a f f b b b a . . . . . 
        . . . . . a b b c c . . . . . . 
        . . . . . . . . . . . . . . . . 
        . . . . . . . . . . . . . . . . 
        . . . . . . . . . . . . . . . . 
        . . . . . . . . . . . . . . . . 
        . . . . . . . . . . . . . . . . 
        `, SpriteKind.Enemy)
})
```

## Step 9 - Randomize enemy position

Make enemies appear at random positions along the top of the screen. Add ``||sprites:set mySprite2 position||`` and use ``||math:pick random||`` for **x** (from `0` to ``||scene:screen width||``) and set **y** to `0`.

```blocks
let mySprite2: Sprite = null
game.onUpdateInterval(500, function () {
    mySprite2 = sprites.create(img`
        . . . . . . . . . . . . . . . . 
        . . . . . . . . . . . . . . . . 
        . . . . . . . . . . . . . . . . 
        . . . . . . c c . . . . . . . . 
        . . . . c a f b c . . . . . . . 
        . . . . b f f b c c . . . . . . 
        . . . a a f b a b a c . . . . . 
        . . . c a c b b f f b . . . . . 
        . . . . b f f b f a b . . . . . 
        . . . . a f f b b b a . . . . . 
        . . . . . a b b c c . . . . . . 
        . . . . . . . . . . . . . . . . 
        . . . . . . . . . . . . . . . . 
        . . . . . . . . . . . . . . . . 
        . . . . . . . . . . . . . . . . 
        . . . . . . . . . . . . . . . . 
        `, SpriteKind.Enemy)
    mySprite2.setPosition(randint(0, scene.screenWidth()), 0)
})
```

## Step 10 - Make enemies fall

Give enemies a random falling speed. Add ``||sprites:set mySprite2 vy||``, change mySprite to mySprite2 and x to vy. Use ``||math:pick random||`` to replace the 0 value to set the random values between `30` and `70`.

```blocks
let mySprite2: Sprite = null
game.onUpdateInterval(500, function () {
    mySprite2 = sprites.create(img`
        . . . . . . . . . . . . . . . . 
        . . . . . . . . . . . . . . . . 
        . . . . . . . . . . . . . . . . 
        . . . . . . c c . . . . . . . . 
        . . . . c a f b c . . . . . . . 
        . . . . b f f b c c . . . . . . 
        . . . a a f b a b a c . . . . . 
        . . . c a c b b f f b . . . . . 
        . . . . b f f b f a b . . . . . 
        . . . . a f f b b b a . . . . . 
        . . . . . a b b c c . . . . . . 
        . . . . . . . . . . . . . . . . 
        . . . . . . . . . . . . . . . . 
        . . . . . . . . . . . . . . . . 
        . . . . . . . . . . . . . . . . 
        . . . . . . . . . . . . . . . . 
        `, SpriteKind.Enemy)
    mySprite2.setPosition(randint(0, scene.screenWidth()), 0)
    mySprite2.vy = randint(30, 70)
})
```

## Step 11 - Handle collisions

When the player touches an enemy, we need to destroy the enemy and lose a life. Drag ``||sprites:on sprite overlaps otherSprite||`` from ``||sprites:Sprites||``. Set the kinds to **Player** and **Enemy**.

```blocks
sprites.onOverlap(SpriteKind.Player, SpriteKind.Enemy, function (sprite, otherSprite) {
    
})
```

## Step 12 - Destroy and lose life

When collision occurs, inside the overlap event, add ``||sprites:destroy||`` to destroy your enemy with a **fire** effect. Press the + sign to display the different options and change the ms to 100 ms. Then add ``||info:change life by -1||`` and a short ``||loops:pause||`` of `1000` ms to give the player a moment to recover.

```blocks
sprites.onOverlap(SpriteKind.Player, SpriteKind.Enemy, function (sprite, otherSprite) {
    sprites.destroy(otherSprite, effects.fire, 100)
    info.changeLifeBy(-1)
    pause(1500)
})
```

## Finale

Congratulations! You've built a complete dodge game! 🎮

Try playing your game and see how long you can survive. Here are some ideas to make it even better:

- Add a score that increases over time
- Make enemies fall faster as time goes on
- Add different types of enemies
- Add power-ups the player can collect

```blocks
scene.setBackgroundColor(9)
let mySprite = sprites.create(img`
    . . . . f f f f f . . . . . . . 
    . . . f e e e e e f . . . . . . 
    . . f d d d d e e e f . . . . . 
    . c d f d d f d e e f f . . . . 
    . c d f d d f d e e d d f . . . 
    c d e e d d d d e e b d c . . . 
    c d d d d c d d e e b d c . f f 
    c c c c c d d d e e f c . f e f 
    . f d d d d d e e f f . . f e f 
    . . f f f f f e e e e f . f e f 
    . . . . f e e e e e e e f f e f 
    . . . f e f f e f e e e e f f . 
    . . . f e f f e f e e e e f . . 
    . . . f d b f d b f f e f . . . 
    . . . f d d c d d b b d f . . . 
    . . . . f f f f f f f f f . . . 
    `, SpriteKind.Player)
controller.moveSprite(mySprite, 100, 0)
mySprite.setStayInScreen(true)
mySprite.setPosition(80, 101)
info.setLife(3)

sprites.onOverlap(SpriteKind.Player, SpriteKind.Enemy, function (sprite, otherSprite) {
    sprites.destroy(otherSprite, effects.fire, 500)
    info.changeLifeBy(-1)
    pause(1500)
})

let mySprite2: Sprite = null
game.onUpdateInterval(500, function () {
    mySprite2 = sprites.create(img`
        . . . . . . . . . . . . . . . . 
        . . . . . . . . . . . . . . . . 
        . . . . . . . . . . . . . . . . 
        . . . . . . c c . . . . . . . . 
        . . . . c a f b c . . . . . . . 
        . . . . b f f b c c . . . . . . 
        . . . a a f b a b a c . . . . . 
        . . . c a c b b f f b . . . . . 
        . . . . b f f b f a b . . . . . 
        . . . . a f f b b b a . . . . . 
        . . . . . a b b c c . . . . . . 
        . . . . . . . . . . . . . . . . 
        . . . . . . . . . . . . . . . . 
        . . . . . . . . . . . . . . . . 
        . . . . . . . . . . . . . . . . 
        . . . . . . . . . . . . . . . . 
        `, SpriteKind.Enemy)
    mySprite2.setPosition(randint(0, scene.screenWidth()), 0)
    mySprite2.vy = randint(30, 70)
})
```


> Open this page at [https://ruizosvaldo.github.io/dodge_tutorial_beginner/](https://ruizosvaldo.github.io/dodge_tutorial_beginner/)

## Use as Extension

This repository can be added as an **extension** in MakeCode.

* open [https://arcade.makecode.com/](https://arcade.makecode.com/)
* click on **New Project**
* click on **Extensions** under the gearwheel menu
* search for **https://github.com/ruizosvaldo/dodge_tutorial_beginner** and import

## Edit this project

To edit this repository in MakeCode.

* open [https://arcade.makecode.com/](https://arcade.makecode.com/)
* click on **Import** then click on **Import URL**
* paste **https://github.com/ruizosvaldo/dodge_tutorial_beginner** and click import

#### Metadata (used for search, rendering)

* for PXT/arcade
<script src="https://makecode.com/gh-pages-embed.js"></script><script>makeCodeRender("{{ site.makecode.home_url }}", "{{ site.github.owner_name }}/{{ site.github.repository_name }}");</script>



> Open this page at [https://ruizosvaldo.github.io/league_arcade_beginner/](https://ruizosvaldo.github.io/league_arcade_beginner/)

## Use as Extension

This repository can be added as an **extension** in MakeCode.

* open [https://arcade.makecode.com/](https://arcade.makecode.com/)
* click on **New Project**
* click on **Extensions** under the gearwheel menu
* search for **https://github.com/ruizosvaldo/league_arcade_beginner** and import

## Edit this project

To edit this repository in MakeCode.

* open [https://arcade.makecode.com/](https://arcade.makecode.com/)
* click on **Import** then click on **Import URL**
* paste **https://github.com/ruizosvaldo/league_arcade_beginner** and click import

#### Metadata (used for search, rendering)

* for PXT/arcade
<script src="https://makecode.com/gh-pages-embed.js"></script><script>makeCodeRender("{{ site.makecode.home_url }}", "{{ site.github.owner_name }}/{{ site.github.repository_name }}");</script>
