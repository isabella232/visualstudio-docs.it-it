---
title: Estensione del sistema del progetto SharePoint | Microsoft Docs
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7dce10c2bc44eb4fde6a6e38417d136ea5e9ba41
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62557024"
---
# <a name="extend-the-sharepoint-project-system"></a>Estendere il sistema del progetto SharePoint
  È possibile creare soluzioni SharePoint usando un set di modelli di progetto e modelli di elemento in Visual Studio. Questi modelli soddisfano i requisiti di molti scenari di sviluppo, ma è possibile individuare alcuni casi in cui non forniscono funzionalità necessarie. In questi casi, è possibile estendere il sistema del progetto SharePoint.

## <a name="overview-of-the-sharepoint-project-system"></a>Panoramica del sistema di progetto SharePoint
 Il sistema del progetto SharePoint è basato sul componente fondamentale degli *elementi del progetto SharePoint*. Un elemento del progetto SharePoint rappresenta una singola personalizzazione di SharePoint, ad esempio una definizione di elenco, una Web part o un tipo di contenuto.

 Un progetto SharePoint è un progetto di Visual Studio che include uno o più elementi del progetto SharePoint. I progetti SharePoint contengono anche componenti aggiuntivi che definiscono il modo in cui gli elementi del progetto vengono raggruppati in funzionalità e pacchetti per la distribuzione.

 Per ulteriori informazioni sul contenuto di elementi di progetto SharePoint e di progetti SharePoint, vedere [creare modelli di elementi e modelli di progetto per gli elementi del progetto SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

## <a name="how-to-extend-the-sharepoint-project-system"></a>Come estendere il sistema di progetto SharePoint
 È possibile estendere il sistema del progetto SharePoint nei modi seguenti:

- Definire i tipi di elementi di progetto SharePoint e associarli ai nuovi modelli di elemento o ai modelli di progetto in Visual Studio. È ad esempio possibile definire un tipo di elemento di progetto SharePoint per la creazione di un'azione personalizzata o di un campo. Per altre informazioni, vedere [definire tipi di elementi di progetto SharePoint personalizzati](../sharepoint/defining-custom-sharepoint-project-item-types.md).

- Estendere i tipi di elementi del progetto SharePoint già installati in Visual Studio. Ad esempio, è possibile aggiungere una voce di menu di scelta rapida a un elemento del progetto in **Esplora soluzioni** e personalizzare l'elemento del progetto quando uno sviluppatore sceglie la voce di menu. Per altre informazioni, vedere [estendere gli elementi del progetto SharePoint](../sharepoint/extending-sharepoint-project-items.md).

- Estensione di progetti SharePoint. È ad esempio possibile aggiungere gestori eventi per eseguire attività specifiche quando gli elementi vengono aggiunti o rimossi dai progetti SharePoint. Per altre informazioni, vedere [estendere i progetti SharePoint](../sharepoint/extending-sharepoint-projects.md).

- Estendere il comportamento di creazione di pacchetti e distribuzione di elementi di progetto SharePoint e di progetti SharePoint. Ad esempio, è possibile creare passaggi di distribuzione personalizzati da eseguire quando si distribuisce o si ritira un progetto oppure è possibile eseguire attività personalizzate aggiuntive quando Visual Studio esegue alcuni passaggi di distribuzione. Per ulteriori informazioni, vedere [estensione della creazione di pacchetti e della distribuzione di SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md).

## <a name="common-development-tasks"></a>Attività di sviluppo comuni
 Nelle estensioni del sistema di progetto SharePoint è possibile eseguire le attività comuni seguenti:

- Salvare i dati stringa personalizzati con gli elementi di progetto e in diversi tipi di file di progetto. Per ulteriori informazioni, vedere [salvare i dati nelle estensioni del sistema del progetto SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).

- Convertire un oggetto nel sistema del progetto SharePoint in un oggetto corrispondente nel modello a oggetti di automazione di Visual Studio o nel modello a oggetti di integrazione o viceversa. Per ulteriori informazioni, vedere [conver tra i tipi di sistema del progetto SharePoint e altri tipi di progetto di Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).

## <a name="see-also"></a>Vedere anche
- [Definire i tipi di elementi di progetto SharePoint personalizzati](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Estendi elementi di progetto SharePoint](../sharepoint/extending-sharepoint-project-items.md)
- [Estensione di progetti SharePoint](../sharepoint/extending-sharepoint-projects.md)
- [Estensione della creazione di pacchetti e della distribuzione di SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [Salvare i dati nelle estensioni del sistema di progetto SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)
- [Conversione tra tipi di sistemi di progetto SharePoint e altri tipi di progetto di Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)
- [Estendere gli strumenti di SharePoint in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)
- [Programmazione di concetti e funzionalità per le estensioni degli strumenti di SharePoint](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)
