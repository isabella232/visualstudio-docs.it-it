---
title: Estensione di elementi di progetto SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d02871b991c999c490aac8aaeafc677711c95266
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53959972"
---
# <a name="extend-sharepoint-project-items"></a>Estendere gli elementi di progetto SharePoint
  Creare un'estensione di elemento di progetto quando si desidera aggiungere funzionalità a un tipo di elemento di progetto SharePoint che è già installato in Visual Studio. Ad esempio, è possibile creare un'estensione per l'oggetto incorporato **ricevitore di eventi** oppure **definizione elenco** gli elementi di progetto in Visual Studio oppure è possibile creare un'estensione per un tipo di elemento di progetto personalizzato. È anche possibile creare un'estensione per tutti i tipi di elementi di progetto SharePoint.  
  
## <a name="tasks-for-extending-sharepoint-project-items"></a>Attività per l'estensione di elementi di progetto SharePoint
 Per estendere un elemento del progetto, creare un assembly di estensioni di Visual Studio che implementa il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> interfaccia. Per altre informazioni, vedere [Procedura: Creare un'estensione di elemento di progetto SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).  
  
 Quando si estende un elemento del progetto, è anche possibile aggiungere le funzionalità seguenti all'elemento del progetto:  
  
- Aggiungere una voce di menu di scelta rapida per l'elemento del progetto. La voce di menu viene visualizzato quando si apre il menu di scelta rapida per l'elemento del progetto in **Esplora soluzioni**. Si apre il menu di scelta rapida facendo clic con l'elemento del progetto o facendo clic su di esso e scegliendo quindi il **Shift**+**F10** chiavi. Per altre informazioni, vedere [Procedura: Aggiungere una voce di menu di scelta rapida per un'estensione di elemento di progetto SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md).  
  
- Aggiungere una proprietà personalizzata per l'elemento del progetto. La proprietà viene visualizzata nel **delle proprietà** finestra quando si sceglie l'elemento del progetto in **Esplora soluzioni**. Per altre informazioni, vedere [Procedura: Aggiungere una proprietà a un'estensione di elemento di progetto SharePoint](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md).  
  
  Per una procedura dettagliata che illustra come creare, distribuire e testare un'estensione di elemento di progetto, vedere [procedura dettagliata: Estendere un tipo di elemento di progetto SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md).  
  
## <a name="understand-the-relationship-between-project-item-extensions-and-project-item-instances"></a>Comprendere la relazione tra estensioni dell'elemento del progetto e le istanze di elemento di progetto
 Quando si crea un'estensione di elemento di progetto, Visual Studio carica l'estensione quando viene aggiunto un elemento di progetto del tipo associato a un progetto SharePoint. Ad esempio, se si crea un'estensione per i **ricevitore di eventi** gli elementi di progetto Visual Studio carica l'estensione quando un utente aggiunge un **ricevitore di eventi** elemento del progetto a un progetto. Visual Studio Usa la stessa istanza dell'estensione per tutte le istanze del tipo di elemento di progetto associato. Nell'esempio precedente, se l'utente aggiunge un secondo **ricevitore di eventi** elemento di progetto al progetto, la stessa istanza dell'estensione viene usata per personalizzare il secondo elemento di progetto.  
  
 Per accedere a un'istanza specifica del tipo di elemento di progetto si estende, gestire uno dei <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> eventi del *projectItemType* parametri nell'implementazione del <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> (metodo). Ad esempio, per determinare quando viene aggiunto un elemento di progetto del tipo si estende a un progetto, gestiscono il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> evento. Per altre informazioni, vedere [Procedura: Creare un'estensione di elemento di progetto SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).  
  
## <a name="identifiers-for-sharepoint-project-items"></a>Identificatori per gli elementi di progetto SharePoint
 Ogni elemento di progetto SharePoint è un identificatore di stringa corrispondente. È necessario conoscere l'identificatore per un elemento del progetto se si desidera eseguire le attività seguenti:  
  
- Creare un'estensione per l'elemento del progetto. In questo caso, è necessario passare l'identificatore per l'elemento del progetto che si vuole estendere al costruttore del <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. Per creare un'estensione per tutti i tipi di progetti elementi, passare il **\\*** valore stringa.  
  
- Aggiungere l'elemento del progetto a un progetto a livello di codice. In questo caso, è necessario passare l'identificatore per l'elemento del progetto per il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemCollection.Add%2A> (metodo).  
  
  Nella tabella seguente sono elencati gli identificatori per gli elementi del progetto SharePoint che sono inclusi con Visual Studio.  
  
|Nome di elemento di progetto|Identificatore di stringa|  
|-----------------------|-----------------------|  
|Modello di catalogo dati business|Microsoft.VisualStudio.SharePoint.BusinessDataConnectivity|  
|Tipo di contenuto|Microsoft.VisualStudio.SharePoint.ContentType|  
|Ricevitore di eventi|Microsoft.VisualStudio.SharePoint.EventHandler|  
|Elemento vuoto|Microsoft.VisualStudio.SharePoint.GenericElement|  
|Definizione di elenco<br /><br /> Definizione di elenco dal tipo di contenuto|Microsoft.VisualStudio.SharePoint.ListDefinition|  
|Istanza di elenco|Microsoft.VisualStudio.SharePoint.ListInstance|  
|Modulo|Microsoft.VisualStudio.SharePoint.Module|  
|Flusso di lavoro sequenziale<br /><br /> Flusso di lavoro della macchina a stati|Microsoft.VisualStudio.SharePoint.Workflow|  
|Definizione di sito|Microsoft.VisualStudio.SharePoint.SiteDefinition|  
|Web Part visiva|Microsoft.VisualStudio.SharePoint.VisualWebPart|  
|Web part|Microsoft.VisualStudio.SharePoint.WebPart|  
|Form di associazione del flusso di lavoro|Microsoft.VisualStudio.SharePoint.WorkflowAssociation|  
  
## <a name="see-also"></a>Vedere anche
 [Procedura: Creare un'estensione di elemento di progetto SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)   
 [Procedura: Aggiungere una voce di menu di scelta rapida per un'estensione di elemento di progetto SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)   
 [Procedura: Aggiungere una proprietà a un'estensione di elemento di progetto SharePoint](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)   
 [Procedura dettagliata: Estendere un tipo di elemento di progetto SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)   
 [Estendere il sistema di progetto SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)  
