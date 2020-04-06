---
title: Framework di estensibilità gestita nell'editor Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - using MEF for extensions
ms.assetid: 3f59a285-6c33-4ae3-a4fb-ec1f5aa21bd1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 888c5206b87079cf9fa91cb68e9801cb3c4f8c1a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702872"
---
# <a name="managed-extensibility-framework-in-the-editor"></a>Managed Extensibility Framework nell'editor
L'editor viene compilato utilizzando i componenti Managed Extensibility Framework (MEF). È possibile compilare i propri componenti MEF per estendere l'editor e il codice può utilizzare anche i componenti dell'editor.

## <a name="overview-of-the-managed-extensibility-framework"></a>Panoramica del framework di estensibilità gestita
 MEF è una libreria .NET che consente di aggiungere e modificare le funzionalità di un'applicazione o di un componente che segue il modello di programmazione MEF. L'editor di Visual Studio può fornire e utilizzare parti del componente MEF.

 MEF è contenuto nell'assembly *System.ComponentModel.Composition.dll* di .NET Framework versione 4.

 Per ulteriori informazioni su MEF, vedere [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).

### <a name="component-parts-and-composition-containers"></a>Parti componenti e contenitori di composizione
 Una parte componente è una classe o un membro di una classe che può eseguire una o entrambe le operazioni seguenti:

- Consumare un altro componente

- Essere consumato da un altro componente

  Si consideri, ad esempio, un'applicazione di acquisti con un componente di immissione ordini che dipende dai dati sulla disponibilità del prodotto forniti da un componente di magazzino warehouse. In termini MEF, la parte di magazzino può *esportare* i dati sulla disponibilità dei prodotti e la parte di immissione ordini può *importare* i dati. La parte di immissione dell'ordine e la parte di magazzino non devono conoscere l'una dell'altra; il *contenitore* di composizione (fornito dall'applicazione host) è responsabile del mantenimento dell'insieme delle esportazioni e della risoluzione delle esportazioni e delle importazioni.

  Il contenitore <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>di composizione, , è in genere di proprietà dell'host. Il contenitore di composizione gestisce un *catalogo* dei componenti esportati.

### <a name="export-and-import-component-parts"></a>Esportare e importare parti componente
 È possibile esportare qualsiasi funzionalità, purché venga implementata come classe pubblica o come membro pubblico di una classe (proprietà o metodo). Non è necessario derivare la <xref:System.ComponentModel.Composition.Primitives.ComposablePart>parte componente da . È invece necessario <xref:System.ComponentModel.Composition.ExportAttribute> aggiungere un attributo alla classe o al membro della classe che si desidera esportare. Questo attributo specifica il *contratto* in base al quale un'altra parte componente può importare la funzionalità.

### <a name="the-export-contract"></a>Il contratto di esportazione
 L'oggetto <xref:System.ComponentModel.Composition.ExportAttribute> definisce l'entità (classe, interfaccia o struttura) che viene esportata. In genere, l'attributo export accetta un parametro che specifica il tipo di esportazione.

```
[Export(typeof(ContentTypeDefinition))]
class TestContentTypeDefinition : ContentTypeDefinition {   }
```

 Per impostazione <xref:System.ComponentModel.Composition.ExportAttribute> predefinita, l'attributo definisce un contratto che è il tipo della classe di esportazione.

```
[Export]
[Name("Structure")]
[Order(After = "Selection", Before = "Text")]
class TestAdornmentLayerDefinition : AdornmentLayerDefinition {   }
```

 Nell'esempio, l'attributo `[Export]` `[Export(typeof(TestAdornmentLayerDefinition))]`default è equivalente a .

 È inoltre possibile esportare una proprietà o un metodo, come illustrato nell'esempio seguente.

```
[Export]
[Name("Scarlet")]
[Order(After = "Selection", Before = "Text")]
public AdornmentLayerDefinition scarletLayerDefinition;
```

### <a name="import-a-mef-export"></a>Importare un'esportazione MEF
 Quando si desidera utilizzare un'esportazione MEF, è necessario conoscere il contratto (in <xref:System.ComponentModel.Composition.ImportAttribute> genere il tipo) con cui è stato esportato e aggiungere un attributo con tale valore. Per impostazione predefinita, l'attributo import accetta un parametro, ovvero il tipo della classe che modifica. Le seguenti righe di <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService> codice importano il tipo.

```
[Import]
internal IClassificationTypeRegistryService ClassificationRegistry;
```

## <a name="get-editor-functionality-from-a-mef-component-part"></a>Ottenere la funzionalità dell'editor da una parte componente MEFGet editor functionality from a MEF component part
 Se il codice esistente è una parte del componente MEF, è possibile utilizzare i metadati MEF per utilizzare le parti del componente editor.

#### <a name="to-consume-editor-functionality-from-a-mef-component-part"></a>Per utilizzare la funzionalità dell'editor da una parte componente MEF

1. Aggiungere riferimenti a *System.Composition.ComponentModel.dll*, che si trova nella Global Assembly Cache (GAC), e agli assembly dell'editor.

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

4. Una volta ottenuto il servizio, è possibile utilizzarne uno qualsiasi.

5. Dopo aver compilato l'assembly, inserirlo nel file .. \* cartella di componenti dell'installazione di Visual Studio.

## <a name="see-also"></a>Vedere anche
- [Punti di estensione del servizio di linguaggio e dell'editor](../extensibility/language-service-and-editor-extension-points.md)
