Razlog je zato što prompt vraća unos korisnika kao string.

Tako da varijable imaju vrijednosti `"1"` i `"2"` respketivno.

```js run
let a = "1"; // prompt("First number?", 1);
let b = "2"; // prompt("Second number?", 2);

alert(a + b); // 12
```

<<<<<<< HEAD
Ono šta mi trebamo uraditi jeste pretvoriti string-ove u brojeve prije `+`. Na primjer, koristeći `Number()` ili dodavajući `+` ispred njih.
=======
What we should do is to convert strings to numbers before `+`. For example, using `Number()` or prepending them with `+`.
>>>>>>> 8d9ecb724c7df59774d1e5ffb5e5167740b7d321

Na primjer, prije `prompt`:

```js run
let a = +prompt("First number?", 1);
let b = +prompt("Second number?", 2);

alert(a + b); // 3
```

Ili u `alert`:

```js run
let a = prompt("First number?", 1);
let b = prompt("Second number?", 2);

alert(+a + +b); // 3
```

Koristimo i unary i binarne `+` u zadnjem kodu. Izgleda smiješno, zar ne?
