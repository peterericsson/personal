# Input to Cursor

Hej, vi har ett landställe för familjen i Gullunge 187, Rimbo, Sweden.

## Bakgrund

### Samfällighet
Gullunge by, vet ej antal invånare

### Land Area
1) Bebyggt: 2000 sqm
2) Framtidstomt: 2000 sqm - Forest and 1 small 15 sqm cottage

### Bebyggt tomt
1) Runas Stuga, gammal original hus 70 kvm
2) Amrits Stuga, byggt 2018 15kvm
3) Peters Stuga, byggt 2018 24kvm, med avlopp, varmt/kall vatten och kök
4) Max Stuga, byggt 2018 60kvm, med avlopp, varmt/kall vatten och kök

### Framtidstomt
1) Gäststuga, byggt 2020 15kvm, med avlopp, varmt/kall vatten och kök
2) Resten är skog

## Behöver hjälp med

Jag skulle behöva en webapp för att administrera allt som rör fastigheten och dess hus och tomter. 

### Fas 1  
Vill jag bygga in implementationsplan i ett markdown dokument 

*Innehåll*
- Publik hemsida, använd curlrating som vi kommer anpassas senare. Publik hemsida kommer ha en gemensam bild på fastigheten och cards för varje stuga med bild rubrik och beskrivning av stugorna) Kommer sen vara klickbar om du är inloggad, annars bara viewable.
- Magic link login
- Roller:  
  - public: alla på internet, kommer bara se startsidan och login knapp)
  - relative: släktingar som vill ha ett konto, kan se info per stuga med dess innehåll 
  - tenant: ansvarig per stuga, de kan skapa innehåll för den stuga de har
  - admin: kan accessa alla stugor samt en admin dashboard där vi kommer utveckla funktioner som rör fastigheter och ekonomi senare
- Header: login knapp

*Teknik*
- domän: holyhopa.se
- gitrepo: holyhopa
- AWS: kommer ligga på en instance micro, free
- Arkitektur: DockerHub Containers, undersök vilken container images som är bäst för detta projekt
- Databas: PostgreSQL, använd Prisma
- Frontend: React Fastify (samma som crid-poc)
- Backend: Node.js
- All kod och db tabeller skall vara på engelska såklart

När vi har kommit överens om implemenationsplan, skall den användas som input till att bygga kod senare.

