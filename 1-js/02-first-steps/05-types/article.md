# Tipovi podataka

Vrijednost u JavaScript-u uvijek ima određen tip. Na primjer, tekst (eng. string) ili broj (eng. number).

Postoji osam osnovnih tipova podataka u JavaScript-u. Ovdje ćemo ih spomenuti površno a u sljedećim poglavljima ćemo učiti detaljno o svakom pojedinačno.

Možemo staviti svaki tip u varijablu. Na primjer, varijabla može u jednom momentu biti tekst pa se u nju može pohraniti broj:

```js
// ovdje nema greške
let message = "hello";
message = 123456;
```

Programski jezici koji dozvoljavaju ove stvari, kao JavaScript, se nazivaju "dinamički pisani" (eng. dynamically typed), što žnači da postoje tipovi podataka, ali varijable nisu povezane ni za jedan tip.

## Broj

```js
let n = 123;
n = 12.345;
```

 Broj tj. *number* tip reprezentira oboje, i cijele brojeve i brojeve sa decimalnim zarezom.

Postoji mnogo operacija za brojeve, na primjer množenje (eng. multiplication) `*`, dijeljenje (eng. division) `/`,  sabiranje (eng. addition) `+`, oduzimanje (eng. subtraction) `-`, itd.

Pored običnih brojeva, postoje takozvane "specialne numeričke vrijednosti" (eng. special numeric values) koje isto tako pripadaju ovom tipu podataka: `Infinity`, `-Infinity` and `NaN`.

- `Infinity` reprezentira matematičku [beskonačnost](https://en.wikipedia.org/wiki/Infinity) ∞. To je specialna vrijednost koja je veća od svakog broja.

    Možemo je dobiti ako neki broj podijelimo sa nulom:

    ```js run
    alert( 1 / 0 ); // Infinity
    ```

    Ili ako je referenciramo direktno:

    ```js run
    alert( Infinity ); // Infinity
    ```
- `NaN` (eng. not a number) reprezentira grešku u računanju. To je rezultat nepravilne ili neodređene matematičke operacije, na primjer:

    ```js run
    alert( "not a number" / 2 ); // NaN, ovakva podjela je nepravilna
    ```

<<<<<<< HEAD
    `NaN` je ljepljiv. Bilo koje dodatne operacije na `NaN` vraćaju `NaN`:
=======
    `NaN` is sticky. Any further mathematical operation on `NaN` returns `NaN`:
>>>>>>> 1edb0a38330b54d2e1916f5193fc043e6fbbea78

    ```js run
    alert( NaN + 1 ); // NaN
    alert( 3 * NaN ); // NaN
    alert( "not a number" / 2 - 1 ); // NaN
    ```

<<<<<<< HEAD
    Tako da, ako je negdje `NaN` u matematičkom izrazu, širi se na čitav rezultat.
=======
    So, if there's a `NaN` somewhere in a mathematical expression, it propagates to the whole result (there's only one exception to that: `NaN ** 0` is `1`).
>>>>>>> 1edb0a38330b54d2e1916f5193fc043e6fbbea78

```smart header="Matematičke operacije su sigurne"
Raditi matematiku u JavaScript-u je "sigurno". Možemo uraditi bilo šta: podijeliti sa nulom, ophoditi se sa ne numeričkim tekstom kao brojem, itd.

Skripta se nikada neće zaustaviti sa fatalnom greškom ("die"). U najgorem slučaju, dobit ćemo `NaN` kao rezultat.
```

Specijalne numeričke vrijednosti formalno pripadaju "number" tipu. Naravno, nisu brojevi u zdravom smislu ove riječi.

Naučit ćemo više o brojevima i kako raditi sa njima u poglavlju <info:number>.

<<<<<<< HEAD
## BigInt (veliki cijeli broj)

U JavaScript-u, "number" tip ne može reprezentirati vrijednost cijelih brojeva večih od <code>(2<sup>53</sup>-1)</code> (to je `9007199254740991`), ili manjih od <code>-(2<sup>53</sup>-1)</code> za negativne brojeve. To je tehničko ograničenje izazvano od unutrašnje reprezentacije.

Za većinu namjena to je dovoljno, ali nekada nam trebaju veoma veliki brojevi, na primjer za kriptografiju ili vremenske oznake precizne u mikrosekundu.
=======
## BigInt [#bigint-type]

