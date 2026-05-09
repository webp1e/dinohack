# dinohack
если вы столкнулись с тем что вы ну очень хотите сломать динозаврика гугл но гайды пятилетней старости не работают предлагаю вам это!

откройте консоль на F12 на страничке chrome://dino
и введите в консоль это
```javascript
const game = Runner.getInstance();
const trex = game.tRex
```
теперь благодаря этому вы можете:
отключать коллизию
```javascript
game.checkForCollision = () => null;
```
менять скорость динозаврика
```javascript
game.currentSpeed = 30;
```
менять высоту прыжка
```javascript
game.tRex.config.initialJumpVelocity = -30;
```
удалить все препятствия
```javascript
game.horizon.addNewObstacle = () => {};
```
заставить динозаврика бежать назад
```javascript
game.currentSpeed = -10;
```
заставить динозаврика летать
```javascript
trex.yPos = 0;
```
размыть зрение
```javascript
game.canvasCtx.filter = "blur(5px)";
```
отзеркалить
```javascript
game.containerEl.style.transform = "scaleX(-1)";
```
все мигает
```javascript
setInterval(() => {
    game.canvasCtx.filter = `hue-rotate(${Math.random() * 360}deg) brightness(${Math.random()})`;
}, 100);
```

все мигает разными цветами ОСТОРОЖНО!!! МОЖЕТ ВЫЗВАТЬ ЭПИЛЕПСИЮ!!!
```javascript
document.body.style.transition = 'none';
const colors = ['red', 'blue', 'green', 'yellow', 'purple', 'black', 'white'];
setInterval(() => {
    document.body.style.backgroundColor = colors[Math.floor(Math.random() * colors.length)];
}, 80);
```
спам всеми звуками
```javascript
game.hasAudioCuesInternal = true;
let sfx = game.generatedSoundFx;

if (!sfx || !sfx.context) {
    game.generatedSoundFx = new GeneratedSoundFx();
    sfx = game.generatedSoundFx;
}

if (sfx && sfx.context) {
    function soundSpam() {
        const notes = [220, 330, 440, 550, 660, 770, 880, 1040, 1320, 1760];
        const randomNote = notes[Math.floor(Math.random() * notes.length)];
        const randomVol = Math.random() * 0.8 + 0.2;
        const randomPan = Math.random() * 2 - 1;
        
        sfx.playNote(randomNote, sfx.context.currentTime, 0.1, randomVol, randomPan);
    }
    

    const spamInterval = setInterval(soundSpam, 50);
    

    setInterval(() => {
        sfx.playNote(Math.random() * 1000 + 100, sfx.context.currentTime, 0.05, 0.5);
    }, 30);
    
    console.log("ЗВУКОВОЙ СПАМ");
    console.log("остановить: clearInterval(" + spamInterval + ") и clearInterval(" + (spamInterval + 1) + ")")
}
```

