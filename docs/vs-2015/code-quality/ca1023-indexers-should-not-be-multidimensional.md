---
title: 'CA1023: Gli indicizzatori non devono essere multidimensionali | Microsoft Docs'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 2b9cf9cd97dd50577a466ed4d433e0e1dbd5da4d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58966989"
---
# <a name="ca1023-indexers-should-not-be-multidimensional"></a>CA1023: Gli indicizzatori non devono essere multidimensionali
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|IndexersShouldNotBeMultidimensional|
|CheckId|CA1023|
|Category|Microsoft.Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un tipo pubblico o protetto contiene un indicizzatore pubblico o protetto che usa più di un indice.

## <a name="rule-description"></a>Descrizione della regola
 Gli indicizzatori, ovvero, le proprietà indicizzate, devono utilizzare un singolo indice. Gli indicizzatori multidimensionali possono ridurre notevolmente l'usabilità della libreria. Se il progetto richiede più indici, valutare se il tipo rappresenta un archivio dati logici. In caso contrario, usare un metodo.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, modificare la progettazione per utilizzare un unico numero intero o un indice di stringa o usare un metodo invece l'indicizzatore.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Eliminare un avviso da questa regola solo dopo aver considerato con attenzione la necessità per l'indicizzatore non standard.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo, `DayOfWeek03`, con un indicizzatore multidimensionale che viola la regola. L'indicizzatore può essere considerato come un tipo di conversione e pertanto in modo più appropriato è esposta come un metodo. Il tipo è stato riprogettato `RedesignedDayOfWeek03` per soddisfare la regola.

 [!code-cpp[FxCop.Design.OneDimensionForIndexer#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.OneDimensionForIndexer/cpp/FxCop.Design.OneDimensionForIndexer.cpp#1)]
 [!code-csharp[FxCop.Design.OneDimensionForIndexer#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.OneDimensionForIndexer/cs/FxCop.Design.OneDimensionForIndexer.cs#1)]
 [!code-vb[FxCop.Design.OneDimensionForIndexer#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.OneDimensionForIndexer/vb/FxCop.Design.OneDimensionForIndexer.vb#1)]

## <a name="related-rules"></a>Regole correlate
 [CA1043: Usare l'argomento di stringa o integrale per gli indicizzatori](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md)

 [CA1024: Utilizzare proprietà dove appropriato](../code-quality/ca1024-use-properties-where-appropriate.md)
