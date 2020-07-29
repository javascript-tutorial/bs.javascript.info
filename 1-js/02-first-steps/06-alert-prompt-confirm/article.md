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

```smart header="Srednje zagrade u sintaksi `[...]`"
Srednje zagrade oko `default` u sintaksi pokazuju da je taj parametar opcionalan, nije potreban.
```

Posjetilac može nešto u polje napisati i pritisnuti OK. Onda ćemo dobiti taj tekst kao `result`. Ili mogu prekinuti unos pritiskom na Cancel ili `key:Esc` tipku, i tada dobijamo `null` kao `rezultat`.

Poziv na prompt vraća tekst koji je unešen u polju, ili `null` ako je unos prekinut.

Na primjer:

```js run
let age = prompt('How old are you?', 100);

alert(`You are ${age} years old!`); // You are 100 years old (Imate 100 godina) !
```

````warn header="In IE: always supply a `default`"
The second parameter is optional, but if we don't supply it, Internet Explorer will insert the text `"undefined"` into the prompt.

Run this code in Internet Explorer to see:

```js run
let test = prompt("Test");
```

So, for prompts to look good in IE, we recommend always providing the second argument:

```js run
let test = prompt("Test", ''); // <-- for IE
```
````

## confirm

The syntax:

```js
result = confirm(question);
```

The function `confirm` shows a modal window with a `question` and two buttons: OK and Cancel.

The result is `true` if OK is pressed and `false` otherwise.

For example:

```js run
let isBoss = confirm("Are you the boss?");

alert( isBoss ); // true if OK is pressed
```

## Summary

We covered 3 browser-specific functions to interact with visitors:

`alert`
: shows a message.

`prompt`
: shows a message asking the user to input text. It returns the text or, if Cancel button or `key:Esc` is clicked, `null`.

`confirm`
: shows a message and waits for the user to press "OK" or "Cancel". It returns `true` for OK and `false` for Cancel/`key:Esc`.

All these methods are modal: they pause script execution and don't allow the visitor to interact with the rest of the page until the window has been dismissed.

There are two limitations shared by all the methods above:

1. The exact location of the modal window is determined by the browser. Usually, it's in the center.
2. The exact look of the window also depends on the browser. We can't modify it.

That is the price for simplicity. There are other ways to show nicer windows and richer interaction with the visitor, but if "bells and whistles" do not matter much, these methods work just fine.
