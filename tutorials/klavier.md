# Klavier

## Einführung @unplugged

Halte den Calliope mit einer Hand am (-)–Pin. Lass verschiedene Töne erklingen,
indem du mit einem Finger der anderen Hand einen der anderen Pins berührst.


## Step 1

Um einen Ton auf Pin 0 abzuspielen zu können, muss der Block ``||music.spiele Note||`` hinzugefügt werden.
Lege anschließend eine Note und einen Schlag, beziehungsweise die Dauer des Tons fest.

```blocks
input.onPinTouchEvent(TouchPin.P0, input.buttonEventDown(), function () {
    music.playTone(262, music.beat(BeatFraction.Quarter))
})
```

## Step 2

Wir möchte außerdem noch sehen, welche Note gerade gespielt wird, sowie eine LED dazu aufblinken lassen.  
Wähle dazu die Blöcke ``||basic.setze RGB-LED-Farbe auf||`` und ``||basic.zeige Text||`` aus.  
Setze RGB-LED auf eine Farbe deiner Wahl. Der Text sollte mit dem Buchstaben deiner Note übereinstimmen.

```blocks
input.onPinTouchEvent(TouchPin.P0, input.buttonEventDown(), function () {
    basic.setLedColor(0xff0000)
    basic.showString("C")
    music.playTone(262, music.beat(BeatFraction.Quarter))
})
```

## Step 3 

Vermutlich hast du dich gefragt, weshalb die RGB-LED und LED-Matrix in dem Hinweis vor dem Spielen der Note angeschaltet wurden!?  
Das hat den Grund, dass wir diese während und nicht nach dem Abspielen der Note angeschaltet haben möchten.
Schalte den LED-Bildschirm und die RGB-LED mit den beiden Blöcken ``||basic.Bildschirminhalt löschen||`` ``||basic.eingebaute RGB-LED ausschalten||`` wieder aus!

```blocks
input.onPinTouchEvent(TouchPin.P0, input.buttonEventDown(), function () {
    basic.setLedColor(0xff0000)
    basic.showString("C")
    music.playTone(262, music.beat(BeatFraction.Quarter))
    basic.turnRgbLedOff()
    basic.clearScreen()
})
```

## Step 4

Fast geschafft! Jetzt wiederhole diese Schritte für die 3 weiteren Pins und ändere entsprechend die Note, den Text auf dem Bildschirm und die Farbe der RGB-LED.  
Kleiner Tipp: Du kannst mit Strg+C und Strg+V die Blöcke ganz einfach kopieren.

```blocks
input.onPinTouchEvent(TouchPin.P0, input.buttonEventDown(), function () {
    basic.setLedColor(0xff0000)
    basic.showString("C")
    music.playTone(262, music.beat(BeatFraction.Quarter))
    basic.turnRgbLedOff()
    basic.clearScreen()
})
input.onPinTouchEvent(TouchPin.P3, input.buttonEventDown(), function () {
    basic.setLedColor(0x00ff00)
    basic.showString("A")
    music.playTone(440, music.beat(BeatFraction.Quarter))
    basic.turnRgbLedOff()
    basic.clearScreen()
})
input.onPinTouchEvent(TouchPin.P2, input.buttonEventDown(), function () {
    basic.setLedColor(0xffff00)
    basic.showString("F")
    music.playTone(349, music.beat(BeatFraction.Quarter))
    basic.turnRgbLedOff()
    basic.clearScreen()
})
input.onPinTouchEvent(TouchPin.P1, input.buttonEventDown(), function () {
    basic.setLedColor(0x0000ff)
    basic.showString("H")
    music.playTone(494, music.beat(BeatFraction.Quarter))
    basic.turnRgbLedOff()
    basic.clearScreen()
})
```

## Step 5

Super, dein Klavier ist fertig!  
Klicke auf ``|Herunterladen|``, um dein Programm auf deinen Calliope mini zu übertragen und Klavier zu spielen.

```template
input.onPinTouchEvent(TouchPin.P0, input.buttonEventDown(), function () {
	
})
```
