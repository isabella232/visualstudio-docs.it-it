---
title: "Analisi della qualità del codice gestito tramite analisi del codice | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code analysis,managed code
- managed code analyis
ms.assetid: 68510a55-da51-4381-81a5-0feba76b8b4f
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 2008ac649302d87cc2d45274de3fdb1981aa571d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="analyzing-managed-code-quality-by-using-code-analysis"></a>Analisi della qualità del codice gestito tramite analisi del codice
È possibile utilizzare gli strumenti di analisi del codice di Visual Studio per individuare potenziali problemi nel codice, ad esempio accesso ai dati non sicuro, violazioni di utilizzo e problemi di progettazione. Analisi del codice funziona con .NET Framework nativo (C e C++) e applicazioni di database. Analisi del codice gestito consente di organizzare le regole in *set di regole* specifici in diversi problemi di codifica.  
  
## <a name="common-tasks"></a>Attività comuni  
  
|Attività comuni|Contenuto di supporto|  
|------------------|------------------------|  
|**Fare pratica:** nozioni di base di analisi del codice, correggere difetti in una semplice applicazione .NET Framework.|-   [Procedura dettagliata: Analisi del codice gestito per errori del codice](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)|  
|**Configurare l'analisi codice per un progetto:** regole per gestito codice sono organizzate in set di regole destinati ad aree specifiche, ad esempio sicurezza e di progettazione. È possibile utilizzare uno dei Microsoft imposta di regole standard o crearne di proprie.|-   [Analisi del codice per una panoramica del codice gestito](../code-quality/code-analysis-for-managed-code-overview.md)<br />-   [Regola di utilizzo di set per raggruppare regole di analisi codice](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)<br />-   [Esclusione di avvisi tramite l'attributo SuppressMessage](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md)|  
|**Eseguire l'analisi del codice:** è possibile specificare l'analisi del codice venga eseguita automaticamente ogni volta che una configurazione di progetto viene compilata, ed è possibile eseguire manualmente l'analisi del codice su un progetto.|-   [Procedura: abilitare e disabilitare l'analisi automatica del codice](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)<br />-   [Procedura: eseguire manualmente l'analisi codice](../code-quality/how-to-run-code-analysis-manually-for-managed-code.md)|  
|**Analizzare i risultati dell'analisi del codice:** errori e avvisi dell'analisi del codice sono elencati nella finestra Analisi codice. È possibile scegliere un avviso o il titolo di un errore per visualizzare informazioni aggiuntive sull'avviso, nonché per visualizzare e selezionare la riga del codice sorgente che ha attivato la regola. È possibile scegliere l'id di avviso per visualizzare informazioni dettagliate in MSDN Library che include informazioni ed esempi su come risolvere il problema.|-   [Procedura: visualizzare gli errori del codice gestito](../code-quality/how-to-view-managed-code-defects.md)<br />-   [Analisi del codice per avvisi del codice gestito](../code-quality/code-analysis-for-managed-code-warnings.md)<br />-   [Avvisi generati da CheckId](../code-quality/code-analysis-warnings-for-managed-code-by-checkid.md)<br />-   [Metodi anonimi e analisi del codice](../code-quality/anonymous-methods-and-code-analysis.md)|  
|**Integrare l'analisi del codice con il ciclo di sviluppo:** criteri di archiviazione in [!INCLUDE[esprscc](../code-quality/includes/esprscc_md.md)] team di sviluppo attiva per assicurarsi che tutto il codice archiviazioni soddisfino un set comune di standard di analisi codice. Creazione di un elemento di lavoro per la violazione di una regola di analisi codice è una procedura semplice che è possibile eseguire nella finestra Elenco errori.|-   [Miglioramento della qualità del codice con i criteri di controllo del progetto Team](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)<br />-   [Procedura: sincronizzare i set di regole di progetto di codice con i criteri di controllo del progetto Team](../code-quality/how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy.md)<br />-   [Procedura: creare un elemento di lavoro per un errore del codice gestito](../code-quality/how-to-create-a-work-item-for-a-managed-code-defect.md)|