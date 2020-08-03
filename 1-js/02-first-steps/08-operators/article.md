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
alert( 5 % 2 ); // 1, ostatak prilikom dijeljenja 5 sa 2
alert( 8 % 3 ); // 2, ostatak prilikom dijeljenja 8 sa 3
```

###  Eksponencija **

Operator eksponencije `a ** b` množi `a` sa sobom `b` puta.

Na primjer:

```js run
alert( 2 ** 2 ); // 4  (2 pomnoženo sa sobom 2 puta)
alert( 2 ** 3 ); // 8  (2 * 2 * 2, 3 puta)
alert( 2 ** 4 ); // 16 (2 * 2 * 2 * 2, 4 puta)
```

Matematički, eksponencija je određena i za ne-cijele brojeve. Na primjer, korijen je eksponencija od `1/2`:

```js run
alert( 4 ** (1/2) ); // 2 (stepen od 1/2 je isti kao i kvadratni korijen)
alert( 8 ** (1/3) ); // 2 (stepen od 1/3 je isti kao kubični korijen)
```


##  Spajanje stringova sa binarnim +

Upoznajmo se sa mogućnostima JavaScript operatora koji su izvan školske aritmetike.

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

Ovdje, operatori rade jedan poslije drugog. Prvi `+` sabira dva broja, tako da vraća `4`, onda sljedeći `+` dodaje string `1`, tako da bude `4 + '1' = 41`.

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

Evo ekstrakta iz [tabele prioriteta](https://developer.mozilla.org/en/JavaScript/Reference/operators/operator_precedence) (ne trebate ovo zapamtiti, ali zapamtite samo da su unary operatori veći od odgovarajućeg binarnog):

| Precedence | Name | Sign |
|------------|------|------|
| ... | ... | ... |
| 17 | unary plus | `+` |
| 17 | unary negation | `-` |
| 16 | exponentiation | `**` |
| 15 | multiplication | `*` |
| 15 | division | `/` |
| 13 | addition | `+` |
| 13 | subtraction | `-` |
| ... | ... | ... |
| 3 | assignment | `=` |
| ... | ... | ... |

As we can see, the "unary plus" has a priority of `17` which is higher than the `13` of "addition" (binary plus). That's why, in the expression `"+apples + +oranges"`, unary pluses work before the addition.

## Assignment

Let's note that an assignment `=` is also an operator. It is listed in the precedence table with the very low priority of `3`.

That's why, when we assign a variable, like `x = 2 * 2 + 1`, the calculations are done first and then the `=` is evaluated, storing the result in `x`.

```js
let x = 2 * 2 + 1;

alert( x ); // 5
```

### Assignment = returns a value

The fact of `=` being an operator, not a "magical" language construct has an interesting implication.

Most operators in JavaScript return a value. That's obvious for `+` and `-`, but also true for `=`.

The call `x = value` writes the `value` into `x` *and then returns it*.

Here's a demo that uses an assignment as part of a more complex expression:

```js run
let a = 1;
let b = 2;

*!*
let c = 3 - (a = b + 1);
*/!*

alert( a ); // 3
alert( c ); // 0
```

In the example above, the result of expression `(a = b + 1)` is the value which was assigned to `a` (that is `3`). It is then used for further evaluations.

Funny code, isn't it? We should understand how it works, because sometimes we see it in JavaScript libraries.

Although, please don't write the code like that. Such tricks definitely don't make code clearer or readable.

### Chaining assignments

Another interesting feature is the ability to chain assignments:

```js run
let a, b, c;

*!*
a = b = c = 2 + 2;
*/!*

alert( a ); // 4
alert( b ); // 4
alert( c ); // 4
```

Chained assignments evaluate from right to left. First, the rightmost expression `2 + 2` is evaluated and then assigned to the variables on the left: `c`, `b` and `a`. At the end, all the variables share a single value.

Once again, for the purposes of readability it's better to split such code into few lines:

```js
c = 2 + 2;
b = c;
a = c;
```
That's easier to read, especially when eye-scanning the code fast.

## Modify-in-place

We often need to apply an operator to a variable and store the new result in that same variable.

For example:

```js
let n = 2;
n = n + 5;
n = n * 2;
```

This notation can be shortened using the operators `+=` and `*=`:

```js run
let n = 2;
n += 5; // now n = 7 (same as n = n + 5)
n *= 2; // now n = 14 (same as n = n * 2)

alert( n ); // 14
```

Short "modify-and-assign" operators exist for all arithmetical and bitwise operators: `/=`, `-=`, etc.

Such operators have the same precedence as a normal assignment, so they run after most other calculations:

```js run
let n = 2;

n *= 3 + 5;

