---
title: 'CA2241: fornire argomenti corretti ai metodi di formattazione | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2241
- Provide correct arguments to formatting methods
- ProvideCorrectArgumentsToFormattingMethods
helpviewer_keywords:
- ProvideCorrectArgumentsToFormattingMethods
- CA2241
ms.assetid: 83639bc4-4c91-4a07-a40e-dc5e49a84494
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 112065b2a8b9a88241ce62dda7b32a2f2c22fc75
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672019"
---
# <a name="ca2241-provide-correct-arguments-to-formatting-methods"></a>CA2241: Fornire argomenti corretti ai metodi di formattazione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ProvideCorrectArgumentsToFormattingMethods|
|CheckId|CA2241|
|Category|Microsoft. Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 L'argomento di stringa `format` passato a un metodo come <xref:System.Console.WriteLine%2A>, <xref:System.Console.Write%2A> o <xref:System.String.Format%2A?displayProperty=fullName> non contiene un elemento di formato corrispondente a ogni argomento dell'oggetto o viceversa.

## <a name="rule-description"></a>Descrizione della regola
 Gli argomenti dei metodi quali <xref:System.Console.WriteLine%2A>, <xref:System.Console.Write%2A> e <xref:System.String.Format%2A> sono costituiti da una stringa di formato seguita da diverse istanze di <xref:System.Object?displayProperty=fullName>. La stringa di formato è costituita da testo e elementi di formato incorporato nel formato, {index [, Alignment] [: formatString]}. 'index' è un intero in base zero che indica quali oggetti sono da formattare. Se un oggetto non dispone di un indice corrispondente nella stringa di formato, l'oggetto viene ignorato. Se l'oggetto specificato da' index ' non esiste, viene generata un'<xref:System.FormatException?displayProperty=fullName> in fase di esecuzione.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, fornire un elemento di formato per ogni argomento dell'oggetto e fornire un argomento dell'oggetto per ogni elemento di formato.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 Nell'esempio seguente vengono illustrate due violazioni della regola.

 [!code-csharp[FxCop.Usage.FormattingArguments#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.FormattingArguments/cs/FxCop.Usage.FormattingArguments.cs#1)]
 [!code-vb[FxCop.Usage.FormattingArguments#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.FormattingArguments/vb/FxCop.Usage.FormattingArguments.vb#1)]