In JavaScript, the "number" type cannot safely represent integer values larger than <code>(2<sup>53</sup>-1)</code> (that's `9007199254740991`), or less than <code>-(2<sup>53</sup>-1)</code> for negatives.

To be really precise, the "number" type can store larger integers (up to <code>1.7976931348623157 * 10<sup>308</sup></code>), but outside of the safe integer range <code>±(2<sup>53</sup>-1)</code> there'll be a precision error, because not all digits fit into the fixed 64-bit storage. So an "approximate" value may be stored.

For example, these two numbers (right above the safe range) are the same:

```js
console.log(9007199254740991 + 1); // 9007199254740992
console.log(9007199254740991 + 2); // 9007199254740992
```

So to say, all odd integers greater than <code>(2<sup>53</sup>-1)</code> can't be stored at all in the "number" type.

For most purposes <code>±(2<sup>53</sup>-1)</code> range is quite enough, but sometimes we need the entire range of really big integers, e.g. for cryptography or microsecond-precision timestamps.
>>>>>>> 1edb0a38330b54d2e1916f5193fc043e6fbbea78

`BigInt` tip je nedavno dodan u jezik da reprezentira cijele brojeve proizvoljne dužine.

`BigInt` vrijednost je napravljena dodavanjem nastavka `n` na kraj cijelog broja:

```js
// "n" na kraju znači da je u pitanju BigInt
const bigInt = 1234567890123456789012345678901234567890n;
```

Jer `BigInt` brojevi su rijetko potrebni, nećemo ovdje ići u detalje, ali imamo odvojeno poglavlje gdje možete naučiti više o njima <info:bigint>. Pročitajte to ako i kad radili sa velikim brojevima.

<<<<<<< HEAD
```smart header="Problemi kompatibilnosti"
Trenutno `BigInt` je podržan u Firefox-u/Chrome-u/Edge-u, ali nije u Safari-u/Internet Explorer-u.
```

## String (tekst)
=======

```smart header="Compatibility issues"
Right now, `BigInt` is supported in Firefox/Chrome/Edge/Safari, but not in IE.
```

You can check [*MDN* BigInt compatibility table](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/BigInt#Browser_compatibility) to know which versions of a browser are supported.

## String
>>>>>>> 1edb0a38330b54d2e1916f5193fc043e6fbbea78

Tekst u JavaScript-u mora biti okružen navodnicima.

```js
let str = "Hello";
let str2 = 'Single quotes are ok too';
let phrase = `can embed another ${str}`;
```

U JavaScript-u, postoje 3 tipa navodnika.

1. Dvostruki navodnici (eng. double quotes): `"Hello"`.
2. Jednostruki navodnici (eng. single quotes): `'Hello'`.
3. Backtick-ovi (eng. backticks) : <code>&#96;Hello&#96;</code>.

dvostruki i jednostruki su "jednostavni" navodnici. Praktično između njih nema razlike u JavaScript-u.

Backtick-ovi su su navodnici koji imaju "produženu funkcionalnost". Dozvoljavaju nam da ugradimo (eng. embed) varijable i izraze u tekst tako što ih okružimo sa `${…}`, na primjer:

```js run
let name = "John";

// ugrađivanje varijable
alert( `Hello, *!*${name}*/!*!` ); // Hello, John!

// ugrađivanje izraza
alert( `the result is *!*${1 + 2}*/!*` ); // rezultat je 3
```

Izraz između `${…}` je izračunat i rezultat postane dio teksta. Možemo staviti bilo šta unutra: varijablu `name` ili aritmetički izraz kao što je `1 + 2` ili nešto više kompleksno..

Molim vas zapamtite da se ovo može raditi samo u backtick-ovima. Ostali navodnici nemaju ovu funkcionalnost ugrađivanja!
```js run
alert( "the result is ${1 + 2}" ); // the result is ${1 + 2} (dvostruki navodnici ništa ne rade)
```

Naučit ćemo o tekstu više u ovom poglavlju <info:string>.

```smart header="Ne postoji *character* tip"
U nekim jezicima, postoji specialan "character" tip za pojedinačan karakter (znak,slovo,broj). Na primjer, u C jeziku i u Javi ima, i zove se "char".

<<<<<<< HEAD
U JavaScript-u, ne postoji takav tip. Postoji samo jedan tip: `string`. Tekst se može sastojati samo od jednog karaktera ili više njih.
=======
In JavaScript, there is no such type. There's only one type: `string`. A string may consist of zero characters (be empty), one character or many of them.
>>>>>>> 1edb0a38330b54d2e1916f5193fc043e6fbbea78
```

## Boolean (logički tip)

Boolean tip ima samo dvije vrijednosti `true` i `false`.

Ovaj tip je često koristen da pohrani da/ne (eng. yes/no) vrijednosti: `true` znači "da, tačno", a `false` znači "ne, netačno".

Na primjer:

```js
let nameFieldChecked = true; // da, polje za ime je čekirano
let ageFieldChecked = false; // ne, polje za godine nije čekirano
```

Boolean vrijednosti isto dolaze kao rezultat poređenja:

```js run
let isGreater = 4 > 1;

alert( isGreater ); // true (rezultat poređenja je true (tačan) jer je 4 veće od 1)
```

Naučit ćemo o boolean tipu dublje u pogljavlju <info:logical-operators>.

## "null" vrijednost

Specialna `null` vrijednost ne pripada nijednom tipu napisanim iznad.

Ono formira svoj odvojen tip koji samo sadrži `null` vrijednost:

```js
let age = null;
```

U JavaScript-u, `null` nije "referenca nekog ne postojećeg objekta" (eng. reference to a non-existing object) ili "null indikator" (eng. null pointer) kao u drugim jezicima.

To je samo specijalna vrijednost koja reprezentira "ništa" (eng. nothing), "prazno" (eng. empty), ili "vrijednost nepoznata" (eng. value unknown).

Kod iznad navodi da je `age` nepoznat.

## "undefined" (neodređena) vrijednost

Specijalna vrijednost `undefined` isto je drugačija od ostalih. Pravi svoj tip, baš kao `null`.

Značenje `undefined` jeste "vrijednost nije dodijeljena" (eng. value is not assigned).

Ako je varijabla deklarisana, ali joj nije dodijeljena vrijednost, onda vrijednost iznosi `undefined`:

```js run
let age;

alert(age); // pokazuje "undefined"
```

Tehnički, moguće je eksplicitno dodijeliti `undefined` nekoj varijabli:

```js run
let age = 100;

// promijeni vrijednost na undefined
age = undefined;

alert(age); // "undefined"
```

...Ali mi ne preporučujemo da se to radi. Obično, treba se koristiti `null` ako želimo dodijeliti praznu ili nepoznatu vrijednost varijabli, jer je `undefined` rezervisan kao uobičajena inicialna vrijednost za stvari kojima nije dodijeljena vrijednost.

## Objekti i Simboli (eng. objects and symbols)

`object` tip je specialan.

Svi ostali tipovi su takozvani "primitivni" (eng. primitive) jer njihove vrijednosti mogu sadržiti samo jednu stvar (ili tekst ili broj ili bilo šta drugo). U kontrastu, objekti se koriste da pohrane kolekcije podataka i više kompleksnih entiteta.

Pošto su tako bitni, objekti zaslužuju specijalni tretman. O njima ćemo kasnije učiti u poglavlju <info:object>, nakon što naučimo više o primitivnim vrijednostima.

`symbol` tip se koristi da kreira unikatne identifikatore za objekte. Moramo ga spomenuti radi potpunosti, ali ćemo odgoditi detalje sve dok ne naučimo objekte.

## typeof operator [#type-typeof]

`typeof` operator vraća tip podatka datog argumenta. Koristan je kada želimo procesirati vrijednosti različitih tipova drugačije ili kada želimo uraditi brzu provjeru.

<<<<<<< HEAD
Podržava dvije vrste sintakse:

1. Kao operator: `typeof x`.
2. Kao funkcija: `typeof(x)`.

U drugim riječima, radi sa zagradama ili bez njih. Rezultat je isti.

Poziv na `typeof x` vraća tekst sa imenom tipa podatka:
=======
A call to `typeof x` returns a string with the type name:
>>>>>>> 1edb0a38330b54d2e1916f5193fc043e6fbbea78

```js
typeof undefined // "undefined"

typeof 0 // "number"

typeof 10n // "bigint"

typeof true // "boolean"

typeof "foo" // "string"

typeof Symbol("id") // "symbol"

*!*
typeof Math // "object"  (1)
*/!*

*!*
typeof null // "object"  (2)
*/!*

*!*
typeof alert // "function"  (3)
*/!*
```

Zadnje tri linije možda trebaju dodatno objašnjenje:

<<<<<<< HEAD
1. `Math` je ugrađen (eng. built-in) objekat koji pruža matematičke operacije. Učit ćemo više o tome poglavlju <info:number>. Ovjde, služi samo kao primjer objekta.
2. Rezultat `typeof null` je `"object"`. To je zvanično priznata greška u ponašasanju `typeof`, dolazi iz ranih dana JavaScript-a i zadržano je za kompatibilnost. Definitivno, `null` nije objekat. To je specijalna vrijednost sa svojim odvojenim tipom.
3. Rezultat `typeof alert` je `"function"`, jer je `alert` funkcija. Učit ćemo o funkcijama u sljedećim poglavljima gdje ćemo vidjeti da ne postoji specijalni "function" tip u JavaScript-u. Funkcije pripadaju tipu objekat (eng. object). Ali `typeof` se ophodi drugačije, i vraća `"function"`. I ovo isto dolazi iz ranih dana JavaScript-a. Tehnički, ovakvo ponašanje nije tačno, ali može biti prikladno u praksi.

## Sažetak
=======
1. `Math` is a built-in object that provides mathematical operations. We will learn it in the chapter <info:number>. Here, it serves just as an example of an object.
2. The result of `typeof null` is `"object"`. That's an officially recognized error in `typeof`, coming from very early days of JavaScript and kept for compatibility. Definitely, `null` is not an object. It is a special value with a separate type of its own. The behavior of `typeof` is wrong here.
3. The result of `typeof alert` is `"function"`, because `alert` is a function. We'll study functions in the next chapters where we'll also see that there's no special "function" type in JavaScript. Functions belong to the object type. But `typeof` treats them differently, returning `"function"`. That also comes from the early days of JavaScript. Technically, such behavior isn't correct, but can be convenient in practice.

```smart header="The `typeof(x)` syntax"
You may also come across another syntax: `typeof(x)`. It's the same as `typeof x`.

To put it clear: `typeof` is an operator, not a function. The parentheses here aren't a part of `typeof`. It's the kind of parentheses used for mathematical grouping.

Usually, such parentheses contain a mathematical expression, such as `(2 + 2)`, but here they contain only one argument `(x)`. Syntactically, they allow to avoid a space between the `typeof` operator and its argument, and some people like it.

Some people prefer `typeof(x)`, although the `typeof x` syntax is much more common.
```

## Summary
>>>>>>> 1edb0a38330b54d2e1916f5193fc043e6fbbea78

Postoji 8 osnovnih tipova podataka u JavaScript-u.

<<<<<<< HEAD
- `number` za brojeve bilo koje vrste: cijeli broj ili broj sa decimalnim zarezom, cijeli brojevi su ograničeni do ±2<sup>53</sup>.
- `bigint` je za cijele brojeve proizvoljne dužine.
- `string` za tekst. String može imati nula ili više karaktera, ne postoji odvojen singl-karakter tip podatka.
- `boolean` za `true`/`false`.
- `null` za nepoznate vrijednosti -- samostalni tip koji ima samo jednu vrijednost `null`.
- `undefined` za ne dodijeljene vrijednosti -- samostalni tip koji imaju samo jednu vrijednost `undefined`.
- `object` za kompleksnije strukture podataka.
- `symbol` za unikatne identifikatore.
=======
- Seven primitive data types:
    - `number` for numbers of any kind: integer or floating-point, integers are limited by <code>±(2<sup>53</sup>-1)</code>.
    - `bigint` for integer numbers of arbitrary length.
    - `string` for strings. A string may have zero or more characters, there's no separate single-character type.
    - `boolean` for `true`/`false`.
    - `null` for unknown values -- a standalone type that has a single value `null`.
    - `undefined` for unassigned values -- a standalone type that has a single value `undefined`.
    - `symbol` for unique identifiers.
- And one non-primitive data type:
    - `object` for more complex data structures.
>>>>>>> 1edb0a38330b54d2e1916f5193fc043e6fbbea78

`typeof` operator nam dozvoljava da vidimo koji tip podatka je pohranjen u nekoj varijabli.

<<<<<<< HEAD
- Dvije vrste: `typeof x` ili `typeof(x)`.
- Vraća tekst sa imenom tipa podatka, na primjer `"string"`.
- Za `null` vraća `"object"` -- ovo je greška u jeziku, nije zapravo objekat.
=======
- Usually used as `typeof x`, but `typeof(x)` is also possible.
- Returns a string with the name of the type, like `"string"`.
- For `null` returns `"object"` -- this is an error in the language, it's not actually an object.
>>>>>>> 1edb0a38330b54d2e1916f5193fc043e6fbbea78

U sljedećim poglavljima, koncetrirat ćemo se na primitivne vrijednosti i kada se upoznamo s njima, preći ćemo na objekte.
