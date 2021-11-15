# Tamagotchi v2

## 1. Einführung @unplugged

👋 Hallo! Dein eigenes virtuelles Haustier **Betty** wartet auf dich! 🐰 🐶 🐱

## 2. Betty wird geboren

** Betty wird geboren und begrüßt dich! **


► ``||basic:Beim Start||`` soll ein neutrales Gesicht ``-_-`` angezeigt werden. Verwende ``||basic:Zeige LEDs||`` und zeichne es selbst.

► Erzeuge eine ``||variables:Variable||`` mit dem Namen ``||variables:timer||``.

► Abschließend ``||music:spiele den Soundeffekt Hallo bis zu Ende||``


```blocks
let timer = 0
basic.showLeds(`
    . . . . .
    . # . # .
    . . . . .
    . # # # .
    . . . . .
    `)
soundExpression.hello.playUntilDone()
timer = 0
```

## 3. Dauerschleife

** In der dauerhaft-Schleife wird der Timer hinaufgezählt. **

► In der ``||basic:dauerhaft||``-Schleife wird der ``||variables:timer||`` bei jedem Durchlauf um 1 ``||variables:geändert||``

► Wichtig: Vergiss das ``||basic:Pausieren||`` von einer Sekunde (1000 Milisekunden) nicht!

```blocks
basic.forever(function () {
    basic.pause(1000)
    timer += 1
})
```

## 4. Überprüfung 1

** Sind schon 20 Sekunden vergangen? **

► Überprüfe bei jedem Durchlauf: ``||logic:wenn||`` ``||variables:timer||`` = 20?

► Dann ``||basic:zeige Symbol||`` trauriges Gesicht

► Und ``||music:spiele den Soundeffekt Traurig bis zu Ende||``

```blocks
basic.forever(function () {
    basic.pause(1000)
    timer += 1
    if (timer == 20) {
        basic.showIcon(IconNames.Sad)
        soundExpression.sad.playUntilDone()
    }
})
```

## 5. Überprüfung 2

** Sind schon 30 Sekunden vergangen? **

► Überprüfe bei jedem Durchlauf: ``||logic:wenn||`` ``||variables:timer||`` = 30?

► Dann ``||basic:zeige Symbol||`` schlafendes Gesicht

► Und ``||music:spiele den Soundeffekt Gähnen bis zu Ende||``

```blocks
basic.forever(function () {
    basic.pause(1000)
    timer += 1
    if (timer == 20) {
        basic.showIcon(IconNames.Sad)
        soundExpression.sad.playUntilDone()
    }
    if (timer == 30) {
        basic.showIcon(IconNames.Asleep)
        soundExpression.yawn.playUntilDone()
    }
})
```

## 6. Überprüfung 3

** Sind schon 40 Sekunden vergangen? **

► Überprüfe bei jedem Durchlauf: ``||logic:wenn||`` ``||variables:timer||`` = 40?

► Dann ``||music:spiele den Soundeffekt Geheimnisvoll bis zu Ende||``,

► ``||music:schalte Lautsprecher ab||``

► Füge eine Endlosschleife ``||loops:während Wahr||`` ein

► und gib ``||basic:zeige Symbol||`` Totenkopf dort hinein

💡 Wenn das Programm einmal in einer Endloschleife ist, kommt es nicht wieder heraus. Das ist hier wichtig, damit Betty nicht wieder einfach von den Toten aufersteht.

```blocks
basic.forever(function () {
    basic.pause(1000)
    timer += 1
    if (timer == 20) {
        basic.showIcon(IconNames.Sad)
        soundExpression.sad.playUntilDone()
    }
    if (timer == 30) {
        basic.showIcon(IconNames.Asleep)
        soundExpression.yawn.playUntilDone()
    }
    if (timer == 40) {
        soundExpression.mysterious.playUntilDone()
        music.setBuiltInSpeakerEnabled(false)
        while (true) {
            basic.showIcon(IconNames.Skull)
        }
    }
})
```

## 7. Schütteln

** Betty wird von uns liebkost. **

► Wir verwenden den Bewegungssensor und schauen wenn Betty ``||input:geschüttelt||`` wurde.

► Dann ``||variables:setzen||`` wir den ``||variables:timer||`` auf 0

► und ``||basic:zeigen Symbol||`` glückliches Gesicht,

► und ``||music:spiele den Soundeffekt Kichern bis zu Ende||``.

```blocks
input.onGesture(Gesture.Shake, function () {
    timer = 0
    basic.showIcon(IconNames.Surprised)
    soundExpression.giggle.playUntilDone()
})
```

## 8. Kitzeln

** Betty wird von uns gekitzelt. **

► Wir verwenden den Berührungssensor und schauen wenn Bettys ``||input:Logo gedrückt||`` wurde.

► Dann ``||variables:setzen||`` wir den ``||variables:timer||`` auf 0

► und ``||basic:zeigen Symbol||`` mit offenem Mund,

► und ``||music:spiele den Soundeffekt Glücklich bis zu Ende||``.

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    timer = 0
    basic.showIcon(IconNames.Happy)
    soundExpression.happy.playUntilDone()
})
```

## 9. Testen

** Teste dein neues Tamagotchi Betty im Simulator oder lade dir das Programm auf deinen @boardname@ v2! **

► Berühre das Logo! (die glänzende Schweinenase 🐽 über den LEDs)

► Schüttel sie 💫!

► Schaue was passiert, wenn du einmal länger nicht mit ihr spielst... 😔

► Sollte sie trotz deiner liebevollen Zuwendung doch einmal das Zeitliche 💀 segnen, drücke den Reset-Button ↺ 🔘 auf der Rückseite des @boardname@

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    timer = 0
    basic.showIcon(IconNames.Happy)
    soundExpression.happy.playUntilDone()
})
input.onGesture(Gesture.Shake, function () {
    timer = 0
    basic.showIcon(IconNames.Surprised)
    soundExpression.giggle.playUntilDone()
})
let timer = 0
basic.showLeds(`
    . . . . .
    . # . # .
    . . . . .
    . # # # .
    . . . . .
    `)
soundExpression.hello.playUntilDone()
timer = 0
basic.forever(function () {
    basic.pause(1000)
    timer += 1
    if (timer == 20) {
        basic.showIcon(IconNames.Sad)
        soundExpression.sad.playUntilDone()
    }
    if (timer == 30) {
        basic.showIcon(IconNames.Asleep)
        soundExpression.yawn.playUntilDone()
    }
    if (timer == 40) {
        soundExpression.mysterious.playUntilDone()
        music.setBuiltInSpeakerEnabled(false)
        while (true) {
            basic.showIcon(IconNames.Skull)
        }
    }
})
```

<script src="https://makecode.com/gh-pages-embed.js"></script><script>makeCodeRender("{{ site.makecode.home_url }}", "{{ site.github.owner_name }}/{{ site.github.repository_name }}");</script>
