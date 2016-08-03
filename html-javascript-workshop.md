
# Browser Game Workshop: Blockout (deutsch)

Das Ziel dieses Workshops ist, dass Du selbst ein Browser Game programmierst.
Der Workshop teilt die Aufgabe in Teilaufgaben und beschreibt diese.
Mit den Hints solltest Du Anleitungen finden wie die einzelnen Teilaufgaben
gelöst werden können.

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
Rechteck schwarz und gib ihm einen dicken roten Rand.

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
Breite von 20 Pixel und mach den Ball rund. (Hint "border-radius")

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

### Aufgabe 9: Der Spielfeldrand

Sowohl der Ball als auch der Wing können aus dem Spielfeld geraten. Das verhindern wir in der Funktion
do_move().

Wenn der Wing das Spielfeld verlassen würde, dann setze die Position auf die maximal/minimal Position und
setzt die wing_direction auf 0.

Beim Ball ist es schwieriger. Wenn der Ball z.B. die linke Wand treffen würde (ball\_position\_x<0), dann
setze die ball\_position\_x auf 0 und drehe ball\_direction\_x um. Mach das vorerst für alle 4 Wände.

Probier es aus. Fliegt der Ball durch das Spielfeld und prallt sauber ab, oder gibt es noch Fehler ?
Verändere die Variablen ball\_speed, wing\_speed und den Timer Interval so, dass das Spiel flüssig
läuft.

### Aufgabe 10: Wing Kollision

Schreib eine neue Funktion wing_collision die folgende Aufgabe hat:
  
 - Prüfe ob der tief genug ist um mit dem Wing zu kollidieren
 - wenn ja prüfe ob die X Position des Balles auf die X position und Breite des wings passt und errechne eine 
   Wert zwischen 0 und 1, wobei 0 eine Ballberührung am linke Rand und 1 am rechte Rand des Wings bedeutet.
 - aus diesem Wert machen wir jetzt einen Winkel mithilfe dieser Formel 

	$$
	Winkel = PI/4+Wert*PI/2  
	$$

   Das sollte einen Winkel zwischen 45 und 135 Grad (in Radiant!) ergeben.
 - Errechne mit diesem Winkel (Sinus, Cosinus) und ball_speed, neue Werte für ball_direction.

Rufe nun die Funktion in do_move auf, und probiere ob der Wing funktioniert.

*Hint:* 
 - Winkel in Javascript: Math.PI, Math.sin(), Math.cos()
 - Nachdem die Berechnung nicht ganz trivial ist gib deine Werte im DIV "debug" aus. $('#debug').text(...).
   interessant sind Ball und Wing positionen, der errechnete wert 0 bis 1, der Winkel, die ball_direction.

### Aufgabe 11: Steine

Wir brauchen Funktionen die Steine erzeugen, verwalten und entfernen.

Definiere einen globalen leeren Array "bricks".

Definiere eine CSS class "brick" die einen Stein in Größe, Form und Farbe definiert.

Schreib eine neue Funktion "new_brick" mit der Input Paramtern: Position x, y, size_x, size_y

 - Erzeuge ein DOM Element mit $("<div class...");
 - Setze die Position X,Y und die Größe ( .css(...) )
 - Füge das Element dem DIV "field" hinzu.
 - Erzeuge ein lokales Javascript Objekt "brick" mit folgenden Attributen:
   - element: das neue DOM Element
   - pos_x
   - pox_y
   - size_x
   - size_y
 - Füge das Objekt "brick" dem Array "bricks" hinzu.

Schreibe ein Funktion "remove_brick" mit paramter i (eine id im bricks array) die 
den Brick aus dem DOM tree und aus dem brick array löscht.

Probiere die Funtionen im Console Window deines Browser aus. Du solltest
mit new_brick(..) und remove_brick(..) Steine erzeugen und löschen können.

*Hints:*
 - http://www.w3schools.com/js/js_arrays.asp
 - http://api.jquery.com/append/
 - http://www.w3schools.com/js/js_objects.asp
 - http://www.w3schools.com/jsref/jsref_push.asp
 - http://api.jquery.com/remove/
 - http://api.jquery.com/remove/
 - http://www.w3schools.com/jsref/jsref_splice.asp

### Aufgabe 12: Die Wand

Baue eine Funktion "start_level" und eine Funktion "build_wall".

