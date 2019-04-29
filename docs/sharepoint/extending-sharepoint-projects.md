---
title: Estensione di progetti SharePoint | Microsoft Docs
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
ms.openlocfilehash: 6bc92d65ed179c7f2cb2f569a7d254a025887845
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62967481"
---
# <a name="extend-sharepoint-projects"></a>Estendere i progetti SharePoint
  Creare un'estensione di progetto quando si desidera personalizzare le funzionalità a livello di progetto dei progetti di SharePoint. Ad esempio, è possibile aggiungere le proprietà di progetto personalizzati, o rispondere a eventi a livello di progetto che vengono generati quando si sviluppa una soluzione di SharePoint in Visual Studio.

## <a name="create-project-extensions"></a>Creare estensioni per il progetto
 Per estendere un elemento del progetto, creare un assembly di estensioni di Visual Studio che implementa il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> interfaccia. Per altre informazioni, vedere [Procedura: Creare un'estensione di progetto SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).

 Quando si crea un'estensione di progetto, è anche possibile aggiungere le funzionalità seguenti per i progetti di SharePoint:

- Aggiungere una voce di menu di scelta rapida. La voce di menu viene visualizzato quando si apre il menu di scelta rapida per un nodo di progetto SharePoint in **Esplora soluzioni** facendo clic sul nodo o scegliendolo e quindi scegliendo il **MAIUSC** +  **F10** chiavi. Per altre informazioni, vedere [Procedura: Aggiungere una voce di menu di scelta rapida ai progetti SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md).

- Aggiungere una proprietà personalizzata. La proprietà viene visualizzata nel **delle proprietà** finestra quando si sceglie un progetto SharePoint in **Esplora soluzioni**. Per altre informazioni, vedere [Procedura: Aggiungere una proprietà ai progetti SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).

  Per una procedura dettagliata che illustra come creare, distribuire e testare un'estensione di progetto, vedere [procedura dettagliata: Creare un'estensione di progetto SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md).

## <a name="understand-the-relationship-between-project-extensions-and-project-instances"></a>Comprendere la relazione tra le estensioni di progetto e le istanze del progetto
 Quando si crea un'estensione di progetto, l'estensione viene caricata quando qualsiasi tipo di progetto SharePoint viene aperto in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] include vari modelli di progetto SharePoint, ad esempio le definizioni di elenco, i tipi di contenuto e i ricevitori di eventi. Tuttavia, è presente un solo tipo di progetto SharePoint. I tipi di progetto che vengono visualizzati nei **nuovo progetto** nella finestra di dialogo sono solo i modelli che raggruppano uno o più elementi di progetto SharePoint. Poiché è presente un solo tipo di progetto SharePoint, le estensioni create per un progetto si applicano a tutti i progetti SharePoint. È ad esempio, non è possibile, creare un'estensione che si applica solo a un **tipo di contenuto** progetto.

 Per accedere a un'istanza del progetto specifico, gestire uno dei <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents> eventi del *projectService* parametri nell'implementazione del <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> (metodo). Ad esempio, per determinare quando viene aggiunto un progetto SharePoint a una soluzione, gestiscono il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded> evento. Per altre informazioni, vedere [Procedura: Creare un'estensione di progetto SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).

## <a name="see-also"></a>Vedere anche
- [Procedura: Creare un'estensione di progetto SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)
- [Procedura: Aggiungere una voce di menu di scelta rapida ai progetti SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)
- [Procedura: Aggiungere una proprietà ai progetti SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)
- [Procedura dettagliata: Creare un'estensione di progetto SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)
- [Definire tipi di elemento di progetto SharePoint personalizzati](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Estendere gli elementi di progetto SharePoint](../sharepoint/extending-sharepoint-project-items.md)
- [Estendere la distribuzione e creazione di pacchetti di SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [Estendere il sistema di progetto SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)
