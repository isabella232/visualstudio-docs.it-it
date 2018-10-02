---
title: 'CA2241: Fornire argomenti corretti ai metodi di formattazione | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2241
- Provide correct arguments to formatting methods
- ProvideCorrectArgumentsToFormattingMethods
helpviewer_keywords:
- ProvideCorrectArgumentsToFormattingMethods
- CA2241
ms.assetid: 83639bc4-4c91-4a07-a40e-dc5e49a84494
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 6d3b190adfb67e90a50da80453d8ce2db5013723
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2018
ms.locfileid: "47590355"
---
# <a name="ca2241-provide-correct-arguments-to-formatting-methods"></a>CA2241: Fornire argomenti corretti ai metodi di formattazione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [CA2241: fornire argomenti corretti ai metodi di formattazione](https://docs.microsoft.com/visualstudio/code-quality/ca2241-provide-correct-arguments-to-formatting-methods).

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

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 L'esempio seguente illustra due violazioni della regola.

 [!code-csharp[FxCop.Usage.FormattingArguments#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.FormattingArguments/cs/FxCop.Usage.FormattingArguments.cs#1)]
 [!code-vb[FxCop.Usage.FormattingArguments#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.FormattingArguments/vb/FxCop.Usage.FormattingArguments.vb#1)]



