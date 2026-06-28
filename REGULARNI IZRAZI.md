

## 1. Kaj je regex?

Regex je vzorec za iskanje besedila.

Primer:

```python
r"\d+"
```

pomeni:

> “ena ali več števk”

---

# 2. Uporaba v Pythonu

```python
import re
```

## Najpogostejše funkcije

### `re.search`

Najde prvi pojav kjerkoli v nizu.

```python
re.search(r"\d+", "abc123")
```

---

### `re.match`

Preverja samo začetek niza.

```python
re.match(r"\d+", "123abc")
```

---

### `re.fullmatch`

Celoten niz mora ustrezati vzorcu.

```python
re.fullmatch(r"\d+", "123")
```

---

### `re.findall`

Vrne vse zadetke.

```python
re.findall(r"\d", "a1b2c3")
# ['1', '2', '3']
```

---

### `re.sub`

Zamenjava.

```python
re.sub(r"\d", "X", "a1b2")
# 'aXbX'
```

---

# 3. Posebni znaki

## `.`

Poljuben znak.

```python
r"a.c"
```

ujame:

- abc
    
- a7c
    
- a-c
    

ne pa:

- ac
    

---

## `^`

Začetek niza.

```python
r"^abc"
```

---

## `$`

Konec niza.

```python
r"abc$"
```

---

# 4. Ponavljanje

## `*`

0 ali več ponovitev.

```python
r"ab*"
```

ujame:

- a
    
- ab
    
- abbb
    

---

## `+`

1 ali več.

```python
r"ab+"
```

ujame:

- ab
    
- abbb
    

ne pa:

- a
    

---

## `?`

0 ali 1 pojavitev.

```python
r"ab?"
```

ujame:

- a
    
- ab
    

---

## `{n}`

Točno n ponovitev.

```python
r"\d{3}"
```

točno 3 števke.

---

## `{n,m}`

Od n do m ponovitev.

```python
r"\d{2,5}"
```

---

## `{n,}`

Vsaj n ponovitev.

```python
r"\d{3,}"
```

---

# 5. Skupine znakov

## `[abc]`

Eden izmed znakov.

```python
r"[abc]"
```

ujame:

- a
    
- b
    
- c
    

---

## `[a-z]`

Mala črka.

---

## `[A-Z]`

Velika črka.

---

## `[0-9]`

Števka.

---

## `[a-zA-Z0-9]`

Črke ali številke.

---

## `[^abc]`

Karkoli razen a,b,c.

---

# 6. Posebne skupine

## `\d`

Števka.

```python
r"\d"
```

isto kot:

```python
[0-9]
```

---

## `\D`

Ni števka.

---

## `\w`

Črka, številka ali `_`

```python
[a-zA-Z0-9_]
```

---

## `\W`

Ni `\w`

---

## `\s`

Presledek/tab/newline.

---

## `\S`

Ni whitespace.

---

# 7. OR operator

## `|`

ALI

```python
r"mačka|pes"
```

---

# 8. Oklepaji

## `()`

Skupina.

```python
r"(ab)+"
```

ujame:

- ab
    
- abab
    
- ababab
    

---

# 9. Escape znaki

Če želiš dejansko piko:

```python
r"\."
```

ker:

- `.` pomeni “poljuben znak”
    

Enako:

```python
\+
\*
\?
\(
\)
```

---

# 10. Raw string (`r""`)

VEDNO uporabljaj:

```python
r"\d+"
```

ne:

```python
"\\d+"
```

---

# 11. Najpogostejši primeri

## Samo številke

```python
r"^\d+$"
```

---

## Telefonska številka

```python
r"^\+?\d+$"
```

- opcijski +
    
- nato števke
    

---

## Email (preprost)

```python
r"^\w+@\w+\.\w+$"
```

---

## Beseda z veliko začetnico

```python
r"^[A-Z][a-z]+$"
```

---

## Slovenske registrske

```python
r"^[A-Z]{2}\s?\d{3}-[A-Z]{2}$"
```

---

# 12. Kako sestavljamo regex

Regex sestavljaš po korakih:

Primer:  
“ena velika črka + 3 števke”

```python
[A-Z]\d{3}
```

Primer:  
“opcijski + in nato vsaj ena števka”

```python
\+?\d+
```

---

# 13. Zelo pogoste napake

## Pozabiš `r""`

Napačno:

```python
"\d+"
```

Pravilno:

```python
r"\d+"
```

---

## Uporabiš `match` namesto `fullmatch`

```python
re.match(r"\d+", "123abc")
```

TO JE VELJAVNO.

Če želiš preveriti celoten niz:

```python
re.fullmatch(r"\d+", "123abc")
```

to vrne None.

---

## Pozabiš escapati `.`

```python
r".com"
```

pomeni:

- poljuben znak + com
    

za dejansko piko:

```python
r"\.com"
```

---

# 14. Mini povzetek

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