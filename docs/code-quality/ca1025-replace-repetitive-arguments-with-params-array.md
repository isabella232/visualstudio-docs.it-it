---
title: 'Ca1025: Sostituire gli argomenti ripetitivi con una matrice di parametri'
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
ms.openlocfilehash: a6b6c45a8a56cab3927355fc4f03c541bcffc1cf
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72446679"
---
# <a name="ca1025-replace-repetitive-arguments-with-params-array"></a>Ca1025: Sostituire gli argomenti ripetitivi con una matrice di parametri

|||
|-|-|
|TypeName|ReplaceRepetitiveArgumentsWithParamsArray|
|CheckId|CA1025|
|Category|Microsoft. Design|
|Modifica|Senza interruzioni|

## <a name="cause"></a>Causa
Un metodo pubblico o protetto in un tipo pubblico ha più di tre parametri e gli ultimi tre parametri sono dello stesso tipo.

## <a name="rule-description"></a>Descrizione della regola
Usare una matrice di parametri anziché gli argomenti ripetuti quando il numero esatto di argomenti è sconosciuto e gli argomenti della variabile sono dello stesso tipo oppure possono essere passati come lo stesso tipo. Ad esempio, il metodo <xref:System.Console.WriteLine%2A> fornisce un overload di utilizzo generico che usa una matrice di parametri per accettare un numero qualsiasi di argomenti <xref:System.Object>.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
Per correggere una violazione di questa regola, sostituire gli argomenti ripetuti con una matrice di parametri.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
È sempre possibile eliminare un avviso da questa regola. Questo progetto potrebbe tuttavia causare problemi di usabilità.

## <a name="example"></a>Esempio
Nell'esempio seguente viene illustrato un tipo che viola questa regola.

[!code-csharp[FxCop.Design.RepeatArgs#1](../code-quality/codesnippet/CSharp/ca1025-replace-repetitive-arguments-with-params-array_1.cs)]
