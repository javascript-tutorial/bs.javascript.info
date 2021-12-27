# Hello, world!

Ovaj dio tutorijala je o jezgri samog jezika, JavaScript-a.

Ali nam treba radno okruženje gdje ćemo pokretati naše skripte, i pošto je ova knjiga na internetu, pretraživač je dobar izbor. Nećemo puno koristiti komande specifične za pretraživače (kao što je `alert`) tako da ne provedete puno vremena na njih ako planirate da se koncentrirate na drugo okruženje (kao na primjer Node.js). Fokusirat ćemo se na JavaScript u pretraživaču u [sljedećem dijelu](/ui) tutorijala.

Prvo, hajmo vidjeti kako povezati skriptu sa web stranicom. Za okruženja sa serverske strane (kao što je Node.js), možete izvršiti skriptu sa ovom komandom `"node my.js"`.


## "script" oznaka (eng. tag)

<<<<<<< HEAD
JavaScript programi mogu biti ubačeni u bilo koji dio HTML dokumenta uz pomoć `<script>` oznake.
=======
JavaScript programs can be inserted almost anywhere into an HTML document using the `<script>` tag.
>>>>>>> 3c934b5a46a76861255e3a4f29da6fd54ab05c8c

Kao na primjer:

```html run height=100
<!DOCTYPE HTML>
<html>

<body>

  <p>Prije skripte...</p>

*!*
  <script>
    alert( 'Hello, world!' );
  </script>
*/!*

  <p>...Poslije skripte.</p>

</body>

</html>
```

```online
Možete pokrenuti ovaj primjer tako što ćete pritisnuti "Play" tipku u gornjem desnom uglu kocke iznad.
```

`<script>` tag sadrži JavaScript kod koji se automatski izvršava kada pretraživač procesira tag.


## Moderni markup 

The `<script>` tag ima nekoliko atributa koji se rijetko koriste danas ali se i dalje mogu pronaći u starom kodu:

`type` atribut: <code>&lt;script <u>type</u>=...&gt;</code>
: Stari HTML standard, HTML4, je zahtijevao da skripta ima `type`. Obično je to bilo `type="text/javascript"`. Ovo više nije potrebno. Isto tako, moderni HTML standard totalno je promijenio značenje ovog atributa. Sada, može se koristiti za JavaScript module. Ali to je napredna tema, pričat ćemo o modulima u drugom dijelu tutorijala.

`language` atribut: <code>&lt;script <u>language</u>=...&gt;</code>
: Ovaj atribut je trebao predstavljati jezik date skripte. Ovaj atribut više nema smisla za koristiti, jer je JavaScript uobičajeni jezik. Nema razloga da se ovaj atribut više koristi.

Komentari prije i poslije skripta.
: U veoma starim knjigama i vodičima, možete pronaći komentare unutar `<script>` tag-ova, kao na primjer ovdje:

    ```html no-beautify
    <script type="text/javascript"><!--
        ...
    //--></script>
    ```

    Ovaj trik se ne koristi u modernom JavaScript-u. Ovi komentari kriju JavaScript kod od starih pretraživača koji ne znaju kako da procesiraju `<script>` tag. Pošto pretraživači koji su izašli u zadnjih 15 godina nemaju više ovaj problem, ovaj tip komentara može vam pomoći da identifikujete veoma star kod.


## Eksterne skripte

Ako imamo puno JavaScript koda, možemo ga staviti u posebnu datoteku.

Skript datoteke su povezane sa HTMLom preko `src` atributa:

```html
<script src="/put/do/script.js"></script>
```

<<<<<<< HEAD
Ovdje, `/put/do/script.js` je apsolutan put do skripte od korijena stranice. Možete pružiti relativni put od trenutne stranice. Na primjer, `src="script.js"` bi značilo `"script.js"` je u trenutnom folderu.
=======
Here, `/path/to/script.js` is an absolute path to the script from the site root. One can also provide a relative path from the current page. For instance, `src="script.js"`, just like `src="./script.js"`, would mean a file `"script.js"` in the current folder.
>>>>>>> 3c934b5a46a76861255e3a4f29da6fd54ab05c8c

Možemo dati i potpuni URL također. Na primjer:

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/lodash.js/4.17.11/lodash.js"></script>
```

Da bismo povezali više skript datoteka, koristimo više tagova:

```html
<script src="/js/script1.js"></script>
<script src="/js/script2.js"></script>
…
```

```smart
Kao pravilo, samo najjednostavnije skripte se postavljaju direktno u HTML. One koje su više kompleksne trebaju biti u eksternim, odvojenim datotekama.

Prednost odvojene datoteke jeste to da će je pretraživač preuzeti i spasiti u [keš memoriju](https://en.wikipedia.org/wiki/Web_cache).

Ostale stranice koje uzimaju istu skriptu kao referencu uzeti će iz keš memorije umjesto ponovnog preuzimanja, tako da se ta datoteka samo jednom treba preuzeti.

To smanjuje promet i ubrzava stranicu.
```

````warn header="Ako je `src` postavljen, sadržaj skripte će biti ignorisan."
Jedan `<script>` tag ne može imati oboje, i `src` atribut i kod iznutra.

Ovo neće raditi:

```html
<script *!*src*/!*="datoteka.js">
  alert(1); // sadržaj je ignorisan, jer je postavljen src
</script>
```

Moramo odabrati ili eksterni `<script src="…">` ili obični `<script>` tag sa kodom.

Primjer iznad može biti podijeljen na dvije skripte kako bi radio:

```html
<script src="datoteka.js"></script>
<script>
  alert(1);
</script>
```
````

## Sažetak

- Možemo koristiti `<script>` tag da dodamo JavaScript kod na stranicu.
- `type` i `language` atributi više nisu potrebni.
- Skripta u eksternoj datoteci može biti dodana sa `<script src="put/do/script.js"></script>`.


Ima još mnogo toga da se nauči o skriptama u pretraživaču kao i o njihovoj interakciji sa web stranicom. Ali moramo imati na umu da je ovaj dio tutorijala posvećen JavaScript jeziku, tako da ne želimo odvratiti pažnju sa implementacijama specifičnim za pretraživače. Koristit ćemo pretraživač kao način da pokrenemo JavaScript, što je veoma pogodno za online čitanje, ali to je samo jedan od načina.
