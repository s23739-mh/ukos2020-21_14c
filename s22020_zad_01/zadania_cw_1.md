##### Zadania:
###### 1. Uruchom terminal.
###### 2. Wyświetl zawartość aktualnego katalogu.
```
ubuntu@bss-ubu1804:~$ ls
Desktop    Downloads  Pictures  Templates  ukos2020-21_14c
Documents  Music      Public    ukos       Videos
```
###### 3. Sprawdź gdzie aktualnie się znajdujesz. Porównaj to z tym co możesz zobaczyć w interfejsie graficznym.
```
ubuntu@bss-ubu1804:~$ pwd
/home/ubuntu
```
###### 4. Przejdź do katalogu Pulpit za pomocą ścieżki względnej
```
ubuntu@bss-ubu1804:~$ cd ./Desktop/
ubuntu@bss-ubu1804:~/Desktop$ 
```
###### 5. Sprawdź gdzie jesteś.
```
ubuntu@bss-ubu1804:~/Desktop$ pwd
/home/ubuntu/Desktop
```
###### 6. Wyświetl zawartość bieżącego katalogu.
```
ubuntu@bss-ubu1804:~/Desktop$ ls
adding-packages-permanently-info.txt  passwords-info.txt  terminator.desktop
ubuntu@bss-ubu1804:~/Desktop$ 
```
###### 7. Zobacz, czy przechodząc do tego katalogu w sposób graficzny (wyklikać) otrzymamy to samo?
> Przechodząc do katalogu w sposób graficzny zawartość katalogu Pulpit oraz sposób przechodzenia będzie taki sam. 
###### 8. Wyświetl zawartość swojego katalogu domowego bez przechodzenia do niego (ls z odpowiednim parametrem).
```
ubuntu@bss-ubu1804:~/Desktop$ ls ~
Desktop    Downloads  Pictures  Templates  ukos2020-21_14c
Documents  Music      Public    ukos       Videos
```
###### 9. Przejdź do katalogu Obrazy w twoim katalogu domowym za pomocą ścieżki względnej.
```
ubuntu@bss-ubu1804:~/Desktop$ cd ../Pictures/
ubuntu@bss-ubu1804:~/Pictures$ 
```
###### 10. Sprawdź gdzie jesteś.
```
ubuntu@bss-ubu1804:~/Pictures$ pwd
/home/ubuntu/Pictures
```
###### 11. Zobacz do jakiego katalogu przejdziesz za pomocą ścieżki ././././././
```
ubuntu@bss-ubu1804:~/Pictures$ cd ././././././
ubuntu@bss-ubu1804:~/Pictures$ 
```
> Jestem w tym samym katalogu, ponieważ zapis ścieżki względnej z jedną kropką oznacza operację na bieżącym katalogu.
####### 12. Przejdź do swojego katalogu domowego za pomocą ścieżki bezwzględnej.
```
ubuntu@bss-ubu1804:~/Pictures$ cd /home/ubuntu/
ubuntu@bss-ubu1804:~$ 
```
###### 13. Zobacz co się stanie jak wpiszesz komendę 'cd /root'. Jak już to zrobisz, zastanów się co się stało. Proponuję także zapytać prowadzącego.
```
ubuntu@bss-ubu1804:~$ cd /root
bash: cd: /root: Permission denied
```
> Otrzymałam informację zwrotną "permission denied", ponieważ katalog ten należy do użytkownika root, który jako jedyny posiada uprawnienia read-write-execute do tego katalogu. Pozostali użytkownicy (w tym użytkownik ubuntu, na którym wykonywałam polecenia), nie posiadali bitów rwx na katalogu /root.
###### 14. Zobacz, co się stanie, jeśli wciśniesz kombinację klawiszy: Ctrl+Alt+F1
> Maszyna przeszła do terminala nr 1, który działa w trybie headless. Aby powrócić do trybu GUI należy przejść do terminala nr 7 przez wciśnięcie Alt+F7.

##### Zadania c.d.
###### Korzystając z komend cd oraz mkdir stwórz następujące drzewo katalogów w swoim katalogu domowym (w dowolnym podkatalogu, albo bezpośrednio w ~):

```
ukos
 |\ katalog
 |      |\ katalog2
 |       \ katalog3
  \ klamka
```

```
ubuntu@bss-ubu1804:~$ mkdir -p ukos/{katalog/{katalog2,katalog3},klamka}
ubuntu@bss-ubu1804:~$ tree ukos
ukos
├── katalog
│   ├── katalog2
│   └── katalog3
└── klamka

4 directories, 0 files
```

###### W katalogu ukos/klamka stwórz pliki zajęcia2.txt zajęcia2.log inny.txt nowy.txt
```
ubuntu@bss-ubu1804:~$ touch ukos/klamka/{zajęcia2.txt,zajęcia2.log,inny.txt,nowy.txt}
ubuntu@bss-ubu1804:~$ tree ukos/klamka/
ukos/klamka/
├── inny.txt
├── nowy.txt
├── zajęcia2.log
└── zajęcia2.txt

0 directories, 4 files
```
###### Za pomocą jednego polecenia mkdir stwórz w katalogu ukos następujący katalog: ukos/to/jest/dluga/nazwa
```
ubuntu@bss-ubu1804:~$ mkdir -p ukos/to/jest/dluga/nazwa
ubuntu@bss-ubu1804:~$ tree ukos/to
ukos/to
└── jest
    └── dluga
        └── nazwa

3 directories, 0 files
```
###### następnie umieść w katalogu ukos/to/jest/dluga/nazwa plik dane.txt
```
ubuntu@bss-ubu1804:~$ touch ukos/to/jest/dluga/nazwa/dane.txt
ubuntu@bss-ubu1804:~$ ls ukos/to/jest/dluga/nazwa/
dane.txt
```
###### Usuń z katalogu ukos/klamka wszystkie pliki z rozszerzeniem txt
```
ubuntu@bss-ubu1804:~$ rm ukos/klamka/*.txt
ubuntu@bss-ubu1804:~$ ls ukos/klamka/
zajęcia2.log
```
###### Usuń katalog ukos/katalog/katalog2
```
ubuntu@bss-ubu1804:~$ rmdir ukos/katalog/katalog2/
ubuntu@bss-ubu1804:~$ ls ukos/katalog/
katalog3

```
Usuń cały katalog klamka za pomocą jednego polecenia
```
ubuntu@bss-ubu1804:~$ rm -R ukos/klamka/
ubuntu@bss-ubu1804:~$ ls ukos
katalog  to
```
