1. Sensitive Data Exposure — A04 Cryptographic Failures

1. Problemet: Sårbarhet identifierad sensitive data exposure A04 lösenord hittat i klartext i appsettings json
2. Vad kan hända: Det som kan hända är att alla som har tillgång till filen kan se lösenordet i klartext och använda det för att få obehörig åtkomst till systemet. Det som kan hända   är att en angripare kan utnyttja detta för att få tillgång till databasen eller andra system som använder samma lösenord, vilket kan leda till dataintrång och förlust av känslig information.
3. Förebyggande: Detta förebyggs genom säker design, genom att inte spara lösenord i öppna filer, utan alltid spara lösenord hashade med rätt algoritm på server sidan. Använd miljövariabler eller hemliga hanteringssystem för att lagra känslig information istället för att ha dem i konfigurationsfiler. Implementera också regelbundna säkerhetsgranskningar och kodgranskningar för att identifiera och åtgärda sårbarheter innan de kan utnyttjas.
<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<

2. Broken Access Control — A01

1. Problemet: Sårbarhet identifierad broken acces control A01 användaren har tillgång till andra användares data
2. Vad kan hända: Användaren kan läsa, ändra och radera andra användares notes. vilket räknas som dataintrång och förlust av känslig information.
3. Förebyggande: Detta förebyggs genom att implementera korrekt åtkomstkontroll och aktorisering. Se till att varje användare endast har tillgång till sina egna data genom att göra lägga in kontroll i requesten.
<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<

3. Cross-Site Scripting — A05 Injection

1. Problemet: A05 Injection sårbarhet identifierad rotorsak innerHTML tolkar input som HTMLoch därför kan XXS attacker utföras.
2. Vad kan hända: Användaren skriver in XXS i någons notes i form av scripts och när den andra användaren öppnar notes så körs scriptet och kan stjäla känslig information som cookies och sessioner
3. Förebyggande: Detta förebyggs genom att Escapa vid utmatning och använda innerText istället för innerHTML. Använd säkerhetsbibliotek och ramverk som automatiskt hanterar XSS- tex react eller angular 
<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<

4.SQL Injection — A05 Injection

1. Problemet: sårbarhet a05 Injection sql injection identifierad rotorsak att input inte valideras och därför kan sql injection utföras.
2. Vad kan hända: användaren bryter sig ur strängen och lägger till sin egen SQL-kod, och får ut alla andra användares lappar ur databasen. 
3. Förebyggande: Detta förebyggs genom att använda parametriserade frågor eller ORM-ramverk som automatiskt hanterar SQL-injektioner, samt genom att validera och sanera all användarinmatning.
 <<<<<<<<<<<<<<<<<<<<<<<<<<<<<

 5. Insecure Deserialization — A08 Software and Data Integrity Failures

1. Problemet: insecure deserialization A08 sårbarhet identifierad rotorsak endpointen tar emot godtyckliga objekt, Dictionary<string, object>, och JSON.net är satt till TypeNameHandling.Auto. Det innebär att inkommande JSON via $type får bestämma vilken klass som byggs.Servern litar på serialiserad data utan att verifiera den. 
2. Vad kan hända: att bygga objektet kör dess setters. Med rätt klass går det från ofarligt "access granted" till kodkörning på servern och läckt känslig data.
3. Förebyggande: Detta förebyggs genom att inte använda TypeNameHandling.Auto, utan istället använda TypeNameHandling.None och implementera en egen konverterare som endast tillåter kända typer. Dessutom bör man validera inkommande data och undvika att deserialisera okända objekt.
<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<

6.Vulnerable and Outdated Components — A03 Software Supply Chain Failures
1. Problemet: Sårbarhet identifierad: software supply chain failures (typosquatting). Rotorsak: ett felstavat impostor-paket (Swashbukle.AspNetCore, ett c för lite) drogs in i stället för det äkta Swashbuckle.AspNetCore. Paketet kapar en vanlig funktion (.ToArray()), maskerad och med det äkta anropet inbakat, så skadlig kod körs utan att någon egen kodrad ser fel ut. Det är alltså ett falskt paket, inte en känd sårbarhet i ett äkta.
2. Vad kan hända: Om paketet har en känd sårbarhet kan en angripare utnyttja detta för att kompromettera applikationen, vilket kan leda till dataintrång, förlust av känslig information och potentiellt fullständig kontroll över systemet.
3. Förebyggande: Vi bytte det felstavade Swashbukle-paketet mot det korrekta Swashbuckle. Generellt förebyggs detta genom att hålla beroenden uppdaterade och skanna dem med verktyg som Dependabot för kända sårbarheter — och eftersom felstavade fejkpaket inte alltid syns i en sådan skanning, komplettera med granskning av paketnamn och källor innan externa bibliotek används.