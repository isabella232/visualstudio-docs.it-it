---
title: 'CA1023: gli indicizzatori non devono essere multidimensionali | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IndexersShouldNotBeMultidimensional
- CA1023
helpviewer_keywords:
- CA1023
- IndexersShouldNotBeMultidimensional
ms.assetid: ae499879-97f6-434e-a61d-1fedd231d2fb
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 30eee67d54e4fc3c73b265240fff82b0729e1cfc
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546649"
---
# <a name="ca1023-indexers-should-not-be-multidimensional"></a>CA1023: Gli indicizzatori non devono essere multidimensionali
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|IndexersShouldNotBeMultidimensional|
|CheckId|CA1023|
|Category|Microsoft. Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un tipo pubblico o protetto contiene un indicizzatore pubblico o protetto che usa più di un indice.

## <a name="rule-description"></a>Descrizione della regola
 Gli indicizzatori, ovvero le proprietà indicizzate, devono utilizzare un solo indice. Gli indicizzatori multidimensionali possono ridurre significativamente l'usabilità della libreria. Se per la progettazione sono necessari più indici, riconsiderare se il tipo rappresenta un archivio dati logico. In caso contrario, usare un metodo.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, modificare la progettazione in modo da usare un intero solitario o un indice di stringa oppure usare un metodo anziché l'indicizzatore.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Eliminare un avviso da questa regola solo dopo aver valutato attentamente la necessità dell'indicizzatore non standard.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo, `DayOfWeek03` , con un indicizzatore multidimensionale che viola la regola. L'indicizzatore può essere considerato come un tipo di conversione e pertanto viene esposto in modo più appropriato come metodo. Il tipo viene riprogettato in `RedesignedDayOfWeek03` per soddisfare la regola.

 [!code-cpp[FxCop.Design.OneDimensionForIndexer#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.OneDimensionForIndexer/cpp/FxCop.Design.OneDimensionForIndexer.cpp#1)]
 [!code-csharp[FxCop.Design.OneDimensionForIndexer#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.OneDimensionForIndexer/cs/FxCop.Design.OneDimensionForIndexer.cs#1)]
 [!code-vb[FxCop.Design.OneDimensionForIndexer#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.OneDimensionForIndexer/vb/FxCop.Design.OneDimensionForIndexer.vb#1)]

## <a name="related-rules"></a>Regole correlate
 [CA1043: Usare un argomento di tipo stringa o integrale per gli indicizzatori](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md)

 [CA1024: Usare proprietà dove appropriato](../code-quality/ca1024-use-properties-where-appropriate.md)
