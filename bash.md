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
    - [Petla malejaca](#petla-malejaca)
    - [Petla iterujaca o wiecej niz 1](#petla-iterujaca-o-wiecej-niz-1)
  - [Pętla `while`](#pętla-while)
  - [Pętla `do while`](#pętla-do-while)
  - [Nieskonczona petla](#nieskonczona-petla)
- [Analiza skryptu prostopadloscian](#analiza-skryptu-prostopadloscian)
- [Analiza skryptu kulka.sh](#analiza-skryptu-kulkash)
- [Analiza skryptu quiz.sh](#analiza-skryptu-quizsh)
- [Tablice (Array) - przechowywanie wielu wartosci w zmiennej](#tablice-array---przechowywanie-wielu-wartosci-w-zmiennej)
  - [Dostęp do wartosci tablicy](#dostęp-do-wartosci-tablicy)
  - [Modyfikacjia tablicy](#modyfikacjia-tablicy)
  - [Symbol specjalny `@`](#symbol-specjalny-)
  - [Ilosc elementow w tablicy](#ilosc-elementow-w-tablicy)
  - [Wykorzystanie z pętla `for`](#wykorzystanie-z-pętla-for)
  - [Linijka po linijce wyjasnienie petli for ze skryptu quiz.](#linijka-po-linijce-wyjasnienie-petli-for-ze-skryptu-quiz)
- [`printf` - alternatywa do echo](#printf---alternatywa-do-echo)
- [Przkierowywanie wyniku komendy do pliku - `>` i `>>`](#przkierowywanie-wyniku-komendy-do-pliku----i-)
- [Analiza skryptu menu.sh](#analiza-skryptu-menush)
- [Instrukcja sterowania przeplywem programu - `case`](#instrukcja-sterowania-przeplywem-programu---case)
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
  - [Zadania 6 - while](#zadania-6---while)
    - [6.1 Liczby parzyste](#61-liczby-parzyste)
    - [6.2 Suma liczb](#62-suma-liczb)
    - [6.3 Liczby odwrotne](#63-liczby-odwrotne)
    - [6.4\* Suma cyfr](#64-suma-cyfr)
    - [6.5\* Palindrom](#65-palindrom)
  - [Zadania 7 - do while](#zadania-7---do-while)
    - [7.1 Oddaj sterowanie uzytkownikowi - menu](#71-oddaj-sterowanie-uzytkownikowi---menu)
  - [Zadania 8 - tablice](#zadania-8---tablice)


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

Zdefinowalismy zmienna o nazwie `skladnik`, ktorej poczatkowa wartosc to 1 i wypisalismy sume tej zmiennej z liczba 2 na ekranie za pomoca komendy `echo`.
> (za chwile wyjasnię dlaczego trzeba dopisywac `$((...))` .)

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
3. .`*` (Mnożenie): Mnoży dwie liczby. Na przykład, `3 * 2` zwróci `6`.
4. .`/` (Dzielenie): Dzieli pierwszą liczbę przez drugą. Na przykład, `6 / 2` zwróci `3`.
5. .`%` (Modulo): Zwraca resztę z dzielenia pierwszej liczby przez drugą. Na przykład, `10 % 3` zwróci `1`, ponieważ resztą z dzielenia `10` przez `3` jest `1`.
6. `**` (Potęgowanie): Podnosi pierwszą liczbę do potęgi drugiej liczby. Na przykład, `2 ** 3` zwróci `8`, ponieważ `2` podniesione do potęgi `3` wynosi `8`.
7. .`++` (Inkrementacja): Zwiększa wartość zmiennej o `1`. Na przykład, jeśli `x=5`, to `x++` zwiększy wartość `x` do `6`.
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

> (w skrypcie jest uzyta instukcja `for` ale zacznę od prostszych instrukcji warunkowych a nastepnie przejde do pętli)

Instrukcje sterowania przeplywem programu pozwalaja sterowac tym ktore linijki skryptu maja sie wykonać, które maja się wykonac wielokrotnie (w pętli), a które maja zostac pominiete.

## Instrukcje warunkowe (wykonac czy nie wykonac?)

### Instrukcja warunkowa `if`

Instrukcja warunkowa `if` pozwala programiscie kontrolowac kiedy dany kod ma sie wykonac, za pomoca warunku logicznego.

Ogólny format instrukcji `if` w Bashu wygląda następująco:

```bash
if warunek
then
    # blok kodu do wykonania, jeśli warunek jest spełniony
elif inny_warunek
    # blok kodu do wykonania, jeśli inny_warunek jest spełniony
else
    # blok kodu do wykonania, jeśli zaden z warunkow nie jest spełniony
fi
```

Poniżej znajduje się bardziej szczegółowe wyjaśnienie poszczególnych elementów instrukcji `if`:

- `warunek` to wyrażenie logiczne, które jest ewaluowane jako prawda (`true`) lub fałsz (`false`). Warunek może być zbudowany z różnych operatorów porównania, logicznych oraz innych elementów, które określają, czy dany warunek jest spełniony.

- `then` wskazuje początek bloku kodu, który ma być wykonany, jeśli warunek jest spełniony (czyli ma wartość `true`).

- `elif` (opcjonalnie) wskazuje początek bloku kodu, z kolejnym warunkiem, ktory zostanie wziety pod uwagę jesli wcześniejszy nie został spelniony. Jedna instrukcja `if` moze zawiera wiele blokow `elif`

- `inny_warunek` -  warunek ktory zostanie wziety pod uwage jesli w przypadku rozwazania bloku `elif`.

- `else` (opcjonalnie) wskazuje początek bloku kodu, który ma być wykonany, jeśli zadne waruneki nie zostaly spelnione.

- `fi` jest zakończeniem instrukcji `if`. Jest to po prostu odwrócenie słowa `if`.

**Bloki `else` i `elif` sa opcjonalne i moga byc pominiete, wtedy kod wykona sie tylko gdy warunek nastepujacy po `if` będzie spełniony.**

Możesz również używać bardziej złożonych warunków, korzystając z operatorów logicznych (`&&` dla "i" logicznego, `||` dla "lub" logicznego) oraz operatorów porównania (np. `-eq` dla równości, `-lt` dla mniejszości itp.), aby tworzyć bardziej elastyczne instrukcje warunkowe w Bashu.

Przykład:
```bash
#!/bin/bash

wiek=18

if [[ $wiek -ge 67 ]]; then
    echo "Osoba jest emerytem."
elif [[ $wiek -ge 18 ]]; then
    echo "Osoba jest pełnoletnia."
else
    echo "Osoba jest niepełnoletnia."
fi
```

W tym przykładzie, jeśli zmienna `wiek` ma wartość większą lub równą 67, wyświetlany jest komunikat "Osoba jest emerytem.". Jesli wiek ma wartosc wieksza lub rowna 18 ale mniejsza niz 67 to wyswietlone jest komunikat "Osoba jest pelnoletnia.". W przeciwnym razie wyświetlany jest komunikat "Osoba jest niepełnoletnia.". 

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

Zmienna `i` nie musi miec wartosci poczatkowej `0` a operacja wykonywana po wykonaniu petli nie jest ograniczona do operatora inkrementacji `++`.

Przyklady "innych" pętli:

### Petla malejaca
```bash
for ((i=10; i>=5; i--))
do
  echo "Liczba to: $i"
done
```

Petla rozpoczyna się z `i=10`, ktore po kazdej iteracji petli malaje o `1` i konczy sie gdy `i` osiagnie wartosc mniejsza niz `5`.

Wynik skryptu to:
```bash
Liczba to: 10
Liczba to: 9
Liczba to: 8
Liczba to: 7
Liczba to: 6
Liczba to: 5
```

### Petla iterujaca o wiecej niz 1
```bash
for ((i=1; i<=10; i=i+2))
do
  echo "Liczba to: $i"
done
```

Petla rozpoczyna się z `i=0`, ktore po kazdej iteracji petli rosnie o `2` i konczy sie gdy `i` osiagnie wartosc wieksza niz 10.

Wynik skryptu to:
```bash
Liczba to: 1
Liczba to: 3
Liczba to: 5
Liczba to: 7
Liczba to: 9
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

## Pętla `do while` 
 Jest to odmiana pętli `while`, gdzie warunek jest sprawdzany na końcu bloku kodu, co oznacza, że blok kodu zostanie wykonany przynajmniej raz, niezależnie od wartości warunku na początku.

Składnia pętli `do while`
```bash
do
    # blok kodu do wykonania
done while warunek
```
Gdzie:
- `do` i `done` oznaczają początek i koniec bloku kodu, który ma być wykonany.
- `warunek` to wyrażenie logiczne, które jest ewaluowane jako prawda (true) lub fałsz (false). Warunek jest sprawdzany na końcu bloku kodu, po wykonaniu bloku kodu.

Przykład:
```bash
licznik=1

do
   echo "Liczba to: $licznik"
   licznik=$((licznik+1))
done while [ $licznik -le 5 ]
```

W tym przykładzie pętla `do while` wykonuje blok kodu (instrukcję `echo`), dopóki zmienna `licznik` jest mniejsza lub równa `5`. Zmienna `licznik` jest zwiększana o `1` w ramach wykonania bloku. Instrukcja `echo` wyświetla wartość zmiennej `licznik` w ramach każdego wykonania bloku kodu.

Zatem na ekranie terminala zobaczymy:
```bash
Liczba to: 1
Liczba to: 2
Liczba to: 3
Liczba to: 4
Liczba to: 5
```

Najważniejsza rożnica w porownaniu do petli while:
```bash
licznik=10

do
   echo "Liczba to: $licznik"
   licznik=$((licznik+1))
done while [ $licznik -le 5 ]
```

Pomimo tego ze warunek nie jest spelniony to petla i tak zostanie raz wykonana zanim natapi sprawdzenie warunku konca pętli.

Wynik na ekranie terminala:
```bash
Liczba to: 10
```

## Nieskonczona petla
Jesli warunek pętli `while` bedzie zawsze prawdziwy to blok kodu pętli bedzie wykonywany w nieskonczonoc.

Przyklad:
```bash
while true
do
    # blok kodu do wykonania w nieskończoność
done
```

Taka pętla moze byc przydatna jesli w srodku jest "blokujaca" akcja. Np. oczekujemy w niej na podanie wartosci od uzytkownika i bedziemy powtarzac akcje w zaleznosci od jego wyborow. Jednak jeden z wyborów musi wtedy pozwalac na zakonczenie petli i wyjscie z programu.

Aby zakonczyc taką petle konieczne jest wyjscie ze skryptu za pomoca komendy:
```bash
exit 0
```

Jesli jednak w petli while nie bedzie blokujacej akcji jak  np.`read` to program moze powtarzac kod w nieskonczonosc i "zawiesi sie". Konieczne wtedy bedzie zakonczenie procesu skryptu "z zewnatrz skryptu" np za pomocą `Ctrl+C` lub `kill -9 PID`.


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

# Tablice (Array) - przechowywanie wielu wartosci w zmiennej

Linijki skryptu:
```bash
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
```

W języku Bash tablice są strukturami danych, które umożliwiają przechowywanie wielu wartości w jednej zmiennej. Kolejne wartosci w ramach tablicy przechowywane sa pod kolejnymi numerami(indeksami) zaczynajac od 0 - zobacz przyklad ponizej.

Aby zadeklarować tablicę w Bash, używamy składni:

```bash
nazwa_tablicy=(element1 element2 element3 ...)
```

## Dostęp do wartosci tablicy
Przykad:
Tablica zawierjącą trzy elementy: "jabłko", "banan" i "pomarańcza"
```bash
owoce=(
  "jabłko"
  "banan"
  "pomarańcza"
  )
```
Kazdy z elementow tablicy jest zapisany pod konkretnym ideksem, czyli numerem.

Aby uzyskać dostęp do elementu tablicy, używamy indeksu w nawiasach kwadratowych.

```bash
echo ${owoce[0]} # Wyswietli jabłko
echo ${owoce[1]} # Wyswietli banan
echo ${owoce[2]} # Wyswietli pomarancza
```
## Modyfikacjia tablicy
Możemy również przypisać nową wartość do elementu tablicy, odwołując się do niego za pomocą indeksu. Na przykład, aby zmienić drugi element tablicy "owoce" na "gruszka", możemy napisać:

```bash
owoce[1]="gruszka"
```

## Symbol specjalny `@`
Aby uzyskać dostęp do wszystkich elementów tablicy, możemy użyć składni ${nazwa_tablicy[@]}. Na przykład, aby wyświetlić wszystkie elementy tablicy "owoce", możemy napisać:

```bash
echo ${owoce[@]}
```

```
jabłko gruszka pomarańcza
```

## Ilosc elementow w tablicy
Aby uzyskac ilosc elementow w tablicy mozemy skorzystac z zapisu `${#nazwa_tablicy[@]}`:
```bash
echo ${#owoce[@]} # Wyswietli 3
```

## Wykorzystanie z pętla `for`
Linijki skryptu:
```bash
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
```

Aby wykonac operacje na elementach tablicy mozna po niej iterowac za pomoca petli for:

```bash
# z wykorzystaniem for ... in
echo "for in:"
for owoc in ${owoce[@]}
do
  echo $owoc
done

# z wykorzystaniem indeksu
echo "for with i:"
for (( i=0; i<${#owoce[@]}; i++ )); do
  echo "${owoce[$i]}"
done

```
Wynik:
```
for in:
jabłko
gruszka
pomarańcza

for with i:
jabłko
gruszka
pomarańcza
```

## Linijka po linijce wyjasnienie petli for ze skryptu quiz.
```bash
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
```

1. `for (( i=0; i<${#questions[@]}; i++ ))` - Rozpoczyna pętlę for, która będzie iterować po elementach tablicy questions. Zaczynamy od indeksu 0 poniewaz `i=0`, aż do ostatniego indeksu w tablicy questions poniewaz `${#questions[@]}` to ilosc elemntow w tablicy questions czyli w tym przypadku 5.

2. `do` - Rozpoczyna blok kodu, który będzie wykonywany w każdej iteracji pętli.

3. `echo "${questions[$i]}"` - Wyświetla pytanie, które znajduje się w tablicy `questions` pod indeksem(numerem) `$i`. Zmienna `$i` reprezentuje aktualny numer petli.

4. `read -p "Odpowiedź: " answer` - Czekaj na wprowadzenie odpowiedzi od użytkownika i przypisz ją do zmiennej answer. Komenda `read` z opcją `-p` wyświetla podany tekst jako prompt przed oczekiwaniem na wprowadzenie danych.

5. `if [[ $answer == ${answers[$i]} ]]; then` - Rozpoczyna instrukcję warunkową if, która sprawdza, czy wartość zmiennej `answer` jest równa wartości w tablicy `answers` pod indeksem `$i`.

6. `echo "Dobrze!"` - Wyświetla komunikat `"Dobrze!"`, jeśli odpowiedź jest poprawna.

7. `((correct++))` - Inkrementuje zmienną `correct` o 1. Zmienna `correct` jest używana do zliczania poprawnych odpowiedzi.

8. `else` - Rozpoczyna blok kodu, który będzie wykonywany, jeśli warunek w instrukcji warunkowej `if` nie jest spełniony.

9. `echo "Źle!"` - Wyświetla komunikat `"Źle!"`, jeśli odpowiedź jest niepoprawna.

10. `((incorrect++))` - Inkrementuje zmienną `incorrect` o `1`. Zmienna `incorrect` jest używana do zliczania niepoprawnych odpowiedzi.

11. `fi` - Kończy blok kodu instrukcji warunkowej `if`.

12. `done` - Kończy

# `printf` - alternatywa do echo
<!-- TODO -->

# Przkierowywanie wyniku komendy do pliku - `>` i `>>`
<!-- TODO -->

# Analiza skryptu menu.sh
```bash
#!/bin/bash

while true
do
    clear
    echo -e "\e[1;37m********************************************************\e[0m"
    echo -e "\e[1;32mMenu:\e[0m"
    echo -e "\e[1;33m1. Uruchom skrypt suma\e[0m"
    echo -e "\e[1;33m2. Uruchom skrypt prostopadloscian\e[0m"
    echo -e "\e[1;33m3. Uruchom skrypt quiz\e[0m"
    echo -e "\e[1;33m4. Uruchom skrypt kwadratek\e[0m"
    echo -e "\e[1;33m5. Uruchom skrypt kulka\e[0m"
    echo -e "\e[1;31m6. Wyjście z programu\e[0m"
    echo -e "\e[1;37m********************************************************\e[0m"
    read -p "Wybierz opcję (1-6) lub pierwszą literę skryptu: " opcja

    case $opcja in
        1) clear ; echo -e "\e[1;5;42;37mUruchamiam skrypt suma\e[0m" ; sleep 5 ; ./suma ;;
        2) clear ; echo -e "\e[1;5;42;37mUruchamiam skrypt prostopadloscian\e[0m" ; sleep 5 ; ./prostopadloscian ;;
        3) clear ; echo -e "\e[1;5;42;37mUruchamiam skrypt quiz\e[0m" ; sleep 5 ; ./quiz ;;
         4) clear ; echo -e "\e[1;5;42;37mUruchamiam skrypt kwadrat\e[0m" ; sleep 5 ; ./kwadratek ;;
         5) clear ; echo -e "\e[1;5;42;37mUruchamiam skrypt kula\e[0m" ; sleep 5 ; ./kulka ;;
        6) echo -e "\e[1;31mNarazie!\e[0m" ; clear ; exit 0 ;;
        *) opcja_1=$(echo $opcja | cut -c 1) 
           case $opcja_1 in
               "k") clear ; echo -e "\e[1;5;42;37mUruchamiam skrypt suma\e[0m" ; sleep 5 ; ./suma ;;
               "k") clear ; echo -e "\e[1;5;42;37mUruchamiam skrypt prostopadloscian\e[0m" ; sleep 5 ; ./prostopadloscian ;;
               "s") clear ; echo -e "\e[1;5;42;37mUruchamiam skrypt quiz\e[0m" ; sleep 5 ; ./quiz ;;
               "kw") clear ; echo -e "\e[1;5;42;37mUruchamiam skrypt kwadrat\e[0m" ; sleep 5 ; ./kwadratek ;;
               "kwa") clear ; echo -e "\e[1;5;42;37mUruchamiam skrypt kula\e[0m" ; sleep 5 ; ./kulka ;;
               *) clear ; echo -e "\e[1;31mNieprawidłowa opcja.\e[0m" ;;
           esac ;;
    esac

    read -n 1 -s -r -p $'\033[33mKliknij dowolny klawisz, aby wrócić do menu...\033[0m'
    echo -e "\e[1;37m********************************************************\e[0m"
done
```

# Instrukcja sterowania przeplywem programu - `case`
Komenda `case` w Bashu jest używana do tworzenia instrukcji warunkowych, które pozwalają na porównywanie wartości zmiennej lub wyrażenia z różnymi wzorcami. Jest to alternatywa dla instrukcji `if-elif-else` i pozwala na bardziej czytelne i zwięzłe sprawdzanie wielu przypadków.

Ogólna składnia instrukcji `case` wygląda następująco:
```bash
case wartość in
    wzorzec1)
        # blok kodu do wykonania, jeśli wartość pasuje do wzorca 1
        ;;
    wzorzec2)
        # blok kodu do wykonania, jeśli wartość pasuje do wzorca 2
        ;;
    wzorzec3)
        # blok kodu do wykonania, jeśli wartość pasuje do wzorca 3
        ;;
    *)
        # blok kodu do wykonania, jeśli wartość nie pasuje do żadnego z powyższych wzorców
        ;;
esac
```

Gdzie:
- `wartość` to zmienna lub wyrażenie, które chcemy porównać z wzorcami.
- `wzorzec1`, `wzorzec2`, `wzorzec3`, ... to różne wzorce, które chcemy porównać z wartością. Wzorce mogą zawierać znaki specjalne, takie jak `*` (dowolny ciąg znaków) i `?` (dowolny pojedynczy znak).
- `blok kodu do wykonania` to kod, który zostanie wykonany, jeśli wartość pasuje do danego wzorca. Bloki kodu są oddzielone od siebie przy użyciu operatora `;;`.
- `*)` to opcjonalny wzorzec "domyślny", który pasuje, gdy żaden z powyższych wzorców nie pasuje do wartości. Można w nim umieścić kod, który zostanie wykonany, jeśli żaden z powyższych wzorców nie pasuje

Przykład:
```bash
#!/bin/bash

read -p "Podaj ocenę (A, B, C, D, F): " grade

case $grade in
    A)
        echo "Doskonała ocena!"
        ;;
    B)
        echo "Bardzo dobra ocena!"
        ;;
    C)
        echo "Dobra ocena!"
        ;;
    D)
        echo "Dostateczna ocena!"
        ;;
    F)
        echo "Niezdany!"
        ;;
    *)
        echo "Nieprawidłowa ocena!"
        ;;
esac
```

W tym przykładzie użytkownik jest proszony o podanie oceny (A, B, C, D lub F). Następnie instrukcja `case` porównuje wartość zmiennej `grade` z różnymi wzorcami i wykonuje odpowiedni blok kodu, który wyświetla odpowiedni komunikat w zależności od podanej oceny.

Jeśli użytkownik poda ocenę A, zostanie wyświetlony komunikat "Doskonała ocena!". Jeśli poda ocenę B, zostanie wyświetlony komunikat "Bardzo dobra ocena!" i tak dalej. Jeśli podana ocena nie pasuje do żadnego z powyższych wzorców, zostanie wykonany blok kodu oznaczony jako `*`, który wyświetli komunikat "Nieprawidłowa ocena!".

Ważne jest, aby każdy blok kodu w instrukcji case był zakończony operatorem `;;`, który oznacza koniec bloku.

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

## Zadania 4 - Instrukcje warunkowe 
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

Nie jest to taki prosty skrypt jak sie wydaje, moze ci sie tu przydac petla malejaca.
```bash
for ((i=10; i>=1; i--))
do
  echo $i
done
```

## Zadania 6 - while


### 6.1 Liczby parzyste
Napisz skrypt `liczby_parzyste.sh`, który wykorzystuje pętlę `while` do wyświetlenia wszystkich liczb parzystych od 1 do `n`. Wartosc `n` zostaje wczytana jako argument od uzytkownika. 

### 6.2 Suma liczb
Napisz skrypt `suma_liczb.sh`, który wczytuje od użytkownika liczby tak długo, aż zostanie podana liczba 0. Skrypt powinien obliczyć sumę podanych liczb i wypisać ją na ekranie.

### 6.3 Liczby odwrotne
Napisz skrypt `liczby_odwrotne.sh`, który wczytuje od użytkownika liczbę i wypisuje na ekranie wszystkie liczby od tej liczby do 1 w kolejności malejącej.
### 6.4* Suma cyfr
Napisz skrypt `suma_cyfr.sh`, który wczytuje od użytkownika liczbę i oblicza sumę jej cyfr. Skrypt powinien wypisać na ekranie obliczoną sumę.

### 6.5* Palindrom
Napisz skrypt `palindrom.sh`, który wczytuje od użytkownika napis i sprawdza, czy jest on palindromem. Skrypt powinien wypisać na ekranie komunikat "Napis jest palindromem" lub "Napis nie jest palindromem" w zależności od wyniku.

Mozesz skorzystac z komendy `rev` ktora odwaraca przekazany string:
```
odwrocony=$(echo $napis | rev)
```

## Zadania 7 - do while
### 7.1 Oddaj sterowanie uzytkownikowi - menu
Napisz skrypt `sterowanie.sh`, który wczytuje od uzytkownika liczbe od 1 do 3 i w zaleznosci od numeru wypisuje na ekranie `*`, `**` lub `***`. Jesli uzytkownik poda 0 to zakoncz program za pomoca komendy `exit 0`. Jesli uzytkownik poda inna wartosc niz 0,1,2,3 to wyczysc ekran i zapytaj o numer jeszcze raz. 

## Zadania 8 - tablice
<!-- TODO -->
