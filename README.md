Wstęp do programowania w C - końcowy projekt.
==============

Temat
--------------
Makrogenerator (preprocesor), który rozpoznaje i przetwarza jednowierszowe dyrektywy #include i #define, 
a w pozostałym tekście rozpoznaje makrowywołania i zastępuje je rozwinięciami makrodefinicji z #define. 
Uwzględnić należy makrodefinicje z parametrami i bez. Wynikiem programu powninien być przetworzony przez 
makrogenerator tekst (bez dyrektyw i z rozwiniętymi makrowywołaniami).

Pierwsze użycie
--------------
Zainstaluj program używając polecenia make.
Sprawdź, czy w pliku include.dat na pewno znajdują się ścieżki do podstawowych oraz dodanych plików nagłówkowych.
W razie problemu ze znalezieniem potrzebnych ścieżek do plików nagłówkowych polecam spróbować wyszukać ją używając komendy `gcc` z flagą `-M`.

Użytkowanie
--------------
Po uruchomieniu programu podaj nazwy lub ścieżki pliku wejściowego i wyjściowego.
Można je również przekazać jako argumenty uruchomienia.

Opis działania
--------------
Program wczytuje kolejne linie z pliku wejśiowego. Jeżeli dana linia jest podzialona na kilka to na czas obróbki zostaje połączona w jedną.  
Następnie sprawdza, czy dana linia zaczyna się od słowa kluczwowego.   
Jeżeli jest to słowo **#define**, to program dodaje nową definicjie do listy już znanych.  
Jeżeli jest to słowo **#include**, to program uruchomi się rekurencyjnie dla danego pliku nagłówkowego.   
Jeżeli nie jest to żadne ze słów kluczowych, to program przepisze podaną linię po uprzednim rozwnięciu makrowywołań.   
Dodatkowo program usuwa wszystkie znalezione po drodze komentarze.

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