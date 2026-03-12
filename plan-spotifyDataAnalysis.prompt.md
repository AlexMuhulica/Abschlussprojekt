## Plan: Data Science Projektplan für Spotify-Analyse

Dieser Plan strukturiert das Projekt in 6 Phasen, um wertvolle Erkenntnisse aus der `spotify.sqlite` Datenbank zu gewinnen. Ziel ist es, durch saubere Datenaufbereitung und gezielte Modellierung (z.B. Popularitätsvorhersage oder Clustering) geschäftlichen Mehrwert für Spotify zu generieren, unter Vermeidung typischer Anfängerfehler.

### Schritte

1.  **Datenexploration (Exploratory Data Analysis - EDA)**
    *   Verbindung zur `spotify.sqlite` herstellen und Schema aller Tabellen (`tracks`, `audio_features`, `artists`, etc.) prüfen.
    *   Verteilungen visualisieren (Histogramme für `audio_features` wie *danceability*, *tempo*).
    *   Datenqualität prüfen: Gibt es `NULL`-Werte in `tracks` oder inkonsistente IDs in den `r_`-Verknüpfungstabellen?

2.  **Datenaufbereitung (Data Preparation)**
    *   Master-Tabelle erstellen: `tracks` mit `audio_features` (via ID) und `artists` (via `r_track_artist`) joinen.
    *   Feature Engineering: Neue Features ableiten (z.B. Genre-Gruppierung aus `genres` oder Track-Dauer in Minuten).
    *   Bereinigung: Duplikate entfernen und fehlende Werte behandeln (Imputation oder Löschen).

3.  **Fragestellung formulieren (Question Formulation)**
    *   **Option A (Regression):** "Welche Audio-Features treiben die Popularität eines Songs?" (Ziel: Künstlerberatung).
    *   **Option B (Clustering):** "Lassen sich Songs basierend auf Audio-Features in neue 'Mood-Cluster' gruppieren?" (Ziel: Bessere Empfehlungen).
    *   Auswahl einer Hauptfrage mit klarem Business-Case für Spotify.

4.  **Analyse & Modellierung**
    *   Korrelationsmatrix erstellen (Heatmap), um Zusammenhänge zwischen Features und Zielvariable (z.B. Popularität) zu prüfen.
    *   Datensatz splitten (Train/Test).
    *   Modell trainieren: Lineare Regression/Random Forest (für Option A) oder K-Means (für Option B).

5.  **Interpretation**
    *   Modellgüte bewerten (RMSE/R² für Regression, Silhouette Score für Clustering).
    *   Feature Importance analysieren: Welcher Faktor hat den größten Einfluss? (Vermeidung: Korrelation ≠ Kausalität).
    *   Ergebnisse kritisch hinterfragen: Sind die Daten repräsentativ?

6.  **Präsentation**
    *   Storytelling aufbauen: Von der Business-Frage über die Daten zur Lösung.
    *   Visualisierungen exportieren: Klare Grafiken statt roher Code-Outputs.
    *   Handlungsempfehlung für Spotify formulieren.

### Weitere Überlegungen

1.  Soll das bestehende Notebook `ausprobieren.ipynb` als Basis für die EDA (Schritt 1) weiterentwickelt oder ein neues Notebook angelegt werden?
2.  Fokus auf **Supervised Learning** (Vorhersage) oder **Unsupervised Learning** (Mustererkennung)? (Empfehlung: Supervised ist oft einfacher zu interpretieren).
