# bit:balance:board

## 1. Einführung @unplugged

🏄‍♀️ Heute wird gesurft! - Wer kann am besten die Balance halten? 🏄🏾

## 2. Zähler erzeugen und auf 0 setzen

** Eine neue Variable _zähler_ wird erstellt  **

► Erzeuge ``||basic:beim Start||`` eine ``||variables:Variable||`` mit dem Namen ``||variables:zähler||`` und setze diese auf 0.

► In dieser Variable werden unsere Sekunden gezählt.

```blocks
let zähler = 0
timer = 0
```

## 3. Dauerschleife

** Dauerhafte Überprüfung der _Neigung_ des Boards **

► In der ``||basic:dauerhaft||``-Schleife wird bei jedem Durchlauf die Neigung überprüft. 

► Beim @boardname@ wird die Neigung nach links oder rechts mit der ``||input:Beschleunigung (mg) in x||``-Richtung gemessen.

```blocks
let zähler = 0
basic.forever(function () {
    if (input.acceleration(Dimension.X) < 0 ) {

    } else if (input.acceleration(Dimension.X) > 0) {

    } else {
    }
})
```

## 4. Überprüfung ob im Gleichgewicht

😬 **  Zu weit links oder rechts  ** ↙️ ↘️ 

► ``||logic:Wenn||`` diese ``||logic:<||`` **-100** ist, dann lehnt das Board zu weit nach links und ein Pfeil nach rechts soll auf dem ``||basic:Display||`` in die Richtung zeigen, auf die man sich lehnen soll. 👉

► ``||logic:Sonst wenn||`` diese ``||logic:>||`` **100** ist, dann lehnt das Board zu weit nach rechts, der Pfeil auf dem ``||basic:Display||`` muss nach links 👈 zeigen.

► In  beiden Fällen soll der ``||variables:zähler||`` auf **0** gesetzt werden.

🤩 ** Im Gleichgewicht! ** 🧘

► ``||logic:Ansonsten||`` ``||variables:ändere den zähler||`` um **1**

► Und ``||basic:zeige Zahl||`` ``||variables:zähler||``

```blocks
let zähler = 0
basic.forever(function () {
    if (input.acceleration(Dimension.X) < -100) {
        basic.showLeds(`
            . . # . .
            . . # # .
            # # # # #
            . . # # .
            . . # . .
            `)
        zähler = 0
    } else if (input.acceleration(Dimension.X) > 100) {
        basic.showLeds(`
            . . # . .
            . # # . .
            # # # # #
            . # # . .
            . . # . .
            `)
        zähler = 0
    } else {
        zähler += 1
        basic.showNumber(zähler)
    }
})
```

## 5. Überprüfung ob gewonnen

** Bin ich schon 5 Sekunden in Balance? ** 💪

► Überprüfe anschließend in einer neuen Abfrage: ``||logic:wenn||`` ``||variables:zähler||`` = 5?

► Dann ``||basic:zeige LEDs||``-Pokal. 🏆 Super!

► ``||basic:Pausieren||`` 5 Sekunde (5000 Milisekunden), damit man den Pokal länger sieht.

► Damit danach wieder ein Spiel gestartet werden kann,  ``||variables:setze zähler||`` wieder auf 0.

```blocks
let zähler = 0
basic.forever(function () {
    if (input.acceleration(Dimension.X) < -100) {
        basic.showLeds(`
            . . # . .
            . . # # .
            # # # # #
            . . # # .
            . . # . .
            `)
        zähler = 0
    } else if (input.acceleration(Dimension.X) > 100) {
        basic.showLeds(`
            . . # . .
            . # # . .
            # # # # #
            . # # . .
            . . # . .
            `)
        zähler = 0
    } else {
        zähler += 1
        basic.showNumber(zähler)
    }
    if (zähler == 5) {
        basic.showLeds(`
            # # # # #
            # # # # #
            . # # # .
            . . # . .
            . # # # .
            `)
        basic.pause(5000)
        zähler = 0
    }
})
```

## 6. Pausieren

⚠️ ** Achtung: Der @boardname@ kann sehr schnell zählen! ** ⚠️

► Wichtig: Vergiss ganz am Ende der  das ``||basic:Pausieren||`` von einer Sekunde (1000 Milisekunden) nicht!

```blocks
let zähler = 0
basic.forever(function () {
    if (input.acceleration(Dimension.X) < -100) {
        basic.showLeds(`
            . . # . .
            . . # # .
            # # # # #
            . . # # .
            . . # . .
            `)
        zähler = 0
    } else if (input.acceleration(Dimension.X) > 100) {
        basic.showLeds(`
            . . # . .
            . # # . .
            # # # # #
            . # # . .
            . . # . .
            `)
        zähler = 0
    } else {
        zähler += 1
        basic.showNumber(zähler)
    }
    if (zähler == 5) {
        basic.showLeds(`
            # # # # #
            # # # # #
            . # # # .
            . . # . .
            . # # # .
            `)
        basic.pause(5000)
        zähler = 0
    }
    basic.pause(1000)
})
```