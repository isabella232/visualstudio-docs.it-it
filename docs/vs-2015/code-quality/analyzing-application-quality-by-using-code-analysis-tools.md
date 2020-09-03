---
title: Analisi della qualità dell'applicazione tramite gli strumenti di analisi del codice | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.analysisresults
helpviewer_keywords:
- application quality, analyzing
- code analysis
- team-based development, analyzing application quality
ms.assetid: 21680516-ddb5-446d-90d4-19d94f6ec699
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f8ec0706530cd61653d44533654cf453d25eb42e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "75919068"
---
# <a name="analyzing-application-quality-by-using-code-analysis-tools"></a>Analisi della qualità dell'applicazione tramite gli strumenti di analisi del codice
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In questa sezione si [analizza la qualità del codice gestito](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md) analisi del codice di Visual Studio per il codice gestito vengono fornite informazioni sugli assembly gestiti, ad esempio le violazioni delle regole di programmazione e progettazione definite nelle linee guida di progettazione di Microsoft .NET Framework. I messaggi di avviso identificano eventuali problemi di programmazione e progettazione e, se possibile, forniscono informazioni su come risolverli.

 Analisi della [qualità del codice C/C++ tramite l'analisi del codice](../code-quality/analyzing-c-cpp-code-quality-by-using-code-analysis.md) Lo strumento di analisi del codice C/C++ fornisce agli sviluppatori informazioni sui possibili difetti nel codice sorgente C/C++. Gli errori di codifica più comuni segnalati dallo strumento includono i sovraccarichi del buffer, la memoria non inizializzata, dereferenziazioni al puntatore null e perdite di memoria e risorse.

 [Utilizzo di set di regole per raggruppare regole di analisi del codice](../code-quality/using-rule-sets-to-group-code-analysis-rules.md) Selezionare e creare i *set di regole* da applicare al progetto.

 [Errori dell'applicazione di analisi del codice](../code-quality/code-analysis-application-errors.md) Correggere gli errori nella funzionalità di analisi del codice.

 [Miglioramento della qualità del codice con i criteri di archiviazione del progetto team](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md) Quando si usa controllo della versione di Team Foundation (TFVC), è possibile creare criteri di archiviazione per i progetti team che applicano procedure che consentano di migliorare il codice e lo sviluppo di gruppi più efficienti. I criteri di archiviazione sono regole che vengono impostate a livello di progetto team e applicate nei computer degli sviluppatori prima che sia consentita l'archiviazione del codice.

### <a name="code-analysis-for-drivers"></a>Code Analysis for Drivers
 Gli strumenti di analisi del codice consentono di migliorare la stabilità e l'affidabilità del driver analizzando sistematicamente il codice sorgente del driver.

 [Analisi della qualità dei driver tramite gli strumenti di analisi del codice](/windows-hardware/drivers/devtest/tools-for-verifying-drivers) L'analisi del codice per i driver è uno strumento di verifica statica in fase di compilazione che rileva gli errori di codifica di base nei programmi C e C++ e include un modulo specializzato progettato per rilevare gli errori nel codice driver in modalità kernel (principalmente). Static Driver Verifier (SDV) è uno strumento di verifica statica che analizza sistematicamente il codice sorgente dei driver in modalità kernel Windows. SDV stabilisce se il driver interagisce correttamente con il kernel del sistema operativo Windows.

 [Avvisi di analisi del codice per i driver](/windows-hardware/drivers/devtest/prefast-for-drivers-warnings) Vengono descritti gli avvisi segnalati dall'analisi del codice per i driver quando viene rilevato un possibile errore nel codice del driver.

## <a name="related-tasks"></a>Attività correlate
 [Misurazione della complessità e della gestibilità del codice gestito](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md) Inserire qui la descrizione.

 [Eseguire unit test del codice](../test/unit-test-your-code.md) Inserire qui la descrizione.
