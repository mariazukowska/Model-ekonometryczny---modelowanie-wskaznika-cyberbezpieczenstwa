# Model-ekonometryczny---modelowanie-wskaznika-cyberbezpieczenstwa

## Wykorzystane pakiety
Python (Pandas, NumPy)

Statsmodels (regresja i testy diagnostyczne)

Seaborn & Matplotlib (wizualizacja danych)

Stargazer (prezentacja tabelaryczna wyników)

Celem projektu jest zidentyfikowanie i oszacowanie wpływu wybranych czynników społeczno-gospodarczych na poziom cyberbezpieczeństwa państw, mierzonego wskaźnikiem Global Cybersecurity Index (GCI) w roku 2024. Analiza została przeprowadzona na zbiorze danych obejmującym kraje z całego świata, z wykorzystaniem modeli regresji liniowej (OLS) oraz ważonej metody najmniejszych kwadratów (WLS).

## Zmienne w modelu
Zmienna objaśniana: Wskaznik_cyberbezpieczenstwa (GCI 2024).

Zmienne objaśniające:

E-Government Index: Poziom cyfryzacji administracji publicznej.

CPI_2024: Corruption Perception Index (Wskaźnik postrzegania korupcji).

PSAA_2024: Stabilność polityczna i brak przemocy.

URBANIZATION_2024: Procent ludności miejskiej.

log_TRADE & log_UNEMPLOYMENT: Zmienne kontrolne w formie logarytmicznej.

PFI_Score: Wskaźnik wolności prasy.

FOREIGN_2024: Napływ bezpośrednich inwestycji zagranicznych (% PKB)

## Przygotowanie danych (Data Cleaning)
Połączenie wielu baz danych (Bank Światowy, Transparency International) po kodach ISO3.

Wykorzystanie biblioteki country_converter do ujednolicenia nazewnictwa państw.

Imputacja brakujących danych metodą "Backfill" (uzupełnianie braków z 2024 roku danymi z lat 2020–2023).

## Selekcja zmiennych i transformacje
Wstępna analiza korelacji (Heatmapa, Pairplot).

Zastosowanie logarytmowania dla zmiennych o silnej asymetrii (TRADE, UNEMPLOYMENT, CPI).

Wykrycie i usunięcie obserwacji odstających (Outliers) na podstawie Odległości Cooka (np. Malediwy, Tanzania).

## Diagnostyka modelu
Test RESET: Wykazał nieliniowość formy funkcyjnej, co doprowadziło do wyboru modelu log-liniowego.

Test Breuscha-Pagana & White'a: Wykryto problem heteroskedastyczności (zmienność wariancji składnika losowego).

Normalność reszt: Test Jarque-Bera wskazał na brak rozkładu normalnego, jednak ze względu na dużą liczebność próby (N), odwołano się do Centralnego Twierdzenia Granicznego (CTG).

## Finalna Estymacja (WLS)
W celu uzyskania efektywnych estymatorów przy stwierdzonej heteroskedastyczności, zastosowano Ważoną Metodę Najmniejszych Kwadratów (WLS).

## Główne wnioski
E-Government Index oraz CPI (korupcja) mają najsilniejszy, statystycznie istotny wpływ na poziom cyberbezpieczeństwa kraju.

Zależność między kontrolą korupcji a cyberbezpieczeństwem ma charakter logarytmiczny – wzrost transparentności daje największe efekty w krajach o początkowo niskich standardach.

Stabilność polityczna (PSAA) oraz stopień urbanizacji również sprzyjają budowaniu cyfrowych systemów obronnych.
