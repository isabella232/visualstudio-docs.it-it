---
title: Estensione del sistema di progetto SharePoint | Microsoft Docs
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
ms.openlocfilehash: 9f461cae21dfd43bb8fb1d78af65e0ea234d0100
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2019
ms.locfileid: "54869265"
---
# <a name="extend-the-sharepoint-project-system"></a>Estendere il sistema di progetto SharePoint
  È possibile creare soluzioni di SharePoint usando un set di modelli di elementi e modelli di progetto in Visual Studio. Questi modelli di soddisfano i requisiti di numerosi scenari di sviluppo, ma è possibile individuare alcuni casi in cui non dispongono della funzionalità necessarie. In questi casi, è possibile estendere il sistema di progetto SharePoint.  
  
## <a name="overview-of-the-sharepoint-project-system"></a>Panoramica del sistema del progetto SharePoint
 Il sistema di progetto SharePoint è basato sul componente fondamentale della *elementi di progetto SharePoint*. Un elemento del progetto SharePoint rappresenta una singola personalizzazione di SharePoint, ad esempio una definizione di elenco, Web Part o tipo di contenuto.  
  
 Un progetto di SharePoint è un progetto di Visual Studio che include uno o più elementi di progetto SharePoint. Progetti di SharePoint contengono anche i componenti aggiuntivi che definiscono come gli elementi di progetto sono raggruppati in funzionalità e pacchetti per la distribuzione.  
  
 Per altre informazioni sul contenuto di elementi di progetto SharePoint e i progetti SharePoint, vedere [creare elementi di modelli e i modelli di progetto per gli elementi di progetto SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
## <a name="how-to-extend-the-sharepoint-project-system"></a>Come estendere il sistema di progetto SharePoint
 È possibile estendere il sistema di progetto SharePoint nei modi seguenti:  
  
-   Definire i propri tipi di elemento di progetto SharePoint e associarli a nuovi modelli di elementi o modelli di progetto in Visual Studio. Ad esempio, è possibile definire un tipo di elemento di progetto SharePoint per la creazione di un'azione personalizzata o un campo. Per altre informazioni, vedere [definire tipi di elemento di progetto SharePoint personalizzati](../sharepoint/defining-custom-sharepoint-project-item-types.md).  
  
-   Estendere i tipi di elemento di progetto SharePoint che sono già installati in Visual Studio. Ad esempio, è possibile aggiungere una voce di menu di scelta rapida per un elemento del progetto in **Esplora soluzioni** e personalizzare l'elemento del progetto quando lo sviluppatore sceglie la voce di menu. Per altre informazioni, vedere [elementi di progetto SharePoint estendere](../sharepoint/extending-sharepoint-project-items.md).  
  
-   Estendere i progetti SharePoint. Ad esempio, è possibile aggiungere gestori eventi per eseguire attività specifiche, quando gli elementi vengono aggiunti o rimossi dai progetti di SharePoint. Per altre informazioni, vedere [progetti estendere SharePoint](../sharepoint/extending-sharepoint-projects.md).  
  
-   Estendere il comportamento di creazione di pacchetti e distribuzione di elementi di progetto SharePoint e i progetti SharePoint. Ad esempio, è possibile creare i proprio passaggi di distribuzione da eseguire quando si distribuisce o si ritira un progetto oppure è possibile eseguire attività personalizzate aggiuntive quando Visual Studio esegue alcune operazioni di distribuzione. Per altre informazioni, vedere [estendere SharePoint packaging e la distribuzione](../sharepoint/extending-sharepoint-packaging-and-deployment.md).  
  
## <a name="common-development-tasks"></a>Attività di sviluppo comuni
 È possibile eseguire le seguenti attività comuni nelle estensioni del sistema del progetto SharePoint:  
  
-   Salvare i dati di stringa personalizzato con elementi di progetto e in diversi tipi di file di progetto. Per altre informazioni, vedere [salvare i dati nelle estensioni del sistema del progetto SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
-   Convertire un oggetto nel sistema del progetto SharePoint in un oggetto corrispondente nel modello oggetto di automazione di Visual Studio o nel modello oggetto di integrazione, o viceversa. Per altre informazioni, vedere [onverti tra tipi di sistema di progetto SharePoint e altri tipi di progetto di Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).  
  
## <a name="see-also"></a>Vedere anche
 [Definire tipi di elemento di progetto SharePoint personalizzati](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Estendere gli elementi di progetto SharePoint](../sharepoint/extending-sharepoint-project-items.md)   
 [Estendere i progetti SharePoint](../sharepoint/extending-sharepoint-projects.md)   
 [Estendere la distribuzione e creazione di pacchetti di SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Salvare i dati nelle estensioni del sistema del progetto SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)   
 [Eseguire la conversione tra tipi di sistema di progetto SharePoint e altri tipi di progetto di Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)   
 [Estendere gli strumenti di SharePoint in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)   
 [Programmazione di concetti e funzionalità per le estensioni degli strumenti di SharePoint](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)  
