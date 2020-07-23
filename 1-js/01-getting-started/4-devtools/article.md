# Konzola za programere

Kod je sklon greškama. Ti ćeš sasvim vjerovatno praviti greške... O, šta ja pričam? Ti ćeš *definitivno* praviti greške, bar ako si čovjek, a ne [robot](https://en.wikipedia.org/wiki/Bender_(Futurama)).

Ali u pretraživaču, korisnici ne vide greške po uobičajenom. Tako da ako nešto pođe po zlu u skripti, nećemo vidjeti gdje je kvar i nećemo ga moći popraviti.

Da vidimo greške i mnogo ostalih korisnih informacija o skriptama, "alatke za programere" (eng. developer tools) su ugrađene u pretraživače.

Većina programera koriste Chrome ili Firefox za programiranje jer ovi pretraživači imaju najbolje alatke za programere. Ostali pretraživači isto pružaju ove alatke, ponekad sa specijalnim mogućnostima, ali u većini slučajeva pokušavaju sustići Chrome ili Firefox. Tako da većina programera imaju "omiljeni" pretraživač, a prelaze na druge ako imaju problem koji je specifičan za taj pretraživač.

Alatke za programere su potentne; imaju puno mogućnosti. Kako bismo započeli, naučit ćemo kako ih otvoriti, pronaći greške, i izvršavati JavaScript komande.

## Google Chrome

Otvorite stranicu [bug.html](bug.html).

Na ovoj stranici se nalazi greška u JavaScript kodu. Sakrivena je od običnog posjetioca, tako da hajmo otvoriti alatke za programere da vidimo grešku.

Pritisnite `key:F12` ili ako ste na Mac-u, onda `key:Cmd+Opt+J`.

Alatke za programere će se otvoriti na tabu sa konzolom po uobičajenom.

Izgledati će otprilike ovako:

![chrome](chrome.png)

Izgled vaše alatke zavisi od verzije Chrome-a. Vremenom se izgled mijenja, ali trebalo bi izgledati slično.

- Ovdje možemo vidjeti crveno obojenu poruku o grešci. U ovom slučaju, skripta sadrži nepoznatu "lalala" komandu.
- Na desnoj strani, nalazi se link na kojeg se moze kliknuti koji vodi do izvora greške `bug.html:12` sa brojem linije gdje se greška desila.

Ispod poruke o grešci, nalazi se plavi `>` simbol. Označava "komandnu liniju" (eng. command line) gdje možemo pisati JavaScript komande. Pritisnite `key:Enter` kako biste ih pokrenuli.

Sada možemo vidjeti greške, i to je dovoljno za početak. Vratit ćemo se na alatke kasnije i govorit ćemo detaljnije o ispravljanju grešaka (eng. debugging) u poglavlju <info:debugging-chrome>.

```smart header="Višelinijski unos"
Obično, kada napišemo liniju koda u konzolu, i pritisnemo `key:Enter`, ona se izvrši.

Kako bismo unijeli više linija, pritisnemo `key:Shift+Enter`. Na ovaj način, mogu se kucati duži fragmenti JavaScript koda.
```

## Firefox, Edge, i ostali

Većina ostalih pretraživača koristi `key:F12` za otvaranje alatke.

Njihov izgled i osjećaj je jako sličan. Kada znate koristiti jednu vrstu ove alatke (možete započeti sa Chrome-om), možete lagano preći na drugu.

## Safari

Safari (Mac pretraživač, nije podržan od strane Windows/Linux) je ovdje malo specijalan. Moramo uključiti "meni za razvoj" (eng. develop menu) prvo.

Otvorite postavke i idite na "napredni" (eng. advanced) dio. Tu se na dnu nalazi opcija koju trebate zabilježiti:

![safari](safari.png)

Sada `key:Cmd+Opt+C` može uključiti konzolu. Isto tako, možete primijetiti novi meni na vrhu koji se zove "Razvijanje" (eng. develop). Ima mnogo komandi i opcija.

## Sažetak

- Alatke za programere omogućavaju nam da vidimo greške, pokrećemo komande, ispitujemo varijable (promjenjive), i još mnogo toga.
- Mogu se otvoriti sa `key:F12` u pretraživačima na Windows-u. Chrome za Mac treba `key:Cmd+Opt+J`, Safari: `key:Cmd+Opt+C` (treba se uključiti prvo).

Sada imamo okruženje spremno. U sljedećoj sekciji, krećemo sa pisanjem JavaScript koda.
