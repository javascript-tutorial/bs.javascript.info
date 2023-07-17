
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

<<<<<<< HEAD
1. Sabiranje sa string-om `"" + 1` pretvara `1` u string: `"" + 1 = "1"`, onda imamo `"1" + 0`, isto pravilo je primijenjeno.
2. Oduzimanje `-` (kao većina matematičkih operacija) radi samo sa brojevima, uvijek pretvara prazan string `""` u `0`.
3. Sabiranje sa string-om nadodaje broj `5` na string.
4. Oduzimanje uvijek pretvara u brojeve, tako da pretvara `"  -9  "` u broj `-9` (ignoriše razmake okolo).
5. `null` postaje `0` nakon numeričke konverzije.
6. `undefined` postaje `NaN` nakon numeričke konverzije.
7. Razmaci su sklonjeni sa početka i kraja string-a kada ga pretvaramo u broj. Ovdje se čitav string sastoji od razmaka, kao što su `\t`, `\n` i "obični" razmak između njih. Tako da, slično praznom string-u, postaje `0`.
=======
1. The addition with a string `"" + 1` converts `1` to a string: `"" + 1 = "1"`, and then we have `"1" + 0`, the same rule is applied.
2. The subtraction `-` (like most math operations) only works with numbers, it converts an empty string `""` to `0`.
3. The addition with a string appends the number `5` to the string.
4. The subtraction always converts to numbers, so it makes `"  -9  "` a number `-9` (ignoring spaces around it).
5. `null` becomes `0` after the numeric conversion.
6. `undefined` becomes `NaN` after the numeric conversion.
7. Space characters are trimmed off string start and end when a string is converted to a number. Here the whole string consists of space characters, such as `\t`, `\n` and a "regular" space between them. So, similarly to an empty string, it becomes `0`.
>>>>>>> 733ff697c6c1101c130e2996f7eca860b2aa7ab9
