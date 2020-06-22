# Lastprofile-Bedienungsanleitung mit Image-to-Image Translation

## Filestruktur

- [Applikation, CycleGAN_pools.ipynb](CycleGAN_pools.ipynb)
- [Anaconda-Environment](environment.yml)
- Datenquelle [nopool2pool_256.npz](https://www.dropbox.com/preview/R%26D-Projekt_2019_20_Pichler_Siller/10_Prototyp/Lastprofile/nopool2pool_256.npz?role=personal)

Die Datenquelle ist leider nur in der Dropbox verfügbar, da das File zu groß ist. Es muss im gleichen Verzeichnis wie das Programm abgelegt werden. Beim Programm handelt es sich um ein Jupyter Notebook.

Das Anaconda-Environment kann mit dem Befehl

```
conda env create -f environment.yml
```

angelegt werden.

**ACHTUNG:**
Eventuell muss der Name des Environments noch angepasst werden. Standardmäßiger Name im .yml-File ist ***base***.

## Vorgehensweise

Man muss alle Zellen durchführen, dann startet das Training. Im Block **Train** kann die Anzahl der Epochen konfiguriert werden. Dabei kann man auch einstellen, nach wievielen Epochen die Modelle in das Verzeichnis verspeichert werden.
