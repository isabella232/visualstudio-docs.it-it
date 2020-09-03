---
title: Utilizzo di set di regole per raggruppare regole di analisi del codice | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.rulesets.learnmore
helpviewer_keywords:
- code analysis, rule sets
ms.assetid: ed0f3a2a-1516-42e2-92de-b8986dc75d42
caps.latest.revision: 38
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 30bd2e53531d9abc7d27adba05c3b724c88d61c3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72603473"
---
# <a name="using-rule-sets-to-group-code-analysis-rules"></a>Utilizzo di set di regole per raggruppare regole di analisi del codice
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando si configura l'analisi del codice in [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] , [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] o [!INCLUDE[vsPro](../includes/vspro-md.md)] , è possibile scegliere da un elenco di *set di regole*predefiniti Microsoft. Un set di regole è un raggruppamento logico di regole di analisi del codice che identificano i problemi di destinazione e le condizioni specifiche. Ad esempio, è possibile applicare un set di regole progettato per analizzare il codice per le API disponibili pubblicamente oppure è possibile applicare un set di regole che includa solo le regole minime consigliate. È anche possibile applicare un set di regole che includa tutte le regole.

 Per personalizzare un set di regole è possibile aggiungere o eliminare regole oppure modificare le regole in modo che vengano visualizzate nella finestra **Elenco errori** come avvisi o errori. I set di regole personalizzati possono soddisfare la necessità di un ambiente di sviluppo specifico. Quando si personalizza un set di regole, nella pagina set di regole sono disponibili strumenti di ricerca e filtro che consentono di semplificare il processo.

## <a name="common-tasks"></a>Attività comuni

|Attività|Contenuto correlato|
|----------|---------------------|
|**Esercitazione pratica:** Usare gli strumenti di analisi del codice per specificare un set di regole personalizzato per individuare e risolvere i problemi in una semplice applicazione .NET Framework.|-   [Procedura dettagliata: configurazione e uso di un set di regole personalizzate](../code-quality/walkthrough-configuring-and-using-a-custom-rule-set.md)|
|**Configurare l'analisi del codice per un progetto:** Scegliere un set di regole esistente per un progetto, un sito Web o una soluzione.|-   [Procedura: configurare l'analisi del codice per un progetto di codice gestito](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)<br />-   [Utilizzo di set di regole per specificare le regole C++ da eseguire](../code-quality/using-rule-sets-to-specify-the-cpp-rules-to-run.md)<br />-   [Procedura: configurare l'analisi del codice per un'applicazione Web ASP.NET](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md)<br />-   [Procedura: specificare set di regole per più progetti in una soluzione](../code-quality/how-to-specify-managed-code-rule-sets-for-multiple-projects-in-a-solution.md)|
|**Personalizzare un set di regole:** Specificare le regole da applicare al progetto.|-   [Creazione di set di regole personalizzati](../code-quality/creating-custom-code-analysis-rule-sets.md)|
|**Informazioni sui set di regole predefiniti:** Visualizzare le regole di analisi del codice che costituiscono i set di regole predefiniti.|-   [Riferimento al set di regole di analisi del codice](../code-quality/code-analysis-rule-set-reference.md)|
|**Integra l'analisi del codice con Team Foundation Server:** [!INCLUDE[esprtfs](../includes/esprtfs-md.md)] i criteri di archiviazione consentono ai team di sviluppo di assicurarsi che tutte le archiviazioni del codice soddisfino un insieme comune di standard di analisi del codice.|-   [Procedura: sincronizzare i set di regole del progetto di codice con i criteri di archiviazione del progetto team](../code-quality/how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy.md)|
