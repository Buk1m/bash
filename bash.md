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
- [Operatory arytmetyczne](#operatory-arytmetyczne)
- [Instrukcje sterowania przeplywem programu](#instrukcje-sterowania-przeplywem-programu)
  - [Instrukcje warunkowe (wykonac czy nie wykonac?)](#instrukcje-warunkowe-wykonac-czy-nie-wykonac)
    - [Instrukcja warunkowa `if`](#instrukcja-warunkowa-if)
  - [Pętle (wielokrotne wykonanie bloku kodu)](#pętle-wielokrotne-wykonanie-bloku-kodu)
    - [Pętla`for`](#pętlafor)
  - [Pętla `while`](#pętla-while)
  - [Pętla `do while` inaczej `untill`](#pętla-do-while-inaczej-untill)
- [Analiza skryptu prostopadloscian](#analiza-skryptu-prostopadloscian)
- [Analiza skryptu kulka.sh](#analiza-skryptu-kulkash)
- [Analiza skryptu quiz.sh](#analiza-skryptu-quizsh)
- [Zadania](#zadania)
  - [Zadanie 1 - read, clear, echo](#zadanie-1---read-clear-echo)
  - [Zadanie 2 - zmienne](#zadanie-2---zmienne)
  - [Zadania 3 - operatory](#zadania-3---operatory)
    - [3.1 Suma](#31-suma)
    - [3.2 Roznica](#32-roznica)
    - [3.3 Iloczyn](#33-iloczyn)
    - [3.4 Iloraz](#34-iloraz)
    - [3.5 Potęga](#35-potęga)
- [Zadania 4 - Instrukcje warunkowe](#zadania-4---instrukcje-warunkowe)
    - [4.1 Sprawdzenie liczby](#41-sprawdzenie-liczby)
    - [4.2 Sprawdzenie parzystości](#42-sprawdzenie-parzystości)
    - [4.3 Sprawdzenie podzielności](#43-sprawdzenie-podzielności)
    - [4.4 Sprawdzenie długości napisu](#44-sprawdzenie-długości-napisu)
    - [4.6 Sprawdzenie równości napisów](#46-sprawdzenie-równości-napisów)
    - [4.7\* Sprawdzenie wielkości liter](#47-sprawdzenie-wielkości-liter)
  - [Zadania 5 - petla `for`](#zadania-5---petla-for)
    - [5.1 - Wyświetlanie liczb](#51---wyświetlanie-liczb)
    - [5.2 Silnia](#52-silnia)
    - [5.3 Trojkat](#53-trojkat)
    - [5.4 Liczba sum nieparzystych](#54-liczba-sum-nieparzystych)
    - [5.5 Wielokrotnosci z przedzialu](#55-wielokrotnosci-z-przedzialu)
    - [5.6\* Choinka](#56-choinka)
  - [Zadanie 6 - while](#zadanie-6---while)


# Materialy
- kurs jesli dobrze znasz angielski https://www.codecademy.com/courses/bash-scripting/lessons/learn-bash-scripting
- https://linuxconfig.org/bash-scripting-tutorial-for-beginners
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
read -p "Podaj imię: " -t 10 name
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
# Operatory arytmetyczne 
W Bashu dostępne są następujące operatory arytmetyczne:

1. `+` (Dodawanie): Dodaje dwie liczby. Na przykład, `3 + 2` zwróci `5`.

2. `-` (Odejmowanie): Odejmuje drugą liczbę od pierwszej. Na przykład, `3 - 2` zwróci `1`.

3.`*` (Mnożenie): Mnoży dwie liczby. Na przykład, `3 * 2` zwróci `6`.

4.`/` (Dzielenie): Dzieli pierwszą liczbę przez drugą. Na przykład, `6 / 2` zwróci `3`.

5.`%` (Modulo): Zwraca resztę z dzielenia pierwszej liczby przez drugą. Na przykład, `10 % 3` zwróci `1`, ponieważ resztą z dzielenia `10` przez `3` jest `1`.

6. `**` (Potęgowanie): Podnosi pierwszą liczbę do potęgi drugiej liczby. Na przykład, `2 ** 3` zwróci `8`, ponieważ `2` podniesione do potęgi `3` wynosi `8`.

7.`++` (Inkrementacja): Zwiększa wartość zmiennej o `1`. Na przykład, jeśli `x=5`, to `x++` zwiększy wartość `x` do `6`.

8. `--` (Dekrementacja): Zmniejsza wartość zmiennej o `1`. Na przykład, jeśli `x=5`, to `x--` zmniejszy wartość `x` do `4`.

Operacje arytmetyczne w Bashu można wykonywać za pomocą podwójnych nawiasów `$((wyrażenie))`, na przykład:

```bash
x=5
y=2

suma=$((x + y))
echo $suma  # Wyświetli 7

roznica=$((x - y))
echo $roznica  # Wyświetli 3

iloczyn=$((x * y))
echo $iloczyn  # Wyświetli 10

iloraz=$((x / y))
echo $iloraz  # Wyświetli 2

modulo=$((x % y))
echo $modulo  # Wyświetli 1

potega=$((x ** y))
echo $potega  # Wyświetli 25

x++
echo $x  # Wyświetli 6

x--
echo $x  # Wyświetli 5
```
Pamiętaj, że Bash wykonuje tylko dzielenie całkowite, więc `5 / 2` zwróci `2`, a nie `2.5`. 

Aby osiagnac wartosc zmiennoprzecinkowa mozna skorzystac z komendy `bc` czyli kalkulatora.

Podstawowa składnia komendy `bc` wygląda następująco:
```bash
echo "wyrażenie arytmetyczne" | bc
```

Przykład:
```bash
echo "5.5 / 2.2" | bc -l # Wyswietli 2.5
```

W tym przykładzie dzielimy `5.5` przez `2.2`. Opcja `-l` jest używana do włączenia matematyki zmiennoprzecinkowej. Bez tej opcji `bc` wykonałby dzielenie całkowite.

Możesz również używać zmiennych w wyrażeniach przekazywanych do `bc`. Na przykład:
```bash
x=5.5
y=2.2
echo "$x / $y" | bc -l # Wyswietli 2.5
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

Pętla for w Bashu jest używana do powtarzania bloku kodu (linijek kodu pomiedzy `do` i `done`) określoną liczbę razy. Jest to bardzo przydatne, gdy chcemy wykonać pewne operacje wielokrotnie.

Ogólna składnia pętli for w Bashu wygląda następująco:

```bash
for zmienna in lista_wartosci
do
    # blok kodu do wykonania dla każdej wartości
done
```

Gdzie:
- `zmienna` to nazwa zmiennej, która przyjmuje kolejne wartości z listy wartości.
- `lista_wartosci` to lista wartości, które zmienna przyjmuje po kolei. Może to być ciąg liczb, ciąg znaków, wynik komendy itp.
- `do` i `done` oznaczają początek i koniec bloku kodu, który ma być wykonany dla każdej wartości.

Przykład:

```bash
for i in 1 2 3 4 5
do
   echo "Liczba to: $i"
done
```

W tym przykładzie pętla `for` wykonuje blok kodu (instrukcję `echo`) dla każdej liczby w liście (1, 2, 3, 4, 5). Zmienna `i` przyjmuje kolejne wartości z listy, a instrukcja `echo` wyświetla te wartości.

Po wykonaniu skryptu zobaczymy na ekranie terminala wynik:
```bash
Liczba to: 1
Liczba to: 2
Liczba to: 3
Liczba to: 4
Liczba to: 5
```

Pętla for może również zawierac iterator (zmienną, której wartosc jest zwiekszana o 1 po kazdym wykonaniu bloku kodu z petli) i wykonywac sie az do spenielnia okreslonego warunku logicznego:

```bash
for (( i=0; i<5; i++ ))
do
   echo "Liczba to: $i"
done
```

W tym przypadku pętla `for` zaczyna się od wartości 0 `i=0;`, kończy gdy `i` osiagnie wartośc 5 `i<5;`. Wyrażenie `i++` oznacza, że zmienna `i` zwiększa się o 1 po każdym wykonaniu pętli . Blok kodu (instrukcja echo) jest wykonywany dla każdej wartości i (0, 1, 2, 3, 4).

Po wykonaniu skryptu na ekranie terminala zobaczymy: 
```bash
Liczba to: 0
Liczba to: 1
Liczba to: 2
Liczba to: 3
Liczba to: 4
```

Wiedząc juz jak działa pętla `for` mozemy wytlumaczyc kod ze skryptu kwadracik.sh:
```bash
sum_of_squares=0
for (( i=$lower_bound; i<=$upper_bound; i++ ))
do
  sum_of_squares=$(( $sum_of_squares + $i*$i ))
done
```

Dla przykladu w ktorym zmienna `lower_bound=3` a `upper_bound=5`:
1. zmienna `sum_of_squares` zostaje utworzona z wartoscią `0`
2. `i=$lower_bound;` czyli zmienna `i` przyjmie poczatkowa wartosc `3`.
3. Sprawdzony zostanie warunek `i<=$upper_bound` czyli po podstawieniu wartosci warunek `3 <= 5` jest spelniony wiec blok kodu zostanie wykonany;
4. Wykonany zostaje blok kodu: `sum_of_squares=$(( $sum_of_squares + $i*$i ))` czyli po podstawieniu `sum_of_squares=$(( 0 + 3*3 ))` wartosc zmiennej `sum_of_squares` wynosi `9`
5. `i++` - po wykonaniu bloku kodu wartosc zmienej `i` zostaje powiekszona o 1. czyli inaczej zapisujac `i=$i+1` => `i=3+1` a zatem zmienna `i` ma wartosc `4`
6. Sprawdzony zostanie warunek `i<=$upper_bound` czyli po podstawieniu wartosci warunek `4 <= 5` jest spelniony wiec blok kodu zostanie wykonany;
7. Ponownie wykonany zostaje  blok kodu: `sum_of_squares=$(( $sum_of_squares + $i*$i ))` czyli tym razem po podstawieniu `sum_of_squares=$(( 9 + 4*4 ))` wartosc zmiennej `sum_of_squares` wynosi  `25`
8. `i++` Nastepuje inkrementacja zmiennej `i`  jak w kroku 5 czyli `i=$i+1` => `i=4+1` a zatem zmienna `i` ma wartosc `5`
9. Sprawdzony zostanie warunek `i<=$upper_bound` czyli po podstawieniu wartosci warunek `5 <= 5` jest spelniony wiec blok kodu zostanie wykonany;

Jak latwo zauwazyc kroki 4-6 oraz 7-9 powtarzaja się i jedynie zmieniają się wartości zmiennych `i` oraz `sum_of_squares`

A zatem jeszcze raz:

10. Ponownie wykonany zostaje  blok kodu: `sum_of_squares=$(( $sum_of_squares + $i*$i ))` czyli tym razem po podstawieniu `sum_of_squares=$(( 25 + 5*5 ))` wartosc zmiennej `sum_of_squares` wynosi  `50`
11. `i++` Nastepuje inkrementacja zmiennej `i`  jak w kroku 5 i 8 czyli `i=$i+1` => `i=5+1` a zatem zmienna `i` ma wartosc `6`
12. Sprawdzony zostanie warunek `i<=$upper_bound` czyli po podstawieniu wartosci warunek warunek `6 <= 5` nie jest spelniony i pętla się zakonczy z ostateczym wynikiem zmiennej `sum_of_squares` o wartosci `50`.

Po zakonczonej pętli wykonana zostanie kolejna linijka programu czyli 
```bash
echo "Suma kwadratów kolejnych liczb od $lower_bound do $upper_bound wynosi: $sum_of_squares"
```
która wypisze na ekranie terminala:
```
Suma kwadratów kolejnych liczb od 3 do 5 wynosi: 50
```
## Pętla `while`
Pętla `while` w Bashu jest używana do powtarzania bloku kodu (instrukcji), dopóki określony warunek jest spełniony (ma wartość `true`). Jest to bardzo przydatne, gdy chcemy wykonać pewne operacje wielokrotnie, ale nie znamy dokładnej liczby powtórzeń z góry.

Ogólna składnia pętli `while` w Bashu wygląda następująco:


```bash
while warunek
do
    # blok kodu do wykonania, dopóki warunek jest spełniony
done
```

Gdzie:
- `warunek` to wyrażenie logiczne, które jest ewaluowane jako prawda (`true`) lub fałsz (`false`). Warunek może być zbudowany z różnych operatorów porównania, które poznaleś w ramach instrukcji warunkowej `if`.
- `do` i `done` oznaczają początek i koniec bloku kodu, który ma być wykonany, dopóki warunek jest spełniony.

Przykład:

```bash
licznik=1

while [ $licznik -le 5 ]
do
   echo "Liczba to: $licznik"
   licznik=$((licznik+1))
done
```

W tym przykładzie pętla `while` wykonuje blok kodu (instrukcję `echo`), dopóki zmienna `licznik` jest mniejsza lub równa `5`. Zmienna `licznik` jest zwiększana o 1 za każdym wykonaniem pętli. Instrukcja `echo` wyświetla wartość zmiennej `licznik` w ramach kazdego wykonania bloku kodu.

Zatem na ekranie terminala zobaczymy:
```bash
Liczba to: 1
Liczba to: 2
Liczba to: 3
Liczba to: 4
Liczba to: 5
```

## Pętla `do while` inaczej `untill`

# Analiza skryptu prostopadloscian
```bash
#!/bin/bash

echo "Podaj długość krawędzi a:"
read a
echo "Podaj długość krawędzi b:"
read b
echo "Podaj długość krawędzi c:"
read c

pole=$((2 * (($a * $b) + ($a * $c) + ($b * $c))))

echo "Pole prostopadłościanu o krawędziach a,b,c wynosi: $pole"
```

Ten skrypt nie zawiera nowych koncepcji i powinien byc zrozumialy po przeczytaniu analizy skrptu kwadracik.sh. 


# Analiza skryptu kulka.sh

```bash
#!/bin/bash
echo 'Wyliczanie pola kola'
echo ''
echo 'Wpisz promień r:'
read r
echo ''
pi=$(echo "3.14*$r" | bc)
echo "Pole o promieniu $r = $pi"
```

Skypt kulka.sh rowniez nie powinien juz sprawiac ci problemów. Aby obliczyc pole kola, które wymaga obliczen na liczbach zmiennoprzecinkowych (rzeczywistych) wykorzystano komende `bc` tak jak w rozdziale Operatory arytmetyczne.

# Analiza skryptu quiz.sh

```bash
#!/bin/bash

echo "Witaj w quizie!"
read -p "Podaj swoje imię i nazwisko: " name

questions=(
  "Pytanie 1: ile to 2+2 (a) 5  (b) 3 (c) 4"
  "Pytanie 2: Co to jest myszka? (a) zwierze (b) urządzenie do komputera (c) coś innego"
  "Pytanie 3: Co to jest HTML? (a) język programowania (b) typ strony (c) język lub ciąg znaczników"
  "Pytanie 4: Darmowe oprogramowanie to? (a) trial (b) shareware (c) freeware"	
  "Pytanie 5: Co to jest serwer? (a) puszka po czipsach (b) oprogramowanie (c) urządzenie sieciowe"
)

answers=(
  "a"
  "b"
  "c"
  "c"
  "c"
)

correct=0
incorrect=0

for (( i=0; i<${#questions[@]}; i++ )); do
  echo "${questions[$i]}"
  read -p "Odpowiedź: " answer
  if [[ $answer == ${answers[$i]} ]]; then
    echo "Dobrze!"
    ((correct++))
  else
    echo "Źle!"
    ((incorrect++))
  fi
done


printf "Wynik dla %s:\nPoprawne odpowiedzi: %d\nNiepoprawne odpowiedzi: %d\n" "$name" "$correct" "$incorrect" > ~/quizodp.txt

```


# Zadania
## Zadanie 1 - read, clear, echo

1. Wykorzystaj komendę `echo`, aby wyświetlić pytanie: "Jaki jest Twój ulubiony kolor?"

2. Użyj komendy `read`, aby odczytać odpowiedź użytkownika i przypisać ją do zmiennej `color`.

3. Wykorzystaj komendę `clear`, aby wyczyścić ekran terminala.

4. Wykorzystaj komendę `echo`, aby wyświetlić komunikat: "Twój ulubiony kolor to: [color]", gdzie [color] to wartość zmiennej `color`.

Czy mozemy pominac krok `1.` wykorzystujac jedna z opcji komedy `read`? Sprobuj zmienic odpowiednio swoj program.

## Zadanie 2 - zmienne

1. Zadeklaruj zmienne `imie="John"`, `nazwisko="Doe"` i `rok_urodzenia="1990"`

Wypisz jedna komenda echo `Ja, John o nazwisku Doe urodzilem sie w roku 1990` wykorzystujac zmienne.

Nastepnie w tym samym skrypcie zmien wartosci zmiennych na swoje imie, nazwisko i rok urodzenia i ponownie wypisz na ekranie.

## Zadania 3 - operatory

### 3.1 Suma

Napisz skrypt `suma.sh`, który wczytuje od użytkownika dwie liczby i wypisuje na ekranie wynik dodawania.

### 3.2 Roznica
Napisz skrypt `roznica.sh`, który wczytuje od użytkownika dwie liczby i wypisuje na ekranie wynik odejmowania.

### 3.3 Iloczyn
Napisz skrypt `iloczyn.sh`, który wczytuje od użytkownika dwie liczby i wypisuje na ekranie wynik mnozenia.

### 3.4 Iloraz
Napisz skrypt `iloraz.sh`, który wczytuje od użytkownika dwie liczby i wypisuje na ekranie wynik dzielenia. Uwzględnij liczby zmiennoprzecinkowe.

### 3.5 Potęga
Napisz skrypt `potega.sh`, który wczytuje od użytkownika dwie liczby i wypisuje na ekranie wynik potęgowania.

# Zadania 4 - Instrukcje warunkowe 
### 4.1 Sprawdzenie liczby
Napisz skrypt `sprawdz_liczbe.sh`, który wczytuje od użytkownika jedną liczbę i sprawdza, czy jest ona większa od zera. Jeśli tak, to wypisuje na ekranie komunikat "Liczba jest większa od zera", w przeciwnym razie wypisuje komunikat "Liczba nie jest większa od zera".

### 4.2 Sprawdzenie parzystości
Napisz skrypt `sprawdz_parzystosc.sh`, który wczytuje od użytkownika jedną liczbę i sprawdza, czy jest ona parzysta. Jeśli tak, to wypisuje na ekranie komunikat "Liczba jest parzysta", w przeciwnym razie wypisuje komunikat "Liczba jest nieparzysta".

### 4.3 Sprawdzenie podzielności
Napisz skrypt `sprawdz_podzielnosc.sh`, który wczytuje od użytkownika dwie liczby: `liczba` i `dzielnik`. Skrypt powinien sprawdzić, czy `liczba` jest podzielna przez `dzielnik`. Jeśli tak, to wypisuje na ekranie komunikat "Liczba jest podzielna przez dzielnik", w przeciwnym razie wypisuje komunikat "Liczba nie jest podzielna przez dzielnik".

### 4.4 Sprawdzenie długości napisu
Napisz skrypt `sprawdz_napis.sh`, który wczytuje od użytkownika jeden napis. Skrypt powinien sprawdzić, czy długość napisu jest większa od 5. Jeśli tak, to wypisuje na ekranie komunikat "Napis jest dłuższy niż 5 znaków", w przeciwnym razie wypisuje komunikat "Napis jest krótszy lub równy 5 znakom".


Aby sprawdzić długość zmiennej tekstowej w Bash, możesz użyć wbudowanej zmiennej ${#string}. Oto przykład:

```bash
string="Hello, World!"
length=${#string}
echo "Długość stringa: $length"
```
Wynik:
```bash
Długość stringa: 13
```

### 4.6 Sprawdzenie równości napisów
Napisz skrypt `sprawdz_rownosc.sh`, który wczytuje od użytkownika dwa napisy: `napis1` i `napis2`. Skrypt powinien sprawdzić, czy `napis1` jest równy `napis2`. Jeśli tak, to wypisuje na ekranie komunikat "Napisy są równe", w przeciwnym razie wypisuje komunikat "Napisy nie są równe".

### 4.7* Sprawdzenie wielkości liter
Napisz skrypt `sprawdz_wielkosc.sh`, który wczytuje od użytkownika jeden napis. Skrypt powinien sprawdzić, czy napis składa się tylko z małych liter. Jeśli tak, to wypisuje na ekranie komunikat "Napis składa się tylko z małych liter", w przeciwnym razie wypisuje komunikat "Napis zawiera inne znaki niż małe litery".

## Zadania 5 - petla `for`

### 5.1 - Wyświetlanie liczb

Napisz skrypt `wyswietl_liczby.sh`, który wykorzystuje pętlę `for` do wyświetlenia liczb od `lower_number` do `upper_number` które zostana wczytane od uzytkownika.

### 5.2 Silnia
Napisz skrypt `silnia.sh`, który policzy silnie liczby podanej jako argument przez uzytkownika. np 5!.

### 5.3 Trojkat
Napisz skrypt `trojkat.sh` ktory wyswietli na ekranie trojkat ze znakow * o wielkosci podanej przez uzytkownika.
Przyklad dla wielkosci `5`:
```
*
**
***
****
*****
```

### 5.4 Liczba sum nieparzystych 
Napisz skypt `suma_nieparzystych.sh` obliczający sumę liczb nieparzystych z przedziału <x,y>. Wartości x i y podaje użytkownik.

### 5.5 Wielokrotnosci z przedzialu
Napisz skypt `wielokrotnosci.sh`, który wyświetli wszystkie liczby z przedziału od 50 do 100 podzielne przez dowolną liczbę k, która podaje użytkownik. Przekształć program tak aby przedział liczb również podawał użytkownik.

### 5.6* Choinka
Napisz skrypt `choinka.sh`, który wczyta od uzytkownika 3 cyfry. Kazda kolejna cyfra musi byc wieksza od poprzedniej i narysuje na ekranie choinke.

Przyklad:
Uzytkownik podaje 3 5 7
```
      *
    * * *
      *
    * * *
  * * * * *
      *
    * * *
  * * * * *
* * * * * * *
     ***
```
## Zadanie 6 - while
