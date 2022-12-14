# AWS Neptune Setup

Die nachfolgende Anleitung zeigt das Aufsetzen einer AWS Neptune Datenbank sowie das anschließende Verbinden zu einem Graph Notebook (AWS Sagemaker) in der AWS Academy Umgebung. Aufgrund fehlender Rechte im AWS Learner Lab muss sich beim Aufsetzen des Neptune Setups strikt an die nachfolgende Anleitung gehalten werden. Insbesondere das von Amazon in diversen Demos gezeigt parallele erstellen von Neptune Datenbank und Notebook funktioniert in dem Learner Lab nicht.


## Neptune Datenbank erstellen
Im ersten Schritt wird die AWS Neptune Datenbank erstellt. Die hierbei durchgeführten Schritte sind nachfolgend erläutert.

Um auf die Neptune Startseite zu kommen, sucht man in der AWS Management Console nach "Neptune" und wählt den Service aus.
Anschließend erscheint die Neptune Startseite, wie die nachfolgende Abbildung zeigt. 

<img width=“964” src="https://github.com/NeptuneExample/NeptuneSetup/blob/main/Bilder/Neptune_Start.png?raw=true">

Im nächsten Schritt wird auf der Neptune Startseite das Feld **Datenbanken** ausgewählt, woraufhin eine Auflistung aller bisher erstellten Neptune Datenbanken erscheint. Da für das Konto noch keine Neptune Datenbank erstellt wurde, wird eine neue Datenbank angelegt.

<img width=“964” src="https://github.com/NeptuneExample/NeptuneSetup/blob/main/Bilder/DB_Erstellung.png?raw=true">

In der Ansicht **Datenbank erstellen** wird der Neptune Datenbank eine **DB-Cluster-Kennung** nach Wahl gegeben. Die Engine-Optionen bleiben, wie die nachfolgende Abbildung zeigt, unverändert.

* **DB-Cluster-Kennung** = **neptuneDB**

<img width=“964” src="https://github.com/NeptuneExample/NeptuneSetup/blob/main/Bilder/DB_Name.png?raw=true">

Anschließend wird **Entwicklung und Tests** als Vorlage und eine **DB-Instanz-Klasse** vom Typ **T4** ausgewählt.

* **Entwicklung und Tests** = **selektiert**
* **DB-Instanz-Klasse** = **db.t4g.medium**

<img width=“964” src="https://github.com/NeptuneExample/NeptuneSetup/blob/main/Bilder/Entwickliungs.png?raw=true">

Im nächsten Schritt ist es wichtig, die **Erstellung eines Notebooks** für die Neptune Datenbank zu deselektieren. Andernfalls kommt es aufgrund der fehlenden Berechtigungen im AWS Learner Lab zu einer Fehlermeldung und die Erstellung des Notebooks schlägt fehl.
* **Notebook erstellen** = **deselektiert**

<img width=“964” src="https://github.com/NeptuneExample/NeptuneSetup/blob/main/Bilder/Notebook_Selekt.png?raw=true">

Die Checkbox **Notebook erstellen** wurde deselektiert.

<img width=“964” src="https://github.com/NeptuneExample/NeptuneSetup/blob/main/Bilder/Notebook_Deselektiert.png?raw=true">

Abschließend wird die Neptune Datenbank erstellt.
* **Datenbank erstellen**
<img width=“964” src="https://github.com/NeptuneExample/NeptuneSetup/blob/main/Bilder/DB_Erstellung_Abschluss.png?raw=true">


   
      
   
   
## Graph Notebook erstellen

Nachdem im ersten Schritt die Neptune Datenbank erstellt wurde, kann im nächsten Schritt das Jupiter Notebook erstellt werden, mit dem auf das Neptune Cluster zugegriffen werden kann. Wichtig ist hierbei zu erwähnen, dass für den Einsatz des Notebooks über AWS Sagemaker eine eigene T3 Instanz aufgesetzt wird, die zwar geringe, aber zusätzliche Kosten verursacht.

