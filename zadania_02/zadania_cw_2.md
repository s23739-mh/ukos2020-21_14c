##### Zadania
###### 1. Utworzyć we własnym katalogu domowym niedużą strukturę podkatalogów i plików tekstowych. Przydzielić różne prawa dostępu, następnie spróbować wejść do katalogów domowych innych uczestników zajęć i sprawdzić, które z obiektów są tam dla nas dostępne (i w jakim sensie). 

> Utworzono następującą strukturę katalogów:
```
s22020@szuflandia:~$ mkdir -p dir1/dir2/dir3
s22020@szuflandia:~$ touch dir1/dir2/dir3/file1
s22020@szuflandia:~$ echo 'test file' > dir1/dir2/dir3/file1 
s22020@szuflandia:~$ cat dir1/dir2/dir3/file1 
test file
```

> Katalogi posiadały uprawnienia 755, natomiast plik - 644:
```
s22020@szuflandia:~$ ls -l 
razem 12
drwxr-xr-x 3 s22020 pjwstk 4096 lis 17 08:03 dir1
drwxr-xr-x 2 s22020 pjwstk 4096 lis  7 16:47 public_html
drwxr-xr-x 3 s22020 pjwstk 4096 lis  7 16:39 tmp
s22020@szuflandia:~$ ls -l dir1/dir2/dir3/
razem 4
-rw-r--r-- 1 s22020 pjwstk 10 lis 17 08:03 file1
s22020@szuflandia:~$ ls -l
razem 12
drwxr-xr-x 3 s22020 pjwstk 4096 lis 17 08:03 dir1
drwxr-xr-x 2 s22020 pjwstk 4096 lis  7 16:47 public_html
drwxr-xr-x 3 s22020 pjwstk 4096 lis  7 16:39 tmp
s22020@szuflandia:~$ ls -l dir1/
razem 4
drwxr-xr-x 3 s22020 pjwstk 4096 lis 17 08:03 dir2
s22020@szuflandia:~$ ls -l dir1/dir2/
razem 4
drwxr-xr-x 2 s22020 pjwstk 4096 lis 17 08:03 dir3
s22020@szuflandia:~$ ls -l dir1/dir2/dir3/
razem 4
-rw-r--r-- 1 s22020 pjwstk 10 lis 17 08:03 file1
```

> Przydzielono prawa dostępu 640 do katalogu dir2:
```
s22020@szuflandia:~/dir1$ chmod 640 dir2/
```
```
s22020@szuflandia:~$ ls -al dir1/
razem 12
drwxr-xr-x 3 s22020 pjwstk 4096 lis 17 08:03 .
drwxr-xr-x 9 s22020 pjwstk 4096 lis 17 08:19 ..
drw-r----- 3 s22020 pjwstk 4096 lis 17 08:03 dir2
```
```
s22020@szuflandia:~/dir1$ ls -al dir2/
ls: nie ma dostępu do 'dir2/dir3': Brak dostępu
ls: nie ma dostępu do 'dir2/..': Brak dostępu
ls: nie ma dostępu do 'dir2/.': Brak dostępu
razem 0
d????????? ? ? ? ?            ? .
d????????? ? ? ? ?            ? ..
?????????? ? ? ? ?            ? dir3
```
> Możliwe było przywrócenie uprawnień 755 do katalogu dir2 ze względu na właścicielstwo tego katalogu:
```
s22020@szuflandia:~/dir1$ chmod 755 dir2
s22020@szuflandia:~/dir1$ ls -al
razem 12
drwxr-xr-x 3 s22020 pjwstk 4096 lis 17 08:03 .
drwxr-xr-x 9 s22020 pjwstk 4096 lis 17 08:19 ..
drwxr-xr-x 3 s22020 pjwstk 4096 lis 17 08:03 dir2
```

> Niektóre z katalogów domowych innych użytkowników posiadały uprawnienia 755, inne 777 lub 700.
Spróbować utworzyć własny plik w cudzym katalogu ("kukułcze jajko") oraz spróbować usunąć cudzy plik we własnym katalogu (co można zaobserwować ?). 
> Po stworzeniu pustego pliku z uprawnieniami 644 w moim katalogu domowym przez innego użytkownika, nie mogłam zmienić mu uprawnień, ani zapisywać do niego, natomiast mogłam plik usunąć.
Wypróbować powyższe operacje:
        a. w trybie tekstowym;
        b. przy użyciu programu Midnight Commander (mc);
	> Przy użyciu mc można było w ten sam sposób zmienić uprawnienia do pliku naciskając <F9> > Plik > Zmień uprawnienia
        c. przy użyciu graficznego interfejsu użytkownika
	> Przy użyciu graficznego interfejsu użytkownika można było zmienić uprawnienia do pliku lub katalogu przez naciśnięcie prawego przycisku myszy na katalogu lub pliku > Properties > Permissions. W zakładce permissions znajdowały się 3 listy do odczytu oraz modyfikacji zawartości i wykonywania w przypadku pliku lub do odczytania zawartości, modyfikacji lub dostępu do niej w przypadku folderów. Uprawnienia można było nadać wszystkim, tylko właścicielowi, tylko właścicielowi i grupie lub nikomu. Nie można było odebrać uprawnień do odczytu wszystkim użytkownikom.  
