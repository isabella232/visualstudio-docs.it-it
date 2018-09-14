---
title: 'CA2219: Non generare eccezioni in clausole di eccezione'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
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
ms.openlocfilehash: e80409a1837da3e82e375561341f4fb4c3da9c28
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2018
ms.locfileid: "45548245"
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
 Se in una clausola di eccezione viene generata un'eccezione, aumenta notevolmente la difficoltà del debug.

 Quando viene generata un'eccezione un `finally` o clausola fault, la nuova eccezione nasconde l'eccezione attiva, se presente. Ciò rende difficile da rilevare ed eseguire il debug dell'errore originale.

 Quando viene generata un'eccezione in una clausola di filtro, il runtime in modo invisibile intercetta l'eccezione e fa sì che il filtro restituisce false. Non è possibile indicare la differenza tra la restituzione di false e un'eccezione da parte di un filtro. Questo rende difficile rilevare e il debug degli errori nella logica del filtro.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere la violazione di questa regola, non generare in modo esplicito un'eccezione da un `finally`, filtro o una clausola fault.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 Non eliminare un avviso per questa regola. Non esistono scenari in cui un'eccezione generata in una clausola di eccezione fornisce un vantaggio per l'esecuzione del codice.

## <a name="related-rules"></a>Regole correlate
 [CA1065: Non generare eccezioni in posizioni impreviste](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)

## <a name="see-also"></a>Vedere anche
 [Avvisi di progettazione](../code-quality/design-warnings.md)