# Osnovni operatori, matematika

Mi znamo mnoge operatore iz škole. To su stvari kao što su sabiranje `+`, množenje `*`, oduzimanje `-`, i tako dalje.

U ovom poglavlju, započet ćemo sa jednostavnim operatorima, pa ćemo se onda koncentrisati na one JavaScript specifične aspekte, koji nisu spomenuti u školi.

## Pojmovi: "unary", "binary", "operand"

Prije nego što krenemo, trebamo shvatiti opštu terminologiju.

- *Operand* -- je ono na šta se operatori primjenjuju. Na primjer, u množenju `5 * 2` imamo dva operanda: lijevi operand je `5` a desni je `2`. Ponekad, ljudi ih nazivaju "argument" umjesto "operand".
- Operator je *unary* (matematička operacija koja uključuje samo jedan element) ako ima samo jedan operand. Na primjer, unary negacija `-` mijenja predznak broja:

    ```js run
    let x = 1;

    *!*
    x = -x;
    */!*
    alert( x ); // -1, unary negacija je primjenjena
    ```
- Operator je *binary* (binarni, uključuje dva elementa) ako ima dva operanda. Isti minus postoji u binarnoj formi:

    ```js run no-beautify
    let x = 1, y = 3;
    alert( y - x ); // 2, binarni minus oduzima vrijednosti
    ```

    Formalno rečeno, u primjerima iznad imamo dva različita operatora koji dijele isti simbol: operator negacije, unary operator koji mijenja predznak, i operator oduzimanja, binarni operator koji oduzima jedan broj od drugog.

## Matematika

Sljedeće matematičke operacije su podržane:

- Sabiranje `+`,
- Oduzimanje `-`,
- Množenje `*`,
- Dijeljenje `/`,
- Ostatak `%`,
- Eksponencija `**`.

Prva četiri su jednostavna, dok o `%` i `**` trebamo nešto reći.

### Ostatak %

Operator za ostatak `%`,  uprkos svom izgledu, nije povezan sa postotcima.

