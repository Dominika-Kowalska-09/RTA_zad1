# API z Regułą Decyzyjną
Przegląd
Projekt implementuje prosty serwis API, który stosuje regułę decyzyjną opartą na sumie dwóch podanych liczb. Aplikacja jest skonteneryzowana przy użyciu Dockera dla łatwego wdrożenia i testowania.

Funkcje
- Endpoint REST API przyjmujący dwa parametry liczbowe
- Implementacja reguły decyzyjnej: zwraca 1, jeśli suma wejść jest większa niż 5.8, w przeciwnym razie zwraca 0
- Obsługa wartości domyślnych: jeśli parametry nie są podane, przyjmują wartość 0
- Formatowanie odpowiedzi JSON z wynikiem predykcji i wejściowymi cechami
- Obsługa błędów dla kodów statusu 404 i 400
- Aplikacja skonteneryzowana przy użyciu Dockera

Użyte technologie
- Python 3.11
- Flask 3.0.3
- Docker

Endpointy API
Endpoint główny:
- URL: /
- Metoda: GET
- Odpowiedź: Komunikat powitalny z podstawowymi instrukcjami użycia

Endpoint predykcji:
- URL: /api/v1.0/predict
- Metoda: GET
- Parametry URL:
num1 (opcjonalny): Pierwsza liczba wejściowa (domyślnie: 0)
num2 (opcjonalny): Druga liczba wejściowa (domyślnie: 0)

Format odpowiedzi:
json{
  "prediction": 0 lub 1,
  "features": {
    "num1": wartość_wejściowa_1,
    "num2": wartość_wejściowa_2
  }
}

Reguła decyzyjna: Jeśli num1 + num2 > 5.8, predykcja = 1, w przeciwnym razie predykcja = 0

Instalacja i uruchamianie
Konfiguracja lokalna:
1. Sklonuj to repozytorium:
git clone https://github.com/Dominika-Kowalska-09/RTA_zad1.git
cd RTA_zad1
2. Zainstaluj wymagane pakiety:
pip install -r requirements.txt
3. Uruchom aplikację:
python app.py
4. API będzie dostępne pod adresem http://localhost:5003

Konfiguracja Docker:
1. Zbuduj obraz Docker:
docker build -t decision-rule-api .
2. Uruchom kontener Docker:
docker run -p 5003:5003 decision-rule-api
3. API będzie dostępne pod adresem http://localhost:5003

Testowanie API
Możesz przetestować API, wysyłając żądania GET do endpointu predykcji z różnymi wartościami parametrów:
- Podstawowy test (suma > 5.8, powinien zwrócić prediction=1):
http://localhost:5003/api/v1.0/predict?num1=3&num2=4
- Test z sumą < 5.8 (powinien zwrócić prediction=0):
http://localhost:5003/api/v1.0/predict?num1=2&num2=3
- Test z wartościami domyślnymi (powinien zwrócić prediction=0):
http://localhost:5003/api/v1.0/predict


Struktura projektu
- app.py: Główny plik aplikacji zawierający implementację API Flask
- requirements.txt: Zależności Pythona
- Dockerfile: Instrukcje do konteneryzacji aplikacji
- README.md: Dokumentacja projektu