Um das Notebook erstellen zu können, wird zuerst von der **Datenbank** in die **Notebook**-Ansicht gewechselt.

<img width=“964” src="https://github.com/NeptuneExample/NeptuneSetup/blob/main/Bilder/Notebook1.png?raw=true">

Anschließend wird auf **Notebook erstellen** geklickt, um die Erstellung des Notebooks zu starten.
* **Notebook erstellen**

<img width=“964” src="https://github.com/NeptuneExample/NeptuneSetup/blob/main/Bilder/Notebook2.png?raw=true">

In der Ansicht **Notebook erstellen** wird zuerst das zuvor erstellte Neptune **Cluster** ausgewählt, mit dem das Notebook verbunden werden soll. Außerdem erhält auch das Notebook einen eigenen **Notebook-Namen**. 

* **Cluster** = **neptuneDB** (Name des zuvor erstellten Clusters )
* **Notebook Name** = **NeptuneNotebook**

<img width=“964” src="https://github.com/NeptuneExample/NeptuneSetup/blob/main/Bilder/Notebook3.png?raw=true">

Im Feld IAM-Rollenname wird die Checkbox **Vorhandene IAM-Rolle auswählen** selektiert und anschließend **LabRole** als **IAM-Rollenname** ausgewählt.

* **Vorhandene IAM-Rolle** = **selektieren**
* **IAM-Rollenname** = **LabRole**

<img width=“964” src="https://github.com/NeptuneExample/NeptuneSetup/blob/main/Bilder/Notebook4.png?raw=true">

Um das Notebook mit der zuvor erstellten Neptune Datenbank verbinden zu können, ohne das es dabei zu Fehler aufgrund fehlender Berechtigungen kommt, muss eine neue Lebenszykluskonfiguration erstellt werden. Dafür wird die Checkbox **Neue Lebenszykluskonfiguration erstellen** selektiert und der vorgeschlagene **Name der Lebenszykluskonfiguration** übernommen. Anschließend wird der **GRAPH_NOTEBOOK_AUTH_MODE** in Zeile fünf des Skripts von **DEFAULT** auf **IAM** geändert, wie die nachfolgende Abbildung zeigt.

* **Neue Lebenszykluskonfiguration erstellen** = **selektiert**
* **Name der Lebenszykluskonfiguration** = **neptuneNotebook-LC**
* **GRAPH_NOTEBOOK_AUTH_MODE** = **IAM**
 
<img width=“964” src="https://github.com/NeptuneExample/NeptuneSetup/blob/main/Bilder/Notebook5.png?raw=true">

Abschließend wird die Netzwerkkonfiguration des Notebooks so angepasst, das es sich in dem gleichen Subnetz befindet wie die zuvor erstellte Neptune Datenbank. Zudem wird **AWS Sagemaker als Zugriffsmethode** für das Internet ausgewählt, da es hier ansonsten wieder zu Fehlern mit den Berechtigungen kommt. Nachdem alle Änderungen vorgenommen wurden, kann das Notebook erstellt werden.

* **Subnetz** = **us-east-a1** (gleiches Subnetz wie die Neptune Datenbank)
* **Direkter Zugang über Amazon SageMaker** = **IAM**
* **Notebook erstellen**
<img width=“964” src="https://github.com/NeptuneExample/NeptuneSetup/blob/main/Bilder/Notebook6v.png?raw=true">

Nachdem sowohl die Neptune Datenbank als auch das Notebook erstellt wurden, kann über das Notebook auf die Neptune Datenbank zugegriffen werden, um Daten in die Datenbank zu laden oder Abfragen auszuführen. Zudem bietet das Notebook viele integrierte Optionen zur Darstellung der Graphen an.
<img width=“964” src="https://github.com/NeptuneExample/NeptuneSetup/blob/main/Bilder/Notebook7.png?raw=true">



