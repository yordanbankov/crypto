# 🧾 Gebruikershandleiding – Crypto Portfolio Beheer Applicatie

## 1. Inleiding en Doel van het Project

Deze webapplicatie is ontworpen om je een duidelijk beeld te geven van hoe frontend en backend samenwerken. Op dit moment toont de app niet alleen eenvoudige "Hello World"-berichten om te testen of alles werkt, maar ook de actuele waarde van Bitcoin ten opzichte van de Amerikaanse dollar (BTC/USD). Die prijs wordt opgehaald via de API van Coinbase. De bedoeling is dat de applicatie later kan uitbreiden met een database zodat je bijvoorbeeld ook zelf portfolios kunt beheren. De hele applicatie is opgebouwd met behulp van moderne technologieën zoals React.js voor de gebruikersinterface, Express.js in combinatie met Node.js voor de serverkant, en PostgreSQL als databasesysteem. Alles draait netjes in aparte Docker-containers die automatisch opgestart worden via Docker Compose.

## 2. Gebruikte Technologieën in het Project

Bij het ontwikkelen van deze toepassing zijn er verschillende technologieën ingezet om ervoor te zorgen dat alles goed samenwerkt:

- **Frontend**: De gebruikersinterface is gemaakt met React.js, een populaire JavaScript-bibliotheek die vaak wordt gebruikt voor het bouwen van interactieve websites.
- **Backend**: Voor de server is er gekozen voor Express.js, een lichtgewicht framework dat draait bovenop Node.js, zodat data veilig en snel kan worden opgehaald en doorgestuurd.
- **Database**: Hoewel de database op dit moment nog niet actief wordt gebruikt, is er al een configuratie voorzien voor PostgreSQL zodat toekomstige uitbreidingen makkelijker te integreren zijn.
- **Containerisatie**: Zowel de frontend als de backend draaien elk in hun eigen container met behulp van Docker. Docker Compose wordt gebruikt om deze containers op te starten en met elkaar te verbinden.

## 3. Hoe Installeer je de Applicatie op je Eigen Computer?

Om deze applicatie lokaal te laten werken, moet je eerst controleren of je systeem de juiste software heeft geïnstalleerd. Je hebt **Docker** en **Docker Compose** nodig. Als je die nog niet hebt, kun je die downloaden via de officiële websites.

### Stap voor stap installatieproces:

1. **Download de broncode:**

   ```bash
   git clone https://github.com/henrique-cavaleiro/crypto.git
   cd crypto
   ```

2. **Pas instellingen aan indien nodig:**

   Afhankelijk van jouw netwerkinstellingen kan het nodig zijn om IP-adressen in de configuratiebestanden aan te passen. Ook de mappen in `docker-compose.yml` kunnen gewijzigd worden als jouw lokale structuur daarvan afwijkt.

3. **Installeer de nodige pakketten:**

   ```bash
   cd backend
   npm install

   cd ../frontend
   npm install
   ```

4. **Start de containers op:**

   ```bash
   cd ../express-docker
   docker-compose up -d --build

   cd ../react-docker
   docker-compose up -d --build
   ```

   Indien je ook de database apart wil starten:

   ```bash
   cd ../database
   docker-compose up -d
   ```

5. **Toegang tot de applicatie:**

   - Voor de gebruikersinterface (frontend): open je browser en ga naar `http://JOUW-IP:3000`
   - Voor de backend (API’s):
     - Hello World route: `http://JOUW-IP:3500/api/hello`
     - Bitcoin realtime prijs: `http://JOUW-IP:3500/api/btc`

## 4. Overzicht van de Mappen en Structuur van het Project

De bestanden van dit project zijn overzichtelijk verdeeld over verschillende mappen zodat alles netjes blijft en je snel vindt wat je zoekt. Hier zie je hoe de structuur eruitziet:

```
crypto/
├── README.md
├── .gitignore
├── config/
│   ├── express-docker/
│   │   └── docker-compose.yml
│   ├── postgresql/
│   │   └── docker-compose.yml
│   └── react-docker/
│       └── docker-compose.yml
├── express-docker/
│   ├── src/
│   │   ├── cryptoAPI.js
│   │   └── db.js
│   ├── Dockerfile
│   ├── package.json
│   ├── package-lock.json
│   └── server.js
└── react-docker/
    └── frontend/
        ├── public/
        │   ├── index.html
        │   ├── manifest.json
        ├── src/
        │   ├── components/
        │   │   ├── CryptoChart.js
        │   │   ├── Portfolio.js
        │   │   └── examen.js
        │   ├── App.js
        │   └── index.js
        ├── Dockerfile
        ├── package.json
```

## 5. Voor Wie Is Deze Applicatie Gemaakt?

Deze applicatie is bedoeld voor verschillende doelgroepen, met elk hun eigen leerdoel of interesse:

- Personen die interesse hebben in cryptomunten en graag de realtime koers van coins willen volgen op een eenvoudige manier.
- Programmeurs die ervaring willen opdoen met moderne technologieën zoals React, Node.js en het opzetten van projecten in Docker-containers.
- Traiders ze hebben een mooie overzicht van de shard en kunnen ermee traiden.

---
