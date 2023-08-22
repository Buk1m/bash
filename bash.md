- [Materialy](#materialy)
- [Analiza skryptu kwadracik.sh](#analiza-skryptu-kwadraciksh)
- [Shebang](#shebang)
- [Instrukcja `clear`](#instrukcja-clear)
- [Instrukcja `read`](#instrukcja-read)
    - [Sygnatura (struktura komendy, aby wiedzieć jak ja wywolać)](#sygnatura-struktura-komendy-aby-wiedzieć-jak-ja-wywolać)
    - [Przyklady opcji](#przyklady-opcji)
- [Zmienne](#zmienne)
  - [Tworzenie zmiennych](#tworzenie-zmiennych)
  - [Dostęp do wartości zmiennej](#dostęp-do-wartości-zmiennej)
  - [Modyfikacja wartości zmiennej](#modyfikacja-wartości-zmiennej)
- [Instrukcje sterowania przeplywem programu](#instrukcje-sterowania-przeplywem-programu)
  - [Instrukcje warunkowe (wykonac czy nie wykonac?)](#instrukcje-warunkowe-wykonac-czy-nie-wykonac)
    - [Instrukcja warunkowa `if`](#instrukcja-warunkowa-if)
  - [Pętle (wielokrotne wykonanie bloku kodu)](#pętle-wielokrotne-wykonanie-bloku-kodu)
    - [Pętla`for`](#pętlafor)


# Materialy
- kurs jesli dobrze znasz angielski https://www.codecademy.com/courses/bash-scripting/lessons/learn-bash-scripting
- https://www.codecademy.com/learn/bash-scripting/modules/bash-scripting/cheatsheet
- https://www.cs.put.poznan.pl/anstroinski/data/uploads/sop1/materials/sop1_lab7-kurs.html
- https://dev.to/ifenna__/adding-colors-to-bash-scripts-48g4
# Analiza skryptu kwadracik.sh
```bash
#!/bin/bash

clear

read -p "Podaj dolną granicę zakresu: " lower_bound
read -p "Podaj górną granicę zakresu: " upper_bound

sum_of_squares=0


for (( i=$lower_bound; i<=$upper_bound; i++ ))
do
  sum_of_squares=$(( $sum_of_squares + $i*$i ))
done


echo "Suma kwadratów kolejnych liczb od $lower_bound do $upper_bound wynosi: $sum_of_squares"


```
# Shebang
Sekwencja znaków umieszczana na początku skryptu, rozpoczynająca się kratką i wykrzyknikiem. Tekst następujący po wykrzykniku, aż do pierwszej spacji, to ścieżka do interpretera. Ta sciezka ma za zadanie poinformowac system o tym jaki interpreter ma zostac uzyty do wykonania skryptu. **W praktyce oznacza to informacje o tym w jakim jezyku zostal napisany skrypt.**

```bash
#!/bin/bash
```

W przypadku twoich skryptow bedzie to zawsze `#!/bin/bash` . Gdyby jednak skrypt byl napisany w jezyku python to trzeba by podac inna sciezke do interpretera:
```bash
#!/usr/bin/python
```
lub w jezyku perl:
```bash
#!/usr/bin/perl
```

Jesli pod podana sciezka nie bedzie odpowiedniego interpretera to system nie bedzie w stanie uruchomic skryptu.

# Instrukcja `clear`

Komenda  `clear` czysci aktualny ekran terminala. Wywolanie tej komendy spowoduje wyczysczenie ekranu terminala w taki sposob zeby kareta znalazla sie w pierwszej linii terminala.

# Instrukcja `read`
Linijki programu:
```bash
	read -p "Podaj dolną granicę zakresu: " lower_bound
	read -p "Podaj górną granicę zakresu: " upper_bound
```

Pozwala na wczytanie danych od uzytkownika. Po wywolaniu tej komendy skrypt bedzie czekac na ciag znakow od uzytkownika aż zostanie on zatwierdzony przyciskiem enter.

### Sygnatura (struktura komendy, aby wiedzieć jak ja wywolać)
Sygnatura komendy `read` w języku Bash ma następującą postać:

```bash
read [opcje] [zmienne]
```

Gdzie:
- `[opcje]`: Opcje, które można przekazać do komendy `read` w celu dostosowania jej zachowania. Opcje te są poprzedzone myślnikiem `-`.
- `[zmienne]`: Zmienne, do których wartości wprowadzone przez użytkownika będą przypisane. Może to być jedna lub więcej zmiennych oddzielonych spacją.

Przykład:
```bash
read -p -t 10 "Podaj imię: " name
```

W tym przykładzie:
- `-p "Podaj imię: "` to opcja `-p`, która umożliwia wyświetlenie tekstu jako promptu dla użytkownika.
- `-t 10`  to opcja `-t`, która ustala limit czasu (w sekundach), w którym użytkownik musi wprowadzić dane.
- `name` to zmienna, do której wprowadzona przez użytkownika wartość (imię) zostanie przypisana.

 Istnieje wiele innych opcji i sposobów użycia komendy `read`, a ich dokładny opis można znaleźć w dokumentacji komendy poprzez [man read](https://linuxcommand.org/lc3_man_pages/readh.html).

### Przyklady opcji
1. `-p "prompt_text"`: Pozwala na wyświetlenie tekstu jako promptu dla użytkownika przed wprowadzeniem danych. Na przykład:
   ```bash
   read -p "Podaj imię: " name
   ```

2. `-s`: Powoduje, że wprowadzone dane nie będą widoczne na ekranie. Jest to przydatne do wprowadzania haseł lub innych poufnych informacji.
   ```bash
   read -s -p "Podaj hasło: " password
   ```

3. `-t timeout`: Ustala limit czasu (w sekundach), w którym użytkownik musi wprowadzić dane. Jeśli nie zostaną wprowadzone żadne dane w określonym czasie, komenda zakończy się z kodem błędu.
   ```bash
   read -t 10 -p "Masz 10 sekund na wprowadzenie danych: " data
   ```

4. `-a array`: Przypisuje wprowadzone dane do tablicy.
   ```bash
   read -a names -p "Podaj imiona (oddzielone spacją): "
   ```

5. `-n num`: Oczekuje na wprowadzenie dokładnie `num` znaków i zakończy się, gdy zostaną wprowadzone.
   ```bash
   read -n 3 -p "Podaj trzy znaki: " chars
   ```

# Zmienne
Linijki programu:
```bash
sum_of_squares=0
```

Bash pozwala na definiowanie **zmiennych**, które przechowuja wartość(dane) i posiadaja nazwę. W ramach skryptu mozna za pomoca nazwy zmiennej odwolywac sie do jej wartości i wykonywac na niej operacje. Najlawiej zrozumiec czym jest zmienna porownujac ja do pliku.
Plik posiada nazwe, po której mozemy sie do niego odwolac i dane. Plik mozemy wyswietlic za pomoca jego nazwy `cat plik.txt` jak i modyfikowac jego wartosc `echo 'dodaj linie' >> plik.txt`. Podobnie dzialaja zmienne jak zobaczysz w ponizszych przykladach.

## Tworzenie zmiennych
Możesz utworzyć zmienną, przypisując jej wartość za pomocą znaku rownosci  `=`, bez spacji pomiędzy znakami. Na przykład:
```bash
	moja_zmienna="To jest moja zmienna"
```

podobnie poznana wczesniej komenda `read` spowoduje utworzenie zmiennej `zmienna_imie` z wartoscia wproawadzona przez uzytkownia:
```bash
	read -p "Podaj imię: " zmienna_imie
```

Nazwy zmiennych powinny zaczynać się od **litery** lub **znaku podkreślenia** `_`, a następnie mogą zawierać **litery**, **cyfry** i **znaki podkreślenia**. Nazwy zmiennych są wrażliwe na wielkość liter. `Suma` jest inna zmienna niz `suma`.

W przypadku skryptu kwadracik zdefiniowano zmieną `sum_of_squares`:
```bash
sum_of_squares=0
```

ktora ma poczatkową wartosc 0 i reprezentuje sumę kwadratów dla liczb z zakresu zmiennych od `lower_bound` do `upper_bound`.

## Dostęp do wartości zmiennej
Aby uzyskać wartość zmiennej, użyj znaku `$` przed nazwą
zmiennej. Na przykład:
```bash
echo $moja_zmienna
```
spowoduje wyświetlenie zawartości zmiennej `moja_zmienna`.

Przyklad skryptu dla zmiennej przechowujacej liczbe:
```bash
#!/bin/bash

skladnik=1

echo $(($skladnik + 2))
```

Zdefinowalismy zmienna o nazwie `skladnik`, ktorej poczatkowa wartosc to 1 i wypisalismy sume tej zmiennej z liczba 2 na ekranie za pomoca komendy `echo`. (za chwile wyjasnię dlaczego trzeba dopisywac `$((...))` .)

## Modyfikacja wartości zmiennej
Aby modyfikować wartość zmiennej, przypisz jej nową wartość. Na przykład:
```bash
moja_zmienna="Poczatkowa wartosc"
echo $moja_zmienna # wynik Poczatkowa wartosc

moja_zmienna="Nowa wartosc"
echo $moja_zmienna# wynik Nowa wartosc
```


# Instrukcje sterowania przeplywem programu
Linijki programu:
```bash
for (( i=$lower_bound; i<=$upper_bound; i++ ))
do
  sum_of_squares=$(( $sum_of_squares + $i*$i ))
done
```

( w skrypcie jest uzyta instukcja `for` ale zacznę od prostszych instrukcji warunkowych a nastepnie przejde do pętli)

Instrukcje sterowania przeplywem programu pozwalaja sterowac tym ktore linijki skryptu maja sie wykonać, które maja się wykonac wielokrotnie (w pętli), a które maja zostac pominiete.

## Instrukcje warunkowe (wykonac czy nie wykonac?)

### Instrukcja warunkowa `if`

Instrukcja warunkowa `if` pozwala programiscie kontrolowac kiedy dany kod ma sie wykonac, za pomoca warunku logicznego.

Ogólny format instrukcji `if` w Bashu wygląda następująco:

```bash
if warunek
then
    # blok kodu do wykonania, jeśli warunek jest spełniony
else
    # blok kodu do wykonania, jeśli warunek nie jest spełniony
fi
```

Poniżej znajduje się bardziej szczegółowe wyjaśnienie poszczególnych elementów instrukcji `if`:

- `warunek` to wyrażenie logiczne, które jest ewaluowane jako prawda (`true`) lub fałsz (`false`). Warunek może być zbudowany z różnych operatorów porównania, logicznych oraz innych elementów, które określają, czy dany warunek jest spełniony.

- `then` wskazuje początek bloku kodu, który ma być wykonany, jeśli warunek jest spełniony (czyli ma wartość `true`).

- `else` (opcjonalnie) wskazuje początek bloku kodu, który ma być wykonany, jeśli warunek nie jest spełniony (czyli ma wartość `false`).

- `fi` jest zakończeniem instrukcji `if`. Jest to po prostu odwrócenie słowa `if`.

Możesz również używać bardziej złożonych warunków, korzystając z operatorów logicznych (`&&` dla "i" logicznego, `||` dla "lub" logicznego) oraz operatorów porównania (np. `-eq` dla równości, `-lt` dla mniejszości itp.), aby tworzyć bardziej elastyczne instrukcje warunkowe w Bashu.

Przykład:
```bash
#!/bin/bash

wiek=18

if [ $wiek -ge 18 ]
then
    echo "Osoba jest pełnoletnia."
else
    echo "Osoba jest niepełnoletnia."
fi
```

W tym przykładzie, jeśli zmienna `wiek` ma wartość większą lub równą 18, wyświetlany jest komunikat "Osoba jest pełnoletnia.". W przeciwnym razie wyświetlany jest komunikat "Osoba jest niepełnoletnia.".

W instrukcji warunkowej `if` w Bashu można wykorzystać różne operatory porównania do testowania różnych warunków. Oto lista podstawowych operatorów porównania, które można użyć w instrukcji `if`:

1. `-eq`: Równość (equal to)
2. `-ne`: Nierówność (not equal to)
3. `-lt`: Mniejsze niż (less than)
4. `-le`: Mniejsze lub równe (less than or equal to)
5. `-gt`: Większe niż (greater than)
6. `-ge`: Większe lub równe (greater than or equal to)

Te operatory porównania są wykorzystywane w wyrażeniach logicznych, aby porównać dwie wartości i zwrócić prawdę (`true`) lub fałsz (`false`) w zależności od wyniku porównania.

Przykład:

```bash
#!/bin/bash

a=5
b=10

if [ $a -lt $b ]
then
    echo "$a jest mniejsze niż $b"
fi
```

W tym przykładzie komenda `[ $a -lt $b ]` sprawdza, czy zmienna `a` jest mniejsza niż zmienna `b`. Jeśli warunek jest spełniony, to znaczy, że zmienna `a` rzeczywiście jest mniejsza niż zmienna `b`, więc zostanie wyświetlony komunikat "5 jest mniejsze niż 10".

Ponadto można łączyć operatory porównania w bardziej skomplikowane wyrażenia logiczne przy użyciu operatorów logicznych, takich jak `&&` (AND) i `||` (OR). Na przykład:

```bash
if [ $a -lt $b ] && [ $a -gt 0 ]
then
    echo "$a jest mniejsze niż $b i większe od 0"
fi
```

W tym przypadku komenda `if` sprawdza, czy zmienna `a` jest jednocześnie mniejsza niż zmienna `b` i większa od 0. Jeśli oba warunki są spełnione, zostanie wyświetlony odpowiedni komunikat.

Dzięki tym operatorom porównania i operacjom logicznym instrukcje `if` w Bashu stają się potężnym narzędziem do tworzenia elastycznych struktur warunkowych w skryptach.

## Pętle (wielokrotne wykonanie bloku kodu)
### Pętla`for`
