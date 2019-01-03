---
title: Managed Extensibility Framework nell'Editor | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - using MEF for extensions
ms.assetid: 3f59a285-6c33-4ae3-a4fb-ec1f5aa21bd1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a295d3e3474f478cf3a2aa3efc2e0cefc3086b00
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53925667"
---
# <a name="managed-extensibility-framework-in-the-editor"></a>Managed Extensibility Framework nell'editor
L'editor viene compilato con componenti di Managed Extensibility Framework (MEF). È possibile compilare i componenti MEF per estendere l'editor e il codice può utilizzare anche i componenti dell'editor.  
  
## <a name="overview-of-the-managed-extensibility-framework"></a>Panoramica di Managed Extensibility Framework  
 La libreria MEF è una libreria .NET che consente di aggiungere e modificare le funzionalità di un'applicazione o componente che segue il modello di programmazione MEF. Editor di Visual Studio possa fornire sia utilizzare parti componente MEF.  
  
 In .NET Framework versione 4 è contenuta la MEF *System.ComponentModel.Composition.dll* assembly.  
  
 Per altre informazioni su MEF, vedere [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).  
  
### <a name="component-parts-and-composition-containers"></a>Parti componenti e i contenitori di composizione  
 Una parte del componente è una classe o un membro di una classe che è possibile eseguire uno (o entrambe) delle operazioni seguenti:  
  
- Utilizzare un altro componente  
  
- Essere utilizzati da un altro componente  
  
  Ad esempio, si consideri un'applicazione di acquisti che dispone di un componente di voce dell'ordine che dipende dai dati disponibilità del prodotto forniti da un componente di inventario di magazzino. In termini MEF, è possibile la parte di inventario *esportare* dati disponibilità del prodotto e la parte voce ' ultimo possa *importare* i dati. La voce dell'ordine e parte inventario non è necessario conoscere a vicenda. il *contenitore di composizione* (fornito dall'applicazione host) è responsabile della manutenzione il set di esportazioni e risolvere le esportazioni e importazioni.  
  
  Il contenitore di composizione, <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>, in genere è di proprietà dell'host. Il contenitore di composizione conserva un *catalogo* delle parti di componente esportata.  
  
### <a name="export-and-import-component-parts"></a>Esportare e importare parti componente  
 È possibile esportare alcuna funzionalità, fino a quando viene implementato come classe pubblica o un membro pubblico di una classe (proprietà o metodo). Non è necessario derivare da parte dell'utente componente <xref:System.ComponentModel.Composition.Primitives.ComposablePart>. In alternativa, è necessario aggiungere un <xref:System.ComponentModel.Composition.ExportAttribute> attributo alla classe o membro della classe che si desidera esportare. Questo attributo specifica la *contratto* quale componente di un'altra parte possibile importare le funzionalità.  
  
### <a name="the-export-contract"></a>Il contratto di esportazione  
 Il <xref:System.ComponentModel.Composition.ExportAttribute> definisce l'entità (classe, interfaccia o struttura) da esportare. In genere, l'attributo export accetta un parametro che specifica il tipo dell'esportazione.  
  
```  
[Export(typeof(ContentTypeDefinition))]  
class TestContentTypeDefinition : ContentTypeDefinition {   }  
```  
  
 Per impostazione predefinita, il <xref:System.ComponentModel.Composition.ExportAttribute> attributo definisce un contratto che è il tipo della classe di esportazione.  
  
```  
[Export]  
[Name("Structure")]  
[Order(After = "Selection", Before = "Text")]  
class TestAdornmentLayerDefinition : AdornmentLayerDefinition {   }  
```  
  
 Nell'esempio, il valore predefinito `[Export]` attributo è equivalente a `[Export(typeof(TestAdornmentLayerDefinition))]`.  
  
 È anche possibile esportare una proprietà o metodo, come illustrato nell'esempio seguente.  
  
```  
[Export]  
[Name("Scarlet")]  
[Order(After = "Selection", Before = "Text")]  
public AdornmentLayerDefinition scarletLayerDefinition;  
```  
  
### <a name="import-a-mef-export"></a>Importare un'esportazione MEF  
 Quando si desidera utilizzare un'esportazione MEF, è necessario conoscere il contratto (in genere del tipo) mediante il quale è stato esportato e aggiungere un <xref:System.ComponentModel.Composition.ImportAttribute> attributo con quel valore. Per impostazione predefinita, l'attributo import accetta un parametro, ovvero il tipo della classe che viene modificato. Le seguenti righe di importazione di codice il <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService> tipo.  
  
```  
[Import]  
internal IClassificationTypeRegistryService ClassificationRegistry;  
```  
  
## <a name="get-editor-functionality-from-a-mef-component-part"></a>Ottenere funzionalità dell'editor da una parte del componente MEF  
 Se il codice esistente è una parte del componente MEF, è possibile usare metadati MEF per utilizzare i componenti dell'editor.  
  
#### <a name="to-consume-editor-functionality-from-a-mef-component-part"></a>Per utilizzare la funzionalità dell'editor da una parte del componente MEF  
  
1.  Aggiungere riferimenti agli *System.Composition.ComponentModel.dll*, ovvero nella global assembly cache (GAC) e agli assembly dell'editor.  
  
2.  Aggiungere il relativo utilizzo di istruzioni.  
  
    ```  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.Text;  
    ```  
  
3.  Aggiungere il `[Import]` attributo all'interfaccia di servizio, come indicato di seguito.  
  
    ```  
    [Import]  
    ITextBufferFactoryService textBufferService;  
    ```  
  
4.  Una volta ottenuto il servizio, è possibile usare uno qualsiasi dei relativi componenti.  
  
5.  Quando è stato compilato l'assembly, inserirlo nel *... \Common7\IDE\Components\* cartella di installazione di Visual Studio.  
  
## <a name="see-also"></a>Vedere anche  
 [Punti di estensione del servizio e l'editor di linguaggio](../extensibility/language-service-and-editor-extension-points.md)