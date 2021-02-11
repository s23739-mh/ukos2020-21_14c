##### Zadania
###### 1.Przejdź do swojego katalogu domowego i wydaj taką komendę: ls -a, zobacz ile plików wypisało. Teraz wykonaj komendę: ls -a | grep D. Ile teraz jest wyników? Co się stało? Otóż program grep służy do wyszukiwania wierszy w pliku lub strumieniu wejściowym, które pasują do wzorca. Tu podałem wzorzec jako "D".A teraz wykonaj taką komendę: ls -a | grep D > ListaPlikówZLiterkąD.txt. Zobacz czy utworzył się jakiś plik? Jaka jest jego treść? Co znaczy | oraz co znaczy >?  

> Wynik wykonania komendy ls -a (35 wyników)
```
ubuntu@bss-ubu1804:~$ ls -a
.              Documents   Music                      test                         .viminfo
..             Downloads   Pictures                   .thumbnails                  .Xauthority
.bash_history  .gitconfig  .pki                       ukos2020-21_14c              .xscreensaver
.bash_logout   .gnupg      .profile                   .vboxclient-clipboard.pid    .xsession-errors
.bashrc        .lesshst    Public                     .vboxclient-display.pid      .xsession-errors.old
.cache         .links2     .ssh                       .vboxclient-draganddrop.pid
.config        .local      .sudo_as_admin_successful  .vboxclient-seamless.pid
Desktop        .mozilla    Templates                  Videos
```

> Wynik wykonania komendy ls -a | grep D - wynik zawężony do wierszy mającej w nazwie D
```
ubuntu@bss-ubu1804:~$ ls -a | grep D
Desktop
Documents
Downloads
```

> Wynikiem wykonania komendy ls -a | grep D > ListaPlikówZLiterkąD.txt była lista plików/katalogów zawierających w nazwie D, której wyjście przekierowano do pliku `ListaPlikówZLiterkąD.txt`. Treścią pliku jest wynik komendy ls -a | grep D. Symbol | oznacza przekierowanie standardowego wyjścia komendy ls -a jako standardowe wejście komendy grep D. Symbol > oznacza przekierowanie standardowego wyjścia wyniku komendy do pliku.

###### 2. Program ps służy do wyświetlania listy procesów. Zobacz co się stanie jeśli wpiszemy w terminalu:

    ps
    ps -a
    ps x
    ps aux 

Jak myślisz, co oznacza znak zapytania w kolumnie numer 2? Nie wiesz? Zapytaj prowadzącego, albo przeczytaj manual.

    Wyświetl wszystkie procesy bash.
    Wyświetl wszystkie procesy należące do użytkownika root. 

> ps - zwraca listę procesów
> ps -a - zwraca listę procesów z wyjątkiem session leaders (np. shell) i procesy niezwiązane z terminalem, wyświetlanie w stylu AT&T
> ps x - zwraca listę procesów, których obecny użytkownik jest właścicielem, wyświetlanie w stylu BSD
> ps aux - zwraca listę procesów tak jak w a oraz x, a także właścicieli procesów w kolumnie USER, wyświetlanie w stylu BSD
> Znak zapytania w kolumnie 2 (TTY) oznacza procesy niepotrzebujące terminala
> Wyświetlanie wszystkich procesów bash:
```
ubuntu@bss-ubu1804:~$ ps -C bash
  PID TTY          TIME CMD
  820 pts/0    00:00:00 bash
  860 pts/1    00:00:00 bash
  891 pts/2    00:00:00 bash
 1467 pts/3    00:00:00 bash
```
> Wyświetlanie wszystkich procesów należących do użytkownika root (-F - extra full format):
```
ubuntu@bss-ubu1804:~$ ps -F -u root
UID        PID  PPID  C    SZ   RSS PSR STIME TTY          TIME CMD
root         1     0  0 19400  8604   0 06:08 ?        00:00:01 /sbin/init
root         2     0  0     0     0   0 06:08 ?        00:00:00 [kthreadd]
root         4     2  0     0     0   0 06:08 ?        00:00:00 [kworker/0:0H]
root         6     2  0     0     0   0 06:08 ?        00:00:00 [mm_percpu_wq]
root         7     2  0     0     0   0 06:08 ?        00:00:00 [ksoftirqd/0]
root         8     2  0     0     0   0 06:08 ?        00:00:00 [rcu_sched]
root         9     2  0     0     0   0 06:08 ?        00:00:00 [rcu_bh]
root        10     2  0     0     0   0 06:08 ?        00:00:00 [migration/0]
root        11     2  0     0     0   0 06:08 ?        00:00:00 [watchdog/0]
root        12     2  0     0     0   0 06:08 ?        00:00:00 [cpuhp/0]
root        13     2  0     0     0   0 06:08 ?        00:00:00 [kdevtmpfs]
root        14     2  0     0     0   0 06:08 ?        00:00:00 [netns]
root        15     2  0     0     0   0 06:08 ?        00:00:00 [rcu_tasks_kthre]
root        16     2  0     0     0   0 06:08 ?        00:00:00 [kauditd]
root        17     2  0     0     0   0 06:08 ?        00:00:00 [khungtaskd]
[...]
```

