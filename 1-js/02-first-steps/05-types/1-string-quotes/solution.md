
Backtick-ovi ugrade rezultat izraza unutar `${...}` u string/tekst.

```js run
let name = "Ilya";

// izraz je broj 1
alert( `hello ${1}` ); // hello 1

// izraz je string/tekst "name"
alert( `hello ${"name"}` ); // hello name

// izraz je varijabla, ugradi se u tekst
alert( `hello ${name}` ); // hello Ilya
```
