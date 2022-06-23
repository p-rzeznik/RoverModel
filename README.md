# RoverModel

## Opis
Modelowanym zagadnieniem jest łazik marsjański, którego celem jest dotarcie do wyznaczonego punktu omijając przy tym przeszkody. Na bieżąco uaktualnia mapę przeszkód na podstawie obrazu z kamer i danych z czujników.
Będzie składać się z:
 - komputera pokładowego
 - komputera sterującego
 - modułu komunikacyjnego
 - kamer monitorujących otoczenie
 - czujników zbliżeniowych do wykrywania przeszkód w bliskiej odległości
 - silników elektrycznych po jednym na każde koło

## Spis komponentów z komentarzem
 - Magistrala komunikacyjna - łączy wszystkie fizyczne komponenty.
 - Urządzenia:
    - Silnik(x4) - silniki elektryczne pozwalające łazikowi na poruszanie się.
    - Kamera(x2) - kamery nawigacyjne pozwalające na stworzenie mapy otoczenia
    - Czujniki zbliżeniowe(x6) - czujniki pozwalające uszczegółowienie mapy w najbliższym otoczeniu łazika
    - Antena - antena pozwalająca na komunikację. Z jej pomocą są przekazywane współrzędne miejsca do którego ma dotrzeć łazik.
 - Procesory:
    - Procesor komputera pokładowego - procesor odpowiedzialny za odbieranie i przetwarzanie danych oraz tworzenie map.
    - Procesor modułu sterowania - procesor odpowiedzialny za obliczanie optymalnej trasy i sterowanie łazikiem.

 - Procesy:
    - Główny proces komputera pokładowego:
główny wątek - uaktualnia mapę globalną na podstawie aktualnej mapy najbliższego otoczenia.
wątek odbierający dane z anteny - odbiera informacje nadawane z Ziemi.
    - Proces przetwarzający obraz na mapę - przetwarza obraz z kamer i dane z czujników na mapę.
    - Proces sterujący silnikami w kołach - oblicza optymalną trasę i steruje silnikami w kołach.

## Model - rysunek

![](Diagram2.png?raw=true "Diagram")

## Proponowane metody analizy modelu, dostępne w Osate
### Check connection binding consistency
Nie wykryto braku spójności połączeń.

### Check flow latency
Ta analiza mogłaby być pomocna w szacowaniu czasu wykonania cyklu pracy łazika (odebranie danych dotyczących celu → stworzenie mapy otoczenia → wyznaczenie trasy i ruch → aktualizacja mapy otoczenia → wyznaczenie trasy i ruch … → dotarcie do celu) oraz w wyznaczaniu możliwych opóźnień. Taka analiza pomogłaby ustalić kiedy łazik najszybciej radziłby sobie ze swoim zadaniem.