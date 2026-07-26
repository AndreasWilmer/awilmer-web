Hier müssen zwei echte Bilddateien rein, bevor die Seite fertig ist:

1. home-head-1.jpg
   Quelle: dein wget2-Mirror unter .../awilmer.de/wp-content/uploads/2020/12/home-head-1.jpg
   Verwendung: Hero-Hintergrundbild auf der Startseite (index.html)

2. favicon.ico
   Quelle: dein wget2-Mirror unter .../awilmer.de/wp-content/themes/jupiterx/lib/favicon.ico
   Verwendung: Browser-Tab-Icon (in allen HTML-Dateien via <link rel="icon"> verlinkt)

Einfach beide Dateien 1:1 in diesen images/-Ordner kopieren — die Dateinamen
müssen exakt so bleiben (home-head-1.jpg, favicon.ico), sonst zeigen
index.html und die Kopfzeilen der anderen Seiten auf ein leeres Bild.

Das Logo (Logo-1.png aus dem Original) wird NICHT gebraucht — das Logo ist
als Inline-SVG direkt im HTML gebaut (Hexagon + W-Form), damit es
verlustfrei skaliert und keine zusätzliche Bilddatei braucht.
