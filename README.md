# sammen-infrastructure
Dette repoet inneholder en GitHub Actions-workflow og nødvendige skript for å bygge et tilpasset Ubuntu ISO-image med automatisk installasjon av en infrastrukturserver for appen **SAMMEN**.
Repoet inneholder også en veiledning for å sette opp en GitHub self-hosted runner, som brukes til å bygge og eventuel brenne ISO-filen direkte til en USB-minnepinne.

## Krav til oppsett på GetHub self-hosted runner

### Programvare

#### GIT
Sjekk om du har GIT allerede installert
```git --version```

[Installing GIT](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)

#### Python 3
Sjekk om du allerede har installert Python 3 
```python --version```
```python3 --version```

[Downloading Python](https://www.python.org/downloads/)

#### genisoimage
#### xorriso
#### balenaEtcher CLI
#### GitHub self-hosted runner

## Krav til infrastruktur

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
