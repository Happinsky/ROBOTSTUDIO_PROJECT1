# Projekt RobotStudio: Symulacja precyzyjnych trajektorii (ABB IRB 120)

Projekt symulacji zrobotyzowanego stanowiska zrealizowany w dwuosobowym zespole. Głównym celem było zaprojektowanie, wymodelowanie i zaprogramowanie bezkolizyjnych ścieżek dla robota przemysłowego z zaawansowanym wykorzystaniem układów współrzędnych obiektu (WorkObjects).

## 🎥 Prezentacja działania
[**▶️ Zobacz nagranie z działania stacji na YouTube**](https://www.youtube.com/watch?v=V7BgrqRQbls)

## 🛠️ Technologie i narzędzia
* **Oprogramowanie:** ABB RobotStudio
* **Robot:** ABB IRB 120 (6 stopni swobody)
* **Język programowania:** RAPID

## 🎯 Zrealizowane założenia techniczne

W ramach projektu zaimplementowano następujące rozwiązania:

* **Konfiguracja niestandardowego narzędzia (Tool):** Zaprojektowano własne, zagięte narzędzie z odpowiednio zdefiniowanym punktem TCP (Tool Center Point). TCP zostało wysunięte o kilka milimetrów poza fizyczną końcówkę w celu zabezpieczenia układu przed kolizjami podczas programowania ścieżek.
* **Zarządzanie układami współrzędnych (`wobj`):** Każdy z detali posiada swój własny, niezależny układ współrzędnych (*workobj*). Targety zostały zdefiniowane względem tych układów, co pozwala na bezproblemową relokację obiektów w przestrzeni bez konieczności ponownego programowania robota.
* **Modelowanie 3D i różnorodne trajektorie:** Stacja zawiera trzy własnoręcznie wymodelowane obiekty, z których każdy wymagał innej techniki prowadzenia narzędzia:
  1. **Obiekt prostoliniowy:** Prowadzenie wzdłuż ostrych krawędzi z zachowaniem wysokiej precyzji.
  2. **Obiekt krzywoliniowy z przeszkodą:** Ścieżka interpolowana kołowo z uwzględnieniem "trudnodostępnego" obszaru i koniecznością omijania przeszkody (wymagająca odpowiedniej orientacji narzędzia).
  3. **Obiekt nieregularny (Spline/Extrude):** Trajektoria generowana swobodnie na gładkiej, nieregularnej powierzchni z zachowaniem stałego dystansu.
* **Optymalizacja ruchu:** Zastosowano zmienne parametry ruchu (`MoveJ`, `MoveL`), płynnie kontrolując prędkości (`v`) oraz strefy dokładności (`z`). Parametry te różnią się w zależności od tego, czy robot przemieszcza się między punktami (ruchy swobodne), czy symuluje proces technologiczny (np. klejenie/spawanie).
* **Bezpieczeństwo:** Pełna obsługa detekcji kolizji. Cykl pracy robota zaczyna się i bezbłędnie kończy w zaprogramowanej pozycji bazowej (Home).

## 🚀 Jak uruchomić projekt?

Cała stacja została wyeksportowana z zachowaniem wszystkich zależności.

1. Pobierz z repozytorium plik z rozszerzeniem `.rspag` (Pack & Go).
2. Uruchom oprogramowanie **ABB RobotStudio**.
3. Z menu głównego wybierz **File** -> **Share** -> **Unpack & Work** (Rozpakuj i pracuj).
4. Wskaż pobrany plik `.rspag` i wybierz folder docelowy.
5. Po załadowaniu stacji, uruchom wirtualny kontroler, przejdź do zakładki **Simulation** i kliknij **Play**.
