---
title: Panoramica dell'analisi del codice gestito | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: overview
f1_keywords:
- vs.projectpropertypages.codeanalysis
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
ms.assetid: 12ec0dab-46a4-43d8-984a-440730ef37a9
caps.latest.revision: 37
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 33ab4a000fac75c51c32e8a6d37de62e006160b3
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/20/2020
ms.locfileid: "72610066"
---
# <a name="code-analysis-for-managed-code-overview"></a>Panoramica dell'analisi codice gestito
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L'analisi del codice gestito analizza gli assembly gestiti e fornisce informazioni sugli assembly, ad esempio le violazioni delle regole di programmazione e progettazione definite nelle linee guida di progettazione di Microsoft .NET Framework.

 Lo strumento di analisi rappresenta i controlli eseguiti durante un'analisi come messaggi di avviso. I messaggi di avviso identificano eventuali problemi di programmazione e progettazione e, se possibile, forniscono informazioni su come risolverli.

## <a name="ide-integrated-development-environment-integration"></a>Integrazione nell'IDE (Integrated Development Environment)
 Gli sviluppatori possono eseguire l'analisi del codice del progetto automaticamente o manualmente.

 Per eseguire l'analisi del codice ogni volta che si compila un progetto, selezionare **Abilitare l'analisi codice in fase di compilazione (definisce la costante CODE_ANALYSIS)** nella Pagina delle proprietà del progetto. Per ulteriori informazioni, vedere [Procedura: abilitare e disabilitare l'analisi automatica](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)del codice .

 Per eseguire manualmente l'analisi del codice su un progetto, dal menu **Analizza** fare clic su **Esegui analisi codice su**_NomeProgetto_. Per ulteriori informazioni, vedere [Procedura: abilitare e disabilitare l'analisi automatica](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)del codice .

## <a name="rule-sets"></a>Set di regole
 Le regole per l'analisi del codice gestito vengono raggruppate in *set di regole*. È possibile utilizzare uno dei set di regole standard Microsoft oppure creare un set di regole personalizzato per soddisfare una specifica esigenza. Per altre informazioni, vedere [Uso di set di regole per raggruppare regole di analisi del codice](../code-quality/using-rule-sets-to-group-code-analysis-rules.md).

## <a name="in-source-suppression"></a>Eliminazione nell'origine
 È in genere utile indicare se un avviso non è applicabile. In questo modo lo sviluppatore e altri individui che potrebbero esaminare il codice in un secondo momento verranno informati del fatto che un avviso è stato sottoposto ad analisi, quindi è stato eliminato o ignorato.

 L'eliminazione nell'origine degli avvisi viene implementata attraverso attributi personalizzati. Per non visualizzare un avviso, aggiungere l'attributo `SuppressMessage` al codice sorgente, come illustrato nell'esempio seguente:

 ```csharp
 [System.Diagnostics.CodeAnalysis.SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]
 Public class MyClass
 {
     // code
 }
 ```

 Per altre informazioni, vedere [Rimuovere avvisi tramite l'attributo SuppressMessage](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md).

## <a name="run-code-analysis-as-part-of-check-in-policy"></a>Eseguire l'analisi del codice come parte dei criteri di archiviazione
 Le organizzazioni richiedono talvolta che tutte le archiviazioni soddisfino determinati criteri, tra cui, in particolare:

- Assenza di errori di compilazione nel codice da archiviare.

- Esecuzione dell'analisi del codice durante la compilazione più recente.

  A tale scopo, è utile quindi definire dei criteri specifici per l'archiviazione. Per altre informazioni, vedere [Miglioramento della qualità del codice con i criteri di archiviazione del progetto team](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md).

## <a name="team-build-integration"></a>Integrazione di Team Build
 È possibile utilizzare le funzionalità integrate del sistema di compilazione per eseguire lo strumento di analisi come parte del processo di compilazione. Per altre informazioni, vedere [Build the application](/azure/devops/pipelines/index) (Compilare l'applicazione).

## <a name="see-also"></a>Vedere anche
 Utilizzo di set di [regole per raggruppare le regole](../code-quality/using-rule-sets-to-group-code-analysis-rules.md) di analisi del [codice: abilitare e disabilitare l'analisi automatica del codiceUsing](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md) Rule Sets to Group Code Analysis Rules How to: Enable and Disable Automatic Code Analysis
