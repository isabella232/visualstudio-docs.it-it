---
title: 'Ca1025: Sostituire gli argomenti ripetitivi con una matrice di parametri'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f1ce14b7da80775a9837b5e92f25d141276226cf
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
ms.locfileid: "31900515"
---
# <a name="ca1025-replace-repetitive-arguments-with-params-array"></a>Ca1025: Sostituire gli argomenti ripetitivi con una matrice di parametri
|||
|-|-|
|TypeName|ReplaceRepetitiveArgumentsWithParamsArray|
|CheckId|CA1025|
|Category|Microsoft.Design|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa
 Un metodo pubblico o protetto in un tipo pubblico presenta più di tre parametri e i relativi ultimi tre parametri sono dello stesso tipo.

## <a name="rule-description"></a>Descrizione della regola
 Utilizzare una matrice di parametri anziché argomenti ripetuti quando il numero esatto di argomenti e gli argomenti variabili sono dello stesso tipo oppure possono essere passati come lo stesso tipo. Ad esempio, il <xref:System.Console.WriteLine%2A> metodo fornisce un overload generico che utilizza una matrice di parametri per accettare un numero qualsiasi di <xref:System.Object> argomenti.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, sostituire gli argomenti ripetuti con una matrice di parametri.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È sempre possibile eliminare un avviso da questa regola. Tuttavia, ciò potrebbe causare problemi di usabilità.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo che viola questa regola.

 [!code-csharp[FxCop.Design.RepeatArgs#1](../code-quality/codesnippet/CSharp/ca1025-replace-repetitive-arguments-with-params-array_1.cs)]