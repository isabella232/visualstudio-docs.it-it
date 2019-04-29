---
title: 'CA1025: Sostituire gli argomenti ripetitivi con una matrice di parametri'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1025
- ReplaceRepetitiveArgumentsWithParamsArray
helpviewer_keywords:
- ReplaceRepetitiveArgumentsWithParamsArray
- CA1025
ms.assetid: f009b340-dea3-4459-8fe1-2143aa8b5d0b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b4a292cb3f3221b36c163c87881fd23db0606399
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62779419"
---
# <a name="ca1025-replace-repetitive-arguments-with-params-array"></a>CA1025: Sostituire gli argomenti ripetitivi con una matrice di parametri

|||
|-|-|
|TypeName|ReplaceRepetitiveArgumentsWithParamsArray|
|CheckId|CA1025|
|Category|Microsoft.Design|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa
 Un metodo pubblico o protetto in un tipo pubblico presenta più di tre parametri e le ultime tre parametri sono dello stesso tipo.

## <a name="rule-description"></a>Descrizione della regola
 Usare una matrice di parametri anziché argomenti ripetuti quando il numero esatto di argomenti è sconosciuto e gli argomenti variabili sono dello stesso tipo oppure possono essere passati come lo stesso tipo. Ad esempio, il <xref:System.Console.WriteLine%2A> metodo fornisce un overload generico che usa una matrice di parametri per accettare un numero qualsiasi di <xref:System.Object> argomenti.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, sostituire gli argomenti ripetuti con una matrice di parametri.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 È sempre possibile eliminare un avviso da questa regola. Questa progettazione può tuttavia causare problemi di usabilità.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo che viola la regola.

 [!code-csharp[FxCop.Design.RepeatArgs#1](../code-quality/codesnippet/CSharp/ca1025-replace-repetitive-arguments-with-params-array_1.cs)]