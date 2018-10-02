---
title: Analisi della qualità del codice gestito tramite analisi del codice | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- code analysis,managed code
- managed code analyis
ms.assetid: 68510a55-da51-4381-81a5-0feba76b8b4f
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 3e0538c47dec2dd11b9488a80dd4f71baddc487f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47517881"
---
# <a name="analyzing-managed-code-quality-by-using-code-analysis"></a>Analisi della qualità del codice gestito tramite analisi del codice
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [analisi qualità del codice gestito tramite analisi del codice](https://docs.microsoft.com/visualstudio/code-quality/analyzing-managed-code-quality-by-using-code-analysis).  
  
È possibile utilizzare gli strumenti di analisi del codice di Visual Studio per individuare potenziali problemi nel codice, ad esempio accesso ai dati non sicuro, violazioni di utilizzo e problemi di progettazione. Analisi del codice funziona in .NET Framework nativo (C e C++) e le applicazioni di database. Analisi del codice per il codice gestito consente di organizzare le regole in *set di regole* che hanno come destinazione specifici problemi relativi alla codifica.  
  
## <a name="common-tasks"></a>Attività comuni  
  
|Attività comuni|Contenuto di supporto|  
|------------------|------------------------|  
|**Fare pratica:** Scopri le nozioni di base di analisi del codice, correggere i difetti in una semplice applicazione .NET Framework.|-   [Procedura dettagliata: Analisi del codice gestito per i difetti del codice](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)|  
|**Configurare l'analisi del codice per un progetto:** le regole per managed code sono organizzate in set di regole destinati ad aree specifiche, ad esempio sicurezza e la progettazione. È possibile usare uno dei Microsoft standard regola imposta o creane di personalizzati.|-   [Analisi del codice per la panoramica del codice gestito](../code-quality/code-analysis-for-managed-code-overview.md)<br />-   [Regola di utilizzo di set per raggruppare regole di analisi codice](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)<br />-   [Eliminare gli avvisi tramite l'attributo SuppressMessage](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md)|  
|**Esegui analisi del codice:** è possibile specificare l'analisi del codice da eseguire automaticamente ogni volta che una configurazione di progetto viene compilata ed è possibile eseguire manualmente l'analisi del codice in un progetto.|-   [Procedura: abilitare e disabilitare l'analisi automatica del codice](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)<br />-   [Procedura: eseguire manualmente l'analisi codice](../code-quality/how-to-run-code-analysis-manually-for-managed-code.md)|  
|**Analizzare i risultati dell'analisi codice:** avvisi dell'analisi codice e gli errori sono elencati nella finestra Analisi codice. È possibile scegliere un avviso o un titolo dell'errore per visualizzare informazioni aggiuntive sull'avviso e per visualizzare ed evidenziare la riga del codice sorgente che ha attivato la regola. È possibile scegliere l'id di avviso per visualizzare informazioni dettagliate in MSDN Library che include le informazioni ed esempi su come risolvere il problema.|-   [Procedura: visualizzare gli errori del codice gestito](../code-quality/how-to-view-managed-code-defects.md)<br />-   [Analisi del codice per gli avvisi del codice gestito](../code-quality/code-analysis-for-managed-code-warnings.md)<br />-   [Avvisi generati da CheckId](../code-quality/code-analysis-warnings-for-managed-code-by-checkid.md)<br />-   [Metodi anonimi e analisi del codice](../code-quality/anonymous-methods-and-code-analysis.md)|  
|**Integrare l'analisi del codice con il ciclo di sviluppo:** i criteri di archiviazione in [!INCLUDE[esprscc](../includes/esprscc-md.md)] Abilita i team di sviluppo per assicurarsi che tutto il codice archiviazioni soddisfino un set comune di standard di analisi codice. Creazione di un elemento di lavoro per la violazione di una regola di analisi codice è semplice procedura che è possibile eseguire nella finestra Elenco errori.|-   [Miglioramento della qualità del codice con criteri di controllo del progetto Team](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)<br />-   [Procedura: sincronizzare set di regole di progetto di codice con i criteri di controllo del progetto Team](../code-quality/how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy.md)<br />-   [Procedura: creare un elemento di lavoro per un difetto del codice gestito](../code-quality/how-to-create-a-work-item-for-a-managed-code-defect.md)|



