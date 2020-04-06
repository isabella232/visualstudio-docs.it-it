---
title: Manifesto da Risorse . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0234109b-5dcb-4d9d-acb9-a63f8bd5699c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cb853963cc5ca6fbe6080249daa8fcf9c08bf943
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707283"
---
# <a name="manifest-from-resources"></a>Manifest from Resources
Lo strumento Manifesto da risorse è un'applicazione console che accetta un elenco di risorse immagine (file con estensione png o xaml) e genera un file con estensione imagemanifest che consente l'utilizzo di tali immagini con il servizio immagini di Visual Studio. Inoltre, questo strumento può essere utilizzato per aggiungere immagini a un .imagemanifest esistente. Questo strumento è utile per l'aggiunta di valori DPI ad alto valore DPI e il supporto dei temati per le immagini a un'estensione di Visual Studio.This tool is useful for adding high-DPI and theming support for images to a Visual Studio extension. Il file .imagemanifest generato deve essere incluso e distribuito come parte di un'estensione di Visual Studio (vsix).

## <a name="how-to-use-the-tool"></a>Procedura: utilizzare lo strumento
 **Sintassi**

 ManifestFromResources /resources:\<dir1>; \<Img1> /assembly:\< \<AssemblyName> il> facoltativa Args

 **Argomenti**

||||
|-|-|-|
|**Nome switch**|**Note**|**Obbligatorio o facoltativo**|
|/resources|Elenco delimitato da punti e virgola di immagini o directory. Questo elenco deve sempre contenere l'elenco completo delle immagini che saranno nel manifesto. Se viene fornito solo un elenco parziale, le voci non incluse andranno perse.<br /><br /> Se un determinato file di risorse è una striscia di immagini, lo strumento lo dividerà in immagini separate prima di aggiungere ogni immagine secondaria al manifesto.<br /><br /> Se l'immagine è un file .png, ti consigliamo di formattare il nome in questo \<modo in modo che lo strumento possa inserire gli attributi corretti per l'immagine: Nome>. \<> larghezza. \<Altezza>.png.|Obbligatoria|
|/assembly|Il nome dell'assembly gestito (esclusa l'estensione) o il percorso di runtime dell'assembly nativo che ospita le risorse (relativo al percorso di runtime del manifesto).|Obbligatoria|
|/manifest (manifesto)|Nome da assegnare al file .imagemanifest generato. Può anche includere un percorso assoluto o relativo per creare il file in un percorso diverso. Il nome predefinito corrisponde al nome dell'assembly.<br /><br /> Impostazione \<predefinita: \\>\>directory corrente<Assembly .imagemanifest|Facoltativo|
|/guidNome|Nome da assegnare al simbolo GUID per tutte le immagini nel manifesto generato.<br /><br /> Impostazione predefinita: AssetsGuid|Facoltativo|
|/rootPercorso|Percorso radice che deve essere rimosso prima di creare gli URI delle risorse gestite. Questo flag consente di risolvere i casi in cui lo strumento ottiene il percorso URI relativo errato, causando il mancato caricamento delle risorse.<br /><br /> Impostazione \<predefinita:> directory corrente|Facoltativo|
|/recorsiva|L'impostazione di questo flag indica allo strumento di eseguire ricerche ricorsive in tutte le directory nell'argomento /resources. Se si omette questo flag, si otterrà una ricerca di directory solo di primo livello.|Facoltativo|
|/isNative (informazioni in lingua inglese)|Impostare questo flag quando l'argomento assembly è un percorso per un assembly nativo. Omettere questo flag quando l'argomento dell'assembly è il nome di un assembly gestito. Per ulteriori informazioni su questo flag, vedere la sezione Note.|Facoltativo|
|/nuovaGuids|L'impostazione di questo flag indica allo strumento di creare un nuovo valore per il simbolo GUID delle immagini anziché unire quello dal manifesto esistente.|Facoltativo|
|/nuoviIDs|L'impostazione di questo flag indica allo strumento di creare nuovi valori di simbolo ID per ogni immagine anziché unire i valori dal manifesto esistente.|Facoltativo|
|/noLogo|L'impostazione di questo flag interrompe la stampa delle informazioni sul prodotto e sul copyright.|Facoltativo|
|/?|Stampare le informazioni della Guida.|Facoltativo|
|/help|Stampare le informazioni della Guida.|Facoltativo|

 **Esempi**

- ManifestFromResources /resources:D:/Immagini /assembly:Assembly.Nome /isNative

- ManifestFromResources /resources:D:'Immagini'Image1.png;D:'Immagini'Image1.xaml/assembly:My.Assembly.Name /manifest:MyImageManifest.imagemanifest

- ManifestFromResources /resources:D:/Immagini/Image1.png;D:/Immagini1.xaml/assembly:Nome.assembly/nome/guidNome:Immagini /newGuids /newIds

## <a name="notes"></a>Note

- Lo strumento supporta solo i file con estensione png e xaml. Qualsiasi altro tipo di immagine o file verrà ignorato. Viene generato un avviso per tutti i tipi non supportati rilevati durante l'analisi delle risorse. Se non vengono trovate immagini supportate al termine dell'analisi delle risorse da parte dello strumento, verrà generato un errore