###### 2.PID jest to identyfikator procesu. Za jego pomocą możesz odwoływać się do danego procesu za pomocą różnych mechanizmów systemu. Jednym z takich mechanizmów jest wysłanie sygnału (na przykład zakończenia) do procesu. Do tego służy komenda kill (może brzmi ona dość brutalnie, ale cóż, informatyka nie jest dla mięczaków). Komenda ta domyślnie wysyła sygnał zakończenia procesu do zadanego procesu.
##### Zadanie:

    ##### Uruchom wybrany przez Ciebie edytor tekstowy za pomocą menu "start" (menu aplikacji).
    Zobacz, jaki ma on PID - przyda się do tego komenda ps
    ##### Wydaj komendę kill w taki sposób, aby ten edytor się wyłączył. Zobacz czy to działa. Uwaga - niektóre programy przechwytują sygnały i mogą je częściowo blokować. Jeśli program nie wyłącza się, to zobacz jaka jest jego reakcja. Zobacz czy możesz wysłać do niego SIGKILL (zerknij do man).
    ##### zobacz działanie komendy killall shell
    ##### Zobacz czy kill zadziała dla dowolnego procesu 

> Uruchomiono edytor tekstowy leafpad, jego PID miał wartość 1885
```
ubuntu@bss-ubu1804:~$ ps -C leafpad
  PID TTY          TIME CMD
 1885 ?        00:00:00 leafpad
```
> Zakończono proces poniższą komendą:
```
ubuntu@bss-ubu1804:~$ kill 1885
```
> Wywołanie komendy killall shell - nic się nie stało po wywołaniu tej komendy, ponieważ procesy były uruchomione z basha, natomiast wywołanie killall bash spowodowało zakończenie wszystkich procesów bash, oprócz tego, z którego została wykonana ta komenda
> kill nie zadziała dla procesów innych użytkowników ze względu na brak uprawnień

##### 3. W terminalu jest kilka przydatnych skrótów klawiszowych. Jednym z nich jest Ctrl+C. Niektórzy z Państwa już go mieli okazję przetestować. Jest to sposób na wyłączenie aktywnego programu w terminalu. Proszę go przetestować w taki sposób, że:

    ##### Uruchamiamy komendę cat bez parametrów.
    ##### Wciśnij Ctrl+C i zobacz co się stanie 
> Ctrl+C spowodowało zakończenie programu
##### Kolejnym fajnym (zależy dla kogo ;) ) skrótem klawiszowym jest Ctrl+D - służy on do zakończenia strumienia wejściowego. Działa to trochę inaczej niż poprzednie rozwiązanie, mimo że na pierwszy rzut oka wygląda tak samo. Tym razem nie wysyła sygnału zakończenia, a jedynie zamyka strumień wejściowy. Jest to bardzo przydatne, jeśli chcemy zakończyć działanie jakiegoś programu korzystającego ze standardowego wejścia, ale w sposób możliwie bezpieczny. Zobacz co się stanie, jeśli :

    ##### Wydaj komendę cat > wynik1.txt
    ##### Wpisz tekst witaj bez wciskania klawisza Enter.
    ##### Wciśnij Ctrl+C
    ##### Zobacz co się znalazło w pliku wynik1.txt 
> Plik wynik1.txt jest pusty
```
ubuntu@bss-ubu1804:~$ cat > wynik1.txt
Witaj^C
ubuntu@bss-ubu1804:~$ cat wynik1.txt 
```
    ##### Wydaj komendę cat > wynik2.txt
    ##### Wpisz tekst witaj bez wciskania klawisza Enter.
    ##### Wciśnij Ctrl+D (możliwe że będzie trzeba wcisnąć to dwa razy)
    ##### Zobacz co się znalazło w pliku wynik2.txt 
> Plik zawiera wpisany tekst "Witaj":
```
ubuntu@bss-ubu1804:~$ cat > wynik2.txt
Witajubuntu@bss-ubu1804:~$ cat wynik2.txt 
Witaj
```

##### 4. Ctrl+Z służy do zatrzymania bieżącego procesu i przeniesienia go do tła. To znaczy program ciągle jest w pamięci, ale się nie wykonuje. Zobacz co się stanie jeśli:

    Wpisz komendę gimp
    W terminalu w którym się to uruchomiło wciśnij Ctrl+Z
    Spróbuj coś wyklikać w gimpie ;) 
> Zamiast gimpa użytko gedit. Po wciśnięciu Ctrl+Z program został zatrzymany i wysłany do backgroundu.
Co się stało? Zatrzymaliśmy program Gimp. Program wstrzymany za pomocą kombinacji Ctrl+Z jest zatrzymywany i przenoszony w tło (background). Efekt jest taki, ze taki program przestaje odpowiadać na cokolwiek.

Komenda bg służy do uruchomienia zatrzymanego procesu w tle. Zobacz:

    Wpisz komendę bg 
> Program wznowiono i zachowano w backgroundzie
Jak widać Gimp ożył (jeśli nie, to zapytaj prowadzącego).
Komenda fg służy do przeniesienia procesu na pierwszy plan. Zobacz co się stanie jeśli wpiszesz:

    fg 
> Program wznowiono i przeniesiono na pierwszy plan
Jak widać proces wrócił i można wcisnąć na przykład Ctrl+C aby go zakończyć.

W momencie uruchamiania programu, możemy od razu nakazać wykonanie go w tle. Służy do tego znak & umieszczony na końcu instrukcji. Zobacz:

    Wykonaj komendę gimp &
    Wykonaj komendę gedit &
    Wykonaj komendę geany & 

Zobacz co się stało (domyślam się że uruchomiły się 3 programy, a na terminalu ciągle można coś pisać. Kolejna komenda to jobs. Służy ona do wyświetlenia listy zadań przeniesionych do tła.
> Uruchomiono programy i wysłano je do backgroundu
    Przywróć program gedit z tła na pierwszy plan. Skorzystaj z jobs aby dowiedzieć się jakie mają numery poszczególne procesy działające w tle. 
> Zamiast gimpa użyto leafpad
```
ubuntu@bss-ubu1804:~$ jobs
[2]   Running                 gedit &
[3]-  Running                 geany &
[4]+  Running                 leafpad &
```
