# Moderni način, "use strict"

Već duže vrijeme, JavaScript se razvijao bez problema kompatibilnosti. Nove mogućnosti su se dodavale u jezik ali se stara funkcionalnost nije mijenjala.

Cilj toga je bilo da se ne pokvari već postojeći kod. Ali negativna stvar toga je bilo to što bilo koja greška ili imperfektna odluka napravljena od strane JavaScript kreatora bi u jeziku ostala zauvijek.

Ovo je bio slučaj do 2009. sve dok se ECMAScript 5 (ES5) nije pojavio. Dodao je nove mogućnosti u jezik i modificirao one što su već postojale. Kako bi stari kod radio, većina tih modifikacija je bilo isključeno po uobičajenom. Morate ih eksplicitno uključiti sa posebnom direktivom `"use strict"`.

## "use strict"

Ova direktiva izgleda kao tekst (eng. string) `"use strict"` ili `'use strict'`. Kada je locirana na vrhu skripte, čitava skripta radi na "moderan" način.

Na primjer:

```js
"use strict";

// Ovaj kod radi na moderan način
...
```

Ubrzo ćemo učiti funkcije (način da grupišemo komande), tako da hajdemo zapamtiti unaprijed da `"use strict"` može biti postavljen na početku funkcije. Kada to uradimo, strogi (eng. strict) način je uključen samo u toj funkciji. Ali obično, ljudi koriste ovo za cijelu skriptu.

````warn header="Budite sigurni da je \"use strict\" na vrhu"
Postavite `"use strict"` na vrh vaših skripta, u suprotnom strogi način neće biti uključen.

Strogi način ovdje nije uključen:

```js no-strict
alert("neki kod");
// "use strict" ispod je ignorisan --mora biti na vrhu

"use strict";

// strogi način nije aktiviran
```

Samo komentari smiju biti iznad `"use strict"`.
````

```warn header="Ne postoji način da se otkaže `use strict`"
Ne postoji direktiva kao `"no use strict"` koja vraća motor na staro ponašanje.

Kada uđemo u strogi način, nema vraćanja.
```

## Konzola u pretraživaču

Kada koristite [konzolu za programere](info:devtools) da pokrenete kod, zapamtite da ne koristi `use strict` po uobičajenom.

Ponekad, kada `use strict` napravi razliku, dobit ćete pogrešne rezultate.

Kako onda da koristimo `use strict` u konzoli?

Prvo, možete probati da pritisnete `key:Shift+Enter` da napišete više linija, i stavite `use strict` na vrh, kao ovdje:

```js
'use strict'; <Shift+Enter za novu liniju>
//  ...vaš kod
<Enter da pokrenete>
```

Radi u većini pretraživača, prvenstveno u Chrome-u i Firefox-u.

Ako ne radi u na primjer starijem pretraživaču, postoji ružan, ali pouzdan način da uključite `use strict`. Stavite ovo unutar nekog omota (eng. wrapper):

```js
(function() {
  'use strict';

  // ...vaš kod...
})()
```

## Trebamo li koristiti "use strict"?

Odgovor može zvučiti očigledan, ali nije tako kako vam se čini.

Neko može preporučiti da počinjete skripte sa `"use strict"`... ali znate sta je kul?

Moderni JavaScript podržava "klase" (eng. classes) i "module" (eng. modules) - napredne strukture jezika (doći ćemo sigurno do njih), koje uključuju `use strict` automatski. Tako da ne moramo dodavati `"use strict"` direktivu, ako ih koristimo.

**Za sada, `"use strict";` je dobrodošao gost na vrhu vaših skripta. Kasnije kada vaš kod bude unutar klasa i modula, možete ga izostaviti.**

Od sada, trebamo znati o `use strict` bar ponešto.

U sljedećim poglavljima, dok učili mogućnosti jezika, pogledat ćemo razlike između strogog i starog načina rada. Srećom, ne postoji toliko razlika koje će učiniti naš život nešto boljim.

Svi primjeri u ovom tutorijalu pretpostavljaju strogi način osim (veoma rijetko) ako to napomenemo suprotno.
