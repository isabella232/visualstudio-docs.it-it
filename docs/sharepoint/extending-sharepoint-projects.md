---
title: Estensione di progetti SharePoint | Microsoft Docs
description: Informazioni su come creare un'estensione di progetto quando si desidera personalizzare le funzionalità a livello di progetto dei progetti SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ae4c3c1e606fd436725ef9f54a4568b754b048af
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672639"
---
# <a name="extend-sharepoint-projects"></a>Estensione di progetti SharePoint
  Creare un'estensione di progetto quando si desidera personalizzare le funzionalità a livello di progetto dei progetti SharePoint. Ad esempio, è possibile aggiungere proprietà di progetto personalizzate o rispondere agli eventi a livello di progetto generati quando l'utente sviluppa una soluzione SharePoint in Visual Studio.

## <a name="create-project-extensions"></a>Creazione di estensioni di progetto
 Per estendere un elemento del progetto, compilare un assembly dell'estensione di Visual Studio che implementi l' <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> interfaccia. Per altre informazioni, vedere [procedura: creare un'estensione di progetto SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).

 Quando si crea un'estensione di progetto, è inoltre possibile aggiungere le funzionalità seguenti ai progetti SharePoint:

- Aggiungere una voce di menu di scelta rapida. La voce di menu viene visualizzata quando si apre il menu di scelta rapida per un nodo di progetto SharePoint in **Esplora soluzioni** facendo clic con il pulsante destro del mouse sul nodo oppure scegliendo **MAIUSC** + **F10** . Per ulteriori informazioni, vedere [procedura: aggiungere una voce di menu di scelta rapida ai progetti SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md).

- Aggiungere una proprietà personalizzata. La proprietà viene visualizzata nella finestra **Proprietà** quando si sceglie un progetto SharePoint in **Esplora soluzioni**. Per altre informazioni, vedere [procedura: aggiungere una proprietà ai progetti SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).

  Per una procedura dettagliata in cui viene illustrato come creare, distribuire e testare un'estensione di progetto, vedere [procedura dettagliata: creare un'estensione di progetto SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md).

## <a name="understand-the-relationship-between-project-extensions-and-project-instances"></a>Comprendere la relazione tra le estensioni di progetto e le istanze del progetto
 Quando si crea un'estensione di progetto, l'estensione viene caricata quando un qualsiasi tipo di progetto SharePoint viene aperto in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] include diversi modelli di progetto SharePoint, ad esempio definizioni di elenco, tipi di contenuto e ricevitori di eventi. Tuttavia, esiste un solo tipo di progetto SharePoint. I tipi di progetto visualizzati nella finestra di dialogo **nuovo progetto** sono solo modelli che raggruppano uno o più elementi del progetto SharePoint. Poiché è presente un solo tipo di progetto SharePoint, le estensioni create per un progetto si applicano a tutti i progetti SharePoint. Non è possibile, ad esempio, creare un'estensione che si applica solo a un progetto di **tipo di contenuto** .

 Per accedere a un'istanza del progetto specifica, gestire uno degli <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents> eventi del parametro *ProjectService* nell'implementazione del <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> metodo. Per determinare, ad esempio, quando un progetto SharePoint viene aggiunto a una soluzione, gestire l' <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded> evento. Per altre informazioni, vedere [procedura: creare un'estensione di progetto SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).

## <a name="see-also"></a>Vedere anche
- [Procedura: creare un'estensione di progetto SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)
- [Procedura: aggiungere una voce di menu di scelta rapida ai progetti SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)
- [Procedura: aggiungere una proprietà ai progetti SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)
- [Procedura dettagliata: creare un'estensione di progetto SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)
- [Definire i tipi di elementi di progetto SharePoint personalizzati](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Estendi elementi di progetto SharePoint](../sharepoint/extending-sharepoint-project-items.md)
- [Estensione della creazione di pacchetti e della distribuzione di SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [Estendere il sistema del progetto SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)
