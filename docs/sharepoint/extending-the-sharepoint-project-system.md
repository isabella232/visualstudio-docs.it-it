---
title: Estensione del SharePoint Project di | Microsoft Docs
description: Estendere il SharePoint di progetto. Informazioni su come estendere il SharePoint di progetto. Informazioni su attività di sviluppo comuni.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending projects
- SharePoint development in Visual Studio, extending project items
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 0fea459c7a442d25363c66efc7be69d21a5e3fb2fd5b31b94e8f09665415d872
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121425388"
---
# <a name="extend-the-sharepoint-project-system"></a>Estendere il SharePoint di progetto
  È possibile creare SharePoint soluzioni personalizzate usando un set di modelli di progetto e modelli di elemento in Visual Studio. Questi modelli soddisfano i requisiti di molti scenari di sviluppo, ma è possibile individuare alcuni casi in cui non forniscono funzionalità necessarie. In questi casi è possibile estendere il sistema SharePoint progetto.

## <a name="overview-of-the-sharepoint-project-system"></a>Panoramica del sistema SharePoint progetto
 Il SharePoint di progetto è basato sul componente fondamentale *dell'SharePoint di progetto.* Un SharePoint di progetto rappresenta una singola SharePoint, ad esempio una definizione di elenco, una web part o un tipo di contenuto.

 Un SharePoint è un progetto Visual Studio che include uno o più elementi SharePoint progetto. SharePoint progetti contengono anche componenti aggiuntivi che definiscono il modo in cui gli elementi del progetto vengono raggruppati in funzionalità e pacchetti per la distribuzione.

 Per altre informazioni sul contenuto degli elementi SharePoint progetto e dei SharePoint, vedere Creare modelli di elemento e modelli di progetto per SharePoint [di progetto](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

## <a name="how-to-extend-the-sharepoint-project-system"></a>Come estendere il sistema SharePoint progetto
 È possibile estendere il SharePoint di progetto nei modi seguenti:

- Definire i propri SharePoint di elementi di progetto e associarli a nuovi modelli di elemento o modelli di progetto in Visual Studio. Ad esempio, è possibile definire un tipo SharePoint elemento di progetto per la creazione di un'azione personalizzata o di un campo. Per altre informazioni, vedere [Definire tipi di SharePoint di progetto personalizzati.](../sharepoint/defining-custom-sharepoint-project-item-types.md)

- Estendere SharePoint tipi di elemento di progetto già installati in Visual Studio. Ad esempio, è possibile aggiungere una voce di menu di scelta rapida a una voce di progetto **in** Esplora soluzioni e personalizzare la voce di progetto quando uno sviluppatore sceglie la voce di menu. Per altre informazioni, vedere [Estendere SharePoint di progetto](../sharepoint/extending-sharepoint-project-items.md).

- Estendere SharePoint progetti. Ad esempio, è possibile aggiungere gestori eventi per eseguire attività specifiche quando gli elementi vengono aggiunti o rimossi SharePoint progetti. Per altre informazioni, vedere [Estendere SharePoint progetti](../sharepoint/extending-sharepoint-projects.md).

- Estendere il comportamento di creazione di pacchetti e distribuzione di SharePoint di progetto e SharePoint progetto. Ad esempio, è possibile creare passaggi di distribuzione personalizzati da eseguire quando si distribuisce o si ritira un progetto oppure è possibile eseguire attività personalizzate aggiuntive quando Visual Studio esegue determinati passaggi di distribuzione. Per altre informazioni, vedere [Estendere SharePoint creazione di pacchetti e distribuzione](../sharepoint/extending-sharepoint-packaging-and-deployment.md).

## <a name="common-development-tasks"></a>Attività di sviluppo comuni
 È possibile eseguire le attività comuni seguenti nelle estensioni del SharePoint di progetto:

- Salvare dati di stringa personalizzati con elementi di progetto e in diversi tipi diversi di file di progetto. Per altre informazioni, vedere [Salvare i dati nelle estensioni del sistema SharePoint progetto](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).

- Convertire un oggetto nel sistema SharePoint progetto in un oggetto corrispondente nel modello a oggetti di automazione Visual Studio modello a oggetti di integrazione o viceversa. Per altre informazioni, vedere [Conver tra](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)SharePoint di sistema del progetto e altri Visual Studio tipi di progetto .

## <a name="see-also"></a>Vedi anche
- [Definire tipi di SharePoint di progetto personalizzati](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Estendere SharePoint di progetto](../sharepoint/extending-sharepoint-project-items.md)
- [Estendere SharePoint progetti](../sharepoint/extending-sharepoint-projects.md)
- [Estendere SharePoint creazione di pacchetti e distribuzione](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [Salvare i dati nelle estensioni del sistema SharePoint progetto](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)
- [Eseguire la conversione SharePoint tipi di sistema del progetto e altri Visual Studio di progetto](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)
- [Estendere gli SharePoint in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)
- [Programmazione di concetti e funzionalità per le estensioni degli strumenti di SharePoint](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)
