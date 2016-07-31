
# Browser Game: Blockout Workshop (deutsch)


### Aufgabe 1: HTML Seite

Erstelle einen einfache HTML5 Seite mit Namen "blockout.html", die folgenden 
Bereiche beinhaltet:

 - einer STYLE (css) Section 
 - verlinke jQuery (>=3.1)
 - einer Javascript Section mit der jQuery Startfuntion $(document).ready(..)
 - einem DIV im BODY mit ID "field"

öffne die Seite in Chrome und prüfe in den "Developer Tools" (CTRL-SHIFT I) 
ob die Seite Fehlerfrei lädt.

*Hint:* http://alext.mail.at/wp-content/uploads/2014/11/html5-skeleton.html

### Aufgabe 2: Spielfeld

Positioniere das DIV "field" mit absoluten Koordinaten 20 Pixel von links und
20 Pixel von oben, und mache as 800 mal 600  Pixel groß. Außerdem mach diese
Rechteck schwarz und gib einen dicken roten Rand.

Schau die das Ergebnis im Browser an.

*Hint:* Google nach CSS Styles und position, left, top, color, oder border 

### Aufgabe 3: Wing

Erzeuge ein zweites DIV mit ID "wing" im DIV "field" un gib im einige styles:

 - positioniere es 20 Pixel vom unteren Rand
 - und 200 Pixel von links
 - färbe es weiß
 - mach es 60 mal 10 Pixel groß
 - und Runde die Ecken ein wenig ab

*Hint:* 

 - http://www.w3schools.com/css/css_positioning.asp erklärt wie die Positionierung 
   von Objekten in Objekten funktioniert
 - CSS Style border-radius

### Aufgabe 4: Tastatur

Füge eine Funktion "keyboardhandler" mit dem Parameter "event" in die Javascript Section ein
und registriere diese Funktion als handler für die keydown und keyup events. Das Registrieren als
Handler funktioniert mit der jQuery Funktion ".on()" die du in deine "ready()" Funktion schreibst. 
Der Tastendruck soll auf dem ganzen Dokument erkannt werden ( "$(document).on(...)" ) und benötigt 
keine "selector" oder "data".

In deiner Function "keyboardhandler" gib zum Test die übergebene Variable "event" 
in die console aus ( "console.log(...)" ).

Öffne in deinem Browser die "Developer Tools - Console", klicke in deine HTML Seite, drücke
ein Taste auf der Tastatur und schau Dir in der Console an ob es eine Fehler gibt, oder schau dir
den Inhalt der Variable "event" an.

*Hints:* 
 - Definieren einer Funktion: http://www.w3schools.com/js/js_functions.asp
 - https://api.jquery.com/on/  (" $(document).on("keydown",keyboardhandler); ")

### Aufgabe 5: Debug

Erzeuge ein kleines DIV element mit ID "debug" außerhalb des DIV "field" und positioniere
es Rechts neben dem Spielfeld ("field"). In diesem DIV können wir kleine Informationen 
ausgeben die uns beim Testen helfen.

Jetzt kümmern wir uns um die Funktion "keyboardhanlder". Wie Du in der Console gesehen hast,
gibt es in der übergebenen Variable "event" einige Informationen. Geben wir diese zum Test in
das neue DIV "debug" aus.

Lassen wir uns den Inhalt von "event.key" und "event.type" im DIV "debug" anzeigen.
Benutze dazu die jQuery Funktion: 

> $("selector").text("text")

Selector soll das DIV "debug" sein und "text"  bauest Du indem Du einen
String aus den interessanten event Inhalten zusammenbaust:

> event.key + " " + event.type 

Merke Dir die key und type Werte für das Drücken und Loslassen der Linken und Rechten Cursor Taste.

*Hints:* 
 - Wie baut man jQuery selectors: http://www.w3schools.com/jquery/jquery_selectors.asp
 - die ".text()" Funktion: http://api.jquery.com/text/

### Aufgabe 6: Set Move

