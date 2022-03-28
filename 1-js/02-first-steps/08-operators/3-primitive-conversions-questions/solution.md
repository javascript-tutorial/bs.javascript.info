
```js no-beautify
"" + 1 + 0 = "10" // (1)
"" - 1 + 0 = -1 // (2)
true + false = 1
6 / "3" = 2
"2" * "3" = 6
4 + 5 + "px" = "9px"
"$" + 4 + 5 = "$45"
"4" - 2 = 2
"4px" - 2 = NaN
"  -9  " + 5 = "  -9  5" // (3)
"  -9  " - 5 = -14 // (4)
null + 1 = 1 // (5)
undefined + 1 = NaN // (6)
" \t \n" - 2 = -2 // (7)
```

1. Sabiranje sa string-om `"" + 1` pretvara `1` u string: `"" + 1 = "1"`, onda imamo `"1" + 0`, isto pravilo je primijenjeno.
2. Oduzimanje `-` (kao većina matematičkih operacija) radi samo sa brojevima, uvijek pretvara prazan string `""` u `0`.
3. Sabiranje sa string-om nadodaje broj `5` na string.
4. Oduzimanje uvijek pretvara u brojeve, tako da pretvara `"  -9  "` u broj `-9` (ignoriše razmake okolo).
5. `null` postaje `0` nakon numeričke konverzije.
6. `undefined` postaje `NaN` nakon numeričke konverzije.
7. Razmaci su sklonjeni sa početka i kraja string-a kada ga pretvaramo u broj. Ovdje se čitav string sastoji od razmaka, kao što su `\t`, `\n` i "obični" razmak između njih. Tako da, slično praznom string-u, postaje `0`.
