# AWS Neptune Setup

Die nachfolgende Anleitung zeigt das Aufsetzen einer AWS Neptune Datenbank sowie das anschließende Verbinden zu einem Graph Notebook (AWS Sagemaker) in der AWS Academy Umgebung. Aufgrund fehlernder Rechte im AWS Learner Lab muss sich beim Aufsetzen des Neptune Setups stritkt an die nachfolgende Anleitung gehalten werden. Inbesonderen das von Amazon in diversen Demos gezeigt parrallele erstellen von Neptune Datenbank und Notebook funktinoniert in dem Learner Lab nicht.


## Neptune Datenbank erstellen
Im ersten Schritt wird die AWS Neptune Datenbank erstellt. Die hierbei durchgeführten Schritte sind nachfolgend erläutert.

Um auf die Neptune Startseite zu kommen, sucht man in der AWS Management Console nach "Neptune" und wählt den Service aus.
Anschließend erscheint die Neptune Startseite wie die nachfolgende Abbildung zeigt. 

<img width=“964” src="https://github.com/NeptuneExample/NeptuneSetup/blob/main/Bilder/Neptune_Start.png?raw=true">

Im nächsten Schritt wird auf der Neptune Startseite das Feld **Datenbanken** ausgewählt, woraufhin eine Auflistung aller bisher erstellten Neptune Datenbanken erscheint. Da für das Konto noch keine Neptune Datenbank erstellt wurde, wird mittels des orangen **Datenbank erstellen** Buttons eine neue Datenbank angelegt.

<img width=“964” src="https://github.com/NeptuneExample/NeptuneSetup/blob/main/Bilder/DB_Erstellung.png?raw=true">

In der Ansicht **Datenbank erstellen** wird der Neptune Datenbank eine **DB-Cluster-Kennung** nach wahl gegeben. Die Engine-Optionen bleiben wie die nachfolgende Abbildung zeigt unverändert.

<img width=“964” src="https://github.com/NeptuneExample/NeptuneSetup/blob/main/Bilder/DB_Name.png?raw=true">

Anschließend wird **Entwicklung und Tests** als Vorlage und eine **DB-Instanz-Klasse** vom Typ **T4** ausgewählt.

<img width=“964” src="https://github.com/NeptuneExample/NeptuneSetup/blob/main/Bilder/Entwickliungs.png?raw=true">

Im nächsten Schritt ist es wichtig, die **Erstellung eines Notebooks** für die Neptune Datenbank zu deselektieren. Andernfalls kommt es aufgrund der fehlenden Berechtigungen im AWS Learner Lab zu einer Fehlermeldung und die Erstellung des Notebooks schlägt fehl.

<img width=“964” src="https://github.com/NeptuneExample/NeptuneSetup/blob/main/Bilder/Notebook_Selekt.png?raw=true">

Die Checkbox **Notebook erstellen** wurde deselektiert.

<img width=“964” src="https://github.com/NeptuneExample/NeptuneSetup/blob/main/Bilder/Notebook_Deselektiert.png?raw=true">

Abschließend wird die Neptune Datenbank erstellt.

<img width=“964” src="https://github.com/NeptuneExample/NeptuneSetup/blob/main/Bilder/DB_Erstellung_Abschluss.png?raw=true">



## Graph Notebook erstellen

<img width=“964” src="https://github.com/NeptuneExample/NeptuneSetup/blob/main/Bilder/Notebook1.png?raw=true">
<img width=“964” src="https://github.com/NeptuneExample/NeptuneSetup/blob/main/Bilder/Notebook2.png?raw=true">
<img width=“964” src="https://github.com/NeptuneExample/NeptuneSetup/blob/main/Bilder/Notebook3.png?raw=true">
<img width=“964” src="https://github.com/NeptuneExample/NeptuneSetup/blob/main/Bilder/Notebook4.png?raw=true">
<img width=“964” src="https://github.com/NeptuneExample/NeptuneSetup/blob/main/Bilder/Notebook5.png?raw=true">
<img width=“964” src="https://github.com/NeptuneExample/NeptuneSetup/blob/main/Bilder/Notebook6v.png?raw=true">
<img width=“964” src="https://github.com/NeptuneExample/NeptuneSetup/blob/main/Bilder/Notebook7.png?raw=true">



