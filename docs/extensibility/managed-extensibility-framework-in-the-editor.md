---
title: Managed Extensibility Framework nell'editor | Microsoft Docs
description: Informazioni sul Managed Extensibility Framework, che consente di compilare componenti personalizzati per estendere l'editor in Visual Studio SDK.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - using MEF for extensions
ms.assetid: 3f59a285-6c33-4ae3-a4fb-ec1f5aa21bd1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: f7a98dee0c42188cfc684064744fde0c3e683d70c19d1909de98669edb46b1af
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121359130"
---
# <a name="managed-extensibility-framework-in-the-editor"></a>Managed Extensibility Framework nell'editor
L'editor viene compilato usando Managed Extensibility Framework (MEF). È possibile compilare componenti MEF personalizzati per estendere l'editor e il codice può utilizzare anche i componenti dell'editor.

## <a name="overview-of-the-managed-extensibility-framework"></a>Panoramica del Managed Extensibility Framework
 MEF è una libreria .NET che consente di aggiungere e modificare le funzionalità di un'applicazione o di un componente che segue il modello di programmazione MEF. L Visual Studio editor può fornire e utilizzare parti del componente MEF.

 Il file MEF è contenuto nell'.NET Framework versione 4 *System.ComponentModel.Composition.dll* assembly.

 Per altre informazioni su MEF, vedere [Managed Extensibility Framework (MEF).](/dotnet/framework/mef/index)

### <a name="component-parts-and-composition-containers"></a>Componenti e contenitori di composizione
 Una parte del componente è una classe o un membro di una classe che può eseguire una o entrambe le operazioni seguenti:

- Utilizzare un altro componente

- Essere utilizzato da un altro componente

  Si consideri ad esempio un'applicazione di acquisto con un componente di immissione ordini che dipende dai dati di disponibilità del prodotto forniti da un componente di inventario del magazzino. In termini MEF, la parte relativa all'inventario può *esportare* i dati sulla disponibilità del prodotto e la parte relativa all'immissione dell'ordine *può importare* i dati. La parte relativa all'immissione dell'ordine e la parte relativa all'inventario non devono essere reciproca. Il *contenitore di* composizione (fornito dall'applicazione host) è responsabile della gestione del set di esportazioni e della risoluzione delle esportazioni e delle importazioni.

  Il contenitore di <xref:System.ComponentModel.Composition.Hosting.CompositionContainer> composizione, , è in genere di proprietà dell'host. Il contenitore di composizione gestisce un *catalogo* di parti del componente esportate.

### <a name="export-and-import-component-parts"></a>Esportare e importare parti del componente
 È possibile esportare qualsiasi funzionalità, purché sia implementata come classe pubblica o membro pubblico di una classe (proprietà o metodo). Non è necessario derivare la parte del componente da <xref:System.ComponentModel.Composition.Primitives.ComposablePart> . È invece necessario aggiungere un attributo alla classe o al membro della classe <xref:System.ComponentModel.Composition.ExportAttribute> che si desidera esportare. Questo attributo specifica il contratto *con cui un'altra* parte del componente può importare la funzionalità.

### <a name="the-export-contract"></a>Contratto di esportazione
 definisce <xref:System.ComponentModel.Composition.ExportAttribute> l'entità (classe, interfaccia o struttura) che viene esportata. In genere, l'attributo export accetta un parametro che specifica il tipo di esportazione.

```
[Export(typeof(ContentTypeDefinition))]
class TestContentTypeDefinition : ContentTypeDefinition {   }
```

 Per impostazione predefinita, <xref:System.ComponentModel.Composition.ExportAttribute> l'attributo definisce un contratto che rappresenta il tipo della classe di esportazione.

```
[Export]
[Name("Structure")]
[Order(After = "Selection", Before = "Text")]
class TestAdornmentLayerDefinition : AdornmentLayerDefinition {   }
```

 Nell'esempio l'attributo `[Export]` predefinito è equivalente a `[Export(typeof(TestAdornmentLayerDefinition))]` .

 È anche possibile esportare una proprietà o un metodo, come illustrato nell'esempio seguente.

```
[Export]
[Name("Scarlet")]
[Order(After = "Selection", Before = "Text")]
public AdornmentLayerDefinition scarletLayerDefinition;
```

### <a name="import-a-mef-export"></a>Importare un'esportazione MEF
 Quando si desidera utilizzare un'esportazione MEF, è necessario conoscere il contratto (in genere il tipo) con cui è stato esportato e aggiungere un attributo con <xref:System.ComponentModel.Composition.ImportAttribute> tale valore. Per impostazione predefinita, l'attributo import accetta un parametro, ovvero il tipo della classe che modifica. Le righe di codice seguenti importano il <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService> tipo .

```
[Import]
internal IClassificationTypeRegistryService ClassificationRegistry;
```

## <a name="get-editor-functionality-from-a-mef-component-part"></a>Ottenere la funzionalità dell'editor da una parte del componente MEF
 Se il codice esistente è una parte del componente MEF, è possibile usare i metadati MEF per utilizzare le parti del componente dell'editor.

#### <a name="to-consume-editor-functionality-from-a-mef-component-part"></a>Per utilizzare la funzionalità dell'editor da una parte del componente MEF

1. Aggiungere riferimenti *System.Composition.ComponentModel.dll*, che si trova nella Global Assembly Cache (GAC) e agli assembly dell'editor.

2. Aggiungere le direttive using pertinenti.

    ```
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio.Text;
    ```

3. Aggiungere `[Import]` l'attributo all'interfaccia del servizio, come indicato di seguito.

    ```
    [Import]
    ITextBufferFactoryService textBufferService;
    ```

4. Dopo aver ottenuto il servizio, è possibile utilizzare uno qualsiasi dei relativi componenti.

5. Dopo aver compilato l'assembly, inserire l'assembly in *.. Cartella \Common7\IDE\Components \* del Visual Studio installazione.

## <a name="see-also"></a>Vedi anche
- [Punti di estensione del servizio di linguaggio e dell'editor](../extensibility/language-service-and-editor-extension-points.md)
