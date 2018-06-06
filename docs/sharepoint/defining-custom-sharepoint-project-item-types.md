---
title: Definizione di tipi di elemento di progetto SharePoint personalizzato | Documenti Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d9b752aa8162f52746b4487b863557af6dd37fd9
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/05/2018
ms.locfileid: "34765580"
---
# <a name="define-custom-sharepoint-project-item-types"></a>Definire tipi di elemento di progetto SharePoint personalizzati
  Definire un nuovo tipo di elemento di progetto SharePoint quando si desidera creare un nuovo tipo di elemento di progetto SharePoint. Ad esempio, Visual Studio non include elementi di progetto SharePoint per l'aggiunta di campi o azioni personalizzate a un sito di SharePoint. È possibile definire i propri tipi di elementi di progetto SharePoint per la creazione di campi, le azioni personalizzate o altri tipi di componenti di SharePoint.  
  
## <a name="tasks-for-defining-sharepoint-project-item-types"></a>Attività per la definizione di tipi di elemento di progetto SharePoint
 Per definire un tipo di elemento di progetto personalizzati, compilare un assembly di estensione di Visual Studio che implementa il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> interfaccia. Per ulteriori informazioni, vedere [procedura: definire un tipo di elemento di progetto SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).  
  
 Quando si definisce un tipo di elemento di progetto personalizzati, è anche possibile aggiungere le funzionalità seguenti per l'elemento del progetto:  
  
-   Aggiungere una voce di menu di scelta rapida per l'elemento del progetto. La voce di menu viene visualizzata quando si apre il menu di scelta rapida per l'elemento del progetto in **Esplora soluzioni** facendo clic con l'elemento del progetto o scegliendo quest'ultima e quindi scegliendo il **MAIUSC** +  **F10** chiavi. Per ulteriori informazioni, vedere [procedura: aggiungere una voce di Menu di scelta rapida a un tipo di elemento di progetto SharePoint personalizzato](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md).  
  
-   Aggiungere una proprietà personalizzata per l'elemento del progetto. La proprietà viene visualizzata nel **proprietà** finestra quando si sceglie l'elemento del progetto in **Esplora**. Per ulteriori informazioni, vedere [procedura: aggiungere una proprietà a un tipo di elemento di progetto SharePoint personalizzato](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).  
  
 Per consentire ad altri sviluppatori di utilizzare l'elemento di progetto in Visual Studio, creare un file con estensione spdata e creare un modello di elemento o un modello di progetto che è associato l'elemento del progetto. Per ulteriori informazioni, vedere [la creazione di modelli di elemento e i modelli di progetto per gli elementi di progetto SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
## <a name="understand-the-relationship-between-project-item-types-and-project-item-instances"></a>Comprendere la relazione tra tipi di elemento di progetto e istanze di elementi di progetto
 Quando si definisce un tipo di elemento di progetto SharePoint, Visual Studio consente di caricare l'estensione quando viene aggiunto un elemento di progetto del tipo associato a un progetto SharePoint. Ad esempio, se si definisce un nuovo **l'azione personalizzata** tipo di elemento di progetto, Visual Studio consente di caricare l'estensione quando un utente aggiunge un **l'azione personalizzata** elemento di progetto per un progetto. Visual Studio Usa la stessa istanza dell'estensione per tutte le istanze del tipo di elemento di progetto associato. Nell'esempio precedente, se l'utente aggiunge un secondo **l'azione personalizzata** dell'elemento di progetto al progetto, la stessa istanza dell'estensione viene utilizzata per personalizzare il secondo elemento di progetto.  
  
 Per accedere a un'istanza specifica del tipo di elemento di progetto, gestire uno del <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> gli eventi del *projectItemTypeDefinition* parametro nell'implementazione del <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> metodo. Per determinare quando un elemento di progetto del tipo personalizzato viene aggiunto a un progetto, ad esempio, è consigliabile gestire il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> evento. Per ulteriori informazioni, vedere [procedura: definire un tipo di elemento di progetto SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).  
  
## <a name="see-also"></a>Vedere anche
 [Procedura: definire un tipo di elemento di progetto SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)   
 [Procedura: aggiungere una proprietà a un tipo di elemento di progetto SharePoint personalizzato](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)   
 [Procedura: aggiungere una voce di Menu di scelta rapida a un tipo di elemento di progetto SharePoint personalizzato](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)   
 [Creazione di modelli di elementi e modelli di progetto per gli elementi di progetto SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Procedura dettagliata: Creazione di un elemento di progetto azione personalizzata con un modello di elemento, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [Procedura dettagliata: Creazione di un elemento di progetto colonna del sito con un modello di progetto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)   
 [Procedura dettagliata: Creazione di un elemento di progetto azione personalizzata con un modello di elemento, parte 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)   
 [Procedura dettagliata: Creazione di un elemento di progetto colonna del sito con un modello di progetto, parte 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)   
 [Distribuzione di estensioni per gli strumenti di SharePoint in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
