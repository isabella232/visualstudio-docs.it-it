---
title: Estensione SharePoint Project elementi | Microsoft Docs
description: Esaminare le attività per l'estensione SharePoint di progetto. Informazioni sul modo in cui sono correlate le estensioni degli elementi di progetto e le istanze degli elementi di progetto.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: dc36a1323b9ce1a1a3db0428a35ad9dd5d092629
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122027201"
---
# <a name="extend-sharepoint-project-items"></a>Estendere SharePoint di progetto
  Creare un'estensione dell'elemento di progetto quando si vuole aggiungere funzionalità a un tipo di SharePoint di progetto già installato in Visual Studio. Ad esempio, è possibile creare un'estensione per  gli elementi di progetto predefinito Ricevitore di eventi o Definizione elenco in Visual Studio oppure è possibile creare un'estensione per un tipo di elemento di progetto personalizzato.  È anche possibile creare un'estensione per tutti i tipi di SharePoint di progetto.

## <a name="tasks-for-extending-sharepoint-project-items"></a>Attività per l'estensione SharePoint di progetto
 Per estendere un elemento di progetto, compilare un assembly Visual Studio di estensione che implementa <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> l'interfaccia . Per altre informazioni, vedere [Procedura: Creare un'estensione di SharePoint progetto .](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)

 Quando si estende un elemento di progetto, è anche possibile aggiungere le funzionalità seguenti all'elemento di progetto:

- Aggiungere una voce di menu di scelta rapida all'elemento del progetto. La voce di menu viene visualizzata quando si apre il menu di scelta rapida per la voce di progetto in **Esplora soluzioni**. Aprire il menu di scelta rapida facendo clic con il pulsante destro del mouse sull'elemento di progetto o scegliendolo e quindi premendo + **MAIUSC+F10.** Per altre informazioni, vedere [Procedura: Aggiungere una voce](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)di menu di scelta rapida a un'estensione SharePoint elemento di progetto .

- Aggiungere una proprietà personalizzata all'elemento di progetto. La proprietà viene visualizzata nella **finestra Proprietà** quando si sceglie l'elemento di progetto in **Esplora soluzioni**. Per altre informazioni, vedere [Procedura: Aggiungere](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)una proprietà a un'estensione di SharePoint progetto .

  Per una procedura dettagliata che illustra come creare, distribuire e testare un'estensione di elemento di progetto, vedere [Procedura dettagliata:](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)Estendere un SharePoint tipo di elemento di progetto .

## <a name="understand-the-relationship-between-project-item-extensions-and-project-item-instances"></a>Informazioni sulla relazione tra le estensioni degli elementi di progetto e le istanze degli elementi di progetto
 Quando si crea un'estensione dell'elemento di progetto, Visual Studio carica l'estensione quando un elemento di progetto del tipo associato viene aggiunto a un SharePoint progetto. Ad esempio, se si  crea un'estensione per gli elementi di progetto del  ricevitore di eventi, Visual Studio carica l'estensione quando un utente aggiunge un elemento di progetto Ricevitore di eventi a un progetto. Visual Studio la stessa istanza dell'estensione per tutte le istanze del tipo di elemento di progetto associato. Nell'esempio precedente, se l'utente aggiunge un secondo elemento di progetto **Event Receiver** al progetto, viene usata la stessa istanza dell'estensione per personalizzare il secondo elemento di progetto.

 Per accedere a un'istanza specifica del tipo di elemento di progetto che si sta estendendo, gestire uno degli eventi del <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> *parametro projectItemType* nell'implementazione del <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> metodo . Ad esempio, per determinare quando un elemento di progetto del tipo che si sta estendendo viene aggiunto a un progetto, gestire <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> l'evento . Per altre informazioni, vedere [Procedura: Creare un'estensione di SharePoint progetto .](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)

## <a name="identifiers-for-sharepoint-project-items"></a>Identificatori per gli SharePoint di progetto
 Ogni SharePoint di progetto ha un identificatore di stringa corrispondente. È necessario conoscere l'identificatore per un elemento di progetto se si desidera eseguire le attività seguenti:

- Creare un'estensione per l'elemento di progetto. In questo caso, è necessario passare l'identificatore per l'elemento di progetto che si desidera estendere al costruttore di <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> . Per creare un'estensione per tutti i tipi di elemento di progetto, passare il **\\** valore stringa * .

- Aggiungere l'elemento di progetto a un progetto a livello di codice. In questo caso, è necessario passare l'identificatore per l'elemento di progetto al <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemCollection.Add%2A> metodo .

  Nella tabella seguente sono elencati gli identificatori per gli SharePoint di progetto inclusi in Visual Studio.

|Project nome dell'elemento|Identificatore di stringa|
|-----------------------|-----------------------|
|Modello Data Catalog business|Microsoft.VisualStudio. SharePoint. BusinessDataConnectivity|
|Tipo di contenuto|Microsoft.VisualStudio. SharePoint. Contenttype|
|Ricevitore di eventi|Microsoft.VisualStudio. SharePoint. Eventhandler|
|Elemento vuoto|Microsoft.VisualStudio. SharePoint. GenericElement|
|Definizione elenco<br /><br /> Definizione elenco da tipo di contenuto|Microsoft.VisualStudio. SharePoint. ListDefinition|
|Istanza di elenco|Microsoft.VisualStudio. SharePoint. ListInstance|
|Modulo|Microsoft.VisualStudio. SharePoint. Modulo|
|Flusso di lavoro sequenziale<br /><br /> StateMachineWorkflow|Microsoft.VisualStudio. SharePoint. Workflow|
|Definizione del sito|Microsoft.VisualStudio. SharePoint. SiteDefinition|
|Web part visiva|Microsoft.VisualStudio. SharePoint. VisualWebPart|
|Web part|Microsoft.VisualStudio. SharePoint. Webpart|
|Form di associazione del flusso di lavoro|Microsoft.VisualStudio. SharePoint. WorkflowAssociation|

## <a name="see-also"></a>Vedi anche
- [Procedura: Creare un'estensione SharePoint elemento di progetto](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)
- [Procedura: Aggiungere una voce di menu di scelta rapida a un'estensione SharePoint elemento di progetto](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)
- [Procedura: Aggiungere una proprietà a un'estensione SharePoint elemento di progetto](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)
- [Procedura dettagliata: Estendere un tipo SharePoint di elemento di progetto](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)
- [Estendere il SharePoint di progetto](../sharepoint/extending-the-sharepoint-project-system.md)
