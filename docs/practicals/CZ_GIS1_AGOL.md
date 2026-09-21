---
icon: material/numeric-7-box
title: Cvičení 7
---

# ArcGIS Online, webové služby, připojení do ArcGIS Pro

## Cíl cvičení

Náplní cvičení je seznámení s prostředním ArcGIS Online. V rámci cvičení si vyzkoušíte publikaci dat z ArcGIS Pro do ArcGIS Online a jejich využití v opačném směru. Ukážeme si také publikaci standardizovaných mapových služeb pomocí ArcGIS Serveru a to, jak je také lze v prostředí ArcGIS Online využít.

## Základní pojmy

- [**ArcGIS Online**](https://doc.arcgis.com/en/arcgis-online/get-started/get-started.htm) – cloudové prostředí pro ukládání, vizualizaci, tvorbu, správu a vytěžování geografických dat

- **webová služba** – rozhraní, skrze které spolu komunikují servery anebo server & klient; speciálně [webová mapová služba](https://mediaspace.esri.com/media/t/1_05edhhbq) je standard pro komunikaci s tzv. *webovým mapovým serverem* poskytujícím geoprostorová data (mapy, vektorová data, dlaždice, nástroje apod.) prostřednictvím internetu

- **publikace dat** – odeslání lokálně uložené mapové kompozice na server (cloud) a vytvoření datové vrstvy přístupné skrze internet

- [**ArcGIS Server**](https://www.esri.com/en-us/arcgis/products/arcgis-enterprise/overview) – součást řešení ArcGIS Enterprise – vlastní mapový server umožňující publikaci webových mapových služeb

- [**Feature Layer**](https://mediaspace.esri.com/media/t/1_ids5c2qs) – typ dat publikovaných do ArcGIS Online – vektorová vrstva nebo skupina vrstev

- [**Tile Layer**](https://www.esri.com/arcgis-blog/products/sharing-collaboration/sharing-collaboration/best-practices-for-using-tile-layers/) – typ dat publikovaných do ArcGIS Online – rastrová vrstva nebo skupina vrstev využívající dlaždicovou cache pro rychlejší načítání obsahu

- [**kredity**](https://www.esri.com/en-us/arcgis/products/credits/overview) – platební jednotka, pomocí které se uskutečňuje úhrada nákladů za vybrané služby ArcGIS Online (úložiště, geoprocessing, data enrichment, využívání cloudových nástrojů jako je on-line geokódování apod.). Každý student má na začátku alokováno 100 kreditů, aby si mohl vyzkoušet používání služeb, které kredity spotřebovávají

## Použité datové podklady

- data ArcČR 500
- datová sada DATA250 

## Náplň cvičení

### **Vlastní obsah na ArcGIS Online a jeho zveřejnění**

### Vytvořte mapu obcí s rozšířenou působností jednoho z krajů ČR


### Vytvořte webovou mapu v cloudu ArcGIS Online, obsahující silnice, železnice a správní členění vašeho kraje na ORP

### Vyzkoušejte si vytvořit mapovou kompozici kraje s využitím dat z různého umístění



## Úlohy k procvičení

!!! task-fg-color "Úlohy"

    K řešení následují úlohy použijte datovou sadu ArcČR
    500 ve verzi 3.3 a DATA250(oboje dostupné na disku *S* ve složce
    ``K155\Public\data\GIS\``). Zde také případně najdete soubor s
    popisem dat ve formátu PDF. 
    
    1. **Vytvořte mapu obcí s rozšířenou působností jednoho z krajů ČR.**

        Použijte data ORP z datové sady ArcČR
        (ObceSRozsirenouPusobnosti_Polygony), vyexportujte do nové třídy prvků
        pouze zvolený kraj. Mapu doplňte zastavěnými oblastmi obcí nad 5 tisíc
        obyvatel (plošky z třídy prvků POP/BuiltupA datové sady DATA250, které jsou větší než 1,6 ha). Tyto zastavěné plošky neobsahují název obce – připojte pomocí Spatial Join z vrstvy Obce_Polygony.

        Vyexportujte mapu (Share ► Web Layer ► Publish web layer) a umístěte
        na ArcGIS Online do svého umístění. Jako typ zvolte Feature Service,
        nikoli Tile Layer. Můžete nasdílet se skupinou CTU Prague.

        Jednotlivé plochy ORP popište. Barevnost zvolte tak, aby z mapy byla
        zároveň poznat i příslušnost ORP k okresům (ORP jsou do okresů
        skladebné).


    2. **Vyexportujte shapefile silnic a železnic ve vašem kraji.**

        Použijte příslušné vrstvy z ArcČR, ořízněte na velikost kraje.

        Připravte si také vrstvu vodních ploch (VodniPlochy_Polygony),
        ořízněte ji na plochu kraje a uložte do své složky jako shapefile,
        poslouží později.


    3. **Vyzkoušejte si vytvořit mapovou kompozici kraje s využitím dat z různého umístění.**

        V mapové kompozici můžete využívat data umístěná v různých formátech:

        - data z ArcGIS Online nebo z vlastního Portal for ArcGIS,
        - data z WMS, WMTS služeb,
        - data ze služeb ArcGIS Serveru,
        - data z WFS služeb,
        - souborová data uložená jako SHP, CSV, GPX aj.,
        - dynamické vrstvy *Živého atlasu Esri*

    4. **Vyzkoušejte si práci s úpravou pop-up (kontextového menu s atributy, které se zobrazí po  kliknutí), s nastavením stylu apod.**
