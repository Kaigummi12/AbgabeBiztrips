# Dokumentation für die Abgabe 12.3 biztrips von Kai Wenninger

Als erstes habe ich das vorgegebene GitLab Repository https://gitlab.com/bbw-m426-group/biztrips-2023 heruntergeladen und auf GitHub gepusht. 

![image](https://github.com/user-attachments/assets/b0b9dbae-7d6d-436c-89ee-9f80dc43bfe3)

Anschliessend habe ich im Internet nach einer möglichen Lösung gesucht und folgendes gefunden auf der Seite Medium. https://medium.com/@ravipatel.it/automating-docker-image-creation-and-push-to-docker-hub-for-a-react-app-using-github-actions-7fa092751fc0
Dieser Anleitung bin ich gefolgt und ich versuchte auch immer zu verstehen was in dieser Anleitung gemacht wird.

# Umsetzung

Ich habe im Projekt ein Dockerfile hinzugefügt mit folgendem Inhalt.

![image](https://github.com/user-attachments/assets/4ec9b16a-3ace-465a-8cc3-300f88e71ae1)

Das Dockerfile baut eine React-Anwendung mit Node.js, erstellt den Produktions-Build und serviert diesen dann mit einem Nginx-Webserver. So wird die Anwendung in einem leichten Webserver bereitgestellt, um sie live zu betreiben.

Kurz darauf habe ich noch ein docker-publish.yml file erstellt mit folgendem Inhalt.

![image](https://github.com/user-attachments/assets/f3bf40bf-7864-4de8-8065-122e83c60f37)

Der Code baut ein Docker-Image, wenn Änderungen auf den main-Branch gepusht werden, und lädt es anschliessend in DockerHub hoch. Dabei wird der Benutzername und das Passwort aus den GitHub-Secrets verwendet.

## Hinzufügen von Logindaten (GitHub Secrets) auf GitHub (Actions)

Nun haben wir unseren fertigen Code und wir müssen jetzt noch die Actions in GitHub hinzufügen. Dazu gehen wir auf unser Repository -> Einstellungen -> Secrets and variables -> Actions

![image](https://github.com/user-attachments/assets/88a8c352-08b1-48e8-a65b-e1ae8ebe04fa)

Hier dann ein neues Secret Repository erstellen.

![image](https://github.com/user-attachments/assets/b386e3a3-fb10-4903-96db-09434c13124c)

Anschliessen USERNMAE und PASSWORD hinzufügen vom Docker Account. 

![image](https://github.com/user-attachments/assets/1e5ba9d4-a2fc-41c7-a2fb-f7b4a7303ffb)

![image](https://github.com/user-attachments/assets/5ad9caaa-6c9d-4923-83d8-90bf9c55d07f)

Hier kann man sehen das beide hinzugefügt wurden.

![image](https://github.com/user-attachments/assets/8ec49018-d7b8-4e76-bb61-b14164fcb1ec)

Kurze Zeit später, als ich dann alles gepusht habe, konnte ich auf GitHub Actions sehen wie der Build erfolgreich durchgelaufen ist.

![image](https://github.com/user-attachments/assets/e7e3bf0a-d4ba-4e22-ae44-aa8eb3c91033)

# Best Practices für CI/CD mit GitHub Actions

1. **Sichere Secrets-Verwaltung**: Verwende GitHub Secrets für Passwörter und API-Keys.
2. **Automatisches Testen**: Führe Tests automatisch vor dem Deployment aus.
3. **Effizientes Caching**: Nutze Caching, um Build-Zeiten zu verkürzen.
