---
title: Managed Extensibility Framework nell'editor | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - using MEF for extensions
ms.assetid: 3f59a285-6c33-4ae3-a4fb-ec1f5aa21bd1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f376a43b6d59ba494db2ad4e5ef26b260d91f6ad
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72632615"
---
# <a name="managed-extensibility-framework-in-the-editor"></a>Managed Extensibility Framework nell'editor
L'editor viene compilato utilizzando i componenti Managed Extensibility Framework (MEF). È possibile creare componenti MEF personalizzati per estendere l'editor e il codice può utilizzare anche i componenti dell'editor.

## <a name="overview-of-the-managed-extensibility-framework"></a>Panoramica dell'Managed Extensibility Framework
 MEF è una libreria .NET che consente di aggiungere e modificare le funzionalità di un'applicazione o di un componente che segue il modello di programmazione MEF. L'editor di Visual Studio è in grado di fornire e utilizzare parti componente MEF.

 MEF è contenuto nell'assembly *System. ComponentModel. Composition. dll* di .NET Framework versione 4.

 Per ulteriori informazioni su MEF, vedere [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).

### <a name="component-parts-and-composition-containers"></a>Componenti componenti e contenitori di composizione
 Una parte del componente è una classe o un membro di una classe che può eseguire una o entrambe le operazioni seguenti:

- Utilizzare un altro componente

- Essere utilizzato da un altro componente

  Si consideri, ad esempio, un'applicazione commerciale che dispone di un componente di immissione dell'ordine che dipende dai dati di disponibilità del prodotto forniti da un componente di inventario warehouse. In termini MEF, la parte di inventario può *esportare* i dati di disponibilità del prodotto e la parte relativa all'ordine può *importare* i dati. Non è necessario che la parte relativa all'ordine e la parte dell'inventario siano in grado di conoscere l'una all'altra. il *contenitore di composizione* (fornito dall'applicazione host) è responsabile della gestione del set di esportazioni e della risoluzione delle esportazioni e delle importazioni.

  Il contenitore di composizione, <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>, è in genere di proprietà dell'host. Il contenitore di composizione mantiene un *Catalogo* di parti del componente esportate.

### <a name="export-and-import-component-parts"></a>Esportare e importare parti componente
 È possibile esportare qualsiasi funzionalità, purché venga implementata come classe pubblica o come membro pubblico di una classe (proprietà o metodo). Non è necessario derivare la parte del componente da <xref:System.ComponentModel.Composition.Primitives.ComposablePart>. Al contrario, è necessario aggiungere un attributo <xref:System.ComponentModel.Composition.ExportAttribute> alla classe o al membro di classe che si desidera esportare. Questo attributo specifica il *contratto* in base al quale un'altra parte del componente può importare la funzionalità.

### <a name="the-export-contract"></a>Il contratto di esportazione
 Il <xref:System.ComponentModel.Composition.ExportAttribute> definisce l'entità (classe, interfaccia o struttura) che viene esportata. In genere, l'attributo Export accetta un parametro che specifica il tipo di esportazione.

```
[Export(typeof(ContentTypeDefinition))]
class TestContentTypeDefinition : ContentTypeDefinition {   }
```

 Per impostazione predefinita, l'attributo <xref:System.ComponentModel.Composition.ExportAttribute> definisce un contratto che è il tipo della classe di esportazione.

```
[Export]
[Name("Structure")]
[Order(After = "Selection", Before = "Text")]
class TestAdornmentLayerDefinition : AdornmentLayerDefinition {   }
```

 Nell'esempio, l'attributo `[Export]` predefinito è equivalente a `[Export(typeof(TestAdornmentLayerDefinition))]`.

 È anche possibile esportare una proprietà o un metodo, come illustrato nell'esempio seguente.

```
[Export]
[Name("Scarlet")]
[Order(After = "Selection", Before = "Text")]
public AdornmentLayerDefinition scarletLayerDefinition;
```

### <a name="import-a-mef-export"></a>Importare un'esportazione MEF
 Quando si desidera utilizzare un'esportazione MEF, è necessario conoscerlo (in genere il tipo) in base al quale è stato esportato e aggiungere un <xref:System.ComponentModel.Composition.ImportAttribute> attributo con tale valore. Per impostazione predefinita, l'attributo Import accetta un parametro, ovvero il tipo della classe che modifica. Le righe di codice seguenti importano il tipo di <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>.

```
[Import]
internal IClassificationTypeRegistryService ClassificationRegistry;
```

## <a name="get-editor-functionality-from-a-mef-component-part"></a>Ottenere la funzionalità dell'editor da una parte del componente MEF
 Se il codice esistente è una parte del componente MEF, è possibile utilizzare i metadati MEF per utilizzare le parti del componente dell'editor.

#### <a name="to-consume-editor-functionality-from-a-mef-component-part"></a>Per utilizzare la funzionalità dell'editor da una parte del componente MEF

1. Aggiungere riferimenti a *System. Composition. ComponentModel. dll*, che si trova nel Global Assembly Cache (GAC) e negli assembly dell'editor.

2. Aggiungere le direttive using pertinenti.

    ```
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio.Text;
    ```

3. Aggiungere l'attributo `[Import]` all'interfaccia del servizio, come indicato di seguito.

    ```
    [Import]
    ITextBufferFactoryService textBufferService;
    ```

4. Una volta ottenuto il servizio, è possibile utilizzare uno dei relativi componenti.

5. Dopo aver compilato l'assembly, inserirlo in *.. \Common7\IDE\Components \* cartella dell'installazione di Visual Studio.

## <a name="see-also"></a>Vedere anche
- [Punti di estensione Editor e servizio di linguaggio](../extensibility/language-service-and-editor-extension-points.md)
