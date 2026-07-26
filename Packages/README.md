# Optionale Packages

Diese Dateien stammen aus demselben Export, werden aber von der aktuellen
Standalone-Konfiguration `../brinkflair400.yaml` nicht eingebunden.

Sie verwenden den Modbus-Controller mit der ID `brink`, während die
Standalone-Datei derzeit `${name}` als Controller-ID nutzt. Außerdem
überschneiden sich zahlreiche Sensoren und Register mit der Hauptdatei.

Die Packages deshalb nur nach einer bewussten Zusammenführung aktivieren.
Ein direktes Hinzufügen aller Dateien zu einem `packages:`-Block würde
doppelte Entitäten erzeugen und ist nicht als getestete Konfiguration
freigegeben.
