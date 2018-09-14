---
title: 'CA1505: evitare codice non manutenibile'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9aae34f6e999bcf74fdfbae4597b22529863e34f
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2018
ms.locfileid: "45546915"
---
# <a name="ca1505-avoid-unmaintainable-code"></a>CA1505: evitare codice non manutenibile

|||
|-|-|
|TypeName|AvoidUnmantainableCode|
|CheckId|CA1505|
|Category|Microsoft.Maintainability|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa
 Un tipo o metodo presenta un valore di indice di gestibilità basso.

## <a name="rule-description"></a>Descrizione della regola
 L'indice di manutenibilità viene calcolato usando le metriche seguenti: righe di codice, il volume del programma e complessità ciclomatica. Il volume del programma è una misura della difficoltà di comprensione di un tipo o metodo che si basa sul numero di operatori e operandi nel codice. Complessità ciclomatica è una misura della complessità strutturale del tipo o metodo. Altre informazioni sulla metrica del codice in [misurazione della complessità e manutenibilità del codice gestito](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md).

 Un indice di manutenibilità basso indica che un tipo o metodo è probabilmente difficile da gestire e sarebbe un buon candidato per la riprogettazione.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere questa violazione, riprogettare il tipo o metodo e tentare di suddividerlo in più mirati e limitati di tipi o metodi.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 Escludere questo avviso quando un tipo o metodo è considerato accettabile nonostante le grandi dimensioni o quando il tipo o metodo non può essere divisa.

## <a name="see-also"></a>Vedere anche

- [Avvisi di manutenibilità](../code-quality/maintainability-warnings.md)
- [Misurazione della complessità e della manutenibilità del codice gestito](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)