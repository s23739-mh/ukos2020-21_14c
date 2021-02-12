###### Zadania
##### Utworz plik o nazwie program.c
```
touch program.c
```
##### Jakie masz obserwacje? Czy dzialo sie cos "ciekawego" po wcisnieciu klawisza Enter? Po wpisaniu nawiasu? Czy cos sie dzieje z kolorami?
> W vimie po wcisnieciu Enter program przechodzi do kolejnej linijki nie tworzac pustej linii w trybie normalnym, po wpisaniu klamry otwierajacej robi automatyczne wciecia, kolory roznia sie w zaleznosci od tego, czy wpisze sie slowo kluczowe, czy wartosc zmiennej, badz jej typ oraz argumenty funkcji. Podobnie w nano. W mcedit wciecia zaznaczone sa w ten sposob \<------\>. Po wcisnieciu Ctrl+Space w geany powoduje to wlaczenie podpowiedzi mozliwych funkcji/metod w C, ktore moglyby zostac uzupelnione.

##### Teraz zamien pionowe kreski na znaki hash \# i zapisz jako nowy plik o nazwie nowy.c. Wykonaj taka komende w terminalu (tam gdzie masz owe dwa pliki):
```
diff nowy.c program.c
```
```
ubuntu@bss-ubu1804:~/ukos2020-21_14c/s22020-zb/s22020_zad_05$ diff nowy.c program.c 
7,9c7,9
\< 		printf("#                  #\n");
\< 		printf("#     Licze: %d    #\n");
\< 		printf("#                  #\n");
\-\-\-
\> 		printf("|                  |\n");
\> 		printf("|     Licze: %d    |\n");
\> 		printf("|                  |\n");
```
> diff pokazuje w ktorych linijkach sa jakie roznice miedzy jednym plikiem a drugim

##### A teraz jeszcze 
```
diff -y nowy.c program.c
```

```
diff -y nowy.c program.c 
#include <stdio.h>						#include <stdio.h>
#include <stdlib.h>						#include <stdlib.h>

int main(int argc, char **argv) {				int main(int argc, char **argv) {
	for (i = 0; i < 10; i++) {					for (i = 0; i < 10; i++) {
		printf("+------------------+\n");				printf("+------------------+\n");
		printf("#                  #\n");	      |			printf("|                  |\n");
		printf("#     Licze: %d    #\n");	      |			printf("|     Licze: %d    |\n");
		printf("#                  #\n");	      |			printf("|                  |\n");
		printf("+------------------+\n");				printf("+------------------+\n");
	}								}
	return 0;							return 0;
}								}
```
> diff z opcja -y zwraca wynik komendy w dwoch kolumnach - porownywane sa w nich dwa pliki w calosci oraz roznice miedzy nimi 
