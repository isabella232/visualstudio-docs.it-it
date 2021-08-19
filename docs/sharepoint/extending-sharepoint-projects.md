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
ms.openlocfilehash: 79cd81292f6551a922744dc03ac9a83da8990e05
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122149468"
---
# <a name="extend-sharepoint-projects"></a>Estendere SharePoint progetti
  Creare un'estensione di progetto quando si vogliono personalizzare le funzionalità a livello di progetto SharePoint progetti. Ad esempio, è possibile aggiungere proprietà di progetto personalizzate o rispondere a eventi a livello di progetto generati quando l'utente sviluppa una soluzione SharePoint in Visual Studio.

## <a name="create-project-extensions"></a>Creare estensioni di progetto
 Per estendere un elemento di progetto, compilare un assembly Visual Studio di estensione che implementa <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> l'interfaccia . Per altre informazioni, vedere [Procedura: Creare un'estensione SharePoint progetto](../sharepoint/how-to-create-a-sharepoint-project-extension.md).

 Quando si crea un'estensione di progetto, è anche possibile aggiungere le funzionalità seguenti ai SharePoint seguenti:

- Aggiungere una voce di menu di scelta rapida. La voce di menu viene visualizzata quando si apre il menu di scelta rapida per un nodo di progetto SharePoint in **Esplora soluzioni** facendo clic con il pulsante destro del mouse sul nodo o scegliendolo e quindi premendo + **MAIUSC+F10.** Per altre informazioni, vedere [Procedura: Aggiungere una voce](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)di menu di scelta rapida a SharePoint progetti .

- Aggiungere una proprietà personalizzata. La proprietà viene visualizzata nella **finestra** Proprietà quando si sceglie un progetto SharePoint in **Esplora soluzioni**. Per altre informazioni, [vedere Procedura: Aggiungere una proprietà a SharePoint progetti](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).

  Per una procedura dettagliata che illustra come creare, distribuire e testare un'estensione di progetto, [vedere Procedura dettagliata: Creare un'estensione SharePoint progetto .](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)

## <a name="understand-the-relationship-between-project-extensions-and-project-instances"></a>Informazioni sulla relazione tra le estensioni di progetto e le istanze del progetto
 Quando si crea un'estensione di progetto, l'estensione viene caricata quando SharePoint progetto viene aperto in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]include diversi SharePoint di progetto, ad esempio definizioni di elenco, tipi di contenuto e ricevitori di eventi. Tuttavia, esiste un solo tipo SharePoint progetto. I tipi di progetto visualizzati nella finestra **di dialogo Nuovo Project** sono solo modelli che aggregano uno o più elementi SharePoint progetto. Poiché esiste un solo tipo SharePoint progetto, le estensioni create per un progetto si applicano a tutti i SharePoint progetto. Non è possibile, ad esempio, creare un'estensione che si applica solo a un **progetto tipo di** contenuto.

 Per accedere a un'istanza di progetto specifica, gestire uno degli <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents> eventi del *parametro projectService* nell'implementazione del <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> metodo . Ad esempio, per determinare quando un SharePoint progetto viene aggiunto a una soluzione, gestire <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded> l'evento . Per altre informazioni, vedere [Procedura: Creare un'estensione SharePoint progetto](../sharepoint/how-to-create-a-sharepoint-project-extension.md).

## <a name="see-also"></a>Vedi anche
- [Procedura: Creare un'estensione SharePoint progetto](../sharepoint/how-to-create-a-sharepoint-project-extension.md)
- [Procedura: Aggiungere una voce di menu di scelta rapida SharePoint progetti](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)
- [Procedura: Aggiungere una proprietà a SharePoint progetti](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)
- [Procedura dettagliata: Creare un'estensione SharePoint progetto](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)
- [Definire tipi di SharePoint di progetto personalizzati](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Estendere SharePoint di progetto](../sharepoint/extending-sharepoint-project-items.md)
- [Estendere la SharePoint creazione di pacchetti e la distribuzione](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [Estendere il SharePoint del progetto](../sharepoint/extending-the-sharepoint-project-system.md)
