# Uvod u JavaScript

<<<<<<< HEAD
Da vidimo šta je tako specijalno u JavaScriptu, šta možemo postići, i koje druge tehnologije su dobri suigrači sa njim.
=======
Let's see what's so special about JavaScript, what we can achieve with it, and what other technologies play well with it.
>>>>>>> 71da17e5960f1c76aad0d04d21f10bc65318d3f6

## Sta je JavaScript?

*JavaScript* je u početku napravljen "kako bi web stranice bile žive".

Programi u ovom jeziku se zovu *skripte*. Mogu biti pisane direktno u HTML kodu web stranica i pokreću se automatski tokom učitavanja stranice. 

Skripte su izvršene kao običan tekst. Ne treba im specijalna priprema ili kompilacija kako bismo ih pokrenuli.


U ovom pogledu, JavaScript je dosta drugaciji od drugog programskog jezika koji se zove [Java](https://bs.wikipedia.org/wiki/Java_(programski_jezik)).

```smart header="Zašto se zove <u>Java</u>Script?"
Kada je JavaScript bio napravljen, u početku je imao drugo ime: "LiveScript". Ali Java je bila veoma popularna u to vrijeme, tako da je bilo odlučeno da imenovanjem ovog novog jezika kao "mlađeg brata" Jave bi moglo pomoći.

Ali kako se razvijao, JavaScript je postao potpuno nezavisan jezik sa svojom specifikacijom nazvanom [ECMAScript](http://en.wikipedia.org/wiki/ECMAScript), i sada nema nikakve povezanosti sa Javom.
```

Danas, JavaScript se može pokrenuti ne samo na pretraživaču, već i na serveru, i u stvari na svakom uređaju koji ima specijalan program koji se naziva [JavaScript mašina,motor](https://en.wikipedia.org/wiki/JavaScript_engine).

Pretraživači imaju ugrađen motor (eng. engine) ponekad nazvan "JavaScript virtualna mašina".

Različiti motori imaju različita "kodna imena" . Na primjer:

<<<<<<< HEAD
- [V8](https://en.wikipedia.org/wiki/V8_(JavaScript_engine)) -- u Chrome-u i Operi.
- [SpiderMonkey](https://en.wikipedia.org/wiki/SpiderMonkey) -- u Firefox-u.
- ...Postoje još neka kodna imena kao što su "Trident" i "Chakra" za različite verzije Internet Explorer-a, "ChakraCore" za Microsoft Edge, "Nitro" i "SquirrelFish" za Safari, itd.

Pojmove iznad je poželjno zapamtiti jer se koriste i spominju u programerskim člancima na internetu. Mi ćemo ih također koristiti. Na primjer, ako "svojstvo X je podržano od strane V8", onda vjerovatno radi u Chrome-u i Operi.
=======
- [V8](https://en.wikipedia.org/wiki/V8_(JavaScript_engine)) -- in Chrome, Opera and Edge.
- [SpiderMonkey](https://en.wikipedia.org/wiki/SpiderMonkey) -- in Firefox.
- ...There are other codenames like "Chakra" for IE, "JavaScriptCore", "Nitro" and "SquirrelFish" for Safari, etc.

The terms above are good to remember because they are used in developer articles on the internet. We'll use them too. For instance, if "a feature X is supported by V8", then it probably works in Chrome, Opera and Edge.
>>>>>>> 71da17e5960f1c76aad0d04d21f10bc65318d3f6

```smart header="Kako motori rade?"

Motori su komplikovani. Ali osnove su jednostavne.

1. Motor (ugrađen ako je u pitanju pretraživač) čita ("raščlanjuje") skriptu.
2. Onda pretvara ("sastavlja") skriptu u mašinski jezik.
3. Onda se pokreće mašinski kod, i to veoma brzo.

Motor primjenjuje optimizacije u svakom koraku procesa. Čak gleda sastavljenu (kompiliranu) skriptu dok se izvršava, analizira podatke koje prolaze kroz nju, i dalje optimizira mašinski kod na osnovu tog znanja.
```

## Šta može JavaScript uraditi u pretraživaču?

Moderni JavaScript je "siguran" programski jezik. Ne pruža niski pristup memoriji ili procesoru, jer je u početku napravljen za pretraživač, kojem to nije potrebno.

JavaScript-ove sposobnosti uveliko ovise o okolini u kojoj se izvršava. Na primjer, [Node.js](https://wikipedia.org/wiki/Node.js) podržava funkcije koje omogućavaju JavaScript-u da čita/piše proizvoljne datoteke, izvršava mrežne zahtjeve, itd.

JavaScript u pretraživaču može uraditi sve što se tiče manipulacije web stranica, interakcije sa korisnicima, kao i sa web serverom.

Na primjer, JavaScript u pretraživacu može da:

- Dodaje novi HTML kod na stranicu, mijenja vec postojeći sadržaj, i modifikuje stil tj. izgled
- Reaguje na akcije korisnika, da izvršava skripte kada korisnik pritisne tipku na mišu, pomjeri kursor, pritisne neku tipku na tastaturi.
- Šalje zahtjeve preko mreže udaljenim serverima, da preuzima i ubacuje datoteke (takozvane [AJAX](https://en.wikipedia.org/wiki/Ajax_(programming)) i [COMET](https://en.wikipedia.org/wiki/Comet_(programming)) tehnologije).
- Dobije i postavi kolačiće, postavlja pitanja posjetiocu, kao i npr. da pokaže poruke.
- Zapamti podatke na strani klijenta ("lokalno skladište").

<<<<<<< HEAD
## Šta ne može JavaScript uraditi u pretraživaču?
=======
JavaScript's abilities in the browser are limited for the sake of a user's safety. The aim is to prevent an evil webpage from accessing private information or harming the user's data.
>>>>>>> 71da17e5960f1c76aad0d04d21f10bc65318d3f6

JavaScript-ove mogućnosti u pretraživaču su ograničene radi korisničke sigurnosti. Cilj je spriječiti zlim stranicama pristup privatnim informacijama ili naškoditi korisničkim podacima.

Primjeri nekih ograničenja su:

- JavaScript na web stranici ne može čitati/pisati datoteke sa tvrdog diska (eng. hard disk), kopirati ih ili izvršavati programe na istom. Nema direktan pristup funkcijama operativnog sistema.

    Moderni pretraživači omogućavaju mu da radi sa datotekama, ali je pristup ograničen i samo obezbjeđen kada korisnik izvrši određene akcije, kao što su "spuštanje" datoteka u prozor pretraživaća ili odabirom istih putem `<input>` tag-a.

    Postoje načini da komunicira sa kamerom/mikrofonom i ostalim uređajima, ali za to je potrebna eksplicitna dozvola od korisnika. To je napravljeno kako stranice koje imaju ukljucen JavaScript ne bi potajno uključile web-kameru, posmatrali vas i vašu okolinu i poslali te informacije [NSA](https://en.wikipedia.org/wiki/National_Security_Agency).
    
- Različiti tabovi/prozori u većini slučajeva ne znaju jedno drugo. Ponekad znaju, na primjer kada jedan prozor koristi JavaScript da otvori drugi. Ali čak i u tom slučaju, JavaScript sa jedne stranice ne može pristupiti drugu ako dolaze sa drugačijih stranica (drugačijih domena, protokola ili portova).
    Ovaj princip se zove "Ista Politika Porijekla" (eng. same origin policy). Kako bi ovo radilo, *obe stranice* moraju prihvatiti razmjenu podataka i imati specijalni JavaScript kod koji će to riješiti. To ćemo spomenuti i preći u ovom tutorijalu.

    Ovo ograničenje je, opet kažemo, za korisničku sigurnost. Stranica `http://anysite.com` koju je korisnik otvorio ne smije imati pristup drugom tabu pretraživača koji ima URL `http://gmail.com` i uzeti informacije odatle.
- JavaScript može lagano komunicirati preko interneta sa serverom odakle je trenutna stranica i došla. Ali sposobnost da prima podatke sa drugih stranica/domena je osakaćena. Iako je moguće, potreban je eksplicitan sporazum (izražen u HTTP zaglavlju) s udaljenim serverom. Još jednom, to je sigurnosno ogranicenje.

![](limitations.svg)

Ovakva ograničenja ne postoje ako se JavaScript koristi izvan pretraživača, na primjer na serveru. Moderni pretraživači isto tako dopuštaju plugin-ove/ekstenzije koje mogu pitati i tražiti proširene dozvole.

## Šta čini JavaScript unikatnim?

Postoje bar *tri* odlične stvari u JavaScriptu:

```compare
<<<<<<< HEAD
+ Potpuna integracija sa HTML/CSS.
+ Jednostavne stvari su urađene na jednostavan način.
+ Podrška od svih glavnih pretraživača i uključen je automatski.
=======
+ Full integration with HTML/CSS.
+ Simple things are done simply.
+ Supported by all major browsers and enabled by default.
>>>>>>> 71da17e5960f1c76aad0d04d21f10bc65318d3f6
```
JavaScript je jedina tehnologija u pretraživaču koja kombinira ove tri stvari.

To je ono što čini JavaScript unikatnim jezikom. To je razlog što je on najrasprostranjeniji alat za izradu pretraživačkog interfejsa.

Isto tako, JavaScript omogućava izradu servera, mobilnih aplikacija, itd.

## Jezici koji su "bolji od" JavaScript-a

Sintaksa JavaScript-a ne odgovara svačijim potrebama. Različiti ljudi žele različite sposobnosti.

To je i očekivano, jer projekti i zahtjevi su drugačiji za sve ljude.

Nedavno mnoštvo novih jezika se pojavilo, koji su *prevedeni* (eng. transpiled) u JavaScript prije nego što se pokrenu u pretraživaču.

Moderne alatke čine prevođenje veoma brzim i transparentnim, i zapravo dopuštaju programerima da kodiraju u drugim jezicima prije nego što se automatski prevede "ispod haube".

Primjeri takvih jezika:

<<<<<<< HEAD
- [CoffeeScript](http://coffeescript.org/) je "sintaktički šećer" za JavaScript. Uvodi kraću sintaksu, što nam dopušta da pišemo jasniji i precizniji kod. Obično, Ruby programeri ga vole.
- [TypeScript](http://www.typescriptlang.org/) je koncentrisan na dodavanje "strogog tipkanja podataka" (eng. strict data typing) da bi olakšao razvoj i podršku složenih sistema. Razvijen je od strane Microsoft-a.
- [Flow](http://flow.org/) isto dodaje strogo tipkanje podataka, ali na drugi način. Razvijen je od strane Facebook-a.
- [Dart](https://www.dartlang.org/) je samostalni jezik koji ima svoj motor koji se pokreće izvan pretraživačkih okruženja (kao npr. u mobilnim aplikacijama), ali isto može biti preveden u JavaScript. Razvijen od strane Google-a.
=======
- [CoffeeScript](http://coffeescript.org/) is a "syntactic sugar" for JavaScript. It introduces shorter syntax, allowing us to write clearer and more precise code. Usually, Ruby devs like it.
- [TypeScript](http://www.typescriptlang.org/) is concentrated on adding "strict data typing" to simplify the development and support of complex systems. It is developed by Microsoft.
- [Flow](http://flow.org/) also adds data typing, but in a different way. Developed by Facebook.
- [Dart](https://www.dartlang.org/) is a standalone language that has its own engine that runs in non-browser environments (like mobile apps), but also can be transpiled to JavaScript. Developed by Google.
- [Brython](https://brython.info/) is a Python transpiler to JavaScript that enables the writing of applications in pure Python without JavaScript.
- [Kotlin](https://kotlinlang.org/docs/reference/js-overview.html) is a modern, concise and safe programming language that can target the browser or Node.
>>>>>>> 71da17e5960f1c76aad0d04d21f10bc65318d3f6

Postoji ih više. Naravno, čak i ako koristimo jedan od ovih prevedenih jezika, moramo dobro znati JavaScript kako bismo stvarno shvatili šta se događa i odvija.

## Sažetak

<<<<<<< HEAD
- JavaScript je u početku bio napravljen i osmišljen kao jezik koji se mogao koristiti samo u pretraživaču, ali se sada koristi u mnogim drugim okruženjima.
- Danas, JavaScript ima unikatnu poziciju kao najčesčće usvojen jezik koji se koristi u pretraživačima, a ima potpunu integraciju sa HTML-om i CSS-om.
- Postoje mnogi jezici koji se prevedu u JavaScript kod, oni pružaju određene karakteristike. Preporučeno ih je proučiti, bar ukratko, nakon što savladate JavaScript.
=======
- JavaScript was initially created as a browser-only language, but it is now used in many other environments as well.
- Today, JavaScript has a unique position as the most widely-adopted browser language, fully integrated with HTML/CSS.
- There are many languages that get "transpiled" to JavaScript and provide certain features. It is recommended to take a look at them, at least briefly, after mastering JavaScript.
>>>>>>> 71da17e5960f1c76aad0d04d21f10bc65318d3f6
