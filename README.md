# Profile Card

Welkom! In deze repo staat mijn profile card. Volg de stappen hieronder om het project te installeren en te runnen.

## Vereisten

- **Node.js** 
- **NPM** (Node.js package manager)
- **GitHub Desktop**

## Installatie

1. **Download het project via GitHub Desktop**  
   - Open **GitHub Desktop**.
   - Klik op **File**  en selecteer **Clone Repository** .
   - Zoek het project op GitHub en klik op **Clone** om het op je computer op te slaan.

2. **Installeer de benodigde pakketten**  
   Open de terminal of command prompt in de projectmap en voer de volgende opdracht uit om alle benodigde bestanden te installeren:
   ```
   npm install
   ```

3. **Directus configureren**  
   Om Directus te gebruiken, moet je Directus opzetten. Volg de stappen van de Directus-documentatie om dit te doen:  
   [Directus Installatiegids]([https://docs.directus.io/getting-started/installation.html](https://docs.directus.io/blog/getting-started-directus-sveltekit.html))

## Het Project Starten

1. **Start de Directus server**  
   Nadat Directus is geïnstalleerd en geconfigureerd, start je de Directus server met:
   ```
   npx directus start
   ```

2. **Start de Svelte applicatie**  
   Open de terminal in de projectmap en voer de volgende opdracht uit:
   ```
   npm run dev
   ```

   Daarna kun je je profielkaart bekijken door naar je webbrowser te gaan en `http://localhost:5173` te openen.

Enjoy!
