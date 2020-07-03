# Deepfake-Bedienungsanleitung mit DeepFaceLab

## Filestruktur

- [Applikation, DFL_Colab_TagderoffenenT.ipynb](DFL_Colab_TagderoffenenT.ipynb) - auszuführen mit Google Colaboratory
- Datenquelle [workspace.zip](https://www.dropbox.com/preview/R%26D-Projekt_2019_20_Pichler_Siller/10_Prototyp/Deepfake/workspace.zip?role=personal) - **ACHTUNG:** etwa 5 GB
- Demovideo [TagDerOffenenTuer.mp4](https://www.dropbox.com/home/R%26D-Projekt_2019_20_Pichler_Siller/10_Prototyp/Deepfake?preview=TagDerOffenenTuer.mp4)

Die Datenquelle ist leider nur in der Dropbox verfügbar, da das File zu groß ist. Es muss in der Google Drive des für die Ausführung verwendeten Users verspeichert sein.

Bei der Applikation handelt es sich um das gleiche File, das auch beim Tag der offenen Tür verwendet worden wäre.

## Vorgehensweise

1. Datei **workspace.zip** in Google Drive-Hauptverzeichnis ablegen.
2. Punkt **Check GPU** durchführen
    - wenn die GPU _Tesla P100_ ist, kann fortgeführt werden
    - wenn die GPU _Tesla P4_ ist, muss später die Batch-Size auf 4 gestellt werden
    - wenn die GPU nicht _Tesla P100_ oder _Tesla P4_ ist, muss die Sitzung terminiert und neu aufgebaut werden, um eine bessere GPU zu erhalten
3. Punkt **Clone Github repository and install requirements** durchführen
    - nach Fertigstellung muss die Sitzung per Button **Restart Runtime** neu gestartet werden, um die eingebundene Packete zu übernehmen
4. Punkt **Import from Drive** in **Manage workspace** mit der Voreinstellung _workspace_ durchführen
    - damit wird das File **workspace.zip** von der Google Drive auf den Google Colaboratory-Server importiert
5. Ein beliebiges Video mit der Endung _.mp4_ auf den Google Colaboratory-Server hochladen und zu **data_dst.mp4** umbenennen
    - je länger das Video ist, desto länger dauert das Training
6. Das Modell, das genutzt werden soll, von _model_rene_ oder _model_mario_ auf **model** umbenennen
7. Den dazugehörigen Ordner _data_src_rene_ oder _data_src_mario_ auf **data_src** umbenennen
8. Das dazugehörige Video _data_src_rene.mp4_ oder _data_src_mario.mp4_ auf **data_src.mp4** umbenennen
9. Punkt **Extract frames** in **Extract, sorting and faceset tools** mit der Voreinstellung _data_dst_ durchführen
    - dabei werden 10 Frames pro Sekunde extrahiert
10. Punkt **Detect faces** in **Extract, sorting and faceset tools** mit den Voreinstellungen _data_dst_ und _S3FD_ durchführen
    - dabei werden die Gesichter den extrahierten Frames zugeordnet
11. Punkt **Sort aligned** in **Extract, sorting and faceset tools** mit den Voreinstellung _data_dst_ und _absdiff_ durchführen
    - bei weiteren Einstellungsabfragen mit **Enter** bestätigen
12. Punkt **Train** in **Train model** mit der Voreinstellung _SAEHD_ durchführen
    - sollte die GPU _Tesla P4_ sein, muss die Batchsize auf 4 gestellt werden, alle anderen Einstellungen können einfach mit **Enter** bestätigt werden
    - sollte die GPU _Tesla P100_ sein, können alle Einstellungen einfach mit **Enter** bestätigt werden
13. Das Training muss für mindestens 100 bis 200 Iterationen durchgeführt werden. Wenn man ein besseres Ergebnis erhalten möchte, trainiert man das Modell länger.
14. Um das Training abzubrechen, muss die Durchführung per Klick auf den **X-Button** beendet werden. Die nachfolgende Warnmeldung kann ignoriert werden.
15. Punkt **Convert** in **Convert frames** mit der Voreinstellung _SAEHD_ durchführen
    - dabei wird das trainierte Modell auf die extrahierten Einzelframes angewandt
    - jegliche Einstellungen können einfach mit **Enter** bestätigt werden
16. Punkt **Get result video and copy to Drive** in **Convert frames** durchführen
    - das Resultatvideo wird direkt am Google Colaboratory-Server als **result.mp4** verspeichert und kann heruntergeladen werden
