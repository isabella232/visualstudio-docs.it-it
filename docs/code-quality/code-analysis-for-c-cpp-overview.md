---
title: Cenni preliminari sull'analisi del codice per C/C++
ms.date: 04/28/2018
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
ms.openlocfilehash: 07ba2c64be0af987b82c870b89d3451b5d48d28f
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55947640"
---
# <a name="code-analysis-for-cc-overview"></a>Analisi del codice per C/C++: Panoramica

Lo strumento di analisi del codice C/C++ fornisce informazioni sui possibili errori nel codice sorgente C/C++. Gli errori di codifica più comuni segnalati dallo strumento includono i sovraccarichi del buffer, l'annullamento dell'inizializzazione della memoria, le dereferenziazioni al puntatore null e le perdite di memoria e risorse. Lo strumento può anche eseguire controlli a fronte di [linee guida di base di C++](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md).

## <a name="ide-integrated-development-environment-integration"></a>Integrazione nell'IDE (ambiente di sviluppo integrato)

Lo strumento di analisi codice è completamente integrato nell'IDE di Visual Studio.

Durante il processo di compilazione, tutti gli avvisi generati a causa del codice sorgente vengono visualizzati nell'Elenco errori. È possibile passare al codice sorgente che ha causato l'avviso e visualizzare informazioni aggiuntive sulla causa e le possibili soluzioni del problema.

## <a name="command-line-support"></a>Supporto della riga di comando

È anche possibile usare lo strumento di analisi dalla riga di comando, come illustrato nell'esempio seguente:

```cmd
C:\>cl /analyze Sample.cpp
```

**Visual Studio 2017 versione 15.7 e successive** è possibile eseguire lo strumento da riga di comando con qualsiasi sistema di compilazione inclusi CMake.

## <a name="pragma-support"></a>supporto #pragma

È possibile usare il `#pragma` direttiva considerarli come errori; Abilita o disabilita gli avvisi e non visualizzare avvisi per singole righe di codice. Per altre informazioni, vedere [Procedura: Impostare le proprietà di analisi codice per progetti C/C++](how-to-set-code-analysis-properties-for-c-cpp-projects.md).

## <a name="annotation-support"></a>Supporto delle annotazioni

Le annotazioni rendono più precisa l'analisi del codice, in quanto offrono informazioni aggiuntive sulle pre- e post-condizioni in parametri di funzione e tipi restituiti. Per altre informazioni, vedere [Procedura: Specificare informazioni aggiuntive sul codice usando __analysis_assume](../code-quality/how-to-specify-additional-code-information-by-using-analysis-assume.md)

## <a name="run-analysis-tool-as-part-of-check-in-policy"></a>Eseguire lo strumento di analisi come parte dei criteri di archiviazione

È possibile che tutte le archiviazioni del codice sorgente debbano soddisfare determinati criteri, in particolare, assicurarsi che l'analisi sia stata eseguita come parte del processo di compilazione locale più recente. Per altre informazioni su come abilitare i criteri di archiviazione dell'analisi codice, vedere [Creazione e uso di criteri di archiviazione di analisi codice](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md)

## <a name="team-build-integration"></a>Integrazione di Team Build

È possibile usare le funzionalità integrate del sistema di compilazione per eseguire lo strumento di analisi del codice come parte del processo di compilazione di [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)]. Per altre informazioni, vedere [Azure Pipelines](/azure/devops/pipelines/index?view=vsts).

## <a name="see-also"></a>Vedere anche

- [Avvio rapido: Analisi del codice per C/C++](quick-start-code-analysis-for-c-cpp.md)
- [Procedura dettagliata: Analizzare il codice C/C++ per i difetti](walkthrough-analyzing-c-cpp-code-for-defects.md)
- [Avvisi dell'analisi codice per C/C++](code-analysis-for-c-cpp-warnings.md)
- [Usare gli strumenti di verifica delle Linee guida di base di C++](using-the-cpp-core-guidelines-checkers.md)
- [Riferimento di controllo linee guida per la base di C++](code-analysis-for-cpp-corecheck.md)
- [Usare set di regole per specificare le regole C++ da eseguire](using-rule-sets-to-specify-the-cpp-rules-to-run.md)
- [Analizzare la qualità del Driver tramite gli strumenti di analisi codice](/windows-hardware/drivers/develop/analyzing-driver-quality-by-using-code-analysis-tools)
- [Analisi del codice per gli avvisi di driver](/windows-hardware/drivers/devtest/prefast-for-drivers-warnings)
