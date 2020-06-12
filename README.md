# M300-Services
## TBZ M300 LB02
### K1
VirtualBox, Vagrant und VSCode sind installiert.
Git-Client ist installiert und konfiguriert.
SSH-Key-Pair ist erstellt und zum SSH-Agent hinzugefügt worden.

### K2
GitHub Account ist erstellt.
Git-Client wurde für Initialisierung des Repos verwendet. Push-Pull & Commit wird via VSCode erledigt.

VSCode wird als Markdown Editor verwendet, mit installiertem Markdown Paket vom VSCode Marketplace.

### K3
Zwei CentOS VMs sind eingerichtet. VM01 als Webserver, VM02 als DB-Server.
Die wichtigsten Vagrant Befehle kenne ich:
| Befehl                    | Beschreibung                                                      |
| ------------------------- | ----------------------------------------------------------------- | 
| `vagrant init`            | Initialisiert im aktuellen Verzeichnis eine Vagrant-Umgebung und erstellt, falls nicht vorhanden, ein Vagrantfile |
| `vagrant up`              |  Erzeugt und Konfiguriert eine neue Virtuelle Maschine, basierend auf dem Vagrantfile |
| `vagrant ssh`             | Baut eine SSH-Verbindung zur gewünschten VM auf                   |
| `vagrant status`          | Zeigt den aktuellen Status der VM an                              |
| `vagrant port`            | Zeigt die Weitergeleiteten Ports der VM an                        |
| `vagrant halt`            | Stoppt die laufende Virtuelle Maschine                            |
| `vagrant destroy`         | Stoppt die Virtuelle Maschine und zerstört sie.                   |
