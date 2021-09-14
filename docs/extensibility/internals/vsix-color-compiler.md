---
title: Compilatore colori VSIX | Microsoft Docs
description: Informazioni sullo strumento compilatore colori Visual Studio estensione, ovvero un'applicazione console che copre i colori Visual Studio temi in un file con estensione pkgdef.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 99395da7-ec34-491d-9baa-0590d23283ce
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 1c724dae82bb8f7f05c83c96d1c331d72eac0abd
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627263"
---
# <a name="vsix-color-compiler"></a>Compilatore dei colori VSIX
Lo strumento Visual Studio Extension Color Compiler è un'applicazione console che accetta un file .xml che rappresenta i colori per i temi Visual Studio esistenti e lo copre in un file con estensione pkgdef in modo che tali colori possano essere usati in Visual Studio. Poiché è facile confrontare le differenze tra i file .xml, questo strumento è utile per la gestione dei colori personalizzati nel controllo del codice sorgente. Può anche essere collegato in ambienti di compilazione in modo che l'output della compilazione sia un file con estensione pkgdef valido.

 **Schema XML del tema**

 Un file di .xml completo è simile al seguente:

```xml
<Themes>
      <!—one or Theme elements -->
      <Theme>
        <!-- one or more Category elements -->
        <Category>
          <!-- one or more Color elements -->
          <Color>
            <!-- zero or one Background element -->
            <Background />
            <!-- zero or one Foreground element -->
            <Foreground />
          </Color>
        </Category>
      </Theme>
</Themes>
```

 **Tema**

 \<Theme>L'elemento definisce un intero tema. Un tema deve contenere almeno un \<Category> elemento . Gli elementi del tema sono definiti nel modo seguente:

```xml
<Theme Name="name" GUID="guid">
      <!-- one or more Category elements -->
</Theme>
```

|**Attributo**|**Definition**|
|-|-|
|Nome|[Obbligatorio] Nome del tema|
|GUID|[Obbligatorio] GUID del tema (deve corrispondere alla formattazione GUID)|

 Quando si creano colori personalizzati Visual Studio, è necessario definire tali colori per i temi seguenti. Se non esistono colori per un particolare tema, Visual Studio tenta di caricare i colori mancanti dal tema Chiaro.

|**Nome del tema**|**GUID tema**|
|-|-|
|Chiaro|{de3dbbcd-f642-433c-8353-8f1df4370aba}|
|Scuro|{1ded0138-47ce-435e-84ef-9ec1f439b749}|
|Blu|{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}|
|Contrasto elevato|{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}|

 **Categoria**

 \<Category>L'elemento definisce una raccolta di colori in un tema. I nomi delle categorie forniscono raggruppamenti logici e devono essere definiti nel modo più ristretto possibile. Una categoria deve contenere almeno un \<Color> elemento. Gli elementi categoria sono definiti nel modo seguente:

```xml
<Category Name="name" GUID="guid">
      <!-- one or more Color elements -->
 </Category>
```

|**Attributo**|**Definition**|
|-|-|
|Nome|[Obbligatorio] Nome della categoria|
|GUID|[Obbligatorio] GUID della categoria (deve corrispondere alla formattazione GUID)|

 **Colore**

 \<Color>L'elemento definisce un colore per un componente o uno stato dell'interfaccia utente. Lo schema di denominazione preferito per un colore è [tipo di interfaccia utente] [Stato]. Non usare la parola "colore" perché è ridondante. Un colore deve indicare chiaramente il tipo di elemento e le situazioni, o "stato", per cui verrà applicato il colore. Un colore non deve essere vuoto e deve contenere uno o entrambi gli elementi \<Background> \<Foreground> e . Gli elementi color sono definiti nel modo seguente:

```xml
<Color Name="name">
        <Background /> <!-- zero or one Background element -->
        <Foreground /> <!-- zero or one Foreground element -->
 </Color>
```

|**Attributo**|**Definition**|
|-|-|
|Nome|[Obbligatorio] Nome del colore|

 **Sfondo e/o primo piano**

 Gli elementi e definiscono il valore e il tipo di un colore \<Background> per lo sfondo o il primo piano di un elemento \<Foreground> dell'interfaccia utente. Questi elementi non hanno elementi figlio.

