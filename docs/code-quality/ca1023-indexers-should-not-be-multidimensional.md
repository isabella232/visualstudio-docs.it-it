---
title: 'CA1023: Gli indicizzatori non devono essere multidimensionali'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IndexersShouldNotBeMultidimensional
- CA1023
helpviewer_keywords:
- CA1023
- IndexersShouldNotBeMultidimensional
ms.assetid: ae499879-97f6-434e-a61d-1fedd231d2fb
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: f788ded21ef5dd9c84d218cedb55ec8dcf7eff2d
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236172"
---
# <a name="ca1023-indexers-should-not-be-multidimensional"></a>CA1023: Gli indicizzatori non devono essere multidimensionali

|||
|-|-|
|TypeName|IndexersShouldNotBeMultidimensional|
|CheckId|CA1023|
|Category|Microsoft.Design|
|Modifica|Interruzione|

## <a name="cause"></a>Causa
Un tipo pubblico o protetto contiene un indicizzatore pubblico o protetto che usa più di un indice.

## <a name="rule-description"></a>Descrizione della regola
Gli indicizzatori, ovvero le proprietà indicizzate, devono utilizzare un solo indice. Gli indicizzatori multidimensionali possono ridurre significativamente l'usabilità della libreria. Se per la progettazione sono necessari più indici, riconsiderare se il tipo rappresenta un archivio dati logico. In caso contrario, usare un metodo.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
Per correggere una violazione di questa regola, modificare la progettazione in modo da usare un intero solitario o un indice di stringa oppure usare un metodo anziché l'indicizzatore.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
Eliminare un avviso da questa regola solo dopo aver valutato attentamente la necessità dell'indicizzatore non standard.

## <a name="example"></a>Esempio
Nell'esempio seguente viene illustrato un tipo `DayOfWeek03`,, con un indicizzatore multidimensionale che viola la regola. L'indicizzatore può essere considerato come un tipo di conversione e pertanto viene esposto in modo più appropriato come metodo. Il tipo viene riprogettato in `RedesignedDayOfWeek03` per soddisfare la regola.

[!code-vb[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/VisualBasic/ca1023-indexers-should-not-be-multidimensional_1.vb)]
[!code-cpp[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/CPP/ca1023-indexers-should-not-be-multidimensional_1.cpp)]
[!code-csharp[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/CSharp/ca1023-indexers-should-not-be-multidimensional_1.cs)]

## <a name="related-rules"></a>Regole correlate
[CA1043: USA argomento di stringa o integrale per gli indicizzatori](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md)

[CA1024: Usare le proprietà laddove appropriato](../code-quality/ca1024-use-properties-where-appropriate.md)