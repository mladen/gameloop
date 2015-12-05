# gameloop

> the core methods/events of a game loop: start, end, pause, resume, update, draw

## Install

    npm install gameloop

Designed for use with browserify.

## Usage

### Create a canvas and game object:

```js
var canvas = document.createElement('canvas')

var game = new Game({
  renderer: canvas.getContext('2d')
})
```

You can use it server-side by not passing in a canvas context: `var game = Game();`

> the `new` keyword is optional

### Use update and draw events

```js
game.on('update', function(dt){})

game.on('draw', function(context){})
```

## API

### createGame

Create the game

**Parameters**

-   `options` **Object** 
    -   `options.renderer` **Object** 
    -   `options.fps` **Number** 

**Examples**

```javascript
var createGame = require('gameloop')

var game = createGame({
  renderer: document.createElement('canvas').getContext('2d')
})
```

### game.draw

Draw the game. Emits the `draw` event. You'll likely never call this method, but you may need to override it. Make sure to always emit the update event with the renderer and `delta` time.

**Parameters**

-   `renderer` **Object** 
-   `delta` **Number** – time elapsed since last update
-   `dt`  

### game.end

End the game. Emits the `end` event/

**Examples**

```javascript
game.end()
```

### game.pause

Pause the game. Emits the `pause` event.

**Examples**

```javascript
game.pause()
```

### game.resume

Resume the game. Emits the `resume` event.

**Examples**

```javascript
game.resume()
```

### game.start

Start the game. Emits the `start` event.

**Examples**

```javascript
game.start()
```

### game.toggle

Pause or start game depending on game state. Emits either the `pause` or `resume` event.

**Examples**

```javascript
game.toggle()
```

### game.update

Update the game state. Emits the `update` event. You'll likely never call this method, but you may need to override it. Make sure to always emit the update event with the `delta` time.

**Parameters**

-   `delta` **Number** – time elapsed since last update
-   `dt`  

### Game#draw

Draw event.

**Parameters**

-   `renderer` **Object** 
-   `delta` **Number** 

**Examples**

```javascript
game.on('draw', function (renderer, dt) {
  console.log(dt)
})
```

### Game#end

End event. Fired when `game.end()` is called.

**Examples**

```javascript
game.on('end', function () {})
```

### Game#pause

Pause event. Fired when `game.pause()` is called.

**Examples**

```javascript
game.on('pause', function () {})
```

### Game#resume

Resume event. Fired when `game.resume()` is called.

**Examples**

```javascript
game.on('resume', function () {})
```

### Game#start

Start event. Fired when `game.start()` is called.

**Examples**

```javascript
game.on('start', function () {})
```

### Game#update

Update event.

**Parameters**

-   `delta` **Number** 

**Examples**

```javascript
game.on('update', function (dt) {
  console.log(dt)
})
```

## Contributing

-   Fork this repository.
-   Create a branch for your changes.
-   Include tests if applicable.
-   Add/edit documentation for any changes.
-   Submit a pull request.

## License

MIT
