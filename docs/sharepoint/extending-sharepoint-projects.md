---
title: Estensione SharePoint progetti | Microsoft Docs
description: Informazioni su come creare un'estensione di progetto quando si vogliono personalizzare le funzionalità a livello di progetto SharePoint progetti.
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
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: c86d67b76169381c6b14d45e30fc6262dccf6d65cbf5897555397b7619bb5de0
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121425405"
---
# <a name="extend-sharepoint-projects"></a>Estendere SharePoint progetti
  Creare un'estensione di progetto quando si vogliono personalizzare le funzionalità a livello di progetto SharePoint progetti. Ad esempio, è possibile aggiungere proprietà di progetto personalizzate o rispondere agli eventi a livello di progetto generati quando l'utente sviluppa una soluzione SharePoint in Visual Studio.

## <a name="create-project-extensions"></a>Creare estensioni di progetto
 Per estendere un elemento di progetto, compilare un assembly Visual Studio di estensione che implementa <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> l'interfaccia . Per altre informazioni, vedere [Procedura: Creare un'estensione SharePoint progetto .](../sharepoint/how-to-create-a-sharepoint-project-extension.md)

 Quando si crea un'estensione di progetto, è anche possibile aggiungere le funzionalità seguenti ai progetti SharePoint progetto:

- Aggiungere una voce di menu di scelta rapida. La voce di menu viene visualizzata quando si apre il menu di scelta rapida per un nodo di progetto SharePoint in **Esplora soluzioni** facendo clic con il pulsante destro del mouse sul nodo o scegliendolo e quindi premendo + **MAIUSC+F10.** Per altre informazioni, vedere [Procedura: Aggiungere una voce di menu](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)di scelta rapida per SharePoint progetti .

- Aggiungere una proprietà personalizzata. La proprietà viene visualizzata nella **finestra Proprietà** quando si sceglie un progetto SharePoint in **Esplora soluzioni**. Per altre informazioni, vedere [Procedura: Aggiungere una proprietà per SharePoint progetti](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).

  Per una procedura dettagliata che illustra come creare, distribuire e testare un'estensione di progetto, vedere [Procedura dettagliata:](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)Creare un'estensione SharePoint progetto .

## <a name="understand-the-relationship-between-project-extensions-and-project-instances"></a>Comprendere la relazione tra le estensioni di progetto e le istanze del progetto
 Quando si crea un'estensione di progetto, l'estensione viene caricata quando un SharePoint progetto viene aperto in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]include diversi SharePoint di progetto, ad esempio definizioni di elenco, tipi di contenuto e ricevitori di eventi. Esiste tuttavia un solo tipo SharePoint progetto. I tipi di progetto visualizzati nella finestra **di dialogo Nuovo Project** sono solo modelli che aggregano uno o più elementi SharePoint progetto. Poiché esiste un solo tipo SharePoint progetto, le estensioni create per un progetto si applicano a tutti SharePoint progetto. Non è ad esempio possibile creare un'estensione che si applica solo a un **progetto tipo di** contenuto.

 Per accedere a un'istanza di progetto specifica, gestire uno degli <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents> eventi del *parametro projectService* nell'implementazione del <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> metodo . Ad esempio, per determinare quando un SharePoint progetto viene aggiunto a una soluzione, gestire <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded> l'evento . Per altre informazioni, vedere [Procedura: Creare un'estensione SharePoint progetto .](../sharepoint/how-to-create-a-sharepoint-project-extension.md)

## <a name="see-also"></a>Vedi anche
- [Procedura: Creare un'estensione SharePoint progetto](../sharepoint/how-to-create-a-sharepoint-project-extension.md)
- [Procedura: Aggiungere una voce di menu di scelta rapida per SharePoint progetti](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)
- [Procedura: Aggiungere una proprietà ai SharePoint progetto](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)
- [Procedura dettagliata: Creare un'estensione SharePoint progetto](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)
- [Definire tipi di SharePoint di progetto personalizzati](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Estendere SharePoint di progetto](../sharepoint/extending-sharepoint-project-items.md)
- [Estendere SharePoint creazione di pacchetti e distribuzione](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [Estendere il SharePoint di progetto](../sharepoint/extending-the-sharepoint-project-system.md)
