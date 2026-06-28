| regex | pomen           |
| ----- | --------------- |
| `.`   | poljuben znak   |
| `\d`  | števka          |
| `\w`  | črka/številka/_ |
| `\s`  | presledek       |
| `*`   | 0 ali več       |
| `+`   | 1 ali več       |
| `?`   | 0 ali 1         |
| `{n}` | točno n         |
| `[]`  | eden izmed      |
| `[^]` | ne              |
| `^`   | začetek         |
| `$`   | konec           |
| `     | `               |
| `()`  | skupina         |

# REGULARNI IZRAZI – STRNJENA TABELA

| Kaj hočem                 | Regex                                              | Primer            |
| ------------------------- | -------------------------------------------------- | ----------------- |
| poljuben znak             | `.`                                                | `a.c`             |
| števka                    | `\d`                                               | `\d+`             |
| ni števka                 | `\D`                                               | `\D+`             |
| črka/številka/_           | `\w`                                               | `\w+`             |
| ni `\w`                   | `\W`                                               | `\W+`             |
| presledek                 | `\s`                                               | `\s+`             |
| ni presledek              | `\S`                                               | `\S+`             |
| mala črka                 | `[a-z]`                                            | `[a-z]+`          |
| velika črka               | `[A-Z]`                                            | `[A-Z]+`          |
| črke                      | `[a-zA-Z]`                                         | `[a-zA-Z]+`       |
| slovenske črke            | `[a-zA-ZčšžČŠŽ]`                                   | `[a-zA-ZčšžČŠŽ]+` |
| ena od možnosti           | `[abc]`                                            | `[abc]+`          |
| vse razen                 | `[^abc]`                                           | `[^0-9]`          |
| začetek niza              | `^`                                                | `^\d`             |
| konec niza                | `$`                                                | `\d$`             |
| nič ali več               | `*`                                                | `a*`              |
| ena ali več               | `+`                                                | `a+`              |
| opcijsko                  | `?`                                                | `a?`              |
| točno n-krat              | `{n}`                                              | `\d{3}`           |
| od n do m                 | `{n,m}`                                            | `\d{2,5}`         |
| vsaj n                    | `{n,}`                                             | `\d{3,}`          |
| ali                       | `\|`                                               | `pes\|mačka`      |
| skupina                   | `()`                                               | `(ab)+`           |
| dejanska pika             | `\.`                                               | `\.com`           |
| dejanski plus             | `\+`                                               | `\+386`           |
| dejanska zvezdica         | `\*`                                               | `a\*b`            |
| karkoli                   | `.*`                                               | `a.*b`            |
| ena beseda                | `\w+`                                              | `Ana`             |
| beseda dolžine 5          | `\w{5}`                                            | `abcde`           |
| samo male črke            | `^[a-z]+$`                                         | `abc`             |
| samo velike črke          | `^[A-Z]+$`                                         | `ABC`             |
| samo številke             | `^\d+$`                                            | `12345`           |
| črke in številke          | `^[a-zA-Z0-9]+$`                                   | `abc123`          |
| beseda z veliko začetnico | `[A-Z][a-z]+`                                      | `Ana`             |
| začne se z veliko         | `[A-Z]\w*`                                         | `Ljubljana`       |
| začne se na a             | `a\w*`                                             | `avto`            |
| konča se na ing           | `\w*ing`                                           | `running`         |
| vsebuje abc               | `\w*abc\w*`                                        | `xxabcxx`         |
| pozitivno/negativno št.   | `-?\d+`                                            | `-15`             |
| decimalno število         | `\d+\.\d+`                                         | `12.5`            |
| decimalno s piko/vejico   | `\d+[.,]\d+`                                       | `12,5`            |
| telefonska številka       | `^\+?\d+$`                                         | `+38640111222`    |
| slovenska telefonska      | `^(\+386\|0)\d{8}$`                                | `041123456`       |
| email (preprost)          | `^\w+@\w+\.\w+$`                                   | `a@b.com`         |
| email (boljši)            | `^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$` | `ime@test.com`    |
| datum DD.MM.LLLL          | `^\d{2}\.\d{2}\.\d{4}$`                            | `28.06.2026`      |
| registrska tablica        | `^[A-Z]{2}\s?\d{3}-[A-Z]{2}$`                      | `LJ 123-AB`       |
| več besed                 | `(\w+\s*)+`                                        | `hello world`     |
| opcijski + in številke    | `\+?\d+`                                           | `+12345`          |
| 3 velike + 2 številki     | `^[A-Z]{3}\d{2}$`                                  | `ABC12`           |

## Python uporaba

|Funkcija|Kaj naredi|
|---|---|
|`re.search()`|išče kjerkoli|
|`re.match()`|preveri začetek|
|`re.fullmatch()`|preveri cel niz|
|`re.findall()`|vrne vse zadetke|
|`re.sub()`|zamenja zadetke|

## Zelo pomembno

Vedno uporabljaj:

```python
r"\d+"
```

namesto:

```python
"\\d+"
```