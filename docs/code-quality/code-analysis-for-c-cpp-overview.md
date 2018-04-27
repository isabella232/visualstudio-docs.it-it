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
ms.openlocfilehash: ea576ba794350e6cee6b20f8ef9adb62f82a9c51
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2018
---
# <a name="code-analysis-for-cc-overview"></a>Analisi del codice per C/C++ overview

Lo strumento di analisi del codice C/C++ fornisce informazioni sui possibili errori nel codice sorgente C/C++. Gli errori di codifica più comuni segnalati dallo strumento includono i sovraccarichi del buffer, l'annullamento dell'inizializzazione della memoria, le dereferenziazioni al puntatore null e le perdite di memoria e risorse. Lo strumento può inoltre eseguire controlli sul [linee guida dei componenti di base di C++](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md).

## <a name="ide-integrated-development-environment-integration"></a>Integrazione nell'IDE (integrated development environment)

Lo strumento di analisi codice è completamente integrato nell'IDE di Visual Studio.

Durante il processo di compilazione, tutti gli avvisi generati per il codice sorgente vengono visualizzati nell'elenco errori. È possibile passare al codice sorgente che ha provocato l'avviso e, è possibile visualizzare informazioni aggiuntive sulla causa e possibili soluzioni del problema.

## <a name="command-line-support"></a>Supporto della riga di comando

È inoltre possibile utilizzare lo strumento di analisi dalla riga di comando, come illustrato nell'esempio seguente:

```cmd
C:\>cl /analyze Sample.cpp
```

**Visual Studio 2017 15.7 e versioni successive** è possibile eseguire lo strumento da riga di comando con qualsiasi sistema di compilazione incluse CMake.

## <a name="pragma-support"></a>supporto #pragma

È possibile utilizzare il `#pragma` direttiva considera gli avvisi come errori; attiva o disattiva gli avvisi e esclusione di avvisi per singole righe di codice. Per altre informazioni, vedere [procedura: impostare le proprietà di analisi codice per progetti C/C++](how-to-set-code-analysis-properties-for-c-cpp-projects.md).

## <a name="annotation-support"></a>Supporto delle annotazioni

Annotazioni migliorano l'accuratezza dell'analisi del codice. Annotazioni informazioni aggiuntive sul pre e post-condizioni nei parametri di funzione e tipi restituiscono. Per altre informazioni, vedere [procedura: specificare informazioni aggiuntive di codice utilizzando analysis_assume](../code-quality/how-to-specify-additional-code-information-by-using-analysis-assume.md)

## <a name="run-analysis-tool-as-part-of-check-in-policy"></a>Eseguire lo strumento di analisi come parte di criteri di archiviazione

Si potrebbe voler richiedono che tutte le origine codice archiviazioni soddisfino determinati criteri. In particolare, si desidera assicurarsi che l'analisi è stata eseguita come un passaggio di compilazione locale più recente. Per ulteriori informazioni sull'abilitazione di criteri di controllo dell'analisi codice, vedere [creazione e utilizzo Check-In Criteri di analisi codice](../code-quality/creating-and-using-code-analysis-check-in-policies.md)

## <a name="team-build-integration"></a>Integrazione di Team Build

È possibile utilizzare le funzionalità integrate del sistema di compilazione per eseguire lo strumento di analisi codice come il [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)] processo di compilazione. Per altre informazioni, vedere [Compilazione e versione](/vsts/build-release/index).

## <a name="see-also"></a>Vedere anche

- [Guida introduttiva: Analisi del codice per C/C++](quick-start-code-analysis-for-c-cpp.md)
- [Procedura dettagliata: Analisi del codice C/C++ per errori del](walkthrough-analyzing-c-cpp-code-for-defects.md)
- [Avvisi dell'analisi codice per C/C++](code-analysis-for-c-cpp-warnings.md)
- [Usare gli strumenti di verifica delle Linee guida di base di C++](using-the-cpp-core-guidelines-checkers.md)
- [Linee guida di base C++ controllo di riferimento](code-analysis-for-cpp-corecheck.md)
- [Usare set di regole per specificare le regole C++ da eseguire](using-rule-sets-to-specify-the-cpp-rules-to-run.md)
- [Analizzare la qualità del Driver tramite gli strumenti di analisi codice](/windows-hardware/drivers/develop/analyzing-driver-quality-by-using-code-analysis-tools)
- [Analisi del codice per gli avvisi di driver](/windows-hardware/drivers/devtest/prefast-for-drivers-warnings)
