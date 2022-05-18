# Kalkulator i Python

Denne workshoppen er designet for dere som ikke har forkunnskaper innenfor programmering. Vi skal prøve å unngå komplisert programmeringsterminologi, men ikke vær redd for å spørre oss om hjelp underveis om noe er uklart - det er derfor vi er her. Teksten er kortfattet med vilje, siden det er mye mer læringsutbytte i å løse en oppgave kreativt enn å følge en oppskrift. Forhåpentligvis er det morsommere også! :)

Dere kan enten programmere lokalt om dere har Python satt opp på maskinen deres, ellers kan dere bruke en online interpreter som f.eks. https://www.programiz.com/python-programming/online-compiler/ - om dere bruker denne er det lurt å ta backups av koden deres til Notepad lokalt så dere ikke mister kode.

I hver del vil vi oppgi noen funksjoner som kan brukes for å løse oppgaven. Det betyr ikke at du må bruke disse - det finnes alltid mange måter å gjøre ting på! Om du vil finne ut hva funksjonene vi foreslår gjør, kan det være lurt å sjekke dokumentasjonen. Der finner du en beskrivelse av hva funksjonen gjør, de tilgjengelige parameterne, og gjerne eksempelkode for bruk. Du kan finne dokumentasjonen for funksjonene vi oppgir her: https://docs.python.org/3/library/functions.html

### Eksempel-output fra ferdig kalkulator:
```
Første tall: 15
Operator(+ - * /): +
Andre tall: 14
15.0 + 14.0 = 29.0
```

## Intro: Om du ikke har programmert noe før

Her går vi raskt gjennom noen de mest grunnleggende byggeklossene i programmering. På skolebenken vil dette gås gjennom mye mer grundig; dette blir bare en rask gjennomgang som forhåpentligvis vil hjelpe dere gjennom oppgavene.

### Variabel
```python
x = 20
y = "Hans og Grete"
tall1 = input("Første tall: ")
```

Variabelen (f. eks. x) blir her satt til en viss verdi (20). Dette kan være nyttig for å lagre verdier for senere bruk, spesielt for returverdier fra funksjoner.

### Funksjoner
Eksempler på funksjoner:
  - **sin(x)**
  - **range(20)**

Funksjoner er en bit med kode som gjerne defineres et annet sted enn programmet ditt, enten for å bidra til organisering, bedre gjenbruk av kode, eller utnytte kode andre har skrevet som allerede gjør det du prøver på. Mange slike funksjoner finnes i standardbiblioteket til Python. Inne i parentesen setter vi parametre som mates inn i funksjonen. Man kan ganske enkelt skrive egne funksjoner også, men for akkurat denne oppgaven er det unødvendig.

## Del 1: Lese input fra terminalen

Mål: Gi en bruker mulighet til å skrive noe inn i terminalen (en 'streng'), og så skrive strengen tilbake i terminalen.

### Funksjoner
- **input()** for å hente input fra brukeren
- **print()** for å skrive ut informasjon i terminalen

For å lage en kalkulator, må vi først kunne motta input fra brukeren. Siden vi lager en terminal-kalkulator, vil den inputen komme i form av noe brukeren skriver inn i terminalen når de blir bedt om det. Funksjonene gitt over er alt som skal til for å kunne nå målet med oppgaven. Sjekk dokumentasjonen!

## Del 2: Konvertere til tall

Mål: Konvertere datatype på input til tall

### Funksjoner:
- **float()** konverterer en streng til et flyttall (flyttall er tall med komma).

Det vi får tilbake fra input() er en streng; en streng representerer som oftest en tekst av noe slag, og det betyr at man ikke kan utføre matematiske funksjoner med dem. Derfor må disse konverteres til tall for å kunne brukes i kalkulatoren vår.

## Del 3: Velg matematisk operasjon

Mål: Gi brukeren mulighet til å velge hvilken operasjon som skal brukes

### Funksjoner:
  ⁃ **if .. else** (ikke en funksjon egentlig)

Her skal vi gi brukeren mulighet til å velge hva de vil skal skje mellom tallene de skriver inn. For eksempel kan de skrive inn '+' for å addere. For å implementere dette, kan det være lurt å prøve seg på en ‘if else blokk’. Disse ser slik ut:
```python
if operator == '+':
	# implementer addisjon her
elif operator == '-':
	# implementer subtraksjon her
...
```

Hvilken rekkefølge du vil at tall og operator skal hentes er helt opp til deg.

## Del 4: Sett alt sammen

Mål: Lag en kalkulator!

All funksjonaliteten som skal til har blitt diskutert allerede, så her er det bare å sette sammen alle delene sånn du føler de passer best. Kanskje du vil implementere noen flere funksjoner også? Tips: om du vil legge inn noe mer avansert enn det som ligger i standard-biblioteket, kan du skrive 'import math' øverst i programmet ditt, og så bruke alle funksjonene du ser her: https://docs.python.org/3/library/math.html

## Bonusoppgaver

Om du er ferdig med delene over, men vil jobbe mer med kalkulatoren, har vi noen forslag til funksjonalitet du kanskje kan prøve å implementere. Om du vil gjøre noe helt annet, er det også mer enn OK! Disse forslagene har enda mindre informasjon enn de forrige delene, så her vil det nok kreves litt ekstra utforskning fra deres side. Eksperimenter, google, og spør oss om hint eller hjelp. :)

### Flere kalkulasjoner

Sånn kalkulatoren er satt opp nå, gjør den en utregning og så stopper programmet. Et annet alternativ er at programmet fortsetter å kjøre helt til brukeren skriver inn en kommando (f. eks. 'q'). Dette kan gjøres ved å bruke en while loop rundt koden din. Men her må du fortsatt bestemme deg for hvordan du vil la brukeren stoppe loopen.

### Exception-handling

Om du prøvde å skrive inn noe annet enn et tall i del 2, oppdaget du sikkert at du fikk en feilmelding av typen 'ValueError'. Dette skjedde fordi float() ikke forsto hvordan å konvertere strengen du skrev inn til et tall. For å takle slike problemer har Python noe som heter en try .. except blokk (strukturen er veldig lik en if .. else blokk).

Eks.
```python
try:
  print(float(tall1))
except ValueError:
  # hopp over eller gi beskjed til bruker om at de ikke skrev inn et ekte tall
```

### Forbedre input-formatteringen

Per nå får vi inn kalkulator-input på et kronglete format, der vi får tall og operator i separate inputs fra brukeren. Det ville være mer naturlig om brukeren kan skrive noe som ‘10+12’ og at kalkulatoren automatisk forstår denne matematiske funksjonen. Det er mange måter å løse akkurat denne oppgaven på. "Quick and dirty" løsning kan gjøres med streng-metoden .split() (https://docs.python.org/3/library/stdtypes.html#str.split), men en mer ordentlig løsning gjerne vil inkludere "regular expressions", eller regex. Dette er langt utenfor det vi sannsynligvis har tid til å se på i denne workshoppen, men kan leses om her: https://docs.python.org/3/library/re.html


