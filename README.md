Wstęp do programowania w C. - Projekt zaliczeniowy.
==============

Temat
--------------
Makrogenerator (preprocesor), który rozpoznaje i przetwarza jednowierszowe dyrektywy #include i #define, a w pozostałym tekście rozpoznaje makrowywołania i zastępuje je rozwinięciami makrodefinicji z #define. Uwzględnić należy makrodefinicje z parametrami i bez. Wynikiem programu powninien być przetworzony przez makrogenerator tekst (bez dyrektyw i z rozwiniętymi makrowywołaniami).

Pierwsze użycie
--------------
Zainstaluj program używając polecenia make.
Następnie wpisz w pliku include.txt listę ścieżek do katalogów, w których znajdują się biblioteki. 
Każda z nich powinna być w osobnej linii i zakończona znakiem '/'.

Użytkowanie
--------------
Po uruchomieniu programu podaj nazwę lub ścieżkę pliku wejściowego i wejściowego.

Opis działania
--------------
Program wczytuje kolejne linie z pliku wejśiowego.
Następnie sprawdza, czy dana linia zaczyna się od słowa kluczwowego.
Jeżeli jest to słowo **#define**, to program dodaje ją do listy znanych definicji.
Jeżeli jest to słowo **#include**, to program uruchomi się rekurencyjnie dla danego pliku nagłówkowego.
Jeżeli nie jest to żadne ze słów kluczowych, to program przepisze podaną linię po uprzednim rozwnięciu definicji.

Podział programu na pliki
--------------
1. Plik **preprocesor.c** zawiera funkcję main i główną funkcję przepisującą dany plik wejściowy.
2. Pliki **define.h** i **define.c** zawierają definicje struktury `_define` oraz funkcji umożliwiających jej obsługę:
   * Funkcje umożliwiające inicjalizaje pojedyńczego elelmentu lub całego drzewa struktury.
   * Funkcje umożliwiające usunięcie pojedyńczego elementu lub całego drzewa struktury.
   * Funkcje umożliwiające stworzenie nowego elementu w drzewie.
   * Funkcje umożliwiające przekształcenie danego tekstu przy pomocy podanych wcześniej definicji.
   * Inne funkcje pomocnicze.
3. Pliki **include.h** i **include.c** zawierają definicje struktury `_include` oraz funkcji umożliwiających jej obsługę:
   * Funkcje umożliwiające inicjalizaje pojedyńczego elelmentu lub całego drzewa struktury.
   * Funkcje umożliwiające usunięcie pojedyńczego elementu lub całego drzewa struktury.
   * Funkcje umożliwiające stworzenie nowego elementu w drzewie.
   * Funkcje umożliwiające wywołanie podanego w pliku wejściowym pliku nagłówkowego wywołanie na nim funkcji przepisującej.
   * Inne funkcje pomocnicze.
4. Plik **my_string.c** zawieraja funkcje pomocnicze ułatwiające obsługę napisów.
5. Plik **errors.c** zawieraja definicje funkcji komunikatów błedów.
   
Autor
--------------
Krzysztof Bednarek