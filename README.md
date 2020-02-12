# PWA Webtech 2020
In diesem Repository sind alle Dateien für die PWA-Übung abgelegt. Einfach als ZIP runterladen und lokal bei euch speichern.
Plus findet ihr hier die Präsi mit der Theorie.
[Link zur Präsi](http://lea-moser.ch/webtech-mmp18_leamoser_pwa.pdf)

## Ordner "Test-PWA_Ausgangslage"
Mit diesen Dateien wird die Programmierung des PWA gestartet, Instruktionen folgen im Unterricht. Bitte öffnet diese Dateien dann im Atom und lädt sie per FTP-Config auf einen Server (sonst geht das mit dem PWA leider nicht). 

Für jene dies nicht mehr ganz präsent haben, hier die Angaben die in der FTP-Config Datei gemacht werden müssen:

![alt text][logo]

[logo]: https://github.com/leamoser/pwa/blob/master/ftpconfig.png "FTP Config"

## Ordner "Test-PWA"
Das ist das fertige PWA, also die Lösung :) 

# Ein PWA Schritt für Schritt
Da es mit der Anleitung in der Präsi einige Probleme gegeben hat (war glaubs zu wenig ausführlich) ergänze ich hier noch eine Ausführliche Schritt für Schritt Anleitung. 

## Grundlage
1. Programmiert eine Responsive Webseite und lädt diese auf einen Webserver (wenn's ein HTW-Server ist in's Web-Verzeichnis).

## Manifest & Icons
1. Erstellt im Ordner, wo ihr die Webseite programmiert habt, einen Ordner **Icons**. 
2. Geht auf diese Webseite (https://www.favicon-generator.org/) und lädt das Icon hoch, das nachher euer Appicon sein soll. Die Häckchen unten könnt ihr ignorieren, die stimmen standartmässig.
3. Dann auf **Create Favicon** klicken und warten.
4. Lädt dann einerseits die generierten Icons runter (in dem ZIP, dass ihr runterlädt ist dann auch das Manifest drin) und kopiert den generierten Quellcode in den Head eurer Seite (muss auf jeder Unterseite eingefügt werden). 
5. Alles was im ZIP ist speichert ihr in eurem neu erstellten Ordner **Icons** ab. Ausser die Datei **manifest.json**, die verschiebt ihr ins Root-Verzeichnis eurer Webseite.
6. Im ganzen Code (mit den Iconverlinkungen und so) den ihr vorher in euren Head eingefügt habt müsst ihr noch die Pfade anpassen, damit auch die richtigen Daten geladen werden. 
7. Auch im Manifest müsst ihr die Pfade zu den Icons anpassen.
8. Ergänzt abschliessend noch folgende Angaben zuoberst in der Datei **manifest.json**.
```
"short_name" : "Kurzname",
"lang" : "de-CH",
"start_url" : "Url der Seite",
"background_color" : "#3B46FF",
"theme_color" : "#35CDE8",
"display" : "standalone",
"scope": "/",
"generated" : "undefined",
```

**Euer Manifest müsste jetzt richtig angezeigt werden**

## Service Worker
1. Kopiert die URL eurer Webseite, auf der ihr euer PWA am aufbauen seid.
2. Öffnet diese Webseite (https://www.pwabuilder.com/) und fügt euere URL ein und klickt auf **Start**
3. Jetzt solltet ihr beim ersten Block auf der Webseite (Manifest) 40/40 Punkten, beim zweiten Block (Service Worker) 0/40. 
4. Klickt unterhalb des zweiten Blocks auf **Choose a Service Worker**.
5. Wählt in der linken Spalte den Service Worker mit dem Namen **Cache-First network**.
6. Kopiert den Code oben in einen `<script></script>` Tag am Ende der Startseite eurer Webseite. 
7. Erstellt eine Datei mit dem Namen **pwabuilder-sw.js** im Root-Verzeichnis eurer Webseite und fügt den Code dort ein. 

**Euer Service-Worker sollte nun funktionieren**

## Offline Pages definieren
Damit auch wirklich etwas offline angezeigt wird, müsst ihr die Seiten definieren, die vorgängig in den Zwischenspeicher der Webseite gelegt werden sollen. Das mach ihr in der Datei **pwabulder-sw.js** auf Zeile 5:
```
const CACHE = "pwabuilder-precache";
const precacheFiles = [
  /* Add an array of files to precache for your app */
  /*Das sind jetzt einfach Beispielseiten, hier kommen dann eure eigenen Seiten*/ "index.html", "style.css", "page2.html", "page3.html", "page4.html", "pwabuilder-sw.js", "color-wheel.png"
];
```
