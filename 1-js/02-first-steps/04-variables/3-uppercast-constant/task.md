važnost: 4

---

# Pisanje const velikim slovima?

Proučite sljedeći kod:

```js
const rođendan = '18.04.1982';

const godine = nekiKod(rođendan);
```

<<<<<<< HEAD
Ovdje imamo konstantu `rođendan` i `godine` koje su izračunate sa `rođendan` uz pomoć nekog koda (kod nije napisan radi kratkoće, i jer detalji ovdje nisu toliko bitni).
=======
Here we have a constant `birthday` for the date, and also the `age` constant.

The `age` is calculated from `birthday` using `someCode()`, which means a function call that we didn't explain yet (we will soon!), but the details don't matter here, the point is that `age` is calculated somehow based on the `birthday`.
>>>>>>> 5dff42ba283bce883428c383c080fa9392b71df8

Da li bi bilo ispravno da se koriste velika slova za `rođendan`? Za `godine`? Ili za oboje?

```js
<<<<<<< HEAD
const ROĐENDAN = '18.04.1982'; // napisati velikim?

const GODINE = nekiKod(ROĐENDAN); // napisati velikim?
=======
const BIRTHDAY = '18.04.1982'; // make birthday uppercase?

const AGE = someCode(BIRTHDAY); // make age uppercase?
>>>>>>> 5dff42ba283bce883428c383c080fa9392b71df8
```
