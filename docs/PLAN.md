# Plan projektu

## Etap 0. Przygotowanie
- [x] Repozytorium na GitHubie, README, opis
- [x] Środowisko Python 3.12 (.venv), requirements.txt
- [x] Akceptacja tematu przez prowadzącego
- [x] Usunięcie plików CEPiK (src/explore_cepik.py, src/cepik_session.py)
- [x] Usunięcie `data/raw/` z .gitignore (pliki są małe, więc trzymamy je w repozytorium)
- [ ] Utworzenie `docs/data_sources.md`

## Etap 1. Pozyskanie danych
- [ ] Eurostat `road_eqr_carpda` → data/raw/eurostat/nowe_rejestracje.csv
- [ ] Eurostat `road_eqs_carpda` → data/raw/eurostat/park_samochodow.csv
- [ ] Eurostat `nama_10_pc` → data/raw/eurostat/pkb_per_capita.csv
- [ ] GUS BDL: rozpoznanie, czy są samochody według rodzaju paliwa (lata, poziom: województwa/powiaty)
- [ ] GUS BDL: eksport pojazdów według paliwa → data/raw/gus/
- [ ] GUS BDL: eksport ludności, wynagrodzeń, gęstości zaludnienia → data/raw/gus/
- [ ] EIPA: stacje ładowania według województw (opcjonalnie)
- [ ] Granice województw/powiatów (GeoJSON) → data/raw/geo/
- [ ] Wpis każdego źródła w docs/data_sources.md: link, kod tabeli, data pobrania, opis kolumn

## Etap 2. Wczytanie i wstępna inspekcja (notebook, sekcja 1–2)
- [ ] Notebook notebooks/eda_elektromobilnosc.ipynb z sekcjami (nagłówki markdown)
- [ ] Wczytanie wszystkich plików
- [ ] Dla każdego zbioru: shape, head, dtypes, info, describe
- [ ] Opis znaczenia kolumn i kodów (np. mot_nrg, geo)
- [ ] Typy danych: kategoryczne, porządkowe, liczbowe

## Etap 3. Czyszczenie i ujednolicenie (sekcja 3)
- [ ] Zamiana formatu szerokiego (lata w kolumnach) na długi (melt)
- [ ] Ujednolicenie nazw kolumn, typów, kodów krajów i regionów
- [ ] Mapowanie kategorii napędu na grupy: BEV, PHEV, HEV, benzyna, diesel, LPG, inne
- [ ] Braki danych: ile, gdzie, dlaczego, decyzja (usunięcie / uzupełnienie / pozostawienie) z uzasadnieniem
- [ ] Duplikaty
- [ ] Połączenie zbiorów (merge po kraju i roku, po regionie i roku)
- [ ] Zapis czystych danych → data/processed/

## Etap 4. Statystyki opisowe i rozkłady (sekcja 4)
- [ ] Średnia, mediana, kwantyle, wariancja, odchylenie standardowe dla kluczowych zmiennych
- [ ] Histogramy i wykresy pudełkowe udziałów EV
- [ ] Opis kształtu rozkładu (skośność), ewentualna transformacja logarytmiczna

## Etap 5. Obserwacje odstające (sekcja 5)
- [ ] Wykrycie: IQR, z-score, wykresy pudełkowe
- [ ] Interpretacja (np. Norwegia, duże miasta, Warszawa przez rejestracje flotowe)
- [ ] Decyzja i uzasadnienie

## Etap 6. Analiza i odpowiedzi na pytania badawcze (sekcja 6)
- [ ] P1: trend udziału BEV i PHEV w Polsce (nowe rejestracje i park)
- [ ] P2: Polska na tle UE, ranking krajów, korelacja z PKB per capita
- [ ] P3: różnice regionalne, korelacje z wynagrodzeniem, urbanizacją, ładowarkami
- [ ] P4: zmiany rok do roku w latach programów dopłat
- [ ] Macierz korelacji (Pearson i Spearman) z interpretacją
- [ ] Mapy choropletyczne regionów

## Etap 7. Przygotowanie danych pod ML (sekcja 7)
- [ ] Inżynieria cech: udziały procentowe, wskaźniki na mieszkańca, dynamika r/r, interakcje
- [ ] Wybór cech z uzasadnieniem
- [ ] Kodowanie zmiennych kategorycznych (one-hot) i porządkowych
- [ ] Normalizacja i standaryzacja (StandardScaler, MinMaxScaler) z porównaniem
- [ ] Podział train/test
- [ ] Model bazowy (regresja liniowa) jako dowód, że dane są gotowe
- [ ] Raport ydata-profiling → reports/profiling.html
- [ ] Zapis gotowego zbioru → data/processed/ml_ready.csv

## Etap 8. Dashboard
- [ ] Wybór narzędzia: Streamlit (aplikacja) lub Plotly (interaktywne wykresy w HTML)
- [ ] 3–5 widoków: trend w Polsce, porównanie UE, mapa regionów, filtry (rok, typ napędu)
- [ ] Plik app/dashboard.py, instrukcja uruchomienia w README

## Etap 9. Finalizacja
- [ ] Podsumowanie i wnioski na końcu notebooka
- [ ] Ograniczenia danych opisane w notebooku i README
- [ ] Najlepsze wykresy w reports/figures/ i w README
- [ ] README: sekcja „Key findings”, instrukcja uruchomienia, struktura repozytorium
- [ ] Restart & Run All, czy notebook działa od zera
- [ ] Prezentacja na obronę (5–10 slajdów)
- [ ] Oddanie projektu