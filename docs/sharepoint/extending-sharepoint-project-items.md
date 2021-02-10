---
title: Estensione di elementi di progetto SharePoint | Microsoft Docs
description: Esaminare le attività per estendere gli elementi del progetto SharePoint. Informazioni sulla correlazione tra le estensioni degli elementi di progetto e le istanze degli elementi di progetto.
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
ms.workload:
- office
ms.openlocfilehash: e8486120b0f08077bc30c2a5177a8aba915c37f4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948674"
---
# <a name="extend-sharepoint-project-items"></a>Estendi elementi di progetto SharePoint
  Creare un'estensione di elemento del progetto quando si desidera aggiungere funzionalità a un tipo di elemento di progetto SharePoint già installato in Visual Studio. Ad esempio, è possibile creare un'estensione per il **ricevitore di eventi** incorporato o gli elementi di progetto di **definizione elenco** in Visual Studio oppure è possibile creare un'estensione per un tipo di elemento di progetto personalizzato. È inoltre possibile creare un'estensione per tutti i tipi di elementi del progetto SharePoint.

## <a name="tasks-for-extending-sharepoint-project-items"></a>Attività per l'estensione di elementi di progetto SharePoint
 Per estendere un elemento del progetto, compilare un assembly dell'estensione di Visual Studio che implementi l' <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> interfaccia. Per altre informazioni, vedere [procedura: creare un'estensione di elemento di progetto SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).

 Quando si estende un elemento del progetto, è anche possibile aggiungere le funzionalità seguenti all'elemento del progetto:

- Aggiungere una voce di menu di scelta rapida all'elemento del progetto. La voce di menu viene visualizzata quando si apre il menu di scelta rapida per l'elemento del progetto in **Esplora soluzioni**. Per aprire il menu di scelta rapida, fare clic con il pulsante destro del mouse sull'elemento del progetto o scegliendo il tasto **MAIUSC** + **F10** . Per ulteriori informazioni, vedere [procedura: aggiungere una voce di menu di scelta rapida a un'estensione di elemento del progetto SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md).

- Aggiungere una proprietà personalizzata all'elemento del progetto. La proprietà viene visualizzata nella finestra **Proprietà** quando si sceglie l'elemento del progetto in **Esplora soluzioni**. Per altre informazioni, vedere [procedura: aggiungere una proprietà a un'estensione di elemento del progetto SharePoint](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md).

  Per una procedura dettagliata in cui viene illustrato come creare, distribuire e testare un'estensione di elemento di progetto, vedere [procedura dettagliata: estendere un tipo di elemento di progetto SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md).

## <a name="understand-the-relationship-between-project-item-extensions-and-project-item-instances"></a>Comprendere la relazione tra le estensioni degli elementi del progetto e le istanze degli elementi di progetto
 Quando si crea un'estensione di elemento di progetto, Visual Studio carica l'estensione quando un elemento del progetto del tipo associato viene aggiunto a un progetto SharePoint. Se, ad esempio, si crea un'estensione per gli elementi di progetto del **ricevitore di eventi** , Visual Studio carica l'estensione quando un utente aggiunge un elemento di progetto **ricevitore di eventi** a un progetto. Visual Studio usa la stessa istanza dell'estensione per tutte le istanze del tipo di elemento di progetto associato. Nell'esempio precedente, se l'utente aggiunge un secondo elemento del progetto **ricevitore di eventi** al progetto, viene utilizzata la stessa istanza dell'estensione per personalizzare il secondo elemento del progetto.

 Per accedere a un'istanza specifica del tipo di elemento del progetto che si sta estendendo, gestire uno degli <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> eventi del parametro *projectItemType* nell'implementazione del <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> metodo. Per determinare, ad esempio, quando un elemento del progetto del tipo che si sta estendendo viene aggiunto a un progetto, gestire l' <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> evento. Per altre informazioni, vedere [procedura: creare un'estensione di elemento di progetto SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).

## <a name="identifiers-for-sharepoint-project-items"></a>Identificatori per elementi di progetto SharePoint
 Ogni elemento del progetto SharePoint dispone di un identificatore di stringa corrispondente. Se si desidera eseguire le attività seguenti, è necessario conoscerne l'identificatore per un elemento di progetto:

- Creare un'estensione per l'elemento del progetto. In questo caso, è necessario passare l'identificatore per l'elemento del progetto che si desidera estendere al costruttore di <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> . Per creare un'estensione per tutti i tipi di elemento di progetto, passare il **\\** valore stringa *.

- Aggiungere l'elemento di progetto a un progetto a livello di codice. In questo caso, è necessario passare l'identificatore per l'elemento del progetto al <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemCollection.Add%2A> metodo.

  Nella tabella seguente sono elencati gli identificatori per gli elementi del progetto SharePoint inclusi in Visual Studio.

|Nome elemento progetto|Identificatore di stringa|
|-----------------------|-----------------------|
|Modello di Business Data Catalog|Microsoft. VisualStudio. SharePoint. BusinessDataConnectivity|
|Tipo di contenuto|Microsoft. VisualStudio. SharePoint. ContentType|
|Ricevitore di eventi|Microsoft. VisualStudio. SharePoint. EventHandler|
|Elemento vuoto|Microsoft. VisualStudio. SharePoint. Genericelement|
|Definizione elenco<br /><br /> Definizione di elenco dal tipo di contenuto|Microsoft. VisualStudio. SharePoint. ListDefinition|
|Istanza di elenco|Microsoft. VisualStudio. SharePoint. ListInstance|
|Modulo|Microsoft. VisualStudio. SharePoint. Module|
|Flusso di lavoro sequenziale<br /><br /> StateMachineWorkflow|Microsoft. VisualStudio. SharePoint. Workflow|
|Definizione del sito|Microsoft. VisualStudio. SharePoint. SiteDefinition|
|Web part visiva|Microsoft. VisualStudio. SharePoint. VisualWebPart|
|Web part|Microsoft. VisualStudio. SharePoint. WebPart|
|Form di associazione del flusso di lavoro|Microsoft. VisualStudio. SharePoint. WorkflowAssociation|

## <a name="see-also"></a>Vedi anche
- [Procedura: creare un'estensione di elemento di progetto SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)
- [Procedura: aggiungere una voce di menu di scelta rapida a un'estensione di elemento di progetto SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)
- [Procedura: aggiungere una proprietà a un'estensione di elemento di progetto SharePoint](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)
- [Procedura dettagliata: estensione di un tipo di elemento di progetto SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)
- [Estendere il sistema del progetto SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)
