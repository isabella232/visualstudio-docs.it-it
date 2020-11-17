---
title: Definizione di tipi di elementi di progetto SharePoint personalizzati | Microsoft Docs
description: Definire un tipo di elemento di progetto SharePoint personalizzato quando si desidera creare un nuovo tipo di elemento di progetto SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: fc2e3670dd734b368795f270fa6c1d63c8c079e8
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672834"
---
# <a name="define-custom-sharepoint-project-item-types"></a>Definire i tipi di elementi di progetto SharePoint personalizzati
  Definire un nuovo tipo di elemento di progetto SharePoint quando si desidera creare un nuovo tipo di elemento di progetto SharePoint. Ad esempio, Visual Studio non include gli elementi del progetto SharePoint per l'aggiunta di campi o azioni personalizzate a un sito di SharePoint. È possibile definire tipi personalizzati di elementi di progetto SharePoint per la creazione di campi, azioni personalizzate o altri tipi di componenti di SharePoint.

## <a name="tasks-for-defining-sharepoint-project-item-types"></a>Attività per la definizione di tipi di elementi di progetto SharePoint
 Per definire un tipo di elemento di progetto personalizzato, compilare un assembly dell'estensione di Visual Studio che implementi l' <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> interfaccia. Per altre informazioni, vedere [procedura: definire un tipo di elemento di progetto SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).

 Quando si definisce un tipo di elemento di progetto personalizzato, è anche possibile aggiungere le funzionalità seguenti all'elemento del progetto:

- Aggiungere una voce di menu di scelta rapida all'elemento del progetto. La voce di menu viene visualizzata quando si apre il menu di scelta rapida per l'elemento del progetto in **Esplora soluzioni** facendo clic con il pulsante destro del mouse sull'elemento del progetto oppure scegliendo il tasto **MAIUSC** + **F10** . Per ulteriori informazioni, vedere [procedura: aggiungere una voce di menu di scelta rapida a un tipo di elemento di progetto SharePoint personalizzato](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md).

- Aggiungere una proprietà personalizzata all'elemento del progetto. La proprietà viene visualizzata nella finestra **Proprietà** quando si sceglie l'elemento del progetto in **Esplora soluzioni**. Per altre informazioni, vedere [procedura: aggiungere una proprietà a un tipo di elemento di progetto SharePoint personalizzato](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).

  Per consentire ad altri sviluppatori di usare l'elemento di progetto in Visual Studio, creare un file con estensione spdata e creare un modello di elemento o un modello di progetto associato all'elemento del progetto. Per altre informazioni, vedere [creare modelli di elementi e modelli di progetto per gli elementi del progetto SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

## <a name="understand-the-relationship-between-project-item-types-and-project-item-instances"></a>Comprendere la relazione tra i tipi di elemento di progetto e le istanze di elementi di progetto
 Quando si definisce un tipo di elemento di progetto SharePoint, Visual Studio carica l'estensione quando un elemento del progetto del tipo associato viene aggiunto a un progetto SharePoint. Se, ad esempio, si definisce un nuovo tipo di elemento di progetto **azione personalizzata** , Visual Studio carica l'estensione quando un utente aggiunge un elemento del progetto di **azione personalizzata** a un progetto. Visual Studio usa la stessa istanza dell'estensione per tutte le istanze del tipo di elemento di progetto associato. Nell'esempio precedente, se l'utente aggiunge un secondo elemento del progetto di **azione personalizzata** al progetto, viene utilizzata la stessa istanza dell'estensione per personalizzare il secondo elemento del progetto.

 Per accedere a un'istanza specifica del tipo di elemento del progetto, gestire uno degli <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> eventi del parametro *ProjectItemTypeDefinition* nell'implementazione del <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> metodo. Ad esempio, per determinare quando un elemento del progetto del tipo personalizzato viene aggiunto a un progetto, gestire l' <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> evento. Per altre informazioni, vedere [procedura: definire un tipo di elemento di progetto SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).

## <a name="see-also"></a>Vedere anche
- [Procedura: definire un tipo di elemento di progetto SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)
- [Procedura: aggiungere una proprietà a un tipo di elemento di progetto SharePoint personalizzato](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)
- [Procedura: aggiungere una voce di menu di scelta rapida a un tipo di elemento di progetto SharePoint personalizzato](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)
- [Creare modelli di elementi e modelli di progetto per gli elementi di progetto SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [Procedura dettagliata: creare un elemento di progetto azione personalizzata con un modello di elemento, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [Procedura dettagliata: creare un elemento di progetto colonna del sito con un modello di progetto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)
- [Procedura dettagliata: creare un elemento di progetto azione personalizzata con un modello di elemento, parte 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)
- [Procedura dettagliata: creare un elemento di progetto colonna del sito con un modello di progetto, parte 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)
- [Distribuire estensioni per gli strumenti di SharePoint in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)
