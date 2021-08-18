---
title: Definizione di tipi di SharePoint Project personalizzati | Microsoft Docs
description: Definire un tipo SharePoint tipo di elemento di progetto quando si vuole creare un nuovo tipo di SharePoint di progetto.
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
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 01360612f19c40d574ea176246e68a1fd0f18ad8
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122149247"
---
# <a name="define-custom-sharepoint-project-item-types"></a>Definire tipi di SharePoint di progetto personalizzati
  Definire un nuovo SharePoint tipo di elemento di progetto quando si vuole creare un nuovo tipo di SharePoint di progetto. Ad esempio, Visual Studio non include elementi SharePoint progetto per l'aggiunta di campi o azioni personalizzate a un SharePoint sito. È possibile definire tipi personalizzati di elementi SharePoint progetto per la creazione di campi, azioni personalizzate o altri tipi di SharePoint componenti.

## <a name="tasks-for-defining-sharepoint-project-item-types"></a>Attività per la definizione di SharePoint tipi di elemento di progetto
 Per definire un tipo di elemento di progetto personalizzato, compilare un assembly Visual Studio'estensione che implementa <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> l'interfaccia . Per altre informazioni, vedere [Procedura: Definire un tipo SharePoint di elemento di progetto](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).

 Quando si definisce un tipo di elemento di progetto personalizzato, è anche possibile aggiungere la funzionalità seguente all'elemento di progetto:

- Aggiungere una voce di menu di scelta rapida all'elemento del progetto. La voce di menu viene visualizzata quando si apre il menu di scelta rapida per l'elemento di progetto in **Esplora soluzioni** facendo clic con il pulsante destro del mouse sull'elemento di progetto o scegliendolo e quindi premendo + **MAIUSC+F10.** Per altre informazioni, vedere Procedura: Aggiungere una voce di menu di scelta rapida [a un tipo di elemento SharePoint progetto personalizzato.](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)

- Aggiungere una proprietà personalizzata all'elemento di progetto. La proprietà viene visualizzata nella **finestra Proprietà** quando si sceglie l'elemento di progetto in **Esplora soluzioni**. Per altre informazioni, vedere Procedura: Aggiungere una proprietà a un tipo [di elemento SharePoint progetto personalizzato.](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)

  Per consentire ad altri sviluppatori di usare l'elemento di progetto in Visual Studio, creare un file con estensione spdata e un modello di elemento o un modello di progetto associato all'elemento di progetto. Per altre informazioni, vedere [Creare modelli di elemento e modelli di progetto per SharePoint di progetto.](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)

## <a name="understand-the-relationship-between-project-item-types-and-project-item-instances"></a>Informazioni sulla relazione tra i tipi di elemento di progetto e le istanze degli elementi di progetto
 Quando si definisce un SharePoint di elemento di progetto, Visual Studio carica l'estensione quando un elemento di progetto del tipo associato viene aggiunto a un SharePoint progetto. Ad esempio, se si  definisce un nuovo tipo di elemento di progetto Azione personalizzata, Visual Studio carica l'estensione quando un utente aggiunge un **elemento** di progetto Azione personalizzata a un progetto. Visual Studio usa la stessa istanza dell'estensione per tutte le istanze del tipo di elemento di progetto associato. Nell'esempio precedente, se l'utente aggiunge un secondo elemento di progetto Azione personalizzata al progetto, la stessa istanza dell'estensione viene usata per personalizzare il secondo elemento di progetto. 

 Per accedere a un'istanza specifica del tipo di elemento di progetto, gestire uno degli eventi del parametro <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> *projectItemTypeDefinition* nell'implementazione del <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> metodo . Ad esempio, per determinare quando un elemento di progetto del tipo personalizzato viene aggiunto a un progetto, gestire <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> l'evento . Per altre informazioni, vedere [Procedura: Definire un tipo SharePoint di elemento di progetto](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).

## <a name="see-also"></a>Vedi anche
- [Procedura: Definire un tipo SharePoint di elemento di progetto](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)
- [Procedura: Aggiungere una proprietà a un tipo di elemento SharePoint progetto personalizzato](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)
- [Procedura: Aggiungere una voce di menu di scelta rapida a un tipo di elemento SharePoint progetto personalizzato](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)
- [Creare modelli di elemento e modelli di progetto per SharePoint di progetto](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [Procedura dettagliata: Creare un elemento di progetto azione personalizzata con un modello di elemento, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [Procedura dettagliata: Creare un elemento di progetto colonna del sito con un modello di progetto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)
- [Procedura dettagliata: Creare un elemento di progetto azione personalizzata con un modello di elemento, parte 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)
- [Procedura dettagliata: Creare un elemento di progetto colonna del sito con un modello di progetto, parte 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)
- [Distribuire estensioni per gli strumenti SharePoint in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)
