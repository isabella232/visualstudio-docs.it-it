---
title: 'CA1025: Sostituire gli argomenti ripetitivi con una matrice | Microsoft Docs'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 83d36f1f5cd31b1ad1833dd805f4386ac71a3ed1
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58970255"
---
# <a name="ca1025-replace-repetitive-arguments-with-params-array"></a>CA1025: Sostituire gli argomenti ripetitivi con una matrice di parametri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È sempre possibile eliminare un avviso da questa regola. Questa progettazione può tuttavia causare problemi di usabilità.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo che viola la regola.

 [!code-csharp[FxCop.Design.RepeatArgs#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.RepeatArgs/cs/FxCop.Design.RepeatArgs.cs#1)]
