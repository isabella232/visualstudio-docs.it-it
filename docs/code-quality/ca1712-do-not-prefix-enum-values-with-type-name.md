---
title: 'CA1712: Non utilizzare nomi di tipo come prefisso nei valori di enumerazione'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1712
- DoNotPrefixEnumValuesWithTypeName
helpviewer_keywords:
- CA1712
- DoNotPrefixEnumValuesWithTypeName
ms.assetid: df0e3a12-67bf-48f1-a10b-2ef60484a5c7
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 9bf4d7d2ee0df2a6c5330fcfb8fe6bd168e318c9
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72439403"
---
# <a name="ca1712-do-not-prefix-enum-values-with-type-name"></a>CA1712: Non utilizzare nomi di tipo come prefisso nei valori di enumerazione

|||
|-|-|
|TypeName|DoNotPrefixEnumValuesWithTypeName|
|CheckId|CA1712|
|Category|Microsoft. Naming|
|Modifica|Interruzione|

## <a name="cause"></a>Causa
Un'enumerazione contiene un membro il cui nome inizia con il nome del tipo dell'enumerazione.

## <a name="rule-description"></a>Descrizione della regola
I nomi dei membri dell'enumerazione non sono preceduti dal nome del tipo perché le informazioni sul tipo devono essere fornite dagli strumenti di sviluppo.

Le convenzioni di denominazione forniscono un aspetto comune per le librerie destinate al Common Language Runtime. In questo modo si riduce il tempo necessario per l'apprendimento di una nuova raccolta di software e aumenta la fiducia dei clienti che la libreria è stata sviluppata da un utente esperto nello sviluppo di codice gestito.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
Per correggere una violazione di questa regola, rimuovere il prefisso del nome del tipo dal membro dell'enumerazione.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
Nell'esempio seguente viene illustrata un'enumerazione con nome non corretto seguita dalla versione corretta.

[!code-csharp[FxCop.Naming.EnumValues#1](../code-quality/codesnippet/CSharp/ca1712-do-not-prefix-enum-values-with-type-name_1.cs)]
[!code-cpp[FxCop.Naming.EnumValues#1](../code-quality/codesnippet/CPP/ca1712-do-not-prefix-enum-values-with-type-name_1.cpp)]
[!code-vb[FxCop.Naming.EnumValues#1](../code-quality/codesnippet/VisualBasic/ca1712-do-not-prefix-enum-values-with-type-name_1.vb)]

## <a name="related-rules"></a>Regole correlate
[CA1711: Gli identificatori non devono contenere un suffisso non corretto](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)

[CA1027: Contrassegnare le enumerazioni con FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

[CA2217: Non contrassegnare le enumerazioni con FlagsAttribute](../code-quality/ca2217.md)

## <a name="see-also"></a>Vedere anche

- <xref:System.Enum?displayProperty=fullName>
