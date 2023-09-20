# 155GISE

[Project Homepage](https://k155cvut.github.io/gise/)

[MkDocs Material dokumentace](https://squidfunk.github.io/mkdocs-material/)

[Markdown dokumentace](https://www.markdownguide.org/basic-syntax/)

[How To Create STUNNING Code Documentation With MkDocs Material Theme](https://www.youtube.com/watch?v=Q-YA_dA8C20&t=767s)

**Formátování**

- **Funkce** – velká písmena + kurzíva: _CLIP RASTER_
- **Vrstvy** – kurzíva: _KrajeBody_
- **Tlačítka a názvy sekcí** – kurzíva: _Add Control Points_, _Catalog_
- **Pevná mezera** – alt + 0160
- **Pomlčka** – alt+0150

- Celkově psát text stylem "Importujeme data ze souboru" a NE "Importovat data ze souboru" (zkrátka snažit se nepoužívat trpný rod, aby dokumentace vypadala přívětivěji a ne jako diplomka)

**Struktura**

- .github/workflows/ci.yml - konfigurační soubor GitHub
- docs
  - assets - obrázky a jiná média k jednotlivýcm cvičení
  - cviceni - Markdown soubory (.md) s obsahem cvičení
  - cviceni.md - záložka se všemi cvičeními se složky cviceni
  - data.md - záložka s informacemi o daty, na které se odkazuje z obsahu cvičení
  - hodnoceni.md - hodnocení domácích úloh
  - index.md - úvodní záložka zobrazená po načtení web. stránky, obsahuje základní info o předmětu, doporučenou literuru, harmonogram přednášek
  - semestralka.md - zadání semestrální práce
  - videa.md - seznam videí na podporu výuky
- .gitignore - soubor ignorovaných souborů při sledování změn při verzování
- LICENSE
- mkdocs.yml - konfigurační soubor MkDocs Material pluginu: nízev stránky, navigace, pluginy, nastavení motivu, lokalizace, další rozšíření..
- README.md

**Instalace**

1. Naklonování repozitáře na lokální zařízení (GitHub Desktop / GitHub CLI - nutná instalace)
   ```
   git clone https://github.com/k155cvut/gise.git
   ```
2. Otevřít naklonovanou složku ve VSCode
   ```
   cd gise
   code .
   ```
3. Otevřít terminál ve VSCode (CTRL + SHIT + ;)
4. Instalace MkDocs Material
   ```
   pip install mkdocs-material --user
   ```
5. Instalace MkDocs Glightbox pluginu
   ```
   pip install mkdocs-glightbox
   ```
7. Spuštění lokálního webového serveru (sleduje změny v kódu a znovu generuje stránku)
   ```
   python -m mkdocs serve
   ```
   http://127.0.0.1:8000/ (nemusí být stejný)

8. Nahrát změny na GitHub
   v GitHub desktop nebo pomocí GitHub CLI v terminálu:
   ```
   git add .
   git commit -m $'popis změn v kódu od posledního commitu'
   git push origin main
   ```

