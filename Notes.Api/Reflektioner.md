1.Problemet: Sårbarhet identifierad sensitive data exposure A02 lösenord hittat i klartext i appsettings json
2.Vad kan hända: Det som kan hända är att alla som har tillgång till filen kan se lösenordet i klartext och använda det för att få obehörig åtkomst till systemet. Det som kan hända är att en angripare kan utnyttja detta för att få tillgång till databasen eller andra system som använder samma lösenord, vilket kan leda till dataintrång och förlust av känslig information.
3.Förebyggande: Detta förebyggs genom säker design, genom att inte spara lösenord i öppna filer, utan alltid spara lösenord hashade med rätt algoritm på server sidan. Använd miljövariabler eller hemliga hanteringssystem för att lagra känslig information istället för att ha dem i konfigurationsfiler. Implementera också regelbundna säkerhetsgranskningar och kodgranskningar för att identifiera och åtgärda sårbarheter innan de kan utnyttjas.

<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<

1 Problemet: Sårbarhet identifierad broken acces control A01 användaren har tillgång till andra användares data
2.vad kan hända: Användaren kan läsa, ändra och radera andra användares notes. vilket räknas som dataintrång och förlust av känslig information.
3.Förebyggande: Detta förebyggs genom att implementera korrekt åtkomstkontroll och aktorisering. Se till att varje användare endast har tillgång till sina egna data genom att göra lägga in kontroll i requesten.

<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<
