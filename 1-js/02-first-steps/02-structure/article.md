# Struktura koda

Prva stvar koju ćemo učiti jesu blokovi za igradnju koda.

## Izjave (eng. statements)

Izjave su sintaksni konstrukti i komande koje vrše akcije.

Već smo vidjeli izjavu `alert('Hello, world!')`, koja nam pokazuje poruku "Hello, World!".

Možemo imati koliko god hoćemo izjava u našem kodu. Izjave se odvajaju sa tačka-zarezom (;).

Na primjer, ovdje dijelimo "Hello World" u dva različita alerta:

```js run no-beautify
alert('Hello'); alert('World');
```

Obično, izjave su pisane na zasebnim linijama kako bi kod bio čitljiviji.

```js run no-beautify
alert('Hello');
alert('World');
```

## Tačka-zarez (eng. semicolon) [#semicolon]

Tačka-zarez može biti izostavljen u većini slučajeva.

Ovo će isto raditi:

```js run no-beautify
alert('Hello')
alert('World')
```

Ovdje, JavaScript interpretira prekid linije kao implicitni tačka-zarez znak. Ovo se naziva [automatski ubacivač tačke-zarez](https://tc39.github.io/ecma262/#sec-automatic-semicolon-insertion).

**U večini slučajeva, nova linija podrazumijeva tačku-zarez. Ali u "u većini slučajeva" ne znači "uvijek"!**

Postoje slučajevi kada nova linija ne znači da će tu biti tačka-zarez. Na primjer:

```js run no-beautify
alert(3 +
1
+ 2);
```

<<<<<<< HEAD
Kod će ispisati `6` jer JavaScript ne ubacuje tačku-zarez ovdje. Ovdje je intuitivno očigledno da ako linija završi sa plus znakom `"+"`, onda je to nepotpun izraz, tako da tačka-zarez znak nije potreban. I u ovom slučaju radi kao i što je predviđeno.
=======
The code outputs `6` because JavaScript does not insert semicolons here. It is intuitively obvious that if the line ends with a plus `"+"`, then it is an "incomplete expression", so a semicolon there would be incorrect. And in this case, that works as intended.
>>>>>>> 30a5d5e2a7c3504c9afd5028f83f4a696e60aede

**Ali postoje situacije kada JavaScript "ne uspije" da pretpostavi gdje treba biti tačka-zarez.

Greške koje se javljaju u ovim slučajevima su malo teže za pronaći i popraviti.

````smart header="Primjer greške"
Ako te zanima konkretan primjer ovakve greške, pogledaj ovaj kod:

```js run
alert("Hello");

[1, 2].forEach(alert);
```

<<<<<<< HEAD
Ne trebate znati značenje ovih zagrada `[]` i `forEach` još. Kasnije ćemo ih naučiti. Za sada, zapamti rezultat koda: pokaže `1` pa onda `2`.

Sada, hajmo dodati `alert` prije koda i *ne* završiti ga sa tačkom-zarez.

```js run no-beautify
alert("Ovdje će biti greška")
=======
No need to think about the meaning of the brackets `[]` and `forEach` yet. We'll study them later. For now, just remember the result of running the code: it shows `Hello`, then `1`, then `2`.

Now let's remove the semicolon after the `alert`:

```js run no-beautify
alert("Hello")
>>>>>>> 30a5d5e2a7c3504c9afd5028f83f4a696e60aede

[1, 2].forEach(alert);
```

<<<<<<< HEAD
Sada ako pokrenemo kod, samo će se prvi `alert` pokazati i onda imamo grešku!

Ali sve je dobro ponovo ako dodamo tačku-zarez poslije `alert`:
```js run
alert("Sada je sve ok");
=======
The difference compared to the code above is only one character: the semicolon at the end of the first line is gone.
>>>>>>> 30a5d5e2a7c3504c9afd5028f83f4a696e60aede

If we run this code, only the first `Hello` shows (and there's an error, you may need to open the console to see it). There are no numbers any more.

<<<<<<< HEAD
Sada imamo "Sada je sve ok" poruku a nakon toga `1` i `2`.


Greška u varijanti bez tačke-zareza se javlja jer JavaScript ne pretpostavi tačku-zarez prije zagrade `[...]`.

Tako da, ako tačka-zarez nije automatski ubačena, kod u prvom primjeru je tretiran kao jedna izjava. Evo kako to motor vidi:

```js run no-beautify
alert("Ovdje će biti greška")[1, 2].forEach(alert)
```

Ali trebaju biti dvije različite izjave, a ne jedna. Povezivanje u ovom slučaju je pogrešno, i zbog toga se javlja greška. Ovo se može desiti u još nekim situacijama.
=======
That's because JavaScript does not assume a semicolon before square brackets `[...]`. So, the code in the last example is treated as a single statement.

Here's how the engine sees it:

```js run no-beautify
alert("Hello")[1, 2].forEach(alert);
```

Looks weird, right? Such merging in this case is just wrong. We need to put a semicolon after `alert` for the code to work correctly.

This can happen in other situations also.
>>>>>>> 30a5d5e2a7c3504c9afd5028f83f4a696e60aede
````

Mi preporučujemo pisanje tačke-zareza između izjava iako su odvojene novom linijom. Ovo pravilo je široko usvojeno od strane zajednice. Hajdemo opet napomenuti *moguće* je izostaviti tačku-zarez u većini vremena. Ali je sigurnije -- pogotovo za početnika -- da se koriste.

## Komentari [#code-comments]

Kako vrijeme proalazi, programi postaju sve kompleksniji i kompleksniji. Postaje neophodno dodavati *komentare* koji opisuju sta kod radi i zašto.

Komentari mogu biti napisani u bilo kojem dijelu skripte. Oni ne utiču na izvršavanje jer ih motor jednostavno ignoriše.

**Jednolinijski komentari počinju sa `//`.**

Ostatak linije onda bude komentar. Može zauzeti cijelu svoju liniju ili biti na liniji uz neku izjavu.

Kao ovdje:
```js run
// Ovaj komentar zauzima cijelu svoju liniju
alert('Hello');

alert('World'); // Ovaj komentar se nalazi uz izjavu
```

**Multilinijski komentari počinju sa <code>/&#42;</code> a završavaju sa <code>&#42;/</code>.**

Kao ovdje:

```js run
/* Primjer sa dvije poruke.
Ovo je multilinijski komentar.
*/
alert('Hello');
alert('World');
```

Sadržaj komentara je ignorisan, tako da ako stavimo kod između <code>/&#42; ... &#42;/</code>, neće biti izvršen.

Ponekad može biti korisno za privremeno isključivanje dijela koda:

```js run
/* Komentarisanje koda
alert('Hello');
*/
alert('World');
```

```smart header="Koristite prečice!"
U većini editora, linija koda može biti komentirana tako što pritisnete `key:Ctrl+/` za jednolinijski komentar i nešto kao `key:Ctrl+Shift+/` -- za multilinijske komentare (prvo zabilježite dio koda pa pritisnite tipke). Za Mac, probajte `key:Cmd` umjesto `key:Ctrl` i `key:Option` umjesto `key:Shift`.
```

````warn header="Ugniježdeni komentari nisu podržani!"
Ne možete stavljati još jedan `/*...*/` unutar `/*...*/`.

Takav kod će prestati raditi sa greškom:

```js run no-beautify
/*
  /* ugniježdeni komentar ?!? */
*/
alert( 'World' );
```
````

Molim vas, nemojte se ustručavati da komentirate vaš kod.

Komentari povećavaju većinu cijelog koda, ali to uopšte nije problem. Postoji mnogo alata koji minimiziraju kod prije nego što ga objavite na produkcijski server. Ti alati brišu komentare, tako da se ne prikazuju u radnim skriptama. Tako da, komentari nemaju negativne uticaje na produkciju.

Kasnije u tutorijalu će biti poglavlje <info:code-quality> koje će objasniti kako pisati bolje komentare.
