# Cvičení

## Cvičení 1

<span style="font-size:2em;">Úvod do práce v prostředí ArcGIS, datové formáty, geodatabáze
</span>

### Cíl cvičení

### Základní pojmy

### Použité datové podklady

### Náplň cvičení

### Zadání domácího úkolu k semestrální práci

## Cvičení 2

<span style="font-size:2em;">Vektorová data, atributové dotazy, prostorové dotazy

</span>

### Cíl cvičení

### Základní pojmy

### Použité datové podklady

### Náplň cvičení

### Zadání domácího úkolu k semestrální práci

## Cvičení 3

<span style="font-size:2em;">Prostorové funkce (geoprocessing), spatial join

</span>

### Cíl cvičení

### Základní pojmy

### Použité datové podklady

### Náplň cvičení

### Zadání domácího úkolu k semestrální práci

## Cvičení 4

<span style="font-size:2em;">Souř. připojení prostorových dat (práce s externími daty Excel, CSV), join
</span>

### Cíl cvičení

### Základní pojmy

### Použité datové podklady

### Náplň cvičení

### Zadání domácího úkolu k semestrální práci

## Cvičení 5

<span style="font-size:2em;">Rastrová data, georeference - zkušební cvičení
</span>

### Cíl cvičení

Seznámení se s rastrovými daty v GISu a ukázka využití těchto dat. Souřadnicové připojení rastrových dat. Práce s mosaic dataset.

### Základní pojmy

- **rastr** - datová struktura založená na buňkách uspořádaných do řádek a sloupců, kde hodnota každé buňky reprezentuje hodnotu jevu
  - **rastrová data** - prostorová data vyjádřená formou matice buněk nebo pixelů; spojitá data (nejčastěji digitální modely terénu, digitalizované mapy)
  - **pixel (buňka)** - základní geometrický prvek zpravidla čtvercového tvaru; jeho množina vytváří rastrový digitální obraz; 1 buňka = 1 hodnota
  - **prostorové rozlišení rastru** - velikost 1 buňky (pixelu) rastru (cell size)
  - **digitální model reliéfu (DMR)** - digitální reprezentace zemského povrchu; rastr; neobsahuje lidské stavby
  - **digitální model terénu (DMT)** - digitální reprezentace zemského povrchu; rastr; obsahuje lidské stavby
  - **transformace** - obecný pojem pro výpočet, jehož cílem je převod souřadnic bodů z jednoho souřadnicového systému do druhého
  - **georeference** - proces určení vztahu mezi polohou dat v přístrojovém souřadnicovém systému a geografickou
  - **pyramidování rastru** - ukládání dat do menšího rozlišení pro rychlejší práci; pyramidy (náhledy) jsou uloženy v souborech .ovr

### Použité datové podklady

- [ArcČR 500](../data/#arccr-500)
- [Císařské otisky stabilního katastru](../data/#cisarske-otisky-stabilniho-katastru)
- [DMR 5G](../data/#dmr-5g)
- [RÚIAN](../data/#ruian)

### Náplň cvičení

#### Práce s digitálním modelem reliéfu

**Zdroj dat** - DMR 4G (ArcČR)

1. Načtení DMR 4G z databáze ArcČR (DigitalniModelReliefu)
2. Výběr okresu k ořezu rastru (OkresyPolygony)
3. Export vybraného okresu do samostatné vrstvy - pravý klik na vybranou vrstvu -> Data -> Export Features

<figure markdown>
  ![Export features](../assets/cviceni5/export_features.png "Export features"){ width="800" }
  <figcaption>Export features</figcaption>
</figure>

4. Ořez DMR dle hranic vybraného okresu

   1. [Clip Raster](../videa/#clip-raster) - vytvoří ořez dle nejmenšího ohraničujícího obdélníka

<figure markdown>
![Clip raster](../assets/cviceni5/dmr_clip_raster.png "Clip raster")
    <figcaption>Clip raster</figcaption>
</figure>

2. [Extract by Mask](../videa/#extract-by-mask) - ořízne rastr přesně dle polygonu (s přesností na pixely)

<figure markdown>
![Extract by mask](../assets/cviceni5/dmr_extract_by_mask.png "Extract by mask")
    <figcaption>Extract by mask</figcaption>
</figure>

#### Georeferencování rastru

1. Načtení rastru do mapového okna
2. Zapnutí funkce Georeference: záložka Imagery -> Georeference
3. Postup dle následujícího videa:

<div style="text-align: center;">
<iframe width="560" height="315" src="https://www.youtube.com/embed/H7m7rX9fswE" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
</div>

### Zadání domácího úkolu k semestrální práci

1. Vytvořte ořez DMR 5G pro území zadané obce.
2. Vytvořte bezešvou mozaiku georeferencovaných rastrů císařských otisků stabilního katastru pro území zadané obce.

## Cvičení 6

<span style="font-size:2em;">Vektorizace, tvorba geodatabáze, kontrola topologie

</span>

### Cíl cvičení

### Základní pojmy

### Použité datové podklady

### Náplň cvičení

### Zadání domácího úkolu k semestrální práci

## Cvičení 7

<span style="font-size:2em;">ModelBuilder (opakování všech předchozích cvičení, ale trochu víc automatizovaně), Batch Processing
</span>

### Cíl cvičení

### Základní pojmy

### Použité datové podklady

### Náplň cvičení

### Zadání domácího úkolu k semestrální práci

## Cvičení 8

<span style="font-size:2em;">ArcGIS Online, webové služby, připojení do APRO

</span>

### Cíl cvičení

### Základní pojmy

### Použité datové podklady

### Náplň cvičení

### Zadání domácího úkolu k semestrální práci

## Cvičení 9

<span style="font-size:2em;">Ukázky webové prezentace map, Experience Builder, Instant Apps, Dashboards

</span>

### Cíl cvičení

### Základní pojmy

### Použité datové podklady

### Náplň cvičení

### Zadání domácího úkolu k semestrální práci

## Cvičení 10

<span style="font-size:2em;">QGIS 1
</span>

### Cíl cvičení

### Základní pojmy

### Použité datové podklady

### Náplň cvičení

### Zadání domácího úkolu k semestrální práci

## Cvičení 11

<span style="font-size:2em;">QGIS 2
</span>

### Cíl cvičení

### Základní pojmy

### Použité datové podklady

### Náplň cvičení

### Zadání domácího úkolu k semestrální práci

## Cvičení 12

<span style="font-size:2em;">

</span>

### Cíl cvičení

### Základní pojmy

### Použité datové podklady

### Náplň cvičení

### Zadání domácího úkolu k semestrální práci
