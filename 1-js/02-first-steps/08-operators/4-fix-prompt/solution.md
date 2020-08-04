Razlog je zato što prompt vraća unos korisnika kao string.

Tako da varijable imaju vrijednosti `"1"` i `"2"` respketivno.

```js run
let a = "1"; // prompt("First number?", 1);
let b = "2"; // prompt("Second number?", 2);

alert(a + b); // 12
```

Ono šta mi trebamo uraditi jeste pretvoriti string-ove u brojeve prije `+`. Na primjer, koristeći `Number()` ili dodavajući `+` ispred njih.

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