Wir werden das Element "wing" öfter verwenden also definieren wir eine global Variable "wing"
und weißen ihr in unserer .ready Funktion per jQuery das Element "wing" zu. 

 - Globale Variable definiert man mit "var variablename;" außerhalb aller JavaScript Funktionen,
aber innerhalb des "script" Bereichs. 
 - Mit $("selector") erhältst Du das jQuery Objekt des Wing elements, 
wenn Du den richtigen selector verwendest.

Außerdem definieren wir drei globale Variablen für die Wing Bewegung:

 - wing_position=100: Die aktuelle Position in Pixel
 - wing_direction=0: Die atuelle Richtung in Pixel/Interval
 - wing_speed=10: Die Wing Geschwindigkeit in Pixel/Interval

In den keyboard handler können wir bei den Richtigen type/key Kombinationen 
wing_direction auf wing_speed, -wing_speed, oder 0 setzten. Das sollte mit 
drei "if ( a=b && c=d )" statements erledigt sein.

Noch bewegt sich nichts aber alles ist bereit.

*Hints:* 
 - http://www.w3schools.com/js/js\_if\_else.asp
 - http://www.w3schools.com/js/js_comparisons.asp

### Aufgabe 7: Do Move

Definiere eine neue Funktion mit namen "do_move()" ohne parameter.

In dieser Funktion berechnen wir die Position und die Bewegung des Wings und 
setzen die Position des Wing Elements:
 
 - Zuerst prüfen wir ob direction ungleich 0 ist 
   - wenn ja dann berechne die neue wing_position
   - und setzen diese mit unserer global variable "wing" und der jQuery funktion ".css()"

Damit do_move() jetzt aufgerufen wird, benutzen wir "setInterval(function,milliseconds);".
Du  kannst setInterval in deiner "ready()" Funktion aufrufen. "function" ist unser
"do_move" und für milliseconds nehmen wir 1/10 Sekunde (wieviel milliseconds sind das ?)

Teste es in deinem Browser, wenn Du den Wing nicht steuern kannst, schau in die
"Developer Tools - Console" ob dort ein Fehler angezeigt wird.

In der Developer Console kannst Du auch mit "wing_position=42" die Bewegung testen.

*Hints:*
 - Setzen der Position: http://api.jquery.com/css/ "wing.css(left,...);"
 - Der parameter zu "left:" sollte ein Sting sein der so aussieht "100px";
 - http://www.w3schools.com/jsref/met\_win\_setinterval.asp

### Aufgabe 8: Der Ball

Für den Ball definiere ein weiteres DIV Element mit ID "ball" innerhalb des DIV "field". 
Wie beim Wing kannst Du die Position, Form und Farbe per CSS setzen. Setze eine Höhe und 
Breite von 20 Pixel und mach den Ball rund. (Hint "border_radius")

Wie für den Wing erzeugen wir ein paar globale Variablen, diesmal haben wir aber
X und Y Koordinaten und Richtungen:

 - ball;  Wie bei "wing" erzeuge eine globale Variable "ball" für des jQuery Objekt 
 - ball\_position\_x=400;
 - ball\_position\_y=500;
 - ball_speed=10;
 - ball\_direction\_x=7;
 - ball\_direction\_y=-7;

Deine Funktion do_move() muss jetzt so erweitert werden, dass Sie nicht nur den Wing sondern
auch den Ball bewegt.

Wenn Du das jetzt ausprobierst wird der Ball einfach aus dem Spielfeld fliegen. Also weiter zu Aufgabe 9.

### Aufgabe 9: Die Wand

Sowohl der Ball als auch der Wing können aus dem Spielfeld geraten. Das verhindern wir in der Funktion
do_move().

Wenn der Wing das Spielfeld verlassen würde, dann setze die Position auf die maximal/minimal Position und
setzt die wing_direction auf 0.

Beim Ball ist es schwieriger. Wenn der Ball z.B. die linke Wand treffen würde (ball\_position\_x<0), dann
setze die ball\_position\_x auf 0 und drehe ball\_direction\_x um. Mach das vorerst für alle 4 Wände.

Probier es aus. Fliegt der Ball durch das Spielfeld und prallt sauber ab, oder gibt es noch Fehler ?