- Seguendo il formato suggerito per le immagini .png, lo strumento imposterà il valore di dimensione/dimensione per il file .png sulla dimensione specificata dal formato, anche se differisce dalle dimensioni effettive dell'immagine.

- Il formato larghezza/altezza può essere omesso per le immagini .png, ma lo strumento leggerà la larghezza/altezza effettiva dell'immagine e utilizzerà quelle per il valore di dimensione/dimensione dell'immagine.

- L'esecuzione di questo strumento sulla stessa striscia di immagini più volte per lo stesso .imagemanifest comporterà voci di manifesto duplicate, perché lo strumento tenta di dividere la striscia di immagini in immagini autonome e aggiungerle al manifesto esistente.

- L'unione (omettendo /newGuids o /newIds) deve essere eseguita solo per i manifesti generati dallo strumento. I manifesti che sono stati personalizzati o generati con altri mezzi potrebbero non essere uniti correttamente.

- I manifesti generati per gli assembly nativi potrebbero dover essere modificati manualmente dopo la generazione per fare in modo che i simboli ID corrispondano agli ID di risorsa del file RC dell'assembly nativo.

## <a name="sample-output"></a>Output di esempio
 **Manifesto dell'immagine semplice**

 Un manifesto dell'immagine sarà simile a questo file XML:An image manifest will be similar to this .xml file:

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- This file was generated by the ManifestFromResources tool.-->
<!-- Version: 14.0.15197 -->
<ImageManifest xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="http://schemas.microsoft.com/VisualStudio/ImageManifestSchema/2014">
  <Symbols>
    <String Name="Resources" Value="/My.Assembly.Name;Component/Resources/Images" />
    <Guid Name="AssetsGuid" Value="{fb41b7ef-6587-480c-aa27-5b559d42cfc9}" />
    <ID Name="MyImage" Value="0" />
  </Symbols>
  <Images>
    <Image Guid="$(AssetsGuid)" ID="$(MyImage)">
      <Source Uri="$(Resources)/Xaml/MyImage.xaml" />
      <Source Uri="$(Resources)/Png/MyImage.16.16.png">
        <Size Value="16" />
      </Source>
    </Image>
  </Images>
  <ImageLists />
</ImageManifest>
```

 **Manifesto dell'immagine per una striscia di immagini**

 Un manifesto dell'immagine per una striscia di immagini sarà simile a questo file XML:An image manifest for an image strip will be similar to this .xml file:

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- This file was generated by the ManifestFromResources tool.-->
<!-- Version: 14.0.15197 -->
<ImageManifest xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="http://schemas.microsoft.com/VisualStudio/ImageManifestSchema/2014">
  <Symbols>
    <String Name="Resources" Value="/My.Assembly.Name;Component/Resources/ImageStrip" />
    <Guid Name="AssetsGuid" Value="{fb41b7ef-6587-480c-aa27-5b559d42cfc9}" />
    <ID Name="MyImageStrip_0" Value="1" />
    <ID Name="MyImageStrip_1" Value="2" />
    <ID Name="MyImageStrip" Value="3" />
  </Symbols>
  <Images>
    <Image Guid="$(AssetsGuid)" ID="$(MyImageStrip_0)">
      <Source Uri="$(Resources)/MyImageStrip_0.png">
        <Size Value="16" />
      </Source>
    </Image>
    <Image Guid="$(AssetsGuid)" ID="$(MyImageStrip_1)">
      <Source Uri="$(Resources)/MyImageStrip_1.png">
        <Size Value="16" />
      </Source>
    </Image>
  </Images>
  <ImageLists>
    <ImageList Guid="$(AssetsGuid)" ID="$(MyImageStrip)">
      <ContainedImage Guid="$(AssetsGuid)" ID="$(MyImageStrip_0)" />
      <ContainedImage Guid="$(AssetsGuid)" ID="$(MyImageStrip_1)" />
    </ImageList>
  </ImageLists>
</ImageManifest>
```

 **Manifesto dell'immagine per le risorse immagine dell'assembly nativoImage manifest for native assembly image resources**

 Un manifesto di immagine per le immagini native sarà simile a questo file XML:An image manifest for native images will be similar to this .xml file:

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- This file was generated by the ManifestFromResources tool.-->
<!-- Version: 14.0.15198 -->
<ImageManifest xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="http://schemas.microsoft.com/VisualStudio/ImageManifestSchema/2014">
  <Symbols>
    <String Name="Resources" Value="..\Assembly\Folder\My.Assembly.Name" />
    <Guid Name="AssetsGuid" Value="{442d8739-efde-46a4-8f29-e3a1e5e7f8b4}" />
    <ID Name="MyImage1" Value="0" />
    <ID Name="MyImage2" Value="1" />
  </Symbols>
  <Images>
    <Image Guid="$(AssetsGuid)" ID="$(MyImage1)">
      <Source Uri="$(Resources)">
        <Size Value="16" />
        <NativeResource ID="$(MyImage1)" Type="PNG" />
      </Source>
    </Image>
    <Image Guid="$(AssetsGuid)" ID="$(MyImage2)">
      <Source Uri="$(Resources)">
        <Size Value="16" />
        <NativeResource ID="$(MyImage2)" Type="PNG" />
      </Source>
    </Image>
  </Images>
  <ImageLists />
</ImageManifest>
```
