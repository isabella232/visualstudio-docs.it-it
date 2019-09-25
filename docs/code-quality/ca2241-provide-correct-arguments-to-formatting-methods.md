---
title: 'CA2241: Specificare argomenti corretti ai metodi di formattazione'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2241
- Provide correct arguments to formatting methods
- ProvideCorrectArgumentsToFormattingMethods
helpviewer_keywords:
- ProvideCorrectArgumentsToFormattingMethods
- CA2241
ms.assetid: 83639bc4-4c91-4a07-a40e-dc5e49a84494
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 3767d361375ce1b3d54281a6850d9ac3b960ece6
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237859"
---
# <a name="ca2241-provide-correct-arguments-to-formatting-methods"></a>CA2241: Specificare argomenti corretti ai metodi di formattazione

|||
|-|-|
|TypeName|ProvideCorrectArgumentsToFormattingMethods|
|CheckId|CA2241|
|Category|Microsoft.Usage|
|Modifica|Senza interruzioni|

## <a name="cause"></a>Causa
L' `format` argomento di stringa passato a un metodo <xref:System.Console.WriteLine%2A>come, <xref:System.Console.Write%2A>o <xref:System.String.Format%2A?displayProperty=fullName> non contiene un elemento di formato corrispondente a ogni argomento dell'oggetto o viceversa.

## <a name="rule-description"></a>Descrizione della regola
Gli argomenti dei metodi <xref:System.Console.WriteLine%2A>come, <xref:System.Console.Write%2A>e <xref:System.String.Format%2A> sono costituiti da una stringa di formato seguita da <xref:System.Object?displayProperty=fullName> più istanze. La stringa di formato è costituita da testo e elementi di formato incorporato nel formato, {index [, Alignment] [: formatString]}. 'index' è un intero in base zero che indica quali oggetti sono da formattare. Se un oggetto non dispone di un indice corrispondente nella stringa di formato, l'oggetto viene ignorato. Se l'oggetto specificato da' index ' non esiste, viene generata <xref:System.FormatException?displayProperty=fullName> un'eccezione in fase di esecuzione.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
Per correggere una violazione di questa regola, fornire un elemento di formato per ogni argomento dell'oggetto e fornire un argomento dell'oggetto per ogni elemento di formato.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
Nell'esempio seguente vengono illustrate due violazioni della regola.

[!code-vb[FxCop.Usage.FormattingArguments#1](../code-quality/codesnippet/VisualBasic/ca2241-provide-correct-arguments-to-formatting-methods_1.vb)]
[!code-csharp[FxCop.Usage.FormattingArguments#1](../code-quality/codesnippet/CSharp/ca2241-provide-correct-arguments-to-formatting-methods_1.cs)]