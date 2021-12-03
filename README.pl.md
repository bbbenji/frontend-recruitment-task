[English](README.md)

# Zadanie rekrutacyjne na Junior Frontend - Galeria zdjęć NASA Mars

**Proste zadanie sprawdzające Twoje umiejętności w zakresie tworzenia frontendów.** 
### Wymagania/warunki:
* Dowolny, wybrany przez Ciebie framework frontendowy (Vanilla, SolidJS, VueJS, React, itp.)
* Dowolny, wybrany przez Ciebie framework CSS (Bootstrap, Tailwind, Material, itp.) 
* Wybraną bibliotekę galerii lightbox (lightGallery 2.3.* np.)
* Google Fonts Space Grotesk (https://fonts.google.com/specimen/Space+Grotesk)
* Bez użycia jQuery
* Layout powinien być responsywny (desktop/tablet/mobile)
* Wynik Lighthouse > 90%

### Przygotowanie
Zarejestruj się w celu uzyskania darmowego klucza *NASA API* (https://api.nasa.gov/index.html#apply-for-an-api-key), aby uzyskać dostęp do *MARS PHOTOS API* (https://api.nasa.gov/api.html#MarsPhotos)

### Opis zadania.
1. Stwórz i wystylizuj responsywny formularz, który pozwoli użytkownikowi wybrać liczbę zdjęć oraz konkretną datę, dla której Mars rovers wykonały zdjęcia dostarczone, przez API.

**Pola formularza:**
* Liczba zdjęć (min = 1 / max = 50)
* Wybór daty (nie zezwalaj na wybór przyszłej daty)

2. Po przesłaniu formularza, wyniki pobrane z API są wyświetlane w postaci siatki (miniaturki z ID zdjęcia i datą wykonania).

3. Miniaturki powinny być klikane - wyświetlane są następnie na pełnym ekranie/oknie modal z większym obrazem (lightbox).

![Demo](README/demo.gif?raw=true)

[Zrzut ekranu Desktop](README/ss_desktop.png?raw=true)  
[Zrzut ekranu Mobile](README/ss_mobile.png?raw=true)  
[Lighthouse Desktop](README/lh_desktop.png?raw=true)  
[Lighthouse Mobile](README/lh_mobile.png?raw=true)

**Po ukończeniu, prześlij na swoje konto Github lub Gitlab z prostymi instrukcjami i podaj nam link.**