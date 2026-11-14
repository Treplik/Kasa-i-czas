# Kasa&Czas

Osobisty budżet w jednym pliku HTML, bez serwera i bez instalacji. Działa w przeglądarce na telefonie i komputerze.

Zakładki: Przegląd, Kalendarz pracy, Budżet, Paliwo, Cele i długi, Skarbonka, Schodki (oszczędzanie z losowaniem kwoty), Ustawienia oraz opcjonalna Wysyłka (podział kosztu paczki). Aplikacja ma tryb jasny i ciemny, cztery motywy kolorów, serię dni, odznaki, eksport do CSV i JSON.

W zakładce **Paliwo** jest moduł **Kalkulator trasy i spalania**: mapa, trasa po prawdziwych drogach z alternatywami, czas, dystans, szacowane spalanie i koszt oraz historia tras.

## Publikacja na GitHub Pages

1. Zaloguj się na github.com i wybierz **+** → **New repository**.
2. Nazwa: np. `kasa-i-czas`. Widoczność: **Public** (na darmowym koncie GitHub Pages działa tylko dla publicznych repozytoriów). Kliknij **Create repository**.
3. W nowym repozytorium wybierz **Add file** → **Upload files** i wgraj plik `index.html` (nazwa musi być dokładnie taka) oraz opcjonalnie `README.md`. Zatwierdź przyciskiem **Commit changes**.
4. Wejdź w **Settings** → **Pages**. W sekcji „Build and deployment” ustaw **Source: Deploy from a branch**, **Branch: main**, folder **/ (root)** i kliknij **Save**.
5. Po chwili (GitHub podaje do 10 minut) strona będzie pod adresem `https://TWOJ-LOGIN.github.io/kasa-i-czas/`.
6. Na iPhonie: otwórz adres w Safari → **Udostępnij** → **Do ekranu początkowego**. Na Androidzie: menu przeglądarki → **Dodaj do ekranu głównego**.

### Aktualizacja

Wgraj nowy `index.html` tą samą drogą (**Add file** → **Upload files**). Plik o tej samej nazwie zastąpi stary, a strona odświeży się po chwili.

## Gdzie są dane

- Wszystkie dane (wydatki, godziny, paliwo, historia tras, ustawienia) zapisują się **tylko w przeglądarce** na danym urządzeniu (localStorage). Nie trafiają do repozytorium.
- Telefon i komputer mają osobne dane. Wyczyszczenie danych witryny w przeglądarce je usuwa.
- Kopię zapasową zrobisz w **Ustawienia** → **Pobierz kopię (.json)**, a przywrócisz przez **Wczytaj kopię zapasową**.
- Repozytorium jest publiczne, więc każdy może zobaczyć kod strony, ale nie Twoje wpisy.
- Plik zawiera przykładowe dane demo. Możesz je usunąć w **Ustawienia** → **Usuń wszystkie dane**.

## Kalkulator trasy i spalania

Moduł korzysta z darmowych, publicznych usług, bez kluczy API:

| Do czego | Usługa |
| --- | --- |
| Mapa | Leaflet + kafelki OpenStreetMap |
| Wyszukiwanie miejscowości | Nominatim (OpenStreetMap), tylko Polska |
| Trasa i alternatywy | OSRM (publiczny serwer demonstracyjny) |

- Usługi mają limity i zasady użycia ([Nominatim](https://operations.osmfoundation.org/policies/nominatim/), [kafelki OSM](https://operations.osmfoundation.org/policies/tiles/)). Do osobistego użytku wystarczą. Nominatim odradza podpowiedzi w trakcie pisania, więc aplikacja wysyła zapytanie dopiero po 1 sekundzie od ostatniego znaku i nie częściej niż raz na sekundę. Przy intensywnym użyciu warto postawić własny serwer albo skorzystać z płatnego dostawcy.
- Czas przejazdu z OSRM bywa niższy niż w praktyce, bo model nie zna korków.
- Spalanie to **szacunek (około ±15%)**. Liczone jest osobno dla dróg miejskich (~50 km/h), krajowych (~90 km/h) i ekspresowych oraz autostrad (~120 km/h), ze stawek, które ustawiasz sam. Nie uwzględnia ruchu, wzniesień ani stylu jazdy. Domyślne liczby (7,5 / 5,0 / 6,0 l/100 km) są tylko przykładem. Wpisz spalanie swojego auta w **Ustawienia auta, spalania i ceny paliwa**.
- Gdy usługi są niedostępne (brak sieci, blokada reklam, limit zapytań), użyj **trybu ręcznego** albo przycisku **Sprawdź w Mapach Google** i przepisz dystans.
- Podpis „© współtwórcy OpenStreetMap” na mapie jest wymagany licencją danych. Zostaw go.

## Pierwszy test po publikacji

Wejdź w **Paliwo** → **Kalkulator trasy i spalania**, wpisz **Skąd**: `Myjomice`, **Dokąd**: `Kraszewice` i kliknij **Wyznacz trasę**. Jeśli mapa jest pusta albo pojawia się błąd, otwórz stronę w zwykłej przeglądarce (nie w podglądzie wewnątrz innej aplikacji) i spróbuj ponownie.
