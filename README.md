# sammen-infrastructure
Veiledning for å sette opp en utvikler-PC som skal brenne et Ubuntu docker server image på en USB-drive for å kjøre automatisk installasjon av serveren.

Dette repoet inneholder en GitHub Actions-workflow og nødvendige skript for å bygge et tilpasset Ubuntu ISO image til bruk som docker server for appen **SAMMEN**.

## Krav til oppsett på utvikler-PC

## Programvare
- GIT
- Python 3
- genisoimage
- xorriso
- balenaEtcher CLI
- GitHub self-hosted runner

### GIT
(Installasjonsveiledning for Windows / Linux macOS)

### Python 3
(Installasjonsveiledning for Windows / Linux macOS)

### genisoimage
(Installasjonsveiledning for Windows / Linux macOS)

### xorisso
(Installasjonsveiledning for Windows / Linux macOS)

### balenaEtcher CLI
(Installasjonsveiledning for Windows / Linux macOS)

### GitHub self-hosted runner
(Installasjonsveiledning for Windows / Linux macOS)

## Krav til skyinfrastruktur

### Duck DNS
Hvis serveren ikke har fast IP-adresse, er det lagt til en mulighet til å bruke Duck DNS for å kunne sette opp eget domene til serveren.
(Installasjonsveiledning for Duck DNS)

### Klon repo ```sammen-api```
(GitHub veiledning)

### Klon privat repo ```sammen-infrastructure```
(GitHub veiledning)
(Set up GitHub Action veiledning)
(Set up secrets in GitHub repo veiledning)

### Rediger `setup-config.json` med ønskede verdier:
- hostname: Navn på Ubuntu infrastruktur server.
- username: Administratorkonto på Ubuntu infrastructure server.
- password: Password til adminstratorkonto, SHA5-hash.
  - (Veiledning for å generere SHA5-hash)
- userDuckDns: For bruk i nettverk som ikke har fast IP-adresse for infrastruktur-serveren. [true|false]
- duckDnsSubdomain: Subdomenenavn brukt i Duck DNS.
- api-repo: lenke til det klonede sammen-api-repoet.
- api-repo-pat: Access token for api-repoet.

### Kjør workflow Bygg sammen-infrastructure-iso
(GitHub veiledning, inklusiv sett inn USB-drive, som vil bli formatert og brukt til å lagre ISO-imaget)

### Boot Infrastructur-serveren fra USB-driven
Serveren vil bli installert automatisk med alle verktøy som trengs, .net 9, ProgreSQL, etc. ferdig satt opp API-et fra api-repoet, og med en GitHub self-hosted runner som skal brukes til å oppdatere API-et.
(GitHub veiledning for å sette opp api-repo til å bygge på infrastruktur-serveren ved push til master branch.
