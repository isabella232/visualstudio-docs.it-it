---
title: 'CA1505: evitare codice non gestibile | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidUnmaintainableCode
- CA1505
helpviewer_keywords:
- AvoidUnmaintainableCode
- CA1505
ms.assetid: 8292b268-5929-4221-b699-f9c414bcec5d
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 87aacfd675181e35d289b2a054c58f83f3f790fa
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72607582"
---
# <a name="ca1505-avoid-unmaintainable-code"></a>CA1505: evitare codice non manutenibile
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidUnmantainableCode|
|CheckId|CA1505|
|Category|Microsoft. gestibilità|
|Modifica importante|Senza interruzioni|

## <a name="cause"></a>Causa
 Un tipo o metodo presenta un valore di indice di gestibilità basso.

## <a name="rule-description"></a>Descrizione della regola
 L'indice di gestibilità viene calcolato usando le metriche seguenti: righe di codice, volume del programma e complessità ciclomatica. Il volume del programma è una misura della difficoltà di comprensione di un tipo o di un metodo basato sul numero di operatori e operandi nel codice. La complessità ciclomatica è una misura della complessità strutturale del tipo o del metodo. È possibile ottenere altre informazioni sulle metriche del codice per [misurare la complessità e la gestibilità del codice gestito](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md).

 Un indice a bassa gestibilità indica che un tipo o un metodo è probabilmente difficile da gestire ed è un buon candidato per la riprogettazione.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere la violazione, riprogettare il tipo o il metodo e provare a suddividerlo in tipi o metodi più piccoli e più specifici.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Escludere questo avviso quando un tipo o un metodo è ancora considerato gestibile nonostante le sue dimensioni grandi o quando il tipo o il metodo non può essere suddiviso.

## <a name="see-also"></a>Vedere anche
 [Avvisi di gestibilità](../code-quality/maintainability-warnings.md) [per la misurazione della complessità e della gestibilità del codice gestito](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)
