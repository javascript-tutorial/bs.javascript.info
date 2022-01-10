# Interakcija: alert, prompt, confirm

Pošto ćemo koristiti pretraživač kao naše okruženje, pogledat ćemo nekoliko funkcija kojim možemo vršiti interakciju sa korisnicima: `alert`, `prompt` i `confirm`.

## alert (znak za uzbunu)

Ovaj smo već vidjeli. Pokaže poruku i čeka na korisnika da pritisne "OK".

Na primjer:

```js run
alert("Hello");
```

Mini-prozorčić se naziva *modalni prozor* (eng. modal window). Riječ "modalni" znači da posjetilac ne može djelovati na ostatak stranice, pritiskati ostale tipke, itd, dok ne ugasi ovaj prozorčić. U ovom slučaju -- dok ne pritisne "OK".

## prompt (redak)

Funkcija `prompt` prihvata dva argumenta:

```js no-beautify
result = prompt(title, [default]);
```

Prikaže modalni prozorčić sa tekstualnom porukom, polje za unos, i tipke OK/Cancel.

`title`
: Tekst prikazan posjetiocu.

`default`
: Neobavezni drugi parametar, inicijalna vrijednost za polje unosa.

<<<<<<< HEAD
```smart header="Srednje zagrade u sintaksi `[...]`"
Srednje zagrade oko `default` u sintaksi pokazuju da je taj parametar opcionalan, nije potreban.
=======
```smart header="The square brackets in syntax `[...]`"
The square brackets around `default` in the syntax above denote that the parameter is optional, not required.
>>>>>>> 246c600f11b4e6c52b4ae14f83e65319671f998f
```

Posjetilac može nešto u polje napisati i pritisnuti OK. Onda ćemo dobiti taj tekst kao `result`. Ili mogu prekinuti unos pritiskom na Cancel ili `key:Esc` tipku, i tada dobijamo `null` kao `rezultat`.

Poziv na prompt vraća tekst koji je unešen u polju, ili `null` ako je unos prekinut.

Na primjer:

```js run
let age = prompt('How old are you?', 100);

alert(`You are ${age} years old!`); // You are 100 years old (Imate 100 godina) !
```

````warn header="U Internet Explorer-u: Uvijek postavite `default` (tj. uobičajenu vrijednost)"
Drugi parametar je opcionalan, ali ako ga ne postavimo, Internet Explorer će ubaciti teksst `"undefined"` u prompt.

Pokrenite ovaj kod u Internet Explorer-u da vidite:

```js run
let test = prompt("Test");
```

Tako da prompt-ovi izgledaju dobro u IE, mi preporučujemo da uvijek unesete drugi argument:

```js run
let test = prompt("Test", ''); // <-- za IE
```
````

## confirm (potvrditi)

Sintaksa:

```js
result = confirm(question);
```

Funkcija `confirm` pokazuje modalni prozorčić sa `question` (eng. pitanje) i dvije tipke: OK i Cancel (eng. otkazati).

Rezultat je `true` ako je pritisnuta tipka OK a `false` u suprotnom.

Na primjer:

```js run
let isBoss = confirm("Are you the boss?");

alert( isBoss ); // true ako je OK pritisnuto
```

## Sažetak

Spomenuli smo 3 funkcije specifične za pretraživače sa kojima možemo vršiti interakciju sa korisnicima:

`alert`
: prikazuje poruku.

`prompt`
: prikazuje poruku i pita korisnika da unese tekst. Vraća tekst ili, ako je pritisnuta tipka Cancel ili `key:Esc`, vraća `null`.

`confirm`
: prikazuje poruku i čeka na korisnika da pritisne "OK" ili "Cancel". Vraća `true` za OK a `false` za Cancel/`key:Esc`.

Sve ove metode (eng. methods) su modalne: zaustave izvršavanje skripte i ne dozvoljavaju posjetiocu da ima interakciju sa ostatkom stranice dok se prozor ne zatvori.

Postoje dva ograničenja za svaku metodu koju smo naveli:

1. Egzaktna lokacija modalnog prozorčića je određena od strane pretraživača. Najčešće je u sredini.
2. Egzaktni izgled prozorčića isto zavisi od pretraživača. Ne možemo izgled mijenjati.

To je cijena koju plaćamo za jednostavnost. Postoje drugi načini da pokažemo prozorčiće sa boljim izgledom i interakcijom sa posjetiocima, ali ako nam ti faktori nisu bitni, ove metode rade sasvim u redu.
