# Pretvaranje tipova podataka

Većinom vremena, operatori i funkcije automatski pretvaraju vrijednosti koje su im date u ispravan tip podatka.

Na primjer, `alert` automatski pretvara bilo koju vrijednost u string da je prikaže. Matematičke operacije pretvaraju vrijednosti u brojeve.

Postoje slučajevi kada trebamo eksplicitno pretvoriti vrijednost u očekivani tip podatka.

<<<<<<< HEAD
```smart header="Ne pričamo još o objektima"
U ovom poglavlju, nećemo preći objekte. Za sada pričamo samo o primitivnim vrijednostima i tipovima.
=======
```smart header="Not talking about objects yet"
In this chapter, we won't cover objects. For now, we'll just be talking about primitives.
>>>>>>> 9e3fa1351f80cfd6353a778a55b2c86bca9e895f

Kasnije, kada naučimo o objektima, u poglavlju <info:object-toprimitive> pogledat ćemo kako se objekti uklapaju.
```

## Pretvaranje u string

Pretvaranje u string se vrši kada nam treba string oblik vrijednosti.

Na primjer, `alert(value)` to radi da pokaže vrijednost.

Možemo isto pozvati `String(value)` funkciju da pretvorimo vrijednost u string:

```js run
let value = true;
alert(typeof value); // boolean

*!*
value = String(value); // sada vrijednost je string "true"
alert(typeof value); // string
*/!*
```

Pretvaranje u string je većinom očigledno. `false` postaje `"false"`, `null` postaje `"null"`, itd.

## Pretvaranje u brojeve

<<<<<<< HEAD
Pretvaranje u brojeve se u matematičkim funkcijama i izrazima vrši automatski.
=======
Numeric conversion in mathematical functions and expressions happens automatically.
>>>>>>> 9e3fa1351f80cfd6353a778a55b2c86bca9e895f

Na primjer, kada primjenjujemo dijeljenje `/` na vrijednostima koje nisu brojevi:

```js run
alert( "6" / "2" ); // 3, string-ovi su pretvoreni u brojeve
```

Možemo koristiti `Number(value)` funkciju da eksplicitno pretvorimo `value` u broj:

```js run
let str = "123";
alert(typeof str); // string

let num = Number(str); // postane broj 123

alert(typeof num); // number
```

Eksplicitna konverzija je obično potrebna kada čitamo vrijednost iz nekog izvora kao što je tekst form-e ali očekujemo broj da bude unesen.

Ako string nije validan broj, rezultat takve konverzije će biti `NaN`. Na primjer:

```js run
let age = Number("an arbitrary string instead of a number");

alert(age); // NaN, konverzija nije bila uspješna
```

Pravila prilikom pretvaranja u brojeve:

| Vrijednost |  Postane... |
|-------|-------------|
|`undefined`|`NaN`|
|`null`|`0`|
<<<<<<< HEAD
|<code>true&nbsp;i&nbsp;false</code> | `1` i `0` |
| `string` | Razmaci sa početka i kraja će biti izbrisani. Ako je preostali string prazan, rezultat je `0`. U suprotnom, broj je "očitan" iz string-a. Greška prilikom konverzije će dati `NaN`. |
=======
|<code>true&nbsp;and&nbsp;false</code> | `1` and `0` |
| `string` | Whitespaces (includes spaces, tabs `\t`, newlines `\n` etc.) from the start and end are removed. If the remaining string is empty, the result is `0`. Otherwise, the number is "read" from the string. An error gives `NaN`. |
>>>>>>> 9e3fa1351f80cfd6353a778a55b2c86bca9e895f

Primjer:

```js run
alert( Number("   123   ") ); // 123
alert( Number("123z") );      // NaN (greška prilikom čitanja broja na "z")
alert( Number(true) );        // 1
alert( Number(false) );       // 0
```

Upamtite da se `null` i `undefined` ponašaju različito ovdje: `null` postaje nula dok `undefined` postaje `NaN`.

Većina matematičkih operatora isto vrše ovakve konverzije, a o tome ćemo pričati u sljedećem poglavlju.

## Pretvaranje u Boolean

Boolean konverzija je najjednostavnija.

Javlja se u logičkim operacijama (kasnije ćemo se upoznati sa kondicionalnim testovima i sličnim stvarima) ali se isto može izvršiti eksplicitno ako pozovemo funkciju `Boolean(value)`.

Pravila tokom konverzije:

- Vrijednosti koje su intuitivno "prazne", kao `0`, prazan string, `null`, `undefined`, i `NaN`, postaju `false`.
- Ostale vrijednosti postaju `true`.

Na primjer:

```js run
alert( Boolean(1) ); // true
alert( Boolean(0) ); // false

alert( Boolean("hello") ); // true
alert( Boolean("") ); // false
```

````warn header="Zapamtite: string sa nulom `\"0\"` je `true`"
Neki jezici (kao što je PHP) tretiraju `"0"` kao `false`. Ali u JavaScript-u, string koji nije prazan je uvijek `true`.

```js run
alert( Boolean("0") ); // true
alert( Boolean(" ") ); // razmaci, isto true (bilo koji string koji nije prazan je true)
```
````

## Sažetak

Tri najčešće korištene konverzije su u string, broj ili boolean.

**`Pretvaranje u string`** -- Javlja se kada nešto prikazujemo kao izlaz. Konverzija može biti izvršena sa `String(value)`. Konverzija u string je obično očigledna za primitivne vrijednosti.

**`Pretvaranje u brojeve`** -- Javlja se u matematičkim operacijama. Konverzija može biti izvršena sa `Number(value)`.

Pravila konverzije:

| Vrijednost |  Postaje... |
|-------|-------------|
|`undefined`|`NaN`|
|`null`|`0`|
|<code>true&nbsp;/&nbsp;false</code> | `1 / 0` |
<<<<<<< HEAD
| `string` | String je pročitan "kakav jeste", razmaci sa obe strane su ignorisani. Prazan string je `0`. Greška prilikom konverzije daje `NaN`. |
=======
| `string` | The string is read "as is", whitespaces (includes spaces, tabs `\t`, newlines `\n` etc.) from both sides are ignored. An empty string becomes `0`. An error gives `NaN`. |
>>>>>>> 9e3fa1351f80cfd6353a778a55b2c86bca9e895f

**`Pretvaranje u boolean`** -- Javlja se u logičkim operacijama. Konverzija može biti izvršena sa `Boolean(value)`.

Prati sljedeća pravila:

| Vrijednost |  Postaje... |
|-------|-------------|
|`0`, `null`, `undefined`, `NaN`, `""` |`false`|
|bilo koja druga vrijednost| `true` |


Većina ovih pravila su lagana za shvatiti i zapamtiti. Izuzeci gdje ljudi često prave greške su:

- `undefined` je `NaN` kao broj, ne `0`.
- `"0"` i stringovi koji imaju samo razmak `"   "` su true kao boolean.

Objekti nisu spomenuti ovdje. Doći ćemo do njih u poglavlju <info:object-toprimitive> koji je posvećen ekskluzivno objektima, ali do njih ćemo doći tek kada naučimo još neke osnovne stvari o JavaScript-u.
