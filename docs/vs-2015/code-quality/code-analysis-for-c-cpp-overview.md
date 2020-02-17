---
title: Panoramica dell'analisi del codice per C-C++ | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: overview
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
caps.latest.revision: 27
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: 1ce41cd1c0dabc94658b83aa5e2bcdc08d005fdb
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2020
ms.locfileid: "77275366"
---
# <a name="code-analysis-for-cc-overview"></a>Cenni preliminari sull'analisi del codice per C/C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Lo strumento di analisi del codice C/C++ fornisce agli sviluppatori informazioni sui possibili errori nel codice sorgente C/C++. Gli errori di codifica più comuni segnalati dallo strumento includono i sovraccarichi del buffer, la memoria non inizializzata, dereferenziazioni al puntatore null e perdite di memoria e risorse.  
  
## <a name="ide-integrated-development-environment-integration"></a>Integrazione nell'IDE (Integrated Development Environment)  
 Per facilitarne l'uso agli sviluppatori, lo strumento di analisi è integrato nell'IDE [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Durante il processo di compilazione, tutti gli avvisi generati a causa del codice sorgente vengono visualizzati nell'Elenco errori. È possibile passare al codice sorgente che ha causato l'avviso e visualizzare informazioni aggiuntive sulla causa e le possibili soluzioni del problema.  
  
## <a name="pragma-support"></a>Supporto di #pragma  
 Gli sviluppatori possono usare la direttiva `#pragma` per considerare gli avvisi come errori, abilitare o disabilitare gli avvisi e non visualizzare gli avvisi per alcune righe di codice. Per altre informazioni, vedere [procedura: abilitare e disabilitare l'analisi del codice per C/C++ avvisi specifici](https://msdn.microsoft.com/910b8518-71f1-4b2e-b012-70647795642a).  
  
## <a name="annotation-support"></a>Supporto di annotazioni  
 Le annotazioni rendono più precisa l'analisi del codice, in quanto offrono informazioni aggiuntive sulle pre- e post-condizioni in parametri di funzione e tipi restituiti. Per altre informazioni, vedere [procedura: specificare informazioni aggiuntive sul codice usando __analysis_assume](../code-quality/how-to-specify-additional-code-information-by-using-analysis-assume.md)  
  
## <a name="run-analysis-tool-as-part-of-check-in-policy"></a>Eseguire lo strumento di analisi come parte dei criteri di archiviazione  
 È possibile che tutte le archiviazioni del codice sorgente debbano soddisfare determinati criteri, in particolare, assicurarsi che l'analisi sia stata eseguita come parte del processo di compilazione locale più recente. Per altre informazioni su come abilitare i criteri di archiviazione dell'analisi codice, vedere [Creazione e uso di criteri di archiviazione di analisi codice](../code-quality/creating-and-using-code-analysis-check-in-policies.md)  
  
## <a name="team-build-integration"></a>Integrazione di Team Build  
 È possibile usare le funzionalità integrate del sistema di compilazione per eseguire lo strumento di analisi del codice come parte del processo di compilazione di [!INCLUDE[esprtfs](../includes/esprtfs-md.md)]. Per altre informazioni, vedere [Build the application](/azure/devops/pipelines/index) (Compilare l'applicazione).  
  
## <a name="command-line-support"></a>Supporto per la riga di comando  
 Gli sviluppatori possono usare lo strumento di analisi come integrazione completa nell'ambiente di sviluppo, ma anche dalla riga di comando, come illustrato nell'esempio seguente:  
  
 `C:\>cl /analyze Sample.cpp`
