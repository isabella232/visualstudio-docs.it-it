---
title: Manifest from Resources | Microsoft Docs
description: Informazioni su come usare lo strumento Manifest from Resources per aggiungere file .png o xaml a un file con estensione imagemanifest da usare con il Visual Studio Image Service.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 0234109b-5dcb-4d9d-acb9-a63f8bd5699c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f69a46362b3076025a63625adb1ee4a478622259
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903178"
---
# <a name="manifest-from-resources"></a>Manifest from Resources
Lo strumento Manifest from Resources è un'applicazione console che accetta un elenco di risorse immagine (file .png o xaml) e genera un file con estensione imagemanifest che consente l'uso di tali immagini con il servizio immagini Visual Studio. Inoltre, questo strumento può essere usato per aggiungere immagini a un file con estensione imagemanifest esistente. Questo strumento è utile per l'aggiunta di valori DPI elevati e il supporto dei colori per le immagini a un'Visual Studio predefinita. Il file con estensione imagemanifest generato deve essere incluso in e distribuito come parte di un'estensione Visual Studio (con estensione vsix).

## <a name="how-to-use-the-tool"></a>Procedura: utilizzare lo strumento
 **Sintassi**

 ManifestFromResources /resources: \<Dir1> ; \<Img1> /assembly: \<AssemblyName>\<Optional Args>

 **Argomenti**

|**Nome del commutatore**|**Note**|**Obbligatorio o facoltativo**|
|-|-|-|
|/resources|Elenco delimitato da punto e virgola di immagini o directory. Questo elenco deve sempre contenere l'elenco completo delle immagini che saranno presenti nel manifesto. Se viene specificato solo un elenco parziale, le voci non incluse andranno perse.<br /><br /> Se un determinato file di risorse è una striscia di immagini, lo strumento lo dividerà in immagini separate prima di aggiungere ogni immagine secondaria al manifesto.<br /><br /> Se l'immagine è un file .png, è consigliabile formattare il nome in questo modo in modo che lo strumento possa inserire gli attributi per l'immagine: \<Name> \<Width> . . \<Height>.png.|Obbligatoria|
|/assembly|Nome dell'assembly gestito (senza l'estensione) o percorso di runtime dell'assembly nativo che ospita le risorse (relativo al percorso di runtime del manifesto).|Obbligatoria|
|/manifest|Nome da assegnare al file con estensione imagemanifest generato. Può anche includere un percorso assoluto o relativo per creare il file in un percorso diverso. Il nome predefinito corrisponde al nome dell'assembly.<br /><br /> Impostazione predefinita: \<Current Directory> \\<\> assembly .imagemanifest|Facoltativo|
|/guidName|Nome da assegnare al simbolo GUID per tutte le immagini nel manifesto generato.<br /><br /> Impostazione predefinita: AssetsGuid|Facoltativo|
|/rootPath|Percorso radice che deve essere disattivato prima di creare GLI URI delle risorse gestite. Questo flag consente di risolvere i casi in cui lo strumento ottiene il percorso URI relativo errato, causando il caricamento delle risorse.<br /><br /> Valore predefinito: \<Current Directory>|Facoltativo|
|/recursive|L'impostazione di questo flag indica agli strumenti di eseguire ricerche ricorsive in tutte le directory nell'argomento /resources. L'omissione di questo flag comporterà una ricerca di directory solo di primo livello.|Facoltativo|
|/isNative|Impostare questo flag quando l'argomento assembly è un percorso per un assembly nativo. Omettere questo flag quando l'argomento assembly è il nome di un assembly gestito. Per altre informazioni su questo flag, vedere la sezione Note.|Facoltativo|
|/newGuids|L'impostazione di questo flag indica agli strumenti di creare un nuovo valore per il simbolo GUID delle immagini invece di unirne uno dal manifesto esistente.|Facoltativo|
|/newIds|L'impostazione di questo flag indica agli strumenti di creare nuovi valori di simboli ID per ogni immagine invece di unire i valori dal manifesto esistente.|Facoltativo|
|/noLogo|L'impostazione di questo flag impedisce la stampa delle informazioni sul prodotto e sul copyright.|Facoltativo|
|/?|Stampare le informazioni della Guida.|Facoltativo|
|/help|Stampare le informazioni della Guida.|Facoltativo|

 **Esempi**

- ManifestFromResources /resources:D:\Images /assembly:My.Assembly.Name /isNative

- ManifestFromResources /resources:D:\Images\Image1.png;D:\Images\Image1.xaml /assembly:My.Assembly.Name /manifest:MyImageManifest.imagemanifest

- ManifestFromResources /resources:D:\Images\Image1.png;D:\Images\Image1.xaml /assembly:My.Assembly.Name /guidName:MyImages /newGuids /newIds

## <a name="notes"></a>Note

- Lo strumento supporta solo file .png e xaml. Qualsiasi altro tipo di immagine o file verrà ignorato. Viene generato un avviso per tutti i tipi non supportati rilevati durante l'analisi delle risorse. Se non viene trovata alcuna immagine supportata al termine dell'analisi delle risorse da parte dello strumento, verrà generato un errore

- Seguendo il formato suggerito per le immagini .png, lo strumento imposta le dimensioni e il valore della dimensione per il .png sulla dimensione specificata dal formato, anche se è diversa dalle dimensioni effettive dell'immagine.

- Il formato larghezza/altezza può essere omesso per le immagini .png, ma lo strumento leggerà la larghezza/altezza effettiva dell'immagine e le userà per il valore di dimensione/dimensione dell'immagine.

- L'esecuzione di questo strumento nella stessa striscia di immagini più volte per lo stesso file con estensione imagemanifest comporta la duplicazione delle voci del manifesto, perché lo strumento tenta di suddividere l'elenco immagini in immagini autonome e di aggiungerle al manifesto esistente.

- L'unione (omettendo /newGuids o /newIds) deve essere eseguita solo per i manifesti generati dagli strumenti. I manifesti che sono stati personalizzati o generati con altri mezzi potrebbero non essere uniti correttamente.

- I manifesti generati per gli assembly nativi potrebbero dover essere modificati manualmente dopo la generazione per fare in modo che i simboli ID corrispondano agli ID risorsa del file RC dell'assembly nativo.

## <a name="sample-output"></a>Output di esempio
 **Manifesto dell'immagine semplice**

 Un manifesto dell'immagine sarà simile al .xml seguente:

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

 Un manifesto dell'immagine per una striscia di immagini sarà simile al .xml seguente:

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

 **Manifesto dell'immagine per le risorse immagine dell'assembly nativo**

 Un manifesto dell'immagine per le immagini native sarà simile al .xml seguente:

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