###### 2. W utworzonej na swoim koncie strukturze podkatalogów przeprowadzić eksperymenty:
        a. usuwając wszelkie prawa dostępu do katalogu bieżącego;
	```
	s22020@szuflandia:~/dir1/dir2/dir3$ chmod 000 .
	s22020@szuflandia:~/dir1/dir2/dir3$ cat file1
	cat: file1: Brak dostępu
	s22020@szuflandia:~/dir1/dir2/dir3$ ls -l
	ls: nie można otworzyć katalogu '.': Brak dostępu
	s22020@szuflandia:~/dir1/dir2/dir3$ echo 'kolejny test' >> file1
	-shell: file1: Brak dostępu
	s22020@szuflandia:~/dir1/dir2/dir3$ rm file1
	rm: nie można usunąć 'file1': Brak dostępu
	s22020@szuflandia:~/dir1/dir2/dir3$ chmod 755 .
	chmod: nie ma dostępu do '.': Brak dostępu
	s22020@szuflandia:~/dir1/dir2/dir3$ cd ..
	s22020@szuflandia:~/dir1/dir2$ cd dir3
	-shell: cd: dir3: Brak dostępu
	s22020@szuflandia:~/dir1/dir2$ 
	```
	> Niemożliwe było wylistowanie zawartości katalogu, zapisu do plików w tym katalogu, wyświetlanie i usuwanie pliku, zmienianie uprawnień do katalogu. Możliwe było przejście do katalogu nadrzędnego.
        b. usuwając wszelkie prawa dostępu do katalogu nadrzędnego (nadkatalogu).
	``` 
	s22020@szuflandia:~/dir1/dir2/dir3$ chmod 000 ..
	chmod: nie ma dostępu do '..': Brak dostępu
	s22020@szuflandia:~/dir1/dir2/dir3$ cd ..
	s22020@szuflandia:~/dir1/dir2$ chmod 000 .
	s22020@szuflandia:~/dir1/dir2$ ls -l
	ls: nie można otworzyć katalogu '.': Brak dostępu
	s22020@szuflandia:~/dir1/dir2$ 
	```
	> Niemożliwa była zmiana uprawnień z bieżącego katalogu (uprawnienia 000) do katalogu nadrzędnego. Możliwe było przejście do katalogu nadrzędnego i dopiero wtedy zmiana uprawnień na 000.
W jakich przypadkach możemy wykonać wtedy polecenie cd ? W jakich przypadkach możemy wykonać polecenie chmod ? Czy możemy bezpośrednio przeskoczyć do katalogu ABC/XYZ, jeśli nie mamy prawa wstępu do ABC, ale mamy do XYZ ?
> cd można wykonać w przypadku gdy do katalogu mamy uprawnienia execute. chmod można wykonać w bieżącym katalogu, jeśli mamy do niego uprawnienia conajmniej execute. 
```
s22020@szuflandia:~/dir1$ ls -l dir2/
razem 4
drwxr-xr-x 2 s22020 pjwstk 4096 lis 17 08:38 dir3
s22020@szuflandia:~/dir1$ chmod 000 dir2
s22020@szuflandia:~/dir1$ cd dir2
-shell: cd: dir2: Brak dostępu
s22020@szuflandia:~/dir1$ cd dir2/dir3
-shell: cd: dir2/dir3: Brak dostępu
s22020@szuflandia:~/dir1$ cat dir2/dir3/file1
cat: dir2/dir3/file1: Brak dostępu
s22020@szuflandia:~/dir1$ 
```
###### 3. W zespołach 2- lub 3-osobowych wypróbować możliwość komunikacji przez współdzielony plik: na jednym z kont w zespole utworzyć pusty plik i przydzielić odpowiednie prawa dostępu (do pliku i do katalogu domowego). Wpisywać i odczytywać komunikaty przy użyciu poleceń:
	echo treść_komunikatu > plik
        cat plik 
Sprawdzić, jaki skutek powoduje zamiana operatora > na operator >> w poleceniu echo. Uruchom także drugi terminal i wykonaj w nim komendę tail -f plik i powtórz powyższe ćwiczenie w pierwszym terminalu (komunikacja za pomocą pliku).
> Operator \> powoduje zapis do pliku w przypadku pustego pliku oraz nadpisanie zawartości pliku w przypadku pliku, który nie jest pusty. Operator \>\> powoduje dopisanie do ostatniej linii pliku zawartości
###### 4. Znaleźć w swoim katalogu domowym podkatalog public_html (jeśli go nie ma, to utworzyć). Umieścić w nim plik o nazwie strona.html i następującej zawartości:
        <HTML>
        <BODY>
        <H1>To jest moja strona domowa</H1>
        </BODY>
        </HTML> 
