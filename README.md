# Shui Message Board

En enkel fullstack **meddelandetavla** byggd med **React/Vite** i frontend och en **serverless backend på AWS**.

Projektet skapades som en individuell examination i kursen **Utveckling och driftsättning i molnmiljö**.

---

## ☁️ Deployment status

Applikationen utvecklades och driftsattes ursprungligen i AWS som en del av examinationen.

Den ursprungliga lösningen använde:

- **Amazon S3** för frontend
- **Amazon API Gateway** för REST API
- **AWS Lambda** för backend-funktioner
- **Amazon DynamoDB** för lagring av användare och meddelanden
- **Serverless Framework** för konfiguration och deployment

Projektet byggdes med ett AWS-konto som användes för utbildning och lärande. Den AWS-miljön är inte längre aktiv, vilket innebär att den ursprungliga live-applikationen och API-endpointen inte längre är tillgängliga.

Källkoden finns kvar i detta repository och visar hur frontend, REST API, autentisering, serverless backend och databas kopplades ihop till en komplett applikation.

Projektet gav mig praktisk erfarenhet av hur de olika delarna i en molnbaserad fullstack-applikation kommunicerar och fungerar tillsammans.

---

## 🛠️ Tekniker

### Frontend

- React
- Vite
- JavaScript
- CSS
- Fetch API
- Environment variables

### Backend & Cloud

- Node.js
- Serverless Framework
- AWS Lambda
- Amazon API Gateway
- Amazon DynamoDB
- Amazon S3
- AWS IAM
- REST API

### Autentisering

- JSON Web Token (JWT)
- bcrypt
- Bearer Token
- Skyddade API-endpoints
- Behörighetskontroll för användarens egna meddelanden

---

## 🎯 Vad kan appen göra?

- ✍️ **Skapa** nya meddelanden
- ✏️ **Redigera** egna meddelanden
- 🗑️ **Ta bort** egna meddelanden
- 👀 **Visa alla** meddelanden
- 🔽 **Sortera** efter nyast eller äldst
- 👤 Visa **Mina meddelanden**
- 🔐 Registrera användare
- 🔑 Logga in med autentisering
- 🛡️ Skydda funktioner så att en användare endast kan ändra eller ta bort sina egna meddelanden

---

## 🏗️ Arkitektur

```text
React / Vite
     │
     ▼
Amazon S3
     │
     ▼
Amazon API Gateway
     │
     ▼
AWS Lambda
     │
     ▼
Amazon DynamoDB
   ├── Users
   └── Messages
```

Frontend kommunicerar med backend genom ett REST API.

API Gateway tar emot HTTP-anrop och skickar dem vidare till Lambda-funktionerna. Lambda-funktionerna hanterar applikationslogiken och kommunicerar med DynamoDB.

---

## 📁 Projektstruktur

```text
shui-message-board/
│
├── backend/
│   ├── handlers/
│   │   ├── _auth.mjs
│   │   ├── createMessage.mjs
│   │   ├── deleteMessage.mjs
│   │   ├── getMessagesByUser.mjs
│   │   ├── listMessages.mjs
│   │   ├── login.mjs
│   │   ├── register.mjs
│   │   └── updateMessage.mjs
│   │
│   ├── package.json
│   └── serverless.yml
│
├── frontend/
│   ├── src/
│   │   ├── pages/
│   │   ├── ui/
│   │   ├── auth.js
│   │   ├── main.jsx
│   │   ├── simpleApi.js
│   │   └── styles.css
│   │
│   ├── package.json
│   └── vite.config.js
│
└── README.md
```

---

## 🔌 REST API

| Syfte                  |  Metod | Path                         | Auth |
| ---------------------- | -----: | ---------------------------- | :--: |
| Hämta alla meddelanden |    GET | `/messages`                  |  –   |
| Skapa meddelande       |   POST | `/messages`                  |  ✅  |
| Uppdatera meddelande   |    PUT | `/messages/{id}`             |  ✅  |
| Ta bort meddelande     | DELETE | `/messages/{id}`             |  ✅  |
| Mina meddelanden       |    GET | `/users/{username}/messages` |  ✅  |
| Registrera användare   |   POST | `/auth/register`             |  –   |
| Logga in               |   POST | `/auth/login`                |  –   |

Skyddade endpoints använder:

```text
Authorization: Bearer <token>
```

Backend kontrollerar autentisering och att användaren har rätt att ändra eller ta bort det aktuella meddelandet.

---

## 💬 Meddelande-modell

Exempel på ett meddelande:

```json
{
  "id": "string",
  "username": "string",
  "text": "string",
  "createdAt": 1758883332536
}
```

---

## 🔐 Säkerhet

Applikationen använder JWT för autentisering och `bcrypt` för lösenordshantering.

Användaren får endast uppdatera eller ta bort sina egna meddelanden.

Projektet byggdes som en utbildningsapplikation. Vid en riktig produktionsdeployment ska känsliga värden, exempelvis `JWT_SECRET`, lagras som miljövariabler eller genom en säker secrets-lösning och inte hårdkodas i källkoden.

---

## 📚 Vad jag lärde mig

Projektet gav praktisk erfarenhet av hela flödet i en cloud-baserad fullstack-applikation:

**Frontend → REST API → Backend → Authentication → Database → Cloud deployment**

Jag fick arbeta med hur en React-applikation kommunicerar med ett API, hur Lambda-funktioner hanterar backend-logik, hur data lagras i DynamoDB och hur AWS-tjänster kopplas ihop genom Serverless Framework.

Det gav framför allt en bättre förståelse för **hur alla delar tillsammans bygger en fungerande applikation**, inte bara hur varje teknik fungerar separat.

---

## 🎓 Examination

Projektet skapades som en **individuell examination** inom cloud development och deployment.

**Betyg: VG (Väl godkänd)**
