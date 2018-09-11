---
title: Cenni preliminari sull'analisi del codice per C/C++
ms.date: 04/28/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- annotations, code analysis
- build integration, code analysis
- C/C++ code analysis
- IDE, code analysis
- pragma directive, code analysis
- code analysis, C/C++
- code analysis tool
- command line, code analysis
- C++, code analysis
- check-in policies, code analysis
- '#pragma directives, code analysis'
- C, code analysis
ms.assetid: 81f0c9e8-f471-4de5-aac4-99db336a8809
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: 35f694d9cc397800249dd9b4acd86bf63d22ad93
ms.sourcegitcommit: 28909340cd0a0d7cb5e1fd29cbd37e726d832631
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/10/2018
ms.locfileid: "44320709"
---
# <a name="code-analysis-for-cc-overview"></a>Analisi del codice per C/C++: Panoramica

Lo strumento di analisi del codice C/C++ fornisce informazioni sui possibili errori nel codice sorgente C/C++. Gli errori di codifica più comuni segnalati dallo strumento includono i sovraccarichi del buffer, l'annullamento dell'inizializzazione della memoria, le dereferenziazioni al puntatore null e le perdite di memoria e risorse. Lo strumento può anche eseguire controlli a fronte di [linee guida di base di C++](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md).

## <a name="ide-integrated-development-environment-integration"></a>Integrazione nell'IDE (ambiente di sviluppo integrato)

Lo strumento di analisi codice è completamente integrato nell'IDE di Visual Studio.

Durante il processo di compilazione, tutti gli avvisi generati per il codice sorgente vengono visualizzati nell'elenco errori. È possibile passare al codice sorgente che ha causato l'avviso ed è possibile visualizzare informazioni aggiuntive sulla causa e le possibili soluzioni del problema.

## <a name="command-line-support"></a>Supporto della riga di comando

È anche possibile usare lo strumento di analisi dalla riga di comando, come illustrato nell'esempio seguente:

```cmd
C:\>cl /analyze Sample.cpp
```

**Visual Studio 2017 versione 15.7 e successive** è possibile eseguire lo strumento da riga di comando con qualsiasi sistema di compilazione inclusi CMake.

## <a name="pragma-support"></a>supporto #pragma

È possibile usare il `#pragma` direttiva considerarli come errori; Abilita o disabilita gli avvisi e non visualizzare avvisi per singole righe di codice. Per altre informazioni, vedere [procedura: impostare le proprietà di analisi codice per progetti C/C++](how-to-set-code-analysis-properties-for-c-cpp-projects.md).

## <a name="annotation-support"></a>Supporto delle annotazioni

Annotazioni di migliorano l'accuratezza dell'analisi del codice. Le annotazioni forniscono informazioni aggiuntive sulle condizioni di pre-elaborazione e post-sui parametri della funzione e i tipi restituiscono. Per altre informazioni, vedere [procedura: specificare informazioni aggiuntive di codice usando analysis_assume](../code-quality/how-to-specify-additional-code-information-by-using-analysis-assume.md)

## <a name="run-analysis-tool-as-part-of-check-in-policy"></a>Eseguire lo strumento di analisi come parte di criteri di archiviazione

È possibile richiedere che tutte le origine codice archiviazioni soddisfino determinati criteri. In particolare, si desidera assicurarsi che l'analisi è stata eseguita come un passaggio di compilazione locale più recente. Per altre informazioni su come abilitare un criterio di controllo dell'analisi codice, vedere [creazione e uso analisi codice Check-In Criteri](../code-quality/creating-and-using-code-analysis-check-in-policies.md)

## <a name="team-build-integration"></a>Integrazione di Team Build

È possibile usare le funzionalità integrate del sistema di compilazione per eseguire lo strumento di analisi di codice come passaggio del [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)] processo di compilazione. Per altre informazioni, vedere [pipeline di Azure](/azure/devops/pipelines/index?view=vsts).

## <a name="see-also"></a>Vedere anche

- [Guida introduttiva: Analisi del codice per C/C++](quick-start-code-analysis-for-c-cpp.md)
- [Procedura dettagliata: Analisi del codice C/C++ per i difetti](walkthrough-analyzing-c-cpp-code-for-defects.md)
- [Avvisi dell'analisi codice per C/C++](code-analysis-for-c-cpp-warnings.md)
- [Usare gli strumenti di verifica delle Linee guida di base di C++](using-the-cpp-core-guidelines-checkers.md)
- [Riferimento di controllo linee guida per la base di C++](code-analysis-for-cpp-corecheck.md)
- [Usare set di regole per specificare le regole C++ da eseguire](using-rule-sets-to-specify-the-cpp-rules-to-run.md)
- [Analizzare la qualità del Driver tramite gli strumenti di analisi codice](/windows-hardware/drivers/develop/analyzing-driver-quality-by-using-code-analysis-tools)
- [Analisi del codice per gli avvisi di driver](/windows-hardware/drivers/devtest/prefast-for-drivers-warnings)