Sprawdzić, jakie są minimalne prawa dostępu, które trzeba przydzielić do:
a. katalogu domowego;
> Potrzebne są uprawnienia execute dla innych użytkowników (o=x) do katalogu domowego - wejście do folderu, ale brak możliwości odczytu i zapisu dla bezpieczeństwa
b. katalogu public_html;
> Potrzebne są uprawnienia read i execute dla innych użytkowników (o=rx) do katalogu public_html, żeby móc wejść do katalogu i wyświetlić jego zawartość przez internet
c. pliku strona.html, aby zawartość pliku była widoczna w przeglądarce internetowej pod adresem http://szuflandia.pjwstk.edu.pl/~nazwa_konta/strona.html 
> Potrzebne są uprawnienia read dla innych użytkowników (o=r) żeby móc wyświetlić zawartość pliku

######  Zadanie

W opisie bash'a (man) przeczytać opis polecenia wewnętrznego umask i wypróbować jego działanie sprawdzając, a następnie zmieniając swoją maskę trybu pliku i tworząc za każdym razem nowe pliki (przy użyciu polecenia touch plik), a później sprawdzając uzyskane prawa dostępu do nich (polecenie ls -l). Jaka operacja logiczna na bitach domyślnych praw dostępu oraz maski jest wykonywana ? 
> Środowisko wykonywania w bashu składa się między innymi z maski trybu tworzonych plików, którą jest ustawiona przez polecenie umask lub odziedziczona po rodzicu powłoki
> umask, tak jak chmod, składa się z cyfr w zapisie ósemkowym lub symbolicznym (char). umask bez argumentów wyświetla obecnie ustawioną maskę trybu tworzonych plików, argument -S powoduje wypisanie maski trybu w zapisie symbolicznym, umask z argumentem -p bez podanego trybu powoduje możliwość wykorzystania wyjścia komendy jako wejście kolejnej komendy
```
s22020@szuflandia:~/test_umask$ umask
0022
s22020@szuflandia:~/test_umask$ echo 'domyslny umask' > domyslny
s22020@szuflandia:~/test_umask$ ls -l
razem 4
-rw-r--r-- 1 s22020 pjwstk 15 lis 17 09:44 domyslny
s22020@szuflandia:~/test_umask$ umask 000
s22020@szuflandia:~/test_umask$ echo 'lucky file' > lucky_file
s22020@szuflandia:~/test_umask$ ls -l
razem 8
-rw-r--r-- 1 s22020 pjwstk 15 lis 17 09:44 domyslny
-rw-rw-rw- 1 s22020 pjwstk 11 lis 17 09:44 lucky_file
s22020@szuflandia:~/test_umask$ umask 077
s22020@szuflandia:~/test_umask$ echo 'file for owner only' > owner_file
s22020@szuflandia:~/test_umask$ ls -l
razem 12
-rw-r--r-- 1 s22020 pjwstk 15 lis 17 09:44 domyslny
-rw-rw-rw- 1 s22020 pjwstk 11 lis 17 09:44 lucky_file
-rw------- 1 s22020 pjwstk 20 lis 17 09:45 owner_file
s22020@szuflandia:~/test_umask$ umask 711
s22020@szuflandia:~/test_umask$ echo 'write to file' > can_write
s22020@szuflandia:~/test_umask$ ls -l
razem 16
----rw-rw- 1 s22020 pjwstk 14 lis 17 09:46 can_write
-rw-r--r-- 1 s22020 pjwstk 15 lis 17 09:44 domyslny
-rw-rw-rw- 1 s22020 pjwstk 11 lis 17 09:44 lucky_file
-rw------- 1 s22020 pjwstk 20 lis 17 09:45 owner_file
s22020@szuflandia:~/test_umask$ umask 011
s22020@szuflandia:~/test_umask$ echo 'owner can do anything, others can rw' > other_file
s22020@szuflandia:~/test_umask$ ls -l
razem 20
----rw-rw- 1 s22020 pjwstk 14 lis 17 09:46 can_write
-rw-r--r-- 1 s22020 pjwstk 15 lis 17 09:44 domyslny
-rw-rw-rw- 1 s22020 pjwstk 11 lis 17 09:44 lucky_file
-rw-rw-rw- 1 s22020 pjwstk 37 lis 17 09:47 other_file
-rw------- 1 s22020 pjwstk 20 lis 17 09:45 owner_file
s22020@szuflandia:~/test_umask$ umask 022
```

>Podczas ustawiania umask na np. 000, bit execute nie jest ustawiany, ponieważ umask służy do odbierania uprawnień, a nie ich nadawania. Umask działa w zgodności ze standardem POSIX, który uniemożliwia ustawienie bitu execute dla wszystkich użytkowników.
