---
title: 'CA1025: Sostituire gli argomenti ripetitivi con una matrice | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
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
ms.openlocfilehash: b649a5eaa26365fcf7b620ae10db037269716b08
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49912812"
---
# <a name="ca1025-replace-repetitive-arguments-with-params-array"></a>Ca1025: Sostituire gli argomenti ripetitivi con una matrice di parametri
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



