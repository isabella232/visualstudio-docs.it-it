---
title: 'CA2219: non generare eccezioni in clausole di eccezione | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotRaiseExceptionsInExceptionClauses
- CA2219
helpviewer_keywords:
- DoNotRaiseExceptionsInExceptionClauses
- CA2219
ms.assetid: 7b9b0bee-4e8e-49a4-8c40-52142b49061f
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 960c74625a04b209dc9aa251256e994517a3a52f
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85538528"
---
# <a name="ca2219-do-not-raise-exceptions-in-exception-clauses"></a>CA2219: Non generare eccezioni in clausole di eccezione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|DoNotRaiseExceptionsInExceptionClauses|
|CheckId|CA2219|
|Category|Microsoft. Usage|
|Modifica importante|Senza interruzioni, interruzioni|

## <a name="cause"></a>Causa
 Viene generata un'eccezione da una `finally` clausola, Filter o fault.

## <a name="rule-description"></a>Descrizione della regola
 Quando un'eccezione viene generata in una clausola di eccezione, aumenta significativamente la difficoltà del debug.

 Quando viene generata un'eccezione in una `finally` clausola o fault, la nuova eccezione nasconde l'eccezione attiva, se presente. In questo modo è difficile rilevare ed eseguire il debug dell'errore originale.

 Quando viene generata un'eccezione in una clausola di filtro, il runtime rileva automaticamente l'eccezione e fa in modo che il filtro restituisca false. Non esiste alcun modo per distinguere la differenza tra il filtro e la valutazione di false e un'eccezione generata da un filtro. Ciò rende difficile rilevare ed eseguire il debug degli errori nella logica del filtro.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere questa violazione di questa regola, non generare in modo esplicito un'eccezione da una `finally` clausola, un filtro o un errore.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non eliminare un avviso per questa regola. Non esistono scenari in cui un'eccezione generata in una clausola di eccezione fornisce un vantaggio al codice in esecuzione.

## <a name="related-rules"></a>Regole correlate
 [CA1065: Non generare eccezioni in posizioni non previste](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)

## <a name="see-also"></a>Vedere anche
 [Avvisi di progettazione](../code-quality/design-warnings.md)
