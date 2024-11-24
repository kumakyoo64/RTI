# Raster-Trick-Images

Ein Programm zum Erstellen von Raster-Trick-Bildern auf dem C64. Bei
den Raster-Trick-Bildern handelt es sich um Grafiken, die in den Text
eingebettet werden können, wie das beispielsweise bei dem bekannten
Spiel "Pirates!" gemacht wird.

Im Unterschied dazu werden bei den Raster-Trick-Bildern aber Sprites
und Raster-Tricks genutzt, um die Grafikfähigkeiten des C64 zu
erweitern.

## Systemvoraussetzungen

Es werden Java und ACME (Assembler-Cross-Compiler) benötigt. Das
Programm SNG (wandelt PNG-Dateien in Text-Dateien um) kann hilfreich
sein.

## Ein Raster-Trick-Bild erstellen

1. RTI.java compilieren: `javac RTI.java`
2. Eine rti-Datei erstellen: Siehe sonderangebot.rti für ein Beispiel.
3. Programm starten: `java RTI -p -o sonderangebot sonderangebot.rti`

   Das Programm erzeugt drei neue Dateien: sonderangebot.plain (das
   Ergebnis wie in der Eingabe), sonderangebot.sng (kann man mit dem
   SNG in eine png-Datei umwandeln und dann am PC anschauen) und
   sonderangebot.a.

4. Die ACME-Datei kompilieren: `acme sonderangebot.a`

   Hierfür werden die beiden Dateien `rti_macros.a` und
   `rt_macros.a` benötigt.

   Das Ergebnis ist eine Datei `sonderangebot.prg`. Diese
   Datei enthält ein C64-Programm, welches man mit SYS49152
   starten und mit SYS49155 beenden kann.

## Einschränkungen

Bekannte Einschränkungen sind derzeit:

- Die ersten vier Zeilen in der RTI-Datei sind fix, das Bild muss also
  zwingend 88x88 Pixel (=11x11-Blocks) groß sein und sich an Position
  1x1 befinden.

- Derzeit werden an Raster-Tricks nur ein Sprite-Multiplexer genutzt.
  Mit weiteren Tricks wären bessere Bilder möglich.
