---
title: Analisi del codice per C/C++ Panoramica | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "25"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 84ba9274258fe41b93a980c815bfd808454b9061
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="code-analysis-for-cc-overview"></a>Cenni preliminari sull'analisi del codice per C/C++
Lo strumento di analisi del codice C/C++ fornisce agli sviluppatori informazioni sui possibili errori nel codice sorgente C/C++. Gli errori di codifica più comuni segnalati dallo strumento includono i sovraccarichi del buffer, la memoria non inizializzata, dereferenziazioni al puntatore null e perdite di memoria e risorse.  
  
## <a name="ide-integrated-development-environment-integration"></a>Integrazione nell'IDE (Integrated Development Environment)  
 Per rendere più naturale per gli sviluppatori di utilizzare lo strumento di analisi, è completamente integrato all'interno di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE. Durante il processo di compilazione, tutti gli avvisi generati per il codice sorgente vengono visualizzati nell'elenco errori. È possibile passare al codice sorgente che ha provocato l'avviso e, è possibile visualizzare informazioni aggiuntive sulla causa e possibili soluzioni del problema.  
  
## <a name="pragma-support"></a>supporto #pragma  
 Gli sviluppatori possono utilizzare il `#pragma` direttiva per considerarli come errori; abilitare o disabilitare gli avvisi e l'esclusione di avvisi per singole righe di codice. Per ulteriori informazioni, vedere [procedura: impostare le proprietà di analisi codice per progetti C/C++ ](how-to-set-code-analysis-properties-for-c-cpp-projects.md).  
  
## <a name="annotation-support"></a>Supporto delle annotazioni  
 Annotazioni migliorano l'accuratezza dell'analisi del codice. Annotazioni informazioni aggiuntive sul pre e post-condizioni nei parametri di funzione e tipi restituiscono. Per ulteriori informazioni, vedere [procedura: specificare informazioni aggiuntive di codice utilizzando analysis_assume](../code-quality/how-to-specify-additional-code-information-by-using-analysis-assume.md)  
  
## <a name="run-analysis-tool-as-part-of-check-in-policy"></a>Eseguire lo strumento di analisi come parte di criteri di archiviazione  
 Si potrebbe voler richiedono che tutte le origine codice archiviazioni soddisfino determinati criteri. In particolare, si desidera assicurarsi che l'analisi è stata eseguita come un passaggio di compilazione locale più recente. Per ulteriori informazioni sull'abilitazione di criteri di controllo dell'analisi codice, vedere [creazione e utilizzo Check-In Criteri di analisi codice](../code-quality/creating-and-using-code-analysis-check-in-policies.md)  
  
## <a name="team-build-integration"></a>Integrazione di Team Build  
 È possibile utilizzare le funzionalità integrate del sistema di compilazione per eseguire lo strumento di analisi codice come il [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)] processo di compilazione. Per altre informazioni, vedere [Build the application](http://msdn.microsoft.com/Library/a971b0f9-7c28-479d-a37b-8fd7e27ef692) (Compilare l'applicazione).  
  
## <a name="command-line-support"></a>Supporto della riga di comando  
 Oltre all'integrazione completa nell'ambiente di sviluppo, gli sviluppatori possono utilizzare lo strumento di analisi dalla riga di comando, come illustrato nell'esempio seguente:  
  
 `C:\>cl /analyze Sample.cpp`