Rezultat `a % b` je [ostatak](https://en.wikipedia.org/wiki/Remainder) prilikom cjelobrojne podjele `a` sa `b`.

Na primjer:

```js run
<<<<<<< HEAD
alert( 5 % 2 ); // 1, ostatak prilikom dijeljenja 5 sa 2
alert( 8 % 3 ); // 2, ostatak prilikom dijeljenja 8 sa 3
=======
alert( 5 % 2 ); // 1, the remainder of 5 divided by 2
alert( 8 % 3 ); // 2, the remainder of 8 divided by 3
alert( 8 % 4 ); // 0, the remainder of 8 divided by 4
>>>>>>> 746ad803c878e33182e7fab1578c0d15b9b75ca0
```

###  Eksponencija **

<<<<<<< HEAD
Operator eksponencije `a ** b` množi `a` sa sobom `b` puta.
=======
The exponentiation operator `a ** b` raises `a` to the power of `b`.

In school maths, we write that as a<sup>b</sup>.
>>>>>>> 746ad803c878e33182e7fab1578c0d15b9b75ca0

Na primjer:

```js run
<<<<<<< HEAD
alert( 2 ** 2 ); // 4  (2 pomnoženo sa sobom 2 puta)
alert( 2 ** 3 ); // 8  (2 * 2 * 2, 3 puta)
alert( 2 ** 4 ); // 16 (2 * 2 * 2 * 2, 4 puta)
```

Matematički, eksponencija je određena i za ne-cijele brojeve. Na primjer, korijen je eksponencija od `1/2`:
=======
alert( 2 ** 2 ); // 2² = 4
alert( 2 ** 3 ); // 2³ = 8
alert( 2 ** 4 ); // 2⁴ = 16
```

Just like in maths, the exponentiation operator is defined for non-integer numbers as well.

For example, a square root is an exponentiation by ½:
>>>>>>> 746ad803c878e33182e7fab1578c0d15b9b75ca0

```js run
alert( 4 ** (1/2) ); // 2 (stepen od 1/2 je isti kao i kvadratni korijen)
alert( 8 ** (1/3) ); // 2 (stepen od 1/3 je isti kao kubični korijen)
```


##  Spajanje stringova sa binarnim +

<<<<<<< HEAD
Upoznajmo se sa mogućnostima JavaScript operatora koji su izvan školske aritmetike.
=======
Let's meet the features of JavaScript operators that are beyond school arithmetics.
>>>>>>> 746ad803c878e33182e7fab1578c0d15b9b75ca0

Obično, plus operator `+` sabira brojeve.

Ali, ako se binarni `+` primijeni na string-ove, spaja ih:

```js
let s = "my" + "string";
alert(s); // mystring
```

Zapamtite da ako je bilo koji operand string, onda će se drugi također pretvoriti u string.

Na primjer:

```js run
alert( '1' + 2 ); // "12"
alert( 2 + '1' ); // "21"
```

Vidite, nije bitno da je li prvi ili drugi operand string.

Evo jedan kompleksniji primjer:

```js run
alert(2 + 2 + '1' ); // "41" a ne "221"
```

<<<<<<< HEAD
Ovdje, operatori rade jedan poslije drugog. Prvi `+` sabira dva broja, tako da vraća `4`, onda sljedeći `+` dodaje string `1`, tako da bude `4 + '1' = 41`.
=======
Here, operators work one after another. The first `+` sums two numbers, so it returns `4`, then the next `+` adds the string `1` to it, so it's like `4 + '1' = '41'`.

```js run
alert('1' + 2 + 2); // "122" and not "14"
```
Here, the first operand is a string, the compiler treats the other two operands as strings too. The `2` gets concatenated to `'1'`, so it's like `'1' + 2 = "12"` and `"12" + 2 = "122"`.
>>>>>>> 746ad803c878e33182e7fab1578c0d15b9b75ca0

Binarni `+` je jedini operator koji podržava string-ove na ovaj način. Ostali aritmetički operatori rade samo sa brojevima i uvijek pretvaraju operand-e u brojeve.

Evo šta se desi ako oduzimamo i dijelimo:

```js run
alert( 6 - '2' ); // 4, pretvara '2' u broj
alert( '6' / '2' ); // 3, pretvara oba operand-a u brojeve
```

## Numerična konverzija, unary +

`+` postoji u dvije forme: binarna forma koju smo koristili iznad i unary forma.

Unary plus, ili u drugim riječima, plus operator `+` koji je primijenjen na samo jednu vrijednost, ne radi ništa brojevimna. Ali ako operand nije broj, unary plus ga pretvara u broj.

Na primjer:

```js run
// Nema uticaj na brojeve
let x = 1;
alert( +x ); // 1

let y = -2;
alert( +y ); // -2

*!*
// Pretvara vrijednosti koje nisu brojevi
alert( +true ); // 1
alert( +"" );   // 0
*/!*
```

Radi istu stvar kao `Number(...)`, ali je kraće.

Potreba za pretvaranje string-ova u brojeve se javlja veoma često. Na primjer, ako dobijamo vrijednosti iz HTML polja za unos, one su obično string-ovi. Šta ako želimo da ih saberemo?

Binarni plus će ih dodati kao string-ove:

```js run
let apples = "2";
let oranges = "3";

alert( apples + oranges ); // "23", binarni plus spaja string-ove
```

Ako ih želimo tretirati kao brojeve, moramo ih pretvoriti i sabrati:

```js run
let apples = "2";
let oranges = "3";

*!*
// obe vrijednosti su pretvorene u brojeve prije binarnog plusa
alert( +apples + +oranges ); // 5
*/!*

// duža varijanta
// alert( Number(apples) + Number(oranges) ); // 5
```

Sa stanovišta matematičara, obilje pluseva možda zvuči čudno. Ali sa stanovišta programera, to nije ništa specijalno: unary plusevi se prvo primijenjuju, oni pretvaraju string-ove u brojeve, pa ih tek onda binarni plus sabira.

Zašto su unary plusevi primijenjeni na vrijednosti prije binarnih? To ćemo naučiti ubrzo, razlog toga jeste njihov *veći prioritet*.

## Prioritet operatora

Ako izraz ima više od jednog operatora, onda je red izvršavanja određen njihovim *prioritetima*, ili, u drugim riječima, uobičajenim redom prioriteta operatora.

Iz škole, svi znamo da množenje u izrazu `1 + 2 * 2` treba biti izračunato prije sabiranja. To je tačno ova stvar o prioritetima. Množenje ima *veći prioritet* od sabiranja.

Zagrade nadjačavaju prioritete, tako da ako nismo zadovoljni sa uobičajenim redom, možemo koristiti iste da promijenimo red. Na primjer, napišite `(1 + 2) * 2`.

Postoji mnogo operatora u JavaScript-u. Svaki operator ima određeni nivo prioriteta. Onaj sa većim nivoom se prvi izvršava. Ako je prioritet isti, red izvršavanja je od lijeve ka desnoj strani.

<<<<<<< HEAD
Evo ekstrakta iz [tabele prioriteta](https://developer.mozilla.org/en/JavaScript/Reference/operators/operator_precedence) (ne trebate ovo zapamtiti, ali zapamtite samo da su unary operatori veći od odgovarajućeg binarnog):
=======
Here's an extract from the [precedence table](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Operator_Precedence) (you don't need to remember this, but note that unary operators are higher than corresponding binary ones):
>>>>>>> 746ad803c878e33182e7fab1578c0d15b9b75ca0

| Prioritet | Ime | Znak |
|------------|------|------|
| ... | ... | ... |
<<<<<<< HEAD
| 17 | unary plus | `+` |
| 17 | unary negacija | `-` |
| 16 | eksponencija | `**` |
| 15 | množenje | `*` |
| 15 | dijeljenje | `/` |
| 13 | sabiranje | `+` |
| 13 | oduzimanje | `-` |
| ... | ... | ... |
| 3 | dodjela | `=` |
| ... | ... | ... |

Kao što možemo da vidimo, "unary plus" ima prioritet `17` koji je veći od `13` prioriteta "sabiranja" (binarni plus). Zato, u izrazu `"+apples + +oranges"`, unary plus se prije sabiranja izvršava.

## Dodjela
=======
| 14 | unary plus | `+` |
| 14 | unary negation | `-` |
| 13 | exponentiation | `**` |
| 12 | multiplication | `*` |
| 12 | division | `/` |
| 11 | addition | `+` |
| 11 | subtraction | `-` |
| ... | ... | ... |
| 2 | assignment | `=` |
| ... | ... | ... |

As we can see, the "unary plus" has a priority of `14` which is higher than the `11` of "addition" (binary plus). That's why, in the expression `"+apples + +oranges"`, unary pluses work before the addition.

## Assignment

Let's note that an assignment `=` is also an operator. It is listed in the precedence table with the very low priority of `2`.
>>>>>>> 746ad803c878e33182e7fab1578c0d15b9b75ca0

Zapamtite da je dodjela `=` isto operator. Na listi prioriteta ima mali prioritet `3`.
 
Zato, kada dodijelimo vrijednost varijabli, `x = 2 * 2 + 1`,  kalkulacije su izvršene prvo pa je `=` evaluiran, pohranjujući rezultat u varijablu `x`.

```js
let x = 2 * 2 + 1;

alert( x ); // 5
```

### Dodjela = vraća vrijednost

Činjenica da je `=` operator, a ne "magični" jezički konstrukt ima interesantnu implikaciju.

<<<<<<< HEAD
Većina operatora u JavaScript-u vraćaju vrijednost. To je očigledno za `+` i `-`, ali to isto vrijedi za `=`.
=======
All operators in JavaScript return a value. That's obvious for `+` and `-`, but also true for `=`.
>>>>>>> 746ad803c878e33182e7fab1578c0d15b9b75ca0

Poziv `x = value` piše `value` u `x` *pa je vraća*.

Evo primjera gdje se koristi operator dodjele kao dio složenog izraza:

```js run
let a = 1;
let b = 2;

*!*
let c = 3 - (a = b + 1);
*/!*

alert( a ); // 3
alert( c ); // 0
```

U primjeru iznad, rezultat izraza `(a = b + 1)` je vrijednost koja je dodijeljena `a` (to je `3`).

Smiješan kod, zar ne? Trebamo shvatiti kako radi, jer ga ponekad vidimo u JavaScript bibliotekama (eng. libraries).

Uprkos tome, ne pišite kod na taj način. Takvi trikovi sigurno ne čine da kod bude jasniji ili čitljiviji.

### Lančanje dodjela

Još jedna interesantna mogućnost jeste sposobnost da lančamo dodjele (eng. chain assignments):

```js run
let a, b, c;

*!*
a = b = c = 2 + 2;
*/!*

alert( a ); // 4
alert( b ); // 4
alert( c ); // 4
```

Lančane dodjele se evaluiraju s desna na lijevo. Prvo, najdesniji izraz `2 + 2` je evaluiran pa je dodijeljen varijablama na lijevoj strani: `c`, `b` i `a`. Na kraju, sve varijable dijele istu vrijednost.

Još jednom, kako bi naš kod bio čitljiviji, bolje ga je podijeliti u nekoliko linija:

```js
c = 2 + 2;
b = c;
a = c;
```
Ovo je lakše za čitati, posebno kada brzo pregledavamo kod.

## Modificiranje u mjestu (eng. modify-in-place)

Mi često trebamo primijeniti operator na nekoj varijabli i pohraniti novi rezultat u istoj varijabli.

For example:

```js
let n = 2;
n = n + 5;
n = n * 2;
```

Ova notacija može biti skraćena koristeći operatore `+=` i `*=`:

```js run
let n = 2;
n += 5; // sada n = 7 (isto kao n = n + 5)
n *= 2; // now n = 14 (isto kao n = n * 2)

alert( n ); // 14
```

Kratki "modificiraj-i-dodijeli" operatori postoje za sve aritmetičke i bitwise operatore: `/=`, `-=`, itd.

Takvi operatori imaju isti prioritet kao i prilikom normalnog dodijeljivanja, tako da su oni izvršeni poslije većine drugih kalkulacija:

```js run
let n = 2;

n *= 3 + 5; // right part evaluated first, same as n *= 8

<<<<<<< HEAD
alert( n ); // 16  (desni dio je prvi evaluiran, isto kao n *= 8)
=======
alert( n ); // 16
>>>>>>> 746ad803c878e33182e7fab1578c0d15b9b75ca0
```

## Povećavanje/smanjivanje (eng. increment/decrement)

<!-- Can't use -- in title, because the built-in parser turns it into a 'long dash' – -->

Povećavanje ili smanjivanje broja za jedan je skoro najčešća numerička operacija.

Postoje specijalni operatori za ovu svrhu:

- **Povećavanje** `++` povećava varijablu za 1:

    ```js run no-beautify
    let counter = 2;
    counter++;        // radi isto kao counter = counter + 1, ali je kraće
    alert( counter ); // 3
    ```
- **Smanjivanje** `--` smanjuje varijablu za 1:

    ```js run no-beautify
    let counter = 2;
    counter--;        // radi isto kao counter = counter - 1, ali je kraće
    alert( counter ); // 1
    ```

```warn
Povećavanje/smanjivanje se može primijeniti samo na varijablama. Ako ih pokušamo koristiti na nekoj vrijednosti kao što je `5++` dobit ćemo grešku.
```

Operatori `++` i `--` mogu biti postavljeni ili prije ili poslije varijable.

- Kada se operator nalazi iza varijable, nalazi se u tzv. "postfix formi": `counter++`.
- "Prefix forma" je kada se operator nalazi ispred varijable: `++counter`.

Obe ove izjave rade istu stvar: povećavaju `counter` za `1`.

Ima li razlike? Da, ali možemo je samo vidjeti ako koristimo vraćenu vrijednost od `++/--`.

Hajmo razjasniti. Kao što znamo, svi operatori vraćaju vrijednost. Povećavanje/smanjivanje nije izuzetak. Prefix forma vraća novu vrijednost dok postfix forma vraća staru vrijednost (prije povećavanja ili smanjivanja).

Da vidimo razliku, evo primjera:

```js run
let counter = 1;
let a = ++counter; // (*)

alert(a); // *!*2*/!*
```

Na liniji `(*)`, *prefix* forma `++counter` povećava `counter` i vraća novu vrijednost, `2`. Tako da `alert` prikazuje `2`.

Sada, hajmo koristiti postfix formu:

```js run
let counter = 1;
let a = counter++; // (*) promijenjeno sa ++counter na counter++

alert(a); // *!*1*/!*
```

Na liniji `(*)`, postfix forma `counter++` isto povećava `counter` ali vraća *staru* vrijednost (prije povećavanja). Tako da `alert` prikazuje `1`.

Da rezimiramo:

- Ako rezultat povećavanja/smanjivanja nije korišten, nema razlike u tome koju formu koristite:

    ```js run
    let counter = 0;
    counter++;
    ++counter;
    alert( counter ); // 2, linije iznad su uradile isto
    ```
- Ako želimo povećati vrijednost *i* odmah koristiti rezultat operatora, treba nam prefix forma:

    ```js run
    let counter = 0;
    alert( ++counter ); // 1
    ```
- Ako želimo povećati vrijednost ali koristiti prethodnu, treba nam postfix forma:

    ```js run
    let counter = 0;
    alert( counter++ ); // 0
    ```

````smart header="Povećavanje/smanjivanje među drugim operatorima"
Operatori `++/--` se mogu koristiti unutar izraza. Njihov prioritet je veći od većine drugih aritmetičkih operacija.

For instance:

```js run
let counter = 1;
alert( 2 * ++counter ); // 4
```

Poredite sa:

```js run
let counter = 1;
alert( 2 * counter++ ); // 2, jer counter++ vraća "staru" vrijednost
```

Iako je tehnički ispravno, takva notacija čini kod manje čitljivijim. Jedna linija radi više stvari -- to nije u redu.

Kada čitamo kod, brzim "vertikalnim" prelazom preko istog možemo lagano izostaviti nešto kao `counter++` i neće biti očigledno da je varijabla povećana.

Mi preporučujemo stil "jedna linija -- jedna akcija":

```js run
let counter = 1;
alert( 2 * counter );
counter++;
```
````

## Bitwise operatori

Bitwise operatori tretiraju argumente kao 32-bitne cijele brojeve i rade na nivou njihove binarne reprezentacije.

Ovi operatori nisu specifični za JavaScript. Oni su podržani u većini drugih programskih jezika.

Lista operatora:

- AND ( `&` )
- OR ( `|` )
- XOR ( `^` )
- NOT ( `~` )
- LEFT SHIFT ( `<<` )
- RIGHT SHIFT ( `>>` )
- ZERO-FILL RIGHT SHIFT ( `>>>` )

<<<<<<< HEAD
Ovi operatori se veoma rijetko koriste, kada trebamo da radimo sa brojevima na veoma niskom (bitwise) nivou. Ovi operatori nam neće trebati u bližoj budućnosti, jer u web programiranju imaju malu upotrebu, ali u nekim specijalnim oblastima kao što su kriptografija, su korisni. Možete pročitati [Bitwise Operatori](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Operators/Bitwise_Operators) poglavlje na MDN kada vam zatreba.
=======
These operators are used very rarely, when we need to fiddle with numbers on the very lowest (bitwise) level. We won't need these operators any time soon, as web development has little use of them, but in some special areas, such as cryptography, they are useful. You can read the [Bitwise Operators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Expressions_and_Operators#bitwise_operators) chapter on MDN when a need arises.
>>>>>>> 746ad803c878e33182e7fab1578c0d15b9b75ca0

## Zarez (eng. comma)

Zarez operator `,` je jedan od najrjeđih i najneobičnijih operatora. Ponekad se koristi da pišemo kraći kod, tako da ga trebamo naučiti da znamo šta on zapravo radi.

Zarez operator nam omogućava da evaluiramo više izraza, odvajajući ih zarezima `,`. Svaki od ovih izraza je evaluiran ali je vraćen samo rezultat posljednjeg.

For example:

```js run
*!*
let a = (1 + 2, 3 + 4);
*/!*

alert( a ); // 7 (the result of 3 + 4)
```

Ovdje, prvi izraz `1 + 2` je evaluiran i njegov rezultat je bačen. Onda, `3 + 4` je evaluiran i vraćen je rezultat.

```smart header="Zarez ima veoma nizak prioritet"
Zapamtite da zarez operator ima veoma nizak prioritet, čak i manji od `=`, tako da su zagrade bitne u primjeru iznad.

Bez njih: `a = 1 + 2, 3 + 4` evaluira `+` prvo, sabira brojeve pa dobijemo `a = 3, 7`, pa onda operator dodjele `=` dodijeli `a = 3`, a ostatak je ignorisan. Isto je kao `(a = 1 + 2), 3 + 4`.
```

Zašto nam onda treba operator koji baci sve osim zadnjeg izraza?

Ponekad, ljudi ga koriste u složenijim konstruktima kako bi stavili više akcija u jednu liniju.

Na primjer:

```js
// tri operacije u jednoj liniji
for (*!*a = 1, b = 3, c = a * b*/!*; a < 10; a++) {
 ...
}
```

Takvi trikovi se koriste u mnogo JavaScript framework-a. Zato ih spominjemo. Ali obično ne poboljšavaju čitljivost koda tako da trebamo dobro razmisliti prije nego što ih upotrijebimo.
