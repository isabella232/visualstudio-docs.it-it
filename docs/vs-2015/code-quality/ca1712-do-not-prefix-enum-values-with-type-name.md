---
title: 'CA1712: non anteporre i valori enum al nome del tipo | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1712
- DoNotPrefixEnumValuesWithTypeName
helpviewer_keywords:
- CA1712
- DoNotPrefixEnumValuesWithTypeName
ms.assetid: df0e3a12-67bf-48f1-a10b-2ef60484a5c7
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 4773a34ab7112434813990b4d25cbeeb865f3a08
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543897"
---
# <a name="ca1712-do-not-prefix-enum-values-with-type-name"></a>CA1712: Non usare nomi di tipo come prefisso nei valori di enumerazione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|DoNotPrefixEnumValuesWithTypeName|
|CheckId|CA1712|
|Category|Microsoft. Naming|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un'enumerazione contiene un membro il cui nome inizia con il nome del tipo dell'enumerazione.

## <a name="rule-description"></a>Descrizione della regola
 I nomi dei membri dell'enumerazione non sono preceduti dal nome del tipo perché le informazioni sul tipo devono essere fornite dagli strumenti di sviluppo.

 Le convenzioni di denominazione forniscono un aspetto comune per le librerie destinate al Common Language Runtime. In questo modo si riduce il tempo necessario per l'apprendimento di una nuova raccolta di software e aumenta la fiducia dei clienti che la libreria è stata sviluppata da un utente esperto nello sviluppo di codice gestito.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, rimuovere il prefisso del nome del tipo dal membro dell'enumerazione.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrata un'enumerazione con nome non corretto seguita dalla versione corretta.

 [!code-cpp[FxCop.Naming.EnumValues#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Naming.EnumValues/cpp/FxCop.Naming.EnumValues.cpp#1)]
 [!code-csharp[FxCop.Naming.EnumValues#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Naming.EnumValues/cs/FxCop.Naming.EnumValues.cs#1)]
 [!code-vb[FxCop.Naming.EnumValues#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Naming.EnumValues/vb/FxCop.Naming.EnumValues.vb#1)]

## <a name="related-rules"></a>Regole correlate
 [CA1711: Gli identificatori non devono contenere un suffisso non corretto](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)

 [CA1027: Contrassegnare le enumerazioni con FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217: Non contrassegnare le enumerazioni con FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Vedere anche
 <xref:System.Enum?displayProperty=fullName>
