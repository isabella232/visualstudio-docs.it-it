---
title: Analisi del codice per C-c + + Panoramica | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
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
caps.latest.revision: 27
author: corob-msft
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c6764e39d55ebe2ce11776035f25d6fdf69be081
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47530392"
---
# <a name="code-analysis-for-cc-overview"></a>Cenni preliminari sull'analisi del codice per C/C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [analisi del codice per C/C++ Panoramica](https://docs.microsoft.com/visualstudio/code-quality/code-analysis-for-c-cpp-overview).  
  
Lo strumento di analisi del codice C/C++ fornisce agli sviluppatori informazioni sui possibili errori nel codice sorgente C/C++. Gli errori di codifica più comuni segnalati dallo strumento includono i sovraccarichi del buffer, la memoria non inizializzata, dereferenziazioni al puntatore null e perdite di memoria e risorse.  
  
## <a name="ide-integrated-development-environment-integration"></a>Integrazione nell'IDE (Integrated Development Environment)  
 Per rendere più naturali agli sviluppatori di utilizzare lo strumento di analisi, è completamente integrato all'interno di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE. Durante il processo di compilazione, tutti gli avvisi generati per il codice sorgente vengono visualizzati nell'elenco errori. È possibile passare al codice sorgente che ha causato l'avviso ed è possibile visualizzare informazioni aggiuntive sulla causa e le possibili soluzioni del problema.  
  
## <a name="pragma-support"></a>#pragma supporto  
 Gli sviluppatori possono utilizzare il `#pragma` direttiva considerarli come errori; Abilita o disabilita gli avvisi e non visualizzare avvisi per singole righe di codice. Per altre informazioni, vedere [procedura: abilitare e disabilitare analisi del codice per avvisi specifici di C/C++](http://msdn.microsoft.com/en-us/910b8518-71f1-4b2e-b012-70647795642a).  
  
## <a name="annotation-support"></a>Supporto delle annotazioni  
 Annotazioni di migliorano l'accuratezza dell'analisi del codice. Le annotazioni forniscono informazioni aggiuntive sulle condizioni di pre-elaborazione e post-sui parametri della funzione e i tipi restituiscono. Per altre informazioni, vedere [procedura: specificare informazioni aggiuntive di codice usando analysis_assume](../code-quality/how-to-specify-additional-code-information-by-using-analysis-assume.md)  
  
## <a name="run-analysis-tool-as-part-of-check-in-policy"></a>Eseguire lo strumento di analisi come parte di criteri di archiviazione  
 È possibile richiedere che tutte le origine codice archiviazioni soddisfino determinati criteri. In particolare, si desidera assicurarsi che l'analisi è stata eseguita come un passaggio di compilazione locale più recente. Per altre informazioni su come abilitare un criterio di controllo dell'analisi codice, vedere [creazione e uso analisi codice Check-In Criteri](../code-quality/creating-and-using-code-analysis-check-in-policies.md)  
  
## <a name="team-build-integration"></a>Integrazione di Team Build  
 È possibile usare le funzionalità integrate del sistema di compilazione per eseguire lo strumento di analisi di codice come passaggio del [!INCLUDE[esprtfs](../includes/esprtfs-md.md)] processo di compilazione. Per altre informazioni, vedere [Build the application](http://msdn.microsoft.com/library/a971b0f9-7c28-479d-a37b-8fd7e27ef692) (Compilare l'applicazione).  
  
## <a name="command-line-support"></a>Supporto della riga di comando  
 Oltre all'integrazione completa nell'ambiente di sviluppo, gli sviluppatori possono inoltre utilizzare lo strumento di analisi dalla riga di comando, come illustrato nell'esempio seguente:  
  
 `C:\>cl /analyze Sample.cpp`