```xml
<Background Type="type" Source="int" />
<Foreground Type="type" Source="int" />
```

|**Attributo**|**Definition**|
|-|-|
|Tipo|[Obbligatorio] Tipo di colore. I possibili valori sono i seguenti:<br /><br /> *CT_INVALID:* Il colore non è valido o non è impostato.<br /><br /> *CT_RAW:* Valore ARGB non elaborato.<br /><br /> *CT_COLORINDEX:* NON USARE.<br /><br /> *CT_SYSCOLOR:* Colore Windows di sistema di SysColor.<br /><br /> *CT_VSCOLOR:* Colore Visual Studio da __VSSYSCOLOREX.<br /><br /> *CT_AUTOMATIC:* Colore automatico.<br /><br /> *CT_TRACK_FOREGROUND:* NON USARE.<br /><br /> *CT_TRACK_BACKGROUND:* NON USARE.|
|Source (Sorgente)|[Obbligatorio] Valore del colore rappresentato in formato esadecimale|

 Tutti i valori supportati dall__VSCOLORTYPE enumere sono supportati dallo schema nell'attributo Type. Tuttavia, è consigliabile usare solo CT_RAW e CT_SYSCOLOR.

 **Tutti insieme**

 Questo è un semplice esempio di un file di .xml valido:

```xml
<Themes>
  <Theme Name="Light" GUID="{de3dbbcd-f642-433c-8353-8f1df4370aba}">
    <Category Name="MyCategory" GUID="{0A96238B-70CE-4479-9170-EECEAA3FCD58}">
      <Color Name="MyActiveBorder">
        <Background Type="CT_RAW" Source="FFCCCEDB" />
      </Color>
    </Category>
  </Theme>
</Themes>
```

## <a name="how-to-use-the-tool"></a>Procedura: utilizzare lo strumento
 **Sintassi**

 VsixColorCompiler \<XML file> \<PkgDef file>\<Optional Args>

 **Argomenti**

|**Nome del commutatore**|**Note**|**Obbligatorio o facoltativo**|
|-|-|-|
|Senza nome (.xml file)|Si tratta del primo parametro senza nome e del percorso del file XML da convertire.|Necessario|
|Senza nome (file con estensione pkgdef)|Si tratta del secondo parametro senza nome ed è il percorso di output per il file con estensione pkgdef generato.<br /><br /> Impostazione predefinita: \<XML Filename> .pkgdef|Facoltativo|
|/noLogo|L'impostazione di questo flag impedisce la stampa delle informazioni sul prodotto e sul copyright.|Facoltativo|
|/?|Stampare le informazioni della Guida.|Facoltativo|
|/help|Stampare le informazioni della Guida.|Facoltativo|

 **Esempi**

- VsixColorCompiler D:\xml\colors.xml D:\pkgdef\colors.pkgdef

- VsixColorCompiler D:\xml\colors.xml /noLogo

## <a name="notes"></a>Note

- Questo strumento richiede l'installazione della versione più recente VC++ runtime di .

- Sono supportati solo singoli file. La conversione in blocco tramite percorsi di cartella non è supportata.

- Lo strumento è disponibile in `<VS Install Path>\VSSDK\VisualStudioIntegration\Tools\Bin\`

## <a name="sample-output"></a>Output di esempio
 Il file con estensione pkgdef generato dallo strumento sarà simile alle chiavi seguenti:

```
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\Environment]
"Data"=hex:3a,00,00,00,0b,00,00,00,01,00,00,00,c3,d9,4e,62,fd,bd,fa,41,96,c3,7c,82,4e,a3,2e,3d,01,00,00,00,0c,00,00,00,41,63,74,69,76,65,42,6f,72,64,65,72,01,cc,ce,db,ff,01,33,31,24,ff

[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\TreeView]
"Data"=hex:38,00,00,00,0b,00,00,00,01,00,00,00,8e,f0,ec,92,13,8b,f4,4c,99,e9,ae,26,92,38,21,85,01,00,00,00,0a,00,00,00,42,61,63,6b,67,72,6f,75,6e,64,01,f5,f5,f5,ff,01,1e,1e,1e,ff
```
