esync - Verschlüsselte Synchronisation
======================================

Über das Programm
-----------------

`esync` ist ein Perl Script, das primär für Linux entwickelt wurde.
Der Zweck des Programmes ist es eine Verbindung zu einem Rootserver über SSH herzustellen (z.B. `sshfs` mount) und Dateien hoch- und runterzuladen.
Du kannst Dateien mit deinem öffentlichen Schlüssel per [gpg][1] verschlüsseln, so dass deine Dateien sicher vor allen sind, die den privaten Schlüssel dazu nicht besitzen.
Beim Hochladen kann `esync` ein komprimiertes TAR (.tar.gz) erzeugen, die Datei mit einem öffentlichen Schlüssel verschlüsseln und dann hochladen. Beim Herunterladen wird alles wieder rückgängig gemacht.

Du kannst `esync` als normaler User ausführen - es werden keine Root-Rechte benötigt.
Du kannst `esync` von der Kommandozeile mit parametern starten, aber es wird dich auch manchmal nach einer Bestätigung fragen.
Über eine Config-Datei in deinem Home-Verzeichnis kannst du das Tool konfigurieren. 

Wenn mehrere Personen sich einen Server teilen, kann jeder User seinen Key in einem gemeinsamen "Schlüssel-Verzeichnis" speichern.
Andere Benutzer können so deren öffentliche Schlüssel importieren und für sie Pakete verschlüsseln, die nur sie lesen können.

`esync`führt einige Operationen in einem "Sandbox" Verzeichnis aus und speichert heruntergeladen Dateien in einem speziellen "Eingansgverzeichnis", so dass das System nicht beschädigt werden kann.

Die folgenden Operation sind in `esync` bereits implementiert:
* Hilfe anzeigen
* Verwendung anzeigen
* Verfügbare Pakete auflisten
* Ein Paket hochladen (und verschlüsseln)
* Ein Paket herunterladen und entschlüsseln
* (Öffentliche) Schlüssel im gemeinsamen Schlüsselspeicher auflisten
* Einen öffentlichen Schlüssel in den gemeinsamen Schlüsselspeicher exportieren
* Alle öffentlichen Schlüssel aus dem Schlüsselspeicher importieren
* Temporäres Verzeichnis leeren

Natürlich müssen dafür alle benötigten Programme (`gpg`, `tar`, `cp`, `mv`, `mount`, etc.) installiert sein.

Warnung
-------

Obwohl ich glaube, dass die meisten Konzepte und Programme heute noch funktionieren müssten, möchte ich hervorheben, dass das Programm *2006* entwickelt wurde und es daher sein kann, dass einige der verwendeten Programm nicht mehr exakt so funktionieren wie damals.

Falls du  dolche Probleme entdeckst und dazu in der Lage bist, entwickle doch gerne einen Patch dafür. 

Ich übernehme KEINERLEI GARANTIE für das Programm `esync`.

Lizenz
------

`esync` ist lizensiert unter der [GNU Public License (GPL), Version 2][2].


[1]: http://www.gnupg.org/
[2]: http://www.gnu.org/licenses/gpl-2.0.html