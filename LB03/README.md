# M300 Services
## TBZ M300 LB03
Laura Weber, Marc Vogelmann

### Aktueller persönlicher Wissensstand
Unser Wissensstand bezüglich containerisierung und Microservices, war zu Beginn des Modules eher gering. Da wir Mittwochnachmittags das Wahlmodul W906 haben, konnten wir uns jedoch bereits einiges an Wissen aneignen. Marc Vogelmann hat im Voraus bereits mit Kubernetes gearbeitet, jedoch immer nur als Proof of Concept und in seinem Arbeitsumfeld werden Microservices noch nicht betrieben.
Laura Weber hat im Voraus noch nicht mit Microservices gearbeitet, aber "schon davon gehört" und mit unserer Zusammenarbeit in der TBZ in einem oder anderem Modul Microservices kurz kennengelernt.

### Probleme mit Kubernetes
Wir wollten diese LB mit Kubernetes als Orchestrierungslösung erledigen, leider hatten wir einige Probleme mit Containern die persistent Volume Claims brauchen. Container wie einfache Webserver funktionierten ohne Probleme. Da diese LB aber einen höheren Anspruch hat, als einen einfachen "Hello World" Webserver und wir dem gerecht werden wollten, haben wir uns dazu entschieden mit Docker fortzufahren.

### Umgebung
Der Einfachheit halber, haben wir zusammen auf der VM von Marc Vogelmann gearbeitet (192.168.133.24) Auch der Einfachheit halber, ist alles auf dem Repository von Marc Vogelmann abgelegt und dokumentiert.
Auf der VM der TBZ-Cloud läuft ein Ubuntu 20.04 Server mit dem 4.15.0 Kernel.
Die Dockerversion ist 19.03.6.

### K1
Siehe LB02

### K2
Siehe LB02

### K3
