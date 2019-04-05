---
title: Managed Extensibility Framework nell'Editor | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - using MEF for extensions
ms.assetid: 3f59a285-6c33-4ae3-a4fb-ec1f5aa21bd1
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 589e392530238249eefb789170f4f986b24a8551
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58964931"
---
# <a name="managed-extensibility-framework-in-the-editor"></a>Managed Extensibility Framework nell'editor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L'editor viene compilato con componenti di Managed Extensibility Framework (MEF). È possibile compilare i componenti MEF per estendere l'editor e il codice può utilizzare anche i componenti dell'editor.  
  
## <a name="overview-of-the-managed-extensibility-framework"></a>Panoramica di Managed Extensibility Framework  
 La libreria MEF è una libreria .NET che consente di aggiungere e modificare le funzionalità di un'applicazione o componente che segue il modello di programmazione MEF. Editor di Visual Studio possa fornire sia utilizzare parti componente MEF.  
  
 La libreria MEF è contenuta nell'assembly .NET Framework versione 4 System.ComponentModel.Composition.dll.  
  
 Per altre informazioni su MEF, vedere [Managed Extensibility Framework (MEF)](http://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde).  
  
### <a name="component-parts-and-composition-containers"></a>Parti componenti e i contenitori di composizione  
 Una parte del componente è una classe o un membro di una classe che è possibile eseguire uno (o entrambe) delle operazioni seguenti:  
  
- Utilizzare un altro componente  
  
- Essere utilizzati da un altro componente  
  
  Ad esempio, si consideri un'applicazione di acquisti che dispone di un componente di voce dell'ordine che dipende dai dati disponibilità del prodotto forniti da un componente di inventario di magazzino. In termini MEF, è possibile la parte di inventario *esportare* dati disponibilità del prodotto e la parte voce ' ultimo possa *importare* i dati. La voce dell'ordine e parte inventario non è necessario conoscere a vicenda. il *contenitore di composizione* (fornito dall'applicazione host) è responsabile della manutenzione il set di esportazioni e risolvere le esportazioni e importazioni.  
  
  Il contenitore di composizione, <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>, in genere è di proprietà dell'host. Il contenitore di composizione conserva un *catalogo* delle parti di componente esportata.  
  
### <a name="exporting-and-importing-component-parts"></a>Esportazione e importazione di parti di componente  
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
  
### <a name="importing-a-mef-export"></a>L'importazione di un'esportazione MEF  
 Quando si desidera utilizzare un'esportazione MEF, è necessario conoscere il contratto (in genere del tipo) mediante il quale è stato esportato e aggiungere un <xref:System.ComponentModel.Composition.ImportAttribute> attributo con quel valore. Per impostazione predefinita, l'attributo import accetta un parametro, ovvero il tipo della classe che viene modificato. Le seguenti righe di importazione di codice il <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService> tipo.  
  
```  
[Import]  
internal IClassificationTypeRegistryService ClassificationRegistry;  
```  
  
## <a name="getting-editor-functionality-from-a-mef-component-part"></a>Recupero di funzionalità dell'Editor da una parte del componente MEF  
 Se il codice esistente è una parte del componente MEF, è possibile usare metadati MEF per utilizzare i componenti dell'editor.  
  
#### <a name="to-consume-editor-functionality-from-a-mef-component-part"></a>Per utilizzare la funzionalità dell'editor da una parte del componente MEF  
  
1.  Aggiungere i riferimenti a System.Composition.ComponentModel.dll, disponibile in global assembly cache (GAC), e gli assembly dell'editor.  
  
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
  
5.  Quando è stato compilato l'assembly, inserirlo nel... Cartella \Common7\IDE\Components\ dell'installazione di Visual Studio.  
  
## <a name="see-also"></a>Vedere anche  
 [Punti di estensione dei servizi di linguaggio e dell'editor](../extensibility/language-service-and-editor-extension-points.md)
