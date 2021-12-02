### @activities 1

## Battlebot - programmering av en enkel fjernkontroll

### Programmer fjernkontroll @unplugged
Vi skal nå programmere en enkel fjernkontroll som styrer battleboten vår.   
Vi skal bruke sensorene og knappene til micro:bit for å styre battleboten.  
__Knapp A__ - styrer battleboten _fremover_   
__Knapp B__ - styrer battleboten _bakover_  
__Roll__ - styrer om battleboten svinger til _høyre_ eller _venstre_  
__Knapp A+B__ - stopper battleboten  

## Styring

### Steg 1
Vi vil at fjernkontrollen skal sende et signal til battleboten når knapp A trykkes. Dette kan være et tall. 
Hent ``||input:når knapp A trykkes||`` fra inndata. Hent ``||radio:radio send tall||`` fra radio. Velg selv hvilket tall som skal bety fremover. Dette må dere huske når dere etterpå programmerer microbiten i battleboten.

```blocks
input.onButtonPressed(Button.A, function () {
    radio.sendNumber(1)
})
```

### Steg 2

Vi skal nå gjenta det samme for knapp B. Hent ``||input:når knapp A trykkes||`` fra inndata. Endre denne til knapp B. Hent ``||radio:radio send tall||`` fra radio. Velg selv hvilket tall som skal bety bakover.

```blocks
input.onButtonPressed(Button.A, function () {
    radio.sendNumber(1)
})
input.onButtonPressed(Button.B, function () {
    radio.sendNumber(2)
})
```

### Roll @unplugged
Vi skal styre __Roll__ ved å vri fjernkontrollen mot høyre eller venstre.
Dette kan vi gjøre ved å bruke blokkene ``||input:når helning venstre||`` og ``||input:når helning høyre||`` fra inndata.
![Roll](https://github.com/olauk/static/blob/master/Roll.png?raw=true)

### Steg 4

Hent ``||input:når ristes||`` fra inndata. Endre denne til ``||input:når helning venstre||``. Hent ``||radio:radio send tall||`` fra radio. Velg selv hvilket tall som skal bety snu til venstre.

```blocks
input.onGesture(Gesture.TiltLeft, function () {
    radio.sendNumber(3)
})
```

### Steg 5
Vi skal nå gjøre det samme for å snu til høyre:   
Hent ``||input:når ristes||`` fra inndata. Endre denne til ``||input:når helning høyre||`` Hent ``||radio:radio send tall||`` fra radio. Velg selv hvilket tall som skal bety snu til høyre.

```blocks
input.onGesture(Gesture.TiltLeft, function () {
    radio.sendNumber(3)
})
input.onGesture(Gesture.TiltRight, function () {
    radio.sendNumber(4)
})
```

### Stopp @unplugged
Det er lurt å ha en mulighet for å stoppe battleboten.
Dette kan gjøres på ulike måter. Vi viser her hvordan dere kan gjøre det ved å bruke ``||input:når knapp A trykkes||``

### Steg 6
Hent ``||input:når knapp A trykkes||`` fra inndata. Hent ``||radio:radio send tall||`` fra radio. Velg selv hvilket tall som skal bety stopp.
```blocks
input.onButtonPressed(Button.AB, function () {
    radio.sendNumber(0)
})
```
### Steg 7
For at vi skal kunne kommunisere med riktig micro:bit er det viktig at både fjernkontroll og mottaker er på samme radiogruppe.   
Hent ``||radio:sett radiogruppe||`` fra radio og plasser i ved start. Sett radiogruppe til et nummer som ingen av de andre gruppene bruker. 

```blocks
radio.setGroup(xx)
```
