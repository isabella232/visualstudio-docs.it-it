---
title: Analisi del codice per la panoramica del codice gestito | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.projectpropertypages.codeanalysis
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
ms.assetid: 12ec0dab-46a4-43d8-984a-440730ef37a9
caps.latest.revision: 37
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 048ea406fd9237640976f3a44bb5e53504276e0c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49279370"
---
# <a name="code-analysis-for-managed-code-overview"></a>Panoramica dell'analisi codice gestito
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L'analisi del codice gestito analizza gli assembly gestiti e fornisce informazioni sugli assembly, ad esempio le violazioni delle regole di programmazione e progettazione definite nelle linee guida di progettazione di Microsoft .NET Framework.  
  
 Lo strumento di analisi rappresenta i controlli eseguiti durante un'analisi come messaggi di avviso. I messaggi di avviso identificano eventuali problemi di programmazione e progettazione e, se possibile, forniscono informazioni su come risolverli.  
  
## <a name="ide-integrated-development-environment-integration"></a>Integrazione nell'IDE (Integrated Development Environment)  
 Gli sviluppatori possono eseguire l'analisi del codice del progetto automaticamente o manualmente.  
  
 Per eseguire l'analisi del codice ogni volta che si compila un progetto, si seleziona **Abilita analisi codice su compilazione (definisce la costante CODE_ANALYSIS)** nella pagina delle proprietà del progetto. Per altre informazioni, vedere [procedura: abilitare e disabilitare analisi del codice automatica](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).  
  
 Per eseguire l'analisi del codice manualmente in un progetto, scegliere il **Analyze** menu, fare clic su **Esegui analisi del codice**_NomeProgetto_. Per altre informazioni, vedere [procedura: abilitare e disabilitare analisi del codice automatica](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).  
  
## <a name="rule-sets"></a>Set di regole  
 Regole di analisi codice per il codice gestito vengono raggruppate in *set di regole*. È possibile utilizzare uno dei set di regole standard Microsoft oppure creare un set di regole personalizzato per soddisfare una specifica esigenza. Per altre informazioni, vedere [usando i set di regole per raggruppare regole di analisi codice](../code-quality/using-rule-sets-to-group-code-analysis-rules.md).  
  
## <a name="in-source-suppression"></a>Eliminazione nell'origine  
 È in genere utile indicare se un avviso non è applicabile. In questo modo lo sviluppatore e altri individui che potrebbero esaminare il codice in un secondo momento verranno informati del fatto che un avviso è stato sottoposto ad analisi, quindi è stato eliminato o ignorato.  
  
 L'eliminazione nell'origine degli avvisi viene implementata attraverso attributi personalizzati. Per non visualizzare un avviso, aggiungere l'attributo `SuppressMessage` al codice sorgente, come illustrato nell'esempio seguente:  
  
 `[System.Diagnosis.CodeAnalysis.SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`  
  
 `Public class MyClass`  
  
 `{`  
  
 `// code`  
  
 `}`  
  
 Per altre informazioni, vedere [non visualizzare avvisi tramite l'utilizzo dell'attributo SuppressMessage](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md).  
  
## <a name="run-code-analysis-as-part-of-check-in-policy"></a>Eseguire l'analisi del codice come parte dei criteri di archiviazione  
 Le organizzazioni richiedono talvolta che tutte le archiviazioni soddisfino determinati criteri, tra cui, in particolare:  
  
-   Assenza di errori di compilazione nel codice da archiviare.  
  
-   Esecuzione dell'analisi del codice durante la compilazione più recente.  
  
 A tale scopo, è utile quindi definire dei criteri specifici per l'archiviazione. Per altre informazioni, vedere [miglioramento della qualità del codice con i criteri di controllo il progetto Team](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md).  
  
## <a name="team-build-integration"></a>Integrazione di Team Build  
 È possibile utilizzare le funzionalità integrate del sistema di compilazione per eseguire lo strumento di analisi come parte del processo di compilazione. Per altre informazioni, vedere [Build the application](http://msdn.microsoft.com/library/a971b0f9-7c28-479d-a37b-8fd7e27ef692) (Compilare l'applicazione).  
  
## <a name="see-also"></a>Vedere anche  
 [Regola di utilizzo di set per raggruppare regole di analisi codice](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)   
 [Procedura: Abilitare e disabilitare l'analisi codice automatica](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)



