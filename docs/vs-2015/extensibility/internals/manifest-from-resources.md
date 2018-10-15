---
title: Manifestfromresources | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0234109b-5dcb-4d9d-acb9-a63f8bd5699c
caps.latest.revision: 5
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b18e81cfa265f79e05f1cfb1dcfbca1f348b341d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49252434"
---
# <a name="manifest-from-resources"></a>Manifest from Resources
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Il manifesto dallo strumento di risorse è un'applicazione console che accetta un elenco di risorse grafiche (file con estensione PNG o XAML) e genera un file .imagemanifest che consente a tali immagini da utilizzare con il servizio di immagini di Visual Studio. Inoltre, questo strumento è utilizzabile per aggiungere immagini a un .imagemanifest esistente. Questo strumento è utile per l'aggiunta di supporto ad alta risoluzione e dei temi per le immagini a un'estensione di Visual Studio. Il file .imagemanifest generato deve essere incluso in e distribuito come parte di un'estensione di Visual Studio (VSIX).  
  
## <a name="how-to-use-the-tool"></a>Come usare lo strumento  
 **Sintassi**  
  
 ManifestFromResources /Resources.:\<Dir1 >;\< Img1 > /assembly:\<AssemblyName > \<Args facoltativo >  
  
 **Argomenti**  
  
||||  
|-|-|-|  
|**Nome del commutatore**|**Note**|**Obbligatoria o facoltativa**|  
|/risorse|Elenco delimitato da punto e virgola di immagini o directory. Questo elenco deve contenere sempre l'elenco completo delle immagini presenti nel manifesto. Se viene fornito un elenco parziale, solo le voci incluse non andranno perse.<br /><br /> Se un file di risorse specificato è una serie di immagini, lo strumento verrà dividerla in immagini separate prima dell'aggiunta di ogni immagine secondaria al manifesto.<br /><br /> Se l'immagine è un file con estensione png, è consigliabile formattare il nome simile al seguente in modo che lo strumento può inserire i giusti attributi per l'immagine: \<Name >.\< Larghezza >. \<Altezza >. PNG.|Obbligatorio|  
|/assembly|Il nome dell'assembly gestito (senza includere l'estensione) o il percorso di runtime dell'assembly nativo che ospita le risorse (rispetto alla posizione di runtime del manifesto).|Obbligatorio|  
|/manifest|Nome da assegnare al file .imagemanifest generato. Può anche includere un percorso assoluto o relativo per creare il file in una posizione diversa. Il nome predefinito corrisponde al nome dell'assembly.<br /><br /> Valore predefinito: \<Directory corrente >\\< Assembly\>.imagemanifest|Facoltativo|  
|/guidName|Il nome da assegnare al simbolo GUID per tutte le immagini nel manifesto generato.<br /><br /> Predefinito: AssetsGuid|Facoltativo|  
|/rootPath|Il percorso radice che devono essere rimossi prima della creazione di URI delle risorse gestiti. (Questo flag è alla Guida in linea con i casi in cui lo strumento Ottiene il percorso relativo di URI errato, causando risorse caricamento).<br /><br /> Valore predefinito: \<Directory corrente >|Facoltativo|  
|/Recursive|L'impostazione di questo flag indica che lo strumento in modo ricorsivo tutte le directory di ricerca nell'argomento /Resources. L'omissione di questo flag causa una ricerca top-multilivello solo delle directory.|Facoltativo|  
|/isNative|Impostare questo flag quando l'argomento assembly è un percorso per un assembly nativo. Omettere questo flag quando l'argomento assembly è il nome di un assembly gestito. (Vedere la sezione Note per altre informazioni su questo flag).|Facoltativo|  
|/newGuids|Impostazione di questo flag indica allo strumento per creare un nuovo valore per il simbolo GUID delle immagini anziché quello dal manifesto esistente di unione.|Facoltativo|  
|/newIds|Impostazione di questo flag indica allo strumento per creare nuovi valori di simbolo ID per ogni immagine invece di unione di valori dal manifesto esistente.|Facoltativo|  
|/noLogo|Impostazione di questo flag arresta prodotto e informazioni sul copyright di stampare le informazioni.|Facoltativo|  
|/?|Stampare le informazioni della Guida.|Facoltativo|  
|/help|Stampare le informazioni della Guida.|Facoltativo|  
  
 **Esempi**  
  
-   ManifestFromResources /resources:D:\Images /assembly:My.Assembly.Name /isNative  
  
-   ManifestFromResources /resources:D:\Images\Image1.png;D:\Images\Image1.xaml /assembly:My.Assembly.Name /manifest:MyImageManifest.imagemanifest  
  
-   ManifestFromResources /resources:D:\Images\Image1.png;D:\Images\Image1.xaml /assembly:My.Assembly.Name /guidName:MyImages /newGuids /newIds  
  
## <a name="notes"></a>Note  
  
-   Lo strumento supporta solo file con estensione png e. Xaml. Qualsiasi altro tipo di immagine o un file verrà ignorato. Viene generato un avviso per tutti i tipi non supportati rilevati durante l'analisi delle risorse. Se non supportata immagini sono disponibili al termine lo strumento di analisi delle risorse, verrà generato un errore  
  
-   Seguendo il formato consigliato per le immagini. PNG, lo strumento imposterà il valore delle dimensioni e delle dimensioni per il formato PNG per la dimensione di formato specificato, anche se è diversa dalla dimensione effettiva dell'immagine.  
  
-   Può essere omesso nel formato larghezza/altezza per immagini con estensione png, ma lo strumento leggerà effettiva larghezza/altezza dell'immagine e usandole per valore delle dimensioni e delle dimensioni dell'immagine.  
  
-   Eseguire questo strumento nella sequenza di immagini stesse più volte per la stessa .imagemanifest comporterà voci duplicate del manifesto, perché lo strumento tenta di suddividere l'elenco di immagini in immagini autonome e aggiungerli al manifesto esistente.  
  
-   Unione (omettendo /newGuids o /newIds) devono essere eseguita solo per i manifesti generati dallo strumento. I manifesti che sono stati personalizzati generati tramite altri mezzi non potrebbero risultare uniti correttamente.  
  
-   I manifesti che vengono generati per gli assembly nativi debba essere modificato manualmente dopo la generazione per uniformare i simboli di ID risorsa ID file RC dell'assembly nativo.  
  
## <a name="sample-output"></a>Esempio di output  
 **Manifesto immagine semplice**  
  
 Un manifesto dell'immagine sarà simile a questo file XML:  
  
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
  
 **Manifesto di immagini per un elenco di immagini**  
  
 Un manifesto di immagini per un elenco di immagini sarà simile a questo file XML:  
  
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
  
 **Manifesto di immagini per le risorse immagine assembly nativo**  
  
 Un manifesto di immagini per le immagini native sarà simile a questo file XML:  
  
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

