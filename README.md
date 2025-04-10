Instrukcje
# Model - reguła decyzyjna

Napisz serwis API który obsługiwał będzie jeden adres `/api/v1.0/predict` i przyjmował dwie liczby.
jeśli użytkownik nie poda liczby powinna wstawić się wartość 0
Zdefiniuj model jako regułę:
- jeśli suma dwóch liczb jest większa niż 5.8 zwróć jako predykcję wartość 1
- w przeciwnym razie zwróć 0

Cała podstrona powinna zwracać słownik zawierający dwa klucze
"prediction", oraz "features" z wypisaniem odpowiedniej informacji zwrotnej.

Aplikację wystaw jako kod w repozytorium na swoim koncie Github 
- skonteneryzuj aplikację tak aby można ją było uruchomić w dockerze 

W odpowiedzi prześlij adres repozytorium GIT
