---
title: Introduzione alla programmazione delle personalizzazioni a livello di documento per Excel
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel solutions in Visual Studio
- Excel projects [Office development in Visual Studio], getting started
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 50c18564604a15265b61b17f74484f959b18b131
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/22/2018
ms.locfileid: "34448428"
---
# <a name="get-started-programming-document-level-customizations-for-excel"></a>Introduzione alla programmazione delle personalizzazioni a livello di documento per Excel
  Se per iniziare la creazione di personalizzazioni a livello di documento per Microsoft Office Excel tramite Visual Studio, ecco cosa è necessario conoscere.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
## <a name="understand-how-document-level-customizations-for-excel-work"></a>Comprendere le personalizzazioni a livello di documento per Excel  
 Una personalizzazione a livello di documento per Excel è basata su una singola cartella di lavoro. Per iniziare a utilizzare la personalizzazione, l'utente finale apre la cartella di lavoro o crea la cartella di lavoro da un modello di Excel. Gli eventi nella cartella di lavoro, ad esempio digitando le celle o facendo clic di pulsanti e voci di menu, possono chiamare i metodi di gestione degli eventi nell'assembly. Quando la cartella di lavoro viene chiusa, le funzionalità fornite dalla personalizzazione non sono più disponibili in Excel, solo nel documento che conteneva.  
  
 Per altre informazioni, vedere [architettura delle personalizzazioni a livello di documento di](../vsto/architecture-of-document-level-customizations.md).  
  
## <a name="create-document-level-projects-for-excel"></a>Creare i progetti a livello di documento per Excel  
 Per creare una personalizzazione a livello di documento per Excel, utilizzare il modello di progetto di cartella di lavoro di Excel o modello di Excel nel **nuovo progetto** la finestra di dialogo. Questi modelli includono riferimenti dell'assembly e file di progetto necessari.  
  
 Per ulteriori informazioni su come creare un progetto a livello di documento per Excel, vedere [procedura: progetti di Office Create in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Per ulteriori informazioni sui modelli di progetto, vedere [panoramica dei modelli di progetto Office](../vsto/office-project-templates-overview.md).  
  
## <a name="program-excel-workbooks-by-using-host-items-and-host-controls"></a>Programmare le cartelle di lavoro di Excel utilizzando gli elementi host e controlli host  
 *Elementi host* e *controlli host* sono classi che forniscono il modello di programmazione per le personalizzazioni a livello di documento create mediante Visual Studio.  
  
 Gli elementi host forniscono un punto di ingresso per il codice e può anche fungono da contenitori per i controlli host e controlli Windows Form. Nei progetti a livello di documento per Excel, questi elementi host sono rappresentati di `ThisWorkbook`, `Sheet1`, `Sheet2`, e `Sheet3` classi.  
  
 Controlli host sono basati sugli oggetti nativi di Excel, ad esempio gli oggetti elenco e gli intervalli. Controlli host offrono funzionalità simili per gli oggetti nativi di Excel, ma dispongono anche di funzionalità di data binding, supporto della finestra di progettazione e nuovi eventi. Vengono visualizzate come oggetti di prima classe nel codice del progetto in IntelliSense, che rende più semplice fare riferimento a oggetti specifici direttamente nel codice senza dover passare il modello a oggetti Excel.  
  
 Per altre informazioni, vedere i seguenti argomenti:  
  
-   [Programmazione delle personalizzazioni a livello di documento](../vsto/programming-document-level-customizations.md)  
  
-   [Automazione di Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md)  
  
-   [Elementi host e Cenni preliminari sui controlli host](../vsto/host-items-and-host-controls-overview.md)  
  
## <a name="customize-the-user-interface-of-excel"></a>Personalizzare l'interfaccia utente di Excel  
 La maggior parte delle soluzioni di Microsoft Office modificare l'interfaccia utente (UI) dell'applicazione di Office allo scopo di consentire agli utenti di interagire con la soluzione. Esistono molti modi in cui è possibile modificare l'interfaccia utente di Excel usando una personalizzazione a livello di documento. Ad esempio, è possibile aggiungere controlli alla barra multifunzione oppure è possibile visualizzare un riquadro azioni. Per altre informazioni, vedere [personalizzazione dell'interfaccia utente Office](../vsto/office-ui-customization.md).  
  
 È anche possibile aprire la cartella di lavoro associata direttamente al progetto in Visual Studio. Quando la cartella di lavoro è aperta in Visual Studio, è possibile modificare la cartella di lavoro tramite l'interfaccia utente di Excel. È anche possibile utilizzare la cartella di lavoro come un'area di progettazione, che consente di trascinare i controlli in fogli di lavoro. Per altre informazioni, vedere [progetti di Office in ambiente di Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
## <a name="use-data-binding"></a>Utilizzare l'associazione dati  
 I controlli host sono anche nell'elenco di controlli che è possibile trascinare il **origini dati** finestra. Aggiunta di controlli host in questo modo automaticamente li associa l'origine dati configurata mediante la finestra. Senza scrivere alcun codice, è possibile visualizzare i dati dal database, servizi web e oggetti business. Per altre informazioni, vedere [associare dati ai controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
## <a name="next-steps"></a>Passaggi successivi  
 Per informazioni su come creare una personalizzazione a livello di documento per Excel, vedere [procedura dettagliata: creazione di una personalizzazione a livello di documento per Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md). Questa procedura dettagliata illustra gli strumenti di sviluppo per Office in Visual Studio e il modello di programmazione per le personalizzazioni a livello di documento di Excel.  
  
 Per un elenco di argomenti che illustrano alcune delle attività comuni nei progetti di Excel, vedere [attività comuni nella programmazione con Office](../vsto/common-tasks-in-office-programming.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Programmazione delle personalizzazioni a livello di documento](../vsto/programming-document-level-customizations.md)   
 [Soluzioni Excel](../vsto/excel-solutions.md)   
 [Procedura dettagliata: Creazione di una personalizzazione a livello di documento per Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)   
 [Procedure dettagliate con Excel](../vsto/walkthroughs-using-excel.md)   
 [Cenni preliminari sul modello a oggetti di Excel](../vsto/excel-object-model-overview.md)   
 [Scrivere il codice nelle soluzioni Office](../vsto/writing-code-in-office-solutions.md)  
  
  