---
title: Errori dell'applicazione di analisi del codice | Microsoft Docs
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
- errors [Visual Studio ALM], code analysis
- code analysis, errors
- managed code, code analysis errors
- code analysis, policy errors
ms.assetid: d8fd9475-ac9b-4085-b5a3-b0c807922cac
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: f33e8cf139193618cfe8fe45d916ec59b38a74c1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47518827"
---
# <a name="code-analysis-application-errors"></a>Errori nell'applicazione dell'analisi del codice
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [errori analisi del codice dell'applicazione](https://docs.microsoft.com/visualstudio/code-quality/code-analysis-application-errors).

In questa sezione è un riferimento dei messaggi di errore generati dallo strumento di analisi codice gestito. Per visualizzare la Guida per un messaggio di errore specifico, digitare il numero di errore nella **cercare** dell'indice.

## <a name="in-this-section"></a>In questa sezione

|||
|-|-|
|[CA0001](ca0001.md)|È stata generata un'eccezione all'interno dello strumento di analisi codice gestito che non indica una condizione di errore previsto.|
|[CA0051](ca0051.md)|Nessuna regola selezionata.|
|[CA0052](ca0052.md)|Nessuna destinazione selezionata per l'analisi.|
|[CA0053](ca0053.md)|Non è stato possibile caricare l'assembly di regole.|
|[CA0054](ca0054.md)|Un assembly di regole personalizzato dispone di risorse XML non valide.|
|[CA0055](ca0055.md)|Impossibile caricare il file:\<percorso >|
|[CA0056](ca0056.md)|Un file di progetto ha una versione non corretta dello strumento di analisi.|
|[CA0057](ca0057.md)|Le violazioni non è possibile eseguire il mapping al set corrente di destinazioni e le regole.|
|[CA0058](ca0058.md)|Impossibile caricare gli assembly cui viene fatto riferimenti.|
|[CA0059](ca0059.md)|Errore di opzione della riga di comando.|
|[CA0060](ca0060.md)|Impossibile caricare gli assembly cui viene fatto riferimento indirettamente.|
|[CA0061](ca0061.md)|La regola '*RuleId*' non è stato trovato.|
|[CA0062](ca0062.md)|La regola '*RuleId*'a cui viene fatto riferimento nel set di regole'*RuleSetName*' non è stato trovato.|
|[CA0063](ca0063.md)|Impossibile caricare il file del set di regole o uno dei relativi file di set di regole dipendenti.|
|[CA0064](ca0064.md)|Analisi non è stata eseguita perché il set di regole specificato non contiene tutte le regole FxCop.|
|[CA0065](ca0065.md)|Costrutto di metadati non supportato: tipo '*nomeTipo*'contiene una proprietà e un campo con lo stesso nome'*NomeCampoProprietà*'|
|[CA0066](ca0066.md)|Il valore '*VersionID*' specificato per il **/targetframeworkversion** non è una versione riconosciuta.|
|[CA0067](ca0067.md)|Directory non trovata.|
|[CA0068](ca0068.md)|Eseguire il debug è stato possibile trovare informazioni per assembly di destinazione *'AssemblyName'*.|
|[CA0069](ca0069.md)|Utilizzo della piattaforma alternativa. *FrameworkVersion1* nebyl nalezen. Usando *FrameworkVersion2* invece. Per risultati di analisi ottimali assicurarsi che la versione corretta di .NET Framework sia installato.|
|[CA0070](ca0070.md)|Impossibile caricare l'assembly o un tipo a causa di autorizzazioni di sicurezza.|
|[CA0501](ca0501.md)|Impossibile leggere il report di output.|
|[CA0502](ca0502.md)|Lingua non supportata.|
|[CA0503](ca0503.md))|Questa proprietà è deprecata. Utilizzare la proprietà superceding|
|[CA0504](ca0504.md)|La directory di regole è stata ignorata perché non esiste|
|[CA0505](ca0505.md)|Questa proprietà è deprecata. Utilizzare la proprietà superceding|
|[Errori di FxCopCmd](fxcopcmd-errors.md)|Errori di analisi codice gestito.|
|[Code Analysis Policy Errors](../code-quality/code-analysis-policy-errors.md)|Gli errori dei criteri di analisi archiviazione di codice.|

## <a name="related-sections"></a>Sezioni correlate

- [Linee guida per la scrittura di codice sicuro](http://msdn.microsoft.com/en-us/9892fd19-45cd-44b6-9fa8-10f1b5cb6ea4)
- [Analisi della qualità del codice gestito](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)
- [Risorse per la risoluzione degli errori negli strumenti di gestione del ciclo di vita dell'applicazione](http://msdn.microsoft.com/library/76ca8f76-1e2d-4b55-89e2-bd59e4abe74c)