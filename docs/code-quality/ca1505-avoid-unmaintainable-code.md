---
title: 'CA1505: Evitare codice non gestibile'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AvoidUnmaintainableCode
- CA1505
helpviewer_keywords:
- AvoidUnmaintainableCode
- CA1505
ms.assetid: 8292b268-5929-4221-b699-f9c414bcec5d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 740ef26af6f1f84d23ef27de5176df1b3de98b34
ms.sourcegitcommit: 36f5ffd6ae3215fe31837f4366158bf0d871f7a9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/08/2019
ms.locfileid: "59232496"
---
# <a name="ca1505-avoid-unmaintainable-code"></a>CA1505: Evitare codice non gestibile

|||
|-|-|
|TypeName|AvoidUnmantainableCode|
|CheckId|CA1505|
|Category|Microsoft.Maintainability|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa

Un tipo o metodo presenta un valore di indice di gestibilità basso.

## <a name="rule-description"></a>Descrizione della regola

L'indice di manutenibilità viene calcolato usando le metriche seguenti: righe di codice, il volume del programma e complessità ciclomatica. Il volume del programma è una misura della difficoltà di comprensione di un tipo o metodo che si basa sul numero di operatori e operandi nel codice. Complessità ciclomatica è una misura della complessità strutturale del tipo o metodo. Altre informazioni sulla metrica del codice in [misurare la complessità e della manutenibilità del codice gestito](../code-quality/code-metrics-values.md).

Un indice di manutenibilità basso indica che un tipo o metodo è probabilmente difficile da gestire e sarebbe un buon candidato per la riprogettazione.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere questa violazione, riprogettare il tipo o metodo e tentare di suddividerlo in più mirati e limitati di tipi o metodi.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

È possibile eliminare questo avviso quando il tipo o metodo non può essere suddivisi o viene considerato accettabile, nonostante le grandi dimensioni.

## <a name="see-also"></a>Vedere anche

- [Avvisi di manutenibilità](../code-quality/maintainability-warnings.md)
- [Misurare la complessità e della manutenibilità del codice gestito](../code-quality/code-metrics-values.md)