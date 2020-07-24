važnost: 4

---

# Pisanje const velikim slovima?

Proučite sljedeći kod:

```js
const rođendan = '18.04.1982';

const godine = nekiKod(rođendan);
```

Ovdje imamo konstantu `rođendan` i `godine` koje su izračunate sa `rođendan` uz pomoć nekog koda (kod nije napisan radi kratkoće, i jer detalji ovdje nisu toliko bitni).

Da li bi bilo ispravno da se koriste velika slova za `rođendan`? Za `godine`? Ili za oboje?

```js
const ROĐENDAN = '18.04.1982'; // napisati velikim?

const GODINE = nekiKod(ROĐENDAN); // napisati velikim?
```

