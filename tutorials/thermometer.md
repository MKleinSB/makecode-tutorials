# Thermometer

## Introduction @unplugged

Mit dem integrierten Temperatursensor kann ein Thermometer mit dem Calliope mini entwickelt werden. Wenn es wärmer wird, dann wird die LED-Matrix aufgeladen und die RGB-LED leuchtet in entsprechend kälteren Farbtönen.

## Step 1

### Variable für die Temperatur anlegen.

Als erstens legen wir eine Variable für die Temperatur an. 
- Erstelle eine ``||variables.Variable||``
- Nenne diese ``Temperatur``

![alt text](https://raw.githubusercontent.com/jasperp92/makecode-tutorials/master/assets/images/variablen.gif)

```template
basic.forever(function () {

})
```

## Step 2

### Temperatursensor auslesen

Verwende den ``||input.Eingabe-Block||``, um die Temperatur zu messen. Die
gemessene Temperatur sollst du in deine ``||variables.Variable||`` schreiben.

```blocks
let Temperatur = 0
basic.forever(function () {
    Temperatur = input.temperature()
})
```

## Step 3

### Temperatur prüfen

Jetzt kommt Farbe ins Spiel: Je nachdem welcher Temperatur, soll die
RGB-LED in einer anderen Farbe leuchten und die LED-Matrix sich auffüllen.
- Ergänze unter dem letzten ``||basic.Zeige Zahl||`` Block eine ``||logic.Wenn/dann||`` Bedingung
- Füge einen logischen Vergleich ein in
denen du prüfst ob eine Temperatur über oder unterschritten wurde.
Dazu wählst du ein aus den Logikblöcken ein ``||logic.<||`` aus, 
fügst es in die Wenn/dann Bedingung ein.
- Prüfe ob die ``Temperatur < 10`` ist
- ``||basic.Setzte die RGB-Farbe||`` auf blau

```blocks
let Temperatur = 0
basic.forever(function () {
    Temperatur = input.temperature()
    if (Temperatur < 10) {
        basic.showLeds(`
            . . . . .
            . . . . .
            . . . . .
            . . . . .
            # . . . .
            `)
        basic.setLedColor(0x007fff)
    } else {
    	
    }
})

```

## Step 4

### Aufgabe: Mehrfachverzweigung

Wenn es unter 10 °C ist, soll die LED blau leuchten und ein Balken auf der LED-Matrix angezeigt werden.  
Wenn es über 10 °C und unter 15 °C ist, soll die LED grün leuchten und zwei Balken auf der LED-Matrix angezeigt werden.  

- Füge in der Verzweigung über das **+** einen weiteren Vergleich hinzu, der prüft, ob die Temperatur unter 15 °C liegt.
- ``||basic.Setzte die RGB-Farbe||`` auf grün
- Schalte zwei Reihen der ``||basic.LED-Matrix||`` 

*Eine Mehrfachverzweigung prüft von oben nach unten jede Bedingung durch und wird beendet wenn die erste Bedingung wahr ist. Die Reihenfolge ist deshalb entscheidend!*

```blocks
let Temperatur = 0
basic.forever(function () {
    Temperatur = input.temperature()
    if (Temperatur < 10) {
        basic.showLeds(`
            . . . . .
            . . . . .
            . . . . .
            . . . . .
            # . . . .
            `)
        basic.setLedColor(0x007fff)
    } else if (Temperatur < 15) {
        basic.showLeds(`
            . . . . .
            . . . . .
            . . . . .
            . # . . .
            # # . . .
            `)
        basic.setLedColor(0x00ff00)
    } else {
    	
    }
})

```

## Step 5

### Aufgabe: Weitere Temperaturbereiche definieren

Je wärmer es wird, desto wärmer leuchtet die RGB-LED und umso mehr Reihen werden aufgefüllt.  

- Füge 3 weitere Vergleiche zu der Mehrfachverzweigung hinzu, die in 5er Schritten die Temperatur prüfen.
- In der letzten Verzweigung sollen die Maximalwerte erreicht sein und die RGB-LED rot leuchten sowie alle LED-Reihen angeschaltet sein.

*Tipp: Du kannst die LED-Blöcke und Vergleiche einfach mit Strg+C und Strg+V rüberkopieren.*

```blocks
let Temperatur = 0
basic.forever(function () {
    Temperatur = input.temperature()
    basic.showNumber(Temperatur)
    if (Temperatur < 10) {
        basic.setLedColor(0x007fff)
        basic.showLeds(`
            . . . . .
            . . . . .
            . . . . .
            . . . . .
            # . . . .
            `)
    } else if (Temperatur < 15) {
        basic.setLedColor(0x00ff00)
        basic.showLeds(`
            . . . . .
            . . . . .
            . . . . .
            . # . . .
            # # . . .
            `)
    } else if (Temperatur < 20) {
        basic.setLedColor(0xffff00)
        basic.showLeds(`
            . . . . .
            . . . . .
            . . # . .
            . # # . .
            # # # . .
            `)
    } else if (Temperatur < 25) {
        basic.setLedColor(0xff8000)
        basic.showLeds(`
            . . . . .
            . . . # .
            . . # # .
            . # # # .
            # # # # .
            `)
    } else if  (Temperatur >= 25) {
        basic.setLedColor(0xff0000)
        basic.showLeds(`
            . . . . #
            . . . # #
            . . # # #
            . # # # #
            # # # # #
            `)
    }
})
```

## Step 6

### Fertig ist das Thermometer!

Geschafft! Passe gerne die Schwellenwerte nach der Temperatur an, die du auf dem Display siehst,
so dass der Wechsel der LED-Farbe auch bei geringeren Temperaturschwankungen zu sehen ist.

*Wenn die anderen Temperaturbereiche schon abgesteckt sind, kannst du 
die rote LED auch für die Maximaltemperatur, in die ansonsten-Bedingung ohne Vergleich einfügen.
Beides führt zum gleichen Ergebnis!*

```blocks
let Temperatur = 0
basic.forever(function () {
    Temperatur = input.temperature()
    basic.showNumber(Temperatur)
    if (Temperatur < 10) {
        basic.setLedColor(0x007fff)
        basic.showLeds(`
            . . . . .
            . . . . .
            . . . . .
            . . . . .
            # . . . .
            `)
    } else if (Temperatur < 15) {
        basic.setLedColor(0x00ff00)
        basic.showLeds(`
            . . . . .
            . . . . .
            . . . . .
            . # . . .
            # # . . .
            `)
    } else if (Temperatur < 20) {
        basic.setLedColor(0xffff00)
        basic.showLeds(`
            . . . . .
            . . . . .
            . . # . .
            . # # . .
            # # # . .
            `)
    } else if (Temperatur < 25) {
        basic.setLedColor(0xff8000)
        basic.showLeds(`
            . . . . .
            . . . # .
            . . # # .
            . # # # .
            # # # # .
            `)
    } else {
        basic.setLedColor(0xff0000)
        basic.showLeds(`
            . . . . #
            . . . # #
            . . # # #
            . # # # #
            # # # # #
            `)
    }
})
```