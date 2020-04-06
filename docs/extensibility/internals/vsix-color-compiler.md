---
title: Compilatore di colori VSIX Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 99395da7-ec34-491d-9baa-0590d23283ce
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f414a56bb05a23b6efef19aa7c99292b8a40038a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703893"
---
# <a name="vsix-color-compiler"></a>Compilatore dei colori VSIX
Lo strumento Visual Studio Extension Color Compiler è un'applicazione console che accetta un file XML che rappresenta i colori per i temi di Visual Studio esistenti e lo converte in un file con estensione pkgdef in modo che tali colori possano essere utilizzati in Visual Studio. Poiché è facile confrontare le differenze tra i file XML, questo strumento è utile per la gestione di colori personalizzati nel controllo del codice sorgente. Può anche essere collegato in ambienti di compilazione in modo che l'output della compilazione sia un file con estensione pkgdef valido.

 **Schema XML del tema**

 Un file .xml a tema completo è simile al seguente:A complete theme .xml file looks like this:

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

 L'elemento \<Theme> definisce un intero tema. Un tema deve contenere \<almeno un elemento di> Category. Gli elementi del tema sono definiti in questo modo:

```xml
<Theme Name="name" GUID="guid">
      <!-- one or more Category elements -->
</Theme>
```

|||
|-|-|
|**Attributo**|**Definizione**|
|Nome|[Obbligatorio] Il nome del tema|
|GUID|[Obbligatorio] GUID del tema (deve corrispondere alla formattazione DEL GUID)|

 Quando si creano colori personalizzati per Visual Studio, tali colori devono essere definiti per i temi seguenti. Se non esistono colori per un tema specifico, Visual Studio tenta di caricare i colori mancanti dal tema Luce.

|||
|-|-|
|**Nome del tema**|**GUID tema**|
|Light|-de3dbbcd-f642-433c-8353-8f1df4370aba|
|Dark (Scuro)|1ded0138-47ce-435e-84ef-9ec1f439b749|
|Blu|4d6a176-b948-4b29-8c66-53c97a1ed7d0|
|Contrasto elevato|4d6a176-b948-4b29-8c66-53c97a1ed7d0|

 **Categoria**

 L'elemento \<> categoria definisce una raccolta di colori in un tema. I nomi delle categorie forniscono raggruppamenti logici e devono essere definiti nel modo più ristretto possibile. Una categoria deve contenere almeno un \<elemento Color>. Gli elementi di categoria sono definiti in questo modo:

```xml
<Category Name="name" GUID="guid">
      <!-- one or more Color elements -->
 </Category>
```

|||
|-|-|
|**Attributo**|**Definizione**|
|Nome|[Obbligatorio] Il nome della categoria|
|GUID|[Obbligatorio] GUID della categoria (deve corrispondere alla formattazione GUID)|

 **Color**

 L'elemento \<Color> definisce un colore per un componente o uno stato dell'interfaccia utente. Lo schema di denominazione preferito per un colore è [tipo di interfaccia utente] [Stato]. Non utilizzare la parola "colore", in quanto è ridondante. Un colore deve indicare chiaramente il tipo di elemento e le situazioni, o "stato", per cui verrà applicato il colore. Un colore non deve essere vuoto e deve \<contenere \<uno o entrambi i> di sfondo e> elemento di primo piano. Gli elementi di colore sono definiti in questo modo:

```xml
<Color Name="name">
        <Background /> <!-- zero or one Background element -->
        <Foreground /> <!-- zero or one Foreground element -->
 </Color>
```

|||
|-|-|
|**Attributo**|**Definizione**|
|Nome|[Obbligatorio] Il nome del colore|

 **Sfondo e/o primo piano**

 Gli \<elementi \<> e> primo piano definiscono il valore e il tipo di un colore per lo sfondo o il primo piano di un elemento dell'interfaccia utente. Questi elementi non hanno figli.

```xml
<Background Type="type" Source="int" />
<Foreground Type="type" Source="int" />
```

|||
|-|-|
|**Attributo**|**Definizione**|
|Type|[Obbligatorio] Tipo del colore. I possibili valori sono i seguenti:<br /><br /> *CT_INVALID:* Il colore non è valido o non è impostato.<br /><br /> *CT_RAW:* Valore ARGB non elaborato.<br /><br /> *CT_COLORINDEX:* NON UTILIZZARE.<br /><br /> *CT_SYSCOLOR:* Un colore di sistema di Windows da SysColor.<br /><br /> *CT_VSCOLOR:* Un colore di Visual Studio da __VSSYSCOLOREX.<br /><br /> *CT_AUTOMATIC:* Colore automatico.<br /><br /> *CT_TRACK_FOREGROUND:* NON UTILIZZARE.<br /><br /> *CT_TRACK_BACKGROUND:* NON UTILIZZARE.|
|Source (Sorgente)|[Obbligatorio] Il valore del colore rappresentato in formato esadecimale|

 Tutti i valori supportati dall'enumerazione __VSCOLORTYPE sono supportati dallo schema nell'attributo Type. Tuttavia, si consiglia di utilizzare solo CT_RAW e CT_SYSCOLOR.

 **Tutti insieme**

 Questo è un semplice esempio di un file .xml a tema valido:

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

 Il file \<XML VsixColorCompiler \<> \<file PkgDef>> facoltativi Args

 **Argomenti**

||||
|-|-|-|
|**Nome switch**|**Note**|**Obbligatorio o facoltativo**|
|Senza nome (file xml)|Questo è il primo parametro senza nome ed è il percorso del file XML da convertire.|Obbligatoria|
|Senza nome (file .pkgdef)|Questo è il secondo parametro senza nome ed è il percorso di output per il file pkgdef generato.<br /><br /> Impostazione \<predefinita: Nome file XML>.pkgdef|Facoltativo|
|/noLogo|L'impostazione di questo flag interrompe la stampa delle informazioni sul prodotto e sul copyright.|Facoltativo|
|/?|Stampare le informazioni della Guida.|Facoltativo|
|/help|Stampare le informazioni della Guida.|Facoltativo|

 **Esempi**

- VsixColorCompiler D:

- VsixColorCompiler D:

## <a name="notes"></a>Note

- Questo strumento richiede l'installazione della versione più recente del runtime di VC.

- Sono supportati solo i singoli file. La conversione in blocco tramite percorsi di cartelle non è supportata.

## <a name="sample-output"></a>Output di esempio
 Il file .pkgdef generato dallo strumento sarà simile alle seguenti chiavi:

```
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\Environment]
"Data"=hex:3a,00,00,00,0b,00,00,00,01,00,00,00,c3,d9,4e,62,fd,bd,fa,41,96,c3,7c,82,4e,a3,2e,3d,01,00,00,00,0c,00,00,00,41,63,74,69,76,65,42,6f,72,64,65,72,01,cc,ce,db,ff,01,33,31,24,ff

[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\TreeView]
"Data"=hex:38,00,00,00,0b,00,00,00,01,00,00,00,8e,f0,ec,92,13,8b,f4,4c,99,e9,ae,26,92,38,21,85,01,00,00,00,0a,00,00,00,42,61,63,6b,67,72,6f,75,6e,64,01,f5,f5,f5,ff,01,1e,1e,1e,ff
```
