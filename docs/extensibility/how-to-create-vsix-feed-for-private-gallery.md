---
title: Come creare un feed vsix per la raccolta privata | Microsoft Docs
description: Informazioni su come creare un feed vsix con VSIX Util e usare il feed nella raccolta privata.
ms.date: 08/19/2021
ms.topic: conceptual
helpviewer_keywords:
- VSIX galleries, private
- private galleries, VSIX
author: anva
ms.author: anva
manager: tinali
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: b5925da18b5d55cc7e5c5c7f77b61a1a97e4962f
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2021
ms.locfileid: "128436024"
---
# <a name="how-to-create-the-atom-feed-vsixfeed-for-visual-studio-private-galleries-using-vsixutil"></a>Procedura: Creare il feed ATOM (VsixFeed) per Visual Studio raccolte private con VsixUtil
È possibile usare lo strumento Visual Studio utilità della riga di comando VSSDK per creare un feed ATOM, vedere [Raccolte private](../extensibility/private-galleries.md)  

```csharp
VsixUtil  createVsixFeed 
```


## <a name="syntax"></a>Sintassi

```csharp
VSIXUtil createVsixFeed -source [sourceValue] -output [outputValue]– filename [fileNameValue] -title [titleValue] – recursive – ignoreErrors  
```

## <a name="arguments"></a>Argomenti

| Parametro | Descrizione |
|---------|-------|
| -source | la directory contiene i file VSIX.  |
| -output | directory di output.  |
| -recursive | include la directory corrente e tutte le relative sottodirectory in un'operazione di ricerca VSIX.  |
| -ignoreErrors | ignorare un elemento VSIX non valido in un'operazione di ricerca VSIX.  |
| -fileName | nome file per il feed VSIX.  |
| -title | title per il feed VSIX. |

## <a name="examples"></a>Esempio 

* Cercare i file VSIX dal percorso *C:\extensions* e creare il feed nel percorso *C:\extensions*. 

    ```csharp
    VsixUtil createVsixFeed -source C:\extensions -output C:\extensions 
    ``` 

* Cercare i file VSIX dal percorso *C:\extensions,* creare il feed nel percorso *C:\extensions* e ignorare i file VSIX non validi (se presenti). 

    ```csharp
    VsixUtil createVsixFeed -source C:\extensions -output C:\extensions -ignoreErrors 
    ``` 
    Questo comando non includerà i file VSIX non validi nel feed. 
 

* Cercare i file VSIX dal percorso *C:\extensions* e in tutte le relative sottodirectory, quindi creare il feed nel percorso *C:\extensions*. 

    ```csharp
    VsixUtil createVsixFeed -source C:\extensions -output C:\extensions  -recursive 
    ``` 

* Cercare i file VSIX dal percorso *C:\extensions* e creare il nome del feed `PreProdFeed` nel percorso *C:\extensions*.  

    ```csharp
    VsixUtil createVsixFeed -source C:\extensions -output C:\extensions -ignoreErrors  -recursive -fileName "PreProdFeed"
    ```

* È possibile eseguire lo strumento nella directory in cui si trovano i file VSIX e quindi eseguire il comando seguente per generare il feed nello stesso percorso. 

    ```csharp
    VsixUtil createVsixFeed 
    ```

* Creare un feed dal repository locale, ad esempio *c:\localExtensionProjectRepo* 
 
    ```csharp
    VsixUtil createVsixFeed –source c:\localExtensionProjectRepo -recursive 
    ```

   
Il percorso di installazione per lo strumento VsixUtil è {Percorso di installazione *di VS}\VSSDK\VisualStudioIntegration\Tools\Bin\VsixUtil.exe*. È anche possibile scaricare la versione più recente di [Microsoft.VSSDK.BuildTools](https://www.nuget.org/packages/Microsoft.VSSDK.BuildTools/) fornita con l'utilità VSIX.
    

## <a name="faq"></a>Domande frequenti

* Come è possibile trovare il percorso del feed generato dal `VsixUtil createVsixFeed` comando? 
    È possibile trovare il percorso del feed dall'output del comando. 

    Ad esempio: `VSIX Feed '<OutPutDirectory>\AtomFeed.xml' created successfully. `

* Viene visualizzato il codice di errore , che cosa `VsixFeed0001` significa e come è possibile risolvere il problema?  
    Significa che l'origine contiene file Vsix non validi. È possibile rimuovere il file non valido dal percorso di origine o usare l'argomento per `-ignoreErrors` ignorare il file non valido.
    

## <a name="example-of-vsix-entry"></a>Esempio di voce VSIX

```xml
<Vsix> 
 <Id></Id> 
 <Version></Version> 
 <References />
 <Rating xsi:nil="true" /> 
 <RatingCount xsi:nil="true" /> 
 <DownloadCount xsi:nil="true" /> 
 <Installations> 
  <Identifier></Identifier> 
  <VersionRange></VersionRange>
  <ProductArchitecture></ProductArchitecture>
 </Installations> 
</Vsix> 
```

## <a name="see-also"></a>Vedi anche
- [Raccolte private](../extensibility/private-galleries.md)