"start_level" soll den Startwerte für ball und wing Position und Richtung setzen 
und build_wall aufrufen.

"build_wall" soll in einer doppelten Schleife 6 Reihen von Steinen in das Spielfeld setzen.
Rechne Dir anhand der Stein- und Spielfeldgröße eine sinvolle Anzahl an Steinen pro Reihe aus.
build_wall soll davor aber alle alten Steine löschen, indem du per jQuery alle class 
"brick" DOM element löscht und den "bricks" Array leerst.

"start_level" trägst Du jetzt in deine .ready() Funktion ein und Du solltest deine Bricks Wall sehen.

### Aufgabe 13: Stein Kollision

Noch fliegt der Ball durch die Steine ohne Schaden an zu richten, also schreiben wir eine Funktion
"brick_collision" die folgende Aufgaben enthält:

 - Geh in einer Schleife durch den Array "bricks" und prüfe ob sich Stein und Ball DIVs überdecken.
 - Wenn ja prüfe ob die X oder Y Überdeckung größer ist.
 - Ist die X Überdeckung größer soll der Ball an einer X Linie abprallen
 - Ist die Y Überdeckung größer soll der Ball an einer Y Linie abprallen
 - Wenn beide Überdeckungen gleich oder ähnlich gleich sind kannst Du den Ball komplett zurück prallen lassen
 - den betroffen Stein kannst Du mit der deiner Funktion remove_brick entfernen.

Das Abprallen kannst Du durch invertieren der der ball_direction erzielen.
"brick_collision" rufst Du jetzt dort auf wo auch "wing_collision" aufgerufen wird.

Probiere dein Spiel aus und beobachte ob alles sinnvoll aussieht. Wahrscheinlich kann man die 
den Algorithums für die Abprallrichtung verbessern.

### Aufgabe 14: Level Ende

Designe ein DIV "level_finished" das Du hinter das DIV "field" setzt. Das DIV soll eine netten groß 
geschriebenen Text beinhalten und mittig über dem Spielfeld liegen. Nach dem Designen versteckst Du 
das DIV aber noch per CSS Style (Siehe CSS: display)

Irgendwann sind alle Steine eliminiert. Das können wir leicht festellen indem wir am Beginn der "brick_collision"
prüfen wie lang der Array "bricks" ist. Ist der Array leer rufen die Funktion "level_finished" auf.

Diese Funktion "level_finished" soll das DIV "level_finished" anzeigen und einen 5 Sekunden Timer setzen 
der start_level aufruft. In "start_level" musst Du den "level_finished" wieder verschwinden lassen.

*Hints:* 
 - http://www.w3schools.com/cssref/pr_class_display.asp
 - http://api.jquery.com/show/
 - http://www.w3schools.com/jsref/met_win_settimeout.asp

### Aufgabe 15: Game Over

Definiere ein global Variable "lifes" und setze sie auf 5.

Definiere ein DIV "game_over", das so wie "level_finished" aussieht, und ein DIV "lifes" das
Du rechts neben dem Spielfeld platzierst. In "start_level" schreibst Du per jQuery die
Variable "lifes" in das DIV "lifes"

Noch kann der Spieler nicht verlieren. Es fehlt noch die Prüfung ob der Ball unten rausfliegt.
In "do_move" kannst Du die Y Position des Balls abfragen. Ist sie unterhalb des "field" DIV
rufst Du die Funktion "ball_dropped" auf:

In "ball_dropped" setze du ball_direction auf 0 und reduzierst Du die variable "lifes" um eins, 
und zeigst dies im DIV "lifes" an.

Ist jetzt "lifes" größer 0, setze Du ball_position auf einen sinnvollen Wert,
und mit einem 2 Sekunden Timer setzt Du ball_direction auf eine Richtung die nach
oben zeigt. Das kannst Du direkt im setTimeout Aufruf als inline Funktion erledigen.

Ist "lifes" auf 0 zeigst Du das DIV "game_over" an.

Damit man das offene untere Ende des Spielfelds erkennt, entferne den unteren border 
der DIVs "field"

Fertig!

Probier Dein Spiel aus. Wenn es funktioniert und Du die Möglichkeit hast dein Spiel auf
einen öffentlichen Webserver zu stellen, schick mir doch das URL an alex@mail.at.

