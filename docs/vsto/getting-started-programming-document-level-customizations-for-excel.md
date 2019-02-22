---
title: Introduzione alla programmazione delle personalizzazioni a livello di documento per Excel
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel solutions in Visual Studio
- Excel projects [Office development in Visual Studio], getting started
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a336463a3a7d8003c949242ad2f295a76633c894
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56603794"
---
# <a name="get-started-programming-document-level-customizations-for-excel"></a>Introduzione alla programmazione delle personalizzazioni a livello di documento per Excel
  Se sta iniziando la creazione di personalizzazioni a livello di documento per Microsoft Office Excel usando Visual Studio, ecco cosa occorre sapere.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

## <a name="understand-how-document-level-customizations-for-excel-work"></a>Comprendere personalizzazioni a livello di documento per Excel
 Una personalizzazione a livello di documento per Excel è basata su una singola cartella di lavoro. Per iniziare a usare la personalizzazione, l'utente finale apre la cartella di lavoro o crea la cartella di lavoro da un modello di Excel. Gli eventi nella cartella di lavoro, ad esempio digitando nelle celle o facendo clic di pulsanti e le voci di menu, è possono chiamare i metodi di gestione degli eventi nell'assembly. Quando la cartella di lavoro viene chiusa, le funzionalità fornite dalla personalizzazione non sono più disponibili in Excel, solo nel documento che li conteneva.

 Per altre informazioni, vedere [architettura delle personalizzazioni a livello di documento](../vsto/architecture-of-document-level-customizations.md).

## <a name="create-document-level-projects-for-excel"></a>Creare i progetti a livello di documento per Excel
 Per creare una personalizzazione a livello di documento per Excel, usare il modello di progetto della cartella di lavoro di Excel o modello di Excel nel **nuovo progetto** nella finestra di dialogo. Questi modelli includono riferimenti dell'assembly e file di progetto necessari.

 Per altre informazioni su come creare un progetto a livello di documento per Excel, vedere [come: Creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Per altre informazioni sui modelli di progetto, vedere [Cenni preliminari sui modelli di progetto di Office](../vsto/office-project-templates-overview.md).

## <a name="program-excel-workbooks-by-using-host-items-and-host-controls"></a>Programmare le cartelle di lavoro di Excel utilizzando gli elementi host e controlli host
 *Elementi host* e *controlli host* sono classi che forniscono il modello di programmazione per le personalizzazioni a livello di documento create mediante Visual Studio.

 Elementi host forniscono un punto di ingresso per il codice e si può anche agire come contenitori per i controlli host e controlli Windows Form. Nei progetti a livello di documento per Excel, questi elementi host sono rappresentati dal `ThisWorkbook`, `Sheet1`, `Sheet2`, e `Sheet3` classi.

 Controlli host sono basati su oggetti di Excel nativi, come elenco degli oggetti e gli intervalli. Controlli host forniscono funzionalità simili per gli oggetti nativi di Excel, ma dispongono anche di nuovi eventi, il supporto della finestra di progettazione e funzionalità di data binding. Vengono visualizzati come oggetti di prima classe nel codice del progetto e in IntelliSense, che rende più semplice fare riferimento a oggetti specifici direttamente nel codice senza la necessità di passare il modello a oggetti Excel.

 Per altre informazioni, vedere i seguenti argomenti:

-   [Programmazione delle personalizzazioni a livello di documento](../vsto/programming-document-level-customizations.md)

-   [Automazione di Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md)

-   [Cenni preliminari sui controlli host e gli elementi host](../vsto/host-items-and-host-controls-overview.md)

## <a name="customize-the-user-interface-of-excel"></a>Personalizzare l'interfaccia utente di Excel
 La maggior parte delle soluzioni di Microsoft Office modificare l'interfaccia utente (UI) dell'applicazione di Office allo scopo di consentire agli utenti di interagire con la soluzione. Esistono diversi modi in cui è possibile modificare l'interfaccia utente di Excel usando una personalizzazione a livello di documento. Ad esempio, è possibile aggiungere controlli alla barra multifunzione oppure è possibile visualizzare un riquadro azioni. Per altre informazioni, vedere [personalizzazione dell'interfaccia utente Office](../vsto/office-ui-customization.md).

 È anche possibile aprire la cartella di lavoro associata direttamente al progetto in Visual Studio. Quando la cartella di lavoro è aperta in Visual Studio, è possibile modificare la cartella di lavoro tramite l'interfaccia utente di Excel. È anche possibile usare la cartella di lavoro come un'area di progettazione, che consente di trascinare i controlli in fogli di lavoro. Per altre informazioni, vedere [progetti di Office in ambiente di Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).

## <a name="use-data-binding"></a>Usare il data binding
 I controlli host sono anche nell'elenco di controlli che è possibile trascinare dal **Zdroje dat** finestra. Aggiunta di controlli host in questo modo automaticamente li associa all'origine dati che si configura utilizzo della finestra. Senza scrivere alcun codice, è possibile visualizzare i dati dal database, servizi web e oggetti business. Per altre informazioni, vedere [associare dati a controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md).

## <a name="next-steps"></a>Passaggi successivi
 Per informazioni su come creare una personalizzazione a livello di documento per Excel, vedere [procedura dettagliata: Creare una personalizzazione a livello di documento per Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md). Questa procedura dettagliata presenta gli strumenti di sviluppo per Office in Visual Studio e il modello di programmazione per le personalizzazioni a livello di documento di Excel.

 Per un elenco di argomenti che illustrano alcune delle attività comuni nei progetti di Excel, vedere [attività comuni nella programmazione Office](../vsto/common-tasks-in-office-programming.md).

## <a name="see-also"></a>Vedere anche
- [Procedura: Creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Programmazione delle personalizzazioni a livello di documento](../vsto/programming-document-level-customizations.md)
- [Soluzioni Excel](../vsto/excel-solutions.md)
- [Procedura dettagliata: Creare una personalizzazione a livello di documento per Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)
- [Procedure dettagliate con Excel](../vsto/walkthroughs-using-excel.md)
- [Cenni preliminari sul modello a oggetti di Excel](../vsto/excel-object-model-overview.md)
- [Scrivere il codice nelle soluzioni Office](../vsto/writing-code-in-office-solutions.md)
