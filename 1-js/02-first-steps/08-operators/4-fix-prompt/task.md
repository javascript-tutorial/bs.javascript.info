važnost: 5

---

# Popravi sabiranje

Ovdje imamo kod koji pita korisnika za dva broja i prikazuje njihov zbir.

Ne radi ispravno. Izlaz u primjeru ispod je `12` (za uobičajene prompt vrijednosti).

Zašto? Popravi. Rezultat treba biti `3`.

```js run
let a = prompt("First number?", 1);
let b = prompt("Second number?", 2);

alert(a + b); // 12
```
