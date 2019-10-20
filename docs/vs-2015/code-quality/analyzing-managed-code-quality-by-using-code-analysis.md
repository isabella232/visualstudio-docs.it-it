---
title: Analisi della qualità del codice gestito tramite l'analisi del codice | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis,managed code
- managed code analyis
ms.assetid: 68510a55-da51-4381-81a5-0feba76b8b4f
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0d5f0646f26226e9895414db512681e0a7a71faa
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671108"
---
# <a name="analyzing-managed-code-quality-by-using-code-analysis"></a>Analisi della qualità del codice gestito tramite analisi del codice
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile utilizzare gli strumenti di analisi del codice di Visual Studio per individuare potenziali problemi nel codice, ad esempio accesso ai dati non sicuro, violazioni di utilizzo e problemi di progettazione. L'analisi del codice funziona nelle applicazioni .NET Framework, Native C++(C e) e di database. L'analisi del codice per il codice gestito organizza le regole nei *set di regole* che hanno come destinazione problemi di codifica specifici.

## <a name="common-tasks"></a>Attività comuni

|Attività comuni|Contenuto di supporto|
|------------------|------------------------|
|**Esercitazione pratica:** Informazioni sulle nozioni di base sull'analisi del codice correggendo i difetti in una semplice applicazione .NET Framework.|-   [procedura dettagliata: analisi del codice gestito per i difetti del codice](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)|
|**Configurare l'analisi del codice per un progetto:** Le regole per il codice gestito sono organizzate in set di regole destinati ad aree specifiche, ad esempio sicurezza e progettazione. È possibile usare uno dei set di regole standard Microsoft o crearne di personalizzati.|[Panoramica dell'analisi codice -    per il codice gestito](../code-quality/code-analysis-for-managed-code-overview.md)<br />-   [utilizzo di set di regole per raggruppare regole di analisi del codice](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)<br />-    non[visualizzare avvisi tramite l'attributo SuppressMessage](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md)|
|**Eseguire l'analisi del codice:** È possibile specificare che l'analisi codice venga eseguita automaticamente ogni volta che viene compilata una configurazione di progetto ed è possibile eseguire manualmente l'analisi del codice in un progetto.|-   [procedura: abilitare e disabilitare l'analisi automatica del codice](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)<br />-   [procedura: eseguire manualmente l'analisi del codice](../code-quality/how-to-run-code-analysis-manually-for-managed-code.md)|
|**Analizzare i risultati dell'analisi del codice:** Gli avvisi e gli errori di analisi codice sono elencati nella finestra analisi codice. È possibile scegliere un avviso o un titolo di errore per visualizzare informazioni aggiuntive sull'avviso e per visualizzare ed evidenziare la riga del codice sorgente che ha attivato la regola. È possibile scegliere l'ID avviso per visualizzare informazioni dettagliate in MSDN Library che includono informazioni ed esempi su come risolvere il problema.|-   [procedura: visualizzare i difetti del codice gestito](../code-quality/how-to-view-managed-code-defects.md)<br />[analisi del codice -    per gli avvisi del codice gestito](../code-quality/code-analysis-for-managed-code-warnings.md)<br />[avvisi di -    per CheckId](../code-quality/code-analysis-warnings-for-managed-code-by-checkid.md)<br />-   [metodi anonimi e l'analisi del codice](../code-quality/anonymous-methods-and-code-analysis.md)|
|**Integra l'analisi del codice con il tuo ciclo di vita di sviluppo:** I criteri di archiviazione in [!INCLUDE[esprscc](../includes/esprscc-md.md)] consentono ai team di sviluppo di assicurarsi che tutte le archiviazioni del codice soddisfino un insieme comune di standard di analisi del codice. La creazione di un elemento di lavoro per la violazione di una regola di analisi del codice è una procedura semplice che è possibile eseguire nella finestra di Elenco errori.|-   [migliorare la qualità del codice con i criteri di archiviazione del progetto team](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)<br />-   [procedura: sincronizzare i set di regole del progetto di codice con i criteri di archiviazione del progetto team](../code-quality/how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy.md)<br />-   [procedura: creare un elemento di lavoro per un difetto del codice gestito](../code-quality/how-to-create-a-work-item-for-a-managed-code-defect.md)|
