###### Zadania
##### 1. Jest takie drzewo katalogów:

.
├── ala
│   ├── i
│   │   └── as
│   └── ma
│       └── kota
└── kot
    └── ma
        └── ale

##### Znajdujesz się w katalogu kota. Katalog ala, jest w katalogu /tmp/ukos.

##### Jak przejść do katalogu ale za pomocą:

    ##### ścieżki względnej (relatywnej)
    ##### ścieżki bezwzględnej (absolutnej) 

> Ścieżka względna:
```
cd ../../../kot/ma/ale
```
> Ścieżka bezwzględna:
```
cd /tmp/ukos/kot/ma/ale
```

##### 2. Masz taki układ katalogów, jak wyżej i ciągle jesteś w katalogu kota. Jak utworzyć poddrzewo katalogów jan/kowalski w katalogu ale za pomocą jednej komendy?
```
mkdir -p ../../../kot/ma/jan/kowalski
```

##### 3. Masz taki układ katalogów, jak wyżej i ciągle jesteś w katalogu kota. Jak przenieść katalog ale do katalogu i?
```
mv ../../../kot/ma/ale ../../i/
```

##### 4. Jak zamknąć program, który nie odpowiada i nie reaguje na ctrl+c?
```
killall <program>
```

##### 5. Jak wypisać wszystkie pliki w bieżącym katalogu, których nazwa zaczyna się od al? (tu będzie trochę opisu ode mnie - http://www.robelle.com/smugbook/regexpr.html
```
ls -a . | grep -e '^al'
```

##### 6. Nadaj uprawnienia do katalogu <ala> tak, aby:

    każdy mógł do niego wejść
    tylko grupa mogła wyświetlić co w nim jest
    właściciel ma pełne prawa 

Skorzystaj raz z notacji ósemkowej, a raz symbolicznej
7

Jak utworzyć plik z listą plików w bieżącym katalogu?
8

Nie możesz utworzyć żadnego pliku na swoim koncie uczelnianym. Co się mogło stać? (wymień co najmniej 2 opcje). Zakładamy że możesz zalogować się w konsoli i nie masz zaległości w opłatach.
9

Jak przyśpieszyć wpisywanie komend w terminalu (jaki klawisz pozwala na uzupełnianie komend?)
10

Jak uruchomić program, aby nie blokował on terminala? Są dwa sposoby. 
