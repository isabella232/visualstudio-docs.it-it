---
title: 'Ca1025: sostituire gli argomenti ripetitivi con la matrice params | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1025
- ReplaceRepetitiveArgumentsWithParamsArray
helpviewer_keywords:
- ReplaceRepetitiveArgumentsWithParamsArray
- CA1025
ms.assetid: f009b340-dea3-4459-8fe1-2143aa8b5d0b
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 84809341d7898aeb3defe0447f2a2f1142eb460a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546627"
---
# <a name="ca1025-replace-repetitive-arguments-with-params-array"></a>CA1025: Sostituire gli argomenti ripetitivi con una matrice di parametri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|ReplaceRepetitiveArgumentsWithParamsArray|
|CheckId|CA1025|
|Category|Microsoft. Design|
|Modifica importante|Senza interruzioni|

## <a name="cause"></a>Causa
 Un metodo pubblico o protetto in un tipo pubblico ha più di tre parametri e gli ultimi tre parametri sono dello stesso tipo.

## <a name="rule-description"></a>Descrizione della regola
 Usare una matrice di parametri anziché gli argomenti ripetuti quando il numero esatto di argomenti è sconosciuto e gli argomenti della variabile sono dello stesso tipo oppure possono essere passati come lo stesso tipo. Ad esempio, il <xref:System.Console.WriteLine%2A> metodo fornisce un overload di utilizzo generico che usa una matrice di parametri per accettare un numero qualsiasi di <xref:System.Object> argomenti.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, sostituire gli argomenti ripetuti con una matrice di parametri.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È sempre possibile eliminare un avviso da questa regola. Questo progetto potrebbe tuttavia causare problemi di usabilità.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo che viola questa regola.

 [!code-csharp[FxCop.Design.RepeatArgs#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.RepeatArgs/cs/FxCop.Design.RepeatArgs.cs#1)]
