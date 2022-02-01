# Heiße Kartoffel - Das Partyspiel

## Einführung @showdialog

In jeder Runde dieses Spiels wird durch Drücken des Buttons A eine Stoppuhr bei einer zufälligen Zahl gestartet. 
Wenn die Stoppuhr fertig heruntergezählt hat, zeigt sie ein Symbol an und die Person, die die Heiße Kartoffel gerade in der Hand hält scheidet aus.
Dann wird die nächste Runde gestartet, bis nur noch eine Person übrig ist.

## Schritt 1 @fullscreen

Das Ereignis ``||input:wenn Knopf A gedrückt||`` startet die Runde.

```blocks
input.onButtonPressed(Button.A, function () {
})
```

## Schritt 2 @fullscreen

Erstelle eine Variable ``||variables:zaehler||`` und ``||variables:setze||`` diese auf eine ``||math:zufällige Zahl||`` zwischen ``5`` and ``15``.

Die Variable ``||variables:zaehler||`` speichert den Startwert der Stoppuhr.

```blocks
let zaehler = 0
input.onButtonPressed(Button.A, function () {
    // @highlight
    zaehler = randint(5, 15)
})
```

## Schritt 3 @fullscreen

Verwende ``||basic:zeige Symbol||`` und das Hakerl um den Start der Stoppuhr / der Runde anzuzeigen.

```blocks
let zaehler = 0
input.onButtonPressed(Button.A, function () {
    zaehler = randint(5, 15)
    // @highlight
    basic.showIcon(IconNames.Yes)
})
```

## Schritt 4 @fullscreen


Die ``||loops:Während / Solange||``-Schleife soll so lange laufen wie ``||variables:zaehler||`` ``||logic:positiv / > 0 ||`` ist. 
Wenn die Stoppuhr negativ / < 0 ist, steigt er aus der Schleife aus und das Spiel ist vorbei.


```blocks
let zaehler = 0
input.onButtonPressed(Button.A, function () {
    zaehler = randint(5, 15)
    basic.showIcon(IconNames.Yes)
    // @highlight
    while (zaehler > 0) {
    }
})
```

## Schritt 5 @fullscreen

In der ``||loops:Während / Solange||``-Schleife, soll er bei jedem Durchlauf ``||variables:zaehler||`` um -1 ``||variables:ändern||``.
Da der @boardname@ sehr schnell rechnen kann, muss man bei jedem Durchlauf eine Sekunde (1000 ms) ``||basic:pausieren||``.

```blocks
let zaehler = 0
input.onButtonPressed(Button.A, function () {
    zaehler = randint(5, 15)
    basic.showIcon(IconNames.Yes)
    while (zaehler > 0) {
        // @highlight
        zaehler += -1
        // @highlight
        basic.pause(1000)
    }
})
```

## Schritt 6 @fullscreen

**Nach** der ``||loops:Während / Solange||``-Schleife soll er ``||basic:zeigen||``, dass die Runde vorbei ist und die Person mit dem @boardname@ in der Hand ausscheidet.

```blocks
let zaehler = 0
input.onButtonPressed(Button.A, function () {
    zaehler = randint(5, 15)
    basic.showIcon(IconNames.Yes)
    while (zaehler > 0) {
        zaehler += -1
        basic.pause(1000)
    }
    // @highlight
    basic.showIcon(IconNames.Skull)
})
```

## Schritt 7 @fullscreen

Jetzt den Code `|Download|` und auf deinen @boardname@ laden und los geht das Spiel!

<script src="https://makecode.com/gh-pages-embed.js"></script><script>makeCodeRender("{{ site.makecode.home_url }}", "{{ site.github.owner_name }}/{{ site.github.repository_name }}");</script>
