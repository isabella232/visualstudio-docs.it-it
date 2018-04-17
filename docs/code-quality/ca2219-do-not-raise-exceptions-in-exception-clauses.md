---
title: 'CA2219: Non generare eccezioni in clausole di eccezione | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- DoNotRaiseExceptionsInExceptionClauses
- CA2219
helpviewer_keywords:
- DoNotRaiseExceptionsInExceptionClauses
- CA2219
ms.assetid: 7b9b0bee-4e8e-49a4-8c40-52142b49061f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: abe5fe25297c61e84e19857747c19b3602f78e0b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="ca2219-do-not-raise-exceptions-in-exception-clauses"></a>CA2219: Non generare eccezioni in clausole di eccezione
|||  
|-|-|  
|TypeName|DoNotRaiseExceptionsInExceptionClauses|  
|CheckId|CA2219|  
|Category|Microsoft.Usage|  
|Modifica importante|Non importante, di rilievo|  
  
## <a name="cause"></a>Causa  
 Viene generata un'eccezione da un `finally`, filtro o una clausola fault.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Quando in una clausola di eccezione viene generata un'eccezione, aumenta notevolmente la difficoltà del debug.  
  
 Quando viene generata un'eccezione un `finally` o clausola fault, la nuova eccezione nasconde l'eccezione attiva, se presente. In questo modo difficili da rilevare ed eseguire il debug dell'errore originale.  
  
 Quando viene generata un'eccezione in una clausola di filtro, il runtime automaticamente intercetta l'eccezione e fa sì che il filtro restituisce false. Non è possibile indicare la differenza tra la restituzione di false e un'eccezione da parte di un filtro. Questo rende difficile rilevare e il debug degli errori nella logica del filtro.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere la violazione di questa regola, non generare in modo esplicito un'eccezione da un `finally`, filtro o una clausola fault.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Non escludere un avviso per questa regola. Non sono scenari in cui un'eccezione generata in una clausola di eccezione offre un vantaggio al codice in esecuzione.  
  
## <a name="related-rules"></a>Regole correlate  
 [CA1065: Non generare eccezioni in posizioni impreviste](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Avvisi di progettazione](../code-quality/design-warnings.md)