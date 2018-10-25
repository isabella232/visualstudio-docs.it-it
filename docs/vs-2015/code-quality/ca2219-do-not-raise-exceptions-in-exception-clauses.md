---
title: 'CA2219: Non generare eccezioni in clausole di eccezione | Microsoft Docs'
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
- DoNotRaiseExceptionsInExceptionClauses
- CA2219
helpviewer_keywords:
- DoNotRaiseExceptionsInExceptionClauses
- CA2219
ms.assetid: 7b9b0bee-4e8e-49a4-8c40-52142b49061f
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 2b5f08043985b6a2eb2b5fe0267fefb58ad00587
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49891180"
---
# <a name="ca2219-do-not-raise-exceptions-in-exception-clauses"></a>CA2219: Non generare eccezioni in clausole di eccezione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non eliminare un avviso per questa regola. Non esistono scenari in cui un'eccezione generata in una clausola di eccezione fornisce un vantaggio per l'esecuzione del codice.

## <a name="related-rules"></a>Regole correlate
 [CA1065: Non generare eccezioni in posizioni impreviste](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)

## <a name="see-also"></a>Vedere anche
 [Avvisi di progettazione](../code-quality/design-warnings.md)