alert( n ); // 16  (right part evaluated first, same as n *= 8)
```

## Increment/decrement

<!-- Can't use -- in title, because the built-in parser turns it into a 'long dash' – -->

Increasing or decreasing a number by one is among the most common numerical operations.

So, there are special operators for it:

- **Increment** `++` increases a variable by 1:

    ```js run no-beautify
    let counter = 2;
    counter++;        // works the same as counter = counter + 1, but is shorter
    alert( counter ); // 3
    ```
- **Decrement** `--` decreases a variable by 1:

    ```js run no-beautify
    let counter = 2;
    counter--;        // works the same as counter = counter - 1, but is shorter
    alert( counter ); // 1
    ```

```warn
Increment/decrement can only be applied to variables. Trying to use it on a value like `5++` will give an error.
```

The operators `++` and `--` can be placed either before or after a variable.

- When the operator goes after the variable, it is in "postfix form": `counter++`.
- The "prefix form" is when the operator goes before the variable: `++counter`.

Both of these statements do the same thing: increase `counter` by `1`.

Is there any difference? Yes, but we can only see it if we use the returned value of `++/--`.

Let's clarify. As we know, all operators return a value. Increment/decrement is no exception. The prefix form returns the new value while the postfix form returns the old value (prior to increment/decrement).

To see the difference, here's an example:

```js run
let counter = 1;
let a = ++counter; // (*)

alert(a); // *!*2*/!*
```

In the line `(*)`, the *prefix* form `++counter` increments `counter` and returns the new value, `2`. So, the `alert` shows `2`.

Now, let's use the postfix form:

```js run
let counter = 1;
let a = counter++; // (*) changed ++counter to counter++

alert(a); // *!*1*/!*
```

In the line `(*)`, the *postfix* form `counter++` also increments `counter` but returns the *old* value (prior to increment). So, the `alert` shows `1`.

To summarize:

- If the result of increment/decrement is not used, there is no difference in which form to use:

    ```js run
    let counter = 0;
    counter++;
    ++counter;
    alert( counter ); // 2, the lines above did the same
    ```
- If we'd like to increase a value *and* immediately use the result of the operator, we need the prefix form:

    ```js run
    let counter = 0;
    alert( ++counter ); // 1
    ```
- If we'd like to increment a value but use its previous value, we need the postfix form:

    ```js run
    let counter = 0;
    alert( counter++ ); // 0
    ```

````smart header="Increment/decrement among other operators"
The operators `++/--` can be used inside expressions as well. Their precedence is higher than most other arithmetical operations.

For instance:

```js run
let counter = 1;
alert( 2 * ++counter ); // 4
```

Compare with:

```js run
let counter = 1;
alert( 2 * counter++ ); // 2, because counter++ returns the "old" value
```

Though technically okay, such notation usually makes code less readable. One line does multiple things -- not good.

While reading code, a fast "vertical" eye-scan can easily miss something like `counter++` and it won't be obvious that the variable increased.

We advise a style of "one line -- one action":

```js run
let counter = 1;
alert( 2 * counter );
counter++;
```
````

## Bitwise operators

Bitwise operators treat arguments as 32-bit integer numbers and work on the level of their binary representation.

These operators are not JavaScript-specific. They are supported in most programming languages.

The list of operators:

- AND ( `&` )
- OR ( `|` )
- XOR ( `^` )
- NOT ( `~` )
- LEFT SHIFT ( `<<` )
- RIGHT SHIFT ( `>>` )
- ZERO-FILL RIGHT SHIFT ( `>>>` )

These operators are used very rarely, when we need to fiddle with numbers on the very lowest (bitwise) level. We won't need these operators any time soon, as web development has little use of them, but in some special areas, such as cryptography, they are useful. You can read the [Bitwise Operators](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Operators/Bitwise_Operators) article on MDN when a need arises.

## Comma

The comma operator `,` is one of the rarest and most unusual operators. Sometimes, it's used to write shorter code, so we need to know it in order to understand what's going on.

The comma operator allows us to evaluate several expressions, dividing them with a comma `,`. Each of them is evaluated but only the result of the last one is returned.

For example:

```js run
*!*
let a = (1 + 2, 3 + 4);
*/!*

alert( a ); // 7 (the result of 3 + 4)
```

Here, the first expression `1 + 2` is evaluated and its result is thrown away. Then, `3 + 4` is evaluated and returned as the result.

```smart header="Comma has a very low precedence"
Please note that the comma operator has very low precedence, lower than `=`, so parentheses are important in the example above.

Without them: `a = 1 + 2, 3 + 4` evaluates `+` first, summing the numbers into `a = 3, 7`, then the assignment operator `=` assigns `a = 3`, and the rest is ignored. It's like `(a = 1 + 2), 3 + 4`.
```

Why do we need an operator that throws away everything except the last expression?

Sometimes, people use it in more complex constructs to put several actions in one line.

For example:

```js
// three operations in one line
for (*!*a = 1, b = 3, c = a * b*/!*; a < 10; a++) {
 ...
}
```

Such tricks are used in many JavaScript frameworks. That's why we're mentioning them. But usually they don't improve code readability so we should think well before using them.
