---
title: Manifest from Resources | Microsoft Docs
description: Informazioni su come usare lo strumento Manifest from Resources per aggiungere file con estensione png o XAML a un file con estensione imagemanifest per l'uso con il servizio immagini di Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0234109b-5dcb-4d9d-acb9-a63f8bd5699c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 42bd932b093ae805e8885bc9fc61324c3cadbe30
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105095173"
---
# <a name="manifest-from-resources"></a>Manifest from Resources
Lo strumento Manifest from Resources è un'applicazione console che accetta un elenco di risorse immagine (file con estensione png o XAML) e genera un file con estensione imagemanifest che consente di usare tali immagini con il servizio immagini di Visual Studio. Inoltre, questo strumento può essere utilizzato per aggiungere immagini a un. imagemanifest esistente. Questo strumento è utile per aggiungere il supporto di valori DPI e per le immagini a un'estensione di Visual Studio. Il file. imagemanifest generato deve essere incluso in e distribuito come parte di un'estensione di Visual Studio (VSIX).

## <a name="how-to-use-the-tool"></a>Procedura: utilizzare lo strumento
 **Sintassi**

 ManifestFromResources/Resources: \<Dir1> ; \<Img1> /assembly: \<AssemblyName>\<Optional Args>

 **Argomenti**

|**Nome dell'opzione**|**Note**|**Obbligatorio o facoltativo**|
|-|-|-|
|/resources|Elenco delimitato da punti e virgola di immagini o directory. Questo elenco deve sempre contenere l'elenco completo delle immagini che saranno presenti nel manifesto. Se viene fornito solo un elenco parziale, le voci non incluse andranno perse.<br /><br /> Se un file di risorse specificato è un elenco di immagini, lo strumento lo suddividerà in immagini separate prima di aggiungere ogni sottoimmagine al manifesto.<br /><br /> Se l'immagine è un file con estensione png, è consigliabile formattare il nome in modo che lo strumento possa inserire gli attributi corretti per l'immagine: \<Name> . \<Width> . \<Height> . png.|Necessario|
|/assembly|Nome dell'assembly gestito (esclusa l'estensione) o percorso di runtime dell'assembly nativo che ospita le risorse (relative al percorso di runtime del manifesto).|Necessario|
|/manifest|Nome da assegnare al file con estensione imagemanifest generato. Può inoltre includere un percorso assoluto o relativo per creare il file in un percorso diverso. Il nome predefinito corrisponde al nome dell'assembly.<br /><br /> Impostazione predefinita: \<Current Directory> \\<assembly \> . imagemanifest|Facoltativo|
|/guidName|Nome da assegnare al simbolo GUID per tutte le immagini nel manifesto generato.<br /><br /> Impostazione predefinita: AssetsGuid|Facoltativo|
|/rootPath|Percorso radice che deve essere rimosso prima di creare gli URI delle risorse gestite. Questo flag è utile nei casi in cui lo strumento ottiene il percorso URI relativo errato, causando il mancato caricamento delle risorse.<br /><br /> Valore predefinito: \<Current Directory>|Facoltativo|
|/Recursive|L'impostazione di questo flag indica allo strumento di cercare in modo ricorsivo tutte le directory nell'argomento/resources. Se si omette questo flag, verrà ricercata solo la directory di primo livello.|Facoltativo|
|/isNative|Impostare questo flag quando l'argomento dell'assembly è un percorso per un assembly nativo. Omettere questo flag quando l'argomento dell'assembly è il nome di un assembly gestito. Per ulteriori informazioni su questo flag, vedere la sezione Note.|Facoltativo|
|/newGuids|L'impostazione di questo flag indica allo strumento di creare un nuovo valore per il simbolo GUID delle immagini anziché unire quello del manifesto esistente.|Facoltativo|
|/newIds|L'impostazione di questo flag indica allo strumento di creare nuovi valori dei simboli ID per ogni immagine anziché unire i valori del manifesto esistente.|Facoltativo|
|/noLogo|L'impostazione di questo flag interrompe le informazioni sul prodotto e sul copyright dalla stampa.|Facoltativo|
|/?|Stampare le informazioni della guida.|Facoltativo|
|/help|Stampare le informazioni della guida.|Facoltativo|

 **Esempi**

- ManifestFromResources/Resources: D:\Images/assembly: My. assembly. Name/isNative

- ManifestFromResources/resources:D:\Images\Image1.png;D: \Images\Image1.xaml/assembly: My. assembly. Name/manifest: MyImageManifest. imagemanifest

- ManifestFromResources/resources:D:\Images\Image1.png;D: \Images\Image1.xaml/assembly: My. assembly. Name/guidName: immagini/newGuids/newIds

## <a name="notes"></a>Note

- Lo strumento supporta solo file con estensione png e XAML. Eventuali altri tipi di file o immagini verranno ignorati. Viene generato un avviso per tutti i tipi non supportati rilevati durante l'analisi delle risorse. Se non vengono trovate immagini supportate al termine dell'analisi delle risorse da parte dello strumento, verrà generato un errore

- Seguendo il formato suggerito per le immagini PNG, lo strumento imposterà il valore Size/Dimension per il. png sulla dimensione specificata dal formato, anche se si differenzia dalle dimensioni effettive dell'immagine.

- Il formato di larghezza/altezza può essere omesso per le immagini. png, ma lo strumento leggerà la larghezza e l'altezza effettive dell'immagine e le userà per il valore dimensione/dimensione dell'immagine.

- L'esecuzione di questo strumento nello stesso elenco di immagini più volte per lo stesso. imagemanifest comporterà la creazione di voci manifesto duplicate, perché lo strumento tenta di suddividere l'elenco delle immagini in immagini autonome e di aggiungerle al manifesto esistente.

- L'Unione (omettendo/newGuids o/newIds) deve essere eseguita solo per i manifesti generati dallo strumento. I manifesti che sono stati personalizzati o generati attraverso altri mezzi potrebbero non essere uniti correttamente.

- È possibile che i manifesti generati per gli assembly nativi debbano essere modificati manualmente dopo la generazione per fare in modo che i simboli ID corrispondano agli ID di risorsa del file RC dell'assembly nativo.

## <a name="sample-output"></a>Output di esempio
 **Manifesto immagine semplice**

 Un manifesto dell'immagine sarà simile a questo file con estensione XML:

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

 **Manifesto immagine per un elenco di immagini**

 Un manifesto dell'immagine per un elenco di immagini sarà simile al file XML seguente:

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

 **Manifesto immagine per le risorse dell'immagine assembly native**

 Un manifesto dell'immagine per le immagini native sarà simile al file XML seguente:

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
