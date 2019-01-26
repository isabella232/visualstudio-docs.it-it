---
title: 'CA2241: Specificare argomenti corretti ai metodi di formattazione'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: f723e9c3a6f204b1a19648b121637f42d1fb4017
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54920843"
---
# <a name="ca2241-provide-correct-arguments-to-formatting-methods"></a>CA2241: Specificare argomenti corretti ai metodi di formattazione

|||
|-|-|
|TypeName|ProvideCorrectArgumentsToFormattingMethods|
|CheckId|CA2241|
|Category|Microsoft.Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Il `format` argomento passato a un metodo, ad esempio di stringa <xref:System.Console.WriteLine%2A>, <xref:System.Console.Write%2A>, o <xref:System.String.Format%2A?displayProperty=fullName> non contiene un elemento di formato che corrisponde a ogni argomento di oggetto, o viceversa.

## <a name="rule-description"></a>Descrizione della regola
 Gli argomenti ai metodi, ad esempio <xref:System.Console.WriteLine%2A>, <xref:System.Console.Write%2A>, e <xref:System.String.Format%2A> costituiti da una stringa di formato, seguita da diversi <xref:System.Object?displayProperty=fullName> istanze. La stringa di formato è costituito da testo e gli elementi di formato incorporato nel formato {index [, allineamento] [: formatString]}. 'index' è un intero in base zero che indica quali oggetti sono da formattare. Se un oggetto non ha un indice corrispondente nella stringa di formato, l'oggetto viene ignorato. Se l'oggetto specificato da 'index' non esiste, un <xref:System.FormatException?displayProperty=fullName> viene generata un'eccezione in fase di esecuzione.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, forniscono un elemento di formato per ogni argomento di oggetto e un argomento di oggetto per ogni elemento di formato.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 L'esempio seguente illustra due violazioni della regola.

 [!code-vb[FxCop.Usage.FormattingArguments#1](../code-quality/codesnippet/VisualBasic/ca2241-provide-correct-arguments-to-formatting-methods_1.vb)]
 [!code-csharp[FxCop.Usage.FormattingArguments#1](../code-quality/codesnippet/CSharp/ca2241-provide-correct-arguments-to-formatting-methods_1.cs)]