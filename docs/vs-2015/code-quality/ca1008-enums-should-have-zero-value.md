---
title: 'CA1008: Le enumerazioni devono avere valore zero | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1008
- EnumsShouldHaveZeroValue
helpviewer_keywords:
- CA1008
- EnumsShouldHaveZeroValue
ms.assetid: 3503a73c-360c-416d-8ee4-c2aa44365a05
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: e9b607c3a3fd7992bf8947c003d240d3d5b1d312
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58968431"
---
# <a name="ca1008-enums-should-have-zero-value"></a>CA1008: Le enumerazioni devono avere valore zero
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|EnumsShouldHaveZeroValue|
|CheckId|CA1008|
|Category|Microsoft.Design|
|Modifica importante|Non sostanziale - Quando viene richiesto di aggiungere un **None** in un'enumerazione di flag di non valore. Rilievo - quando viene richiesto di rinominare o rimuovere eventuali valori di enumerazione.|

## <a name="cause"></a>Causa
 Un'enumerazione senza un applicato <xref:System.FlagsAttribute?displayProperty=fullName> non definisce un membro con valore uguale a zero; o un'enumerazione con un applicato <xref:System.FlagsAttribute> definisce un membro che ha un valore pari a zero, ma il nome non è 'None' o l'enumerazione definisce multiple con valori zero membri.

## <a name="rule-description"></a>Descrizione della regola
 Il valore predefinito di un'enumerazione non inizializzata, come altri tipi di valore, è zero. Un'enumerazione senza attributi flag definisce un membro con il valore pari a zero, in modo che il valore predefinito è un valore valido dell'enumerazione. Se appropriato, denominare il membro 'None'. In caso contrario, assegna zero per i membri usati più di frequente. Si noti che, per impostazione predefinita, se il valore del primo membro di enumerazione non è impostato nella dichiarazione, il relativo valore è zero.

 Se un'enumerazione contenente il <xref:System.FlagsAttribute> applicato definisce un membro con valore zero, il relativo nome deve essere 'None' per indicare che è stato impostato alcun valore nell'enumerazione. Utilizzando un membro con valore zero per altri scopi sono contrario all'utilizzo del <xref:System.FlagsAttribute> in quanto l'operatore AND e OR operatori bit per bit sono inutili con il membro. Ciò implica che solo un membro deve essere assegnato il valore zero. Si noti che se più membri che hanno il valore zero si verifica in un'enumerazione flag con attributi, `Enum.ToString()` restituisce risultati non corretti per i membri che non sono uguali a zero.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola per le enumerazioni senza attributi flag, definire un membro con il valore pari a 0. si tratta di una modifica non sostanziale. Per le enumerazioni flags con attributi che definiscono un membro con valore zero, nome di questo membro 'None' ed eliminare eventuali altri membri che hanno un valore pari a 0. si tratta di una modifica sostanziale.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola, ad eccezione delle enumerazioni flags attributi fornite in precedenza.

## <a name="example"></a>Esempio
 L'esempio seguente mostra due enumerazioni che soddisfano la regola e un'enumerazione, `BadTraceOptions`, che viola la regola.

 [!code-cpp[FxCop.Design.EnumsZeroValue#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumsZeroValue/cpp/FxCop.Design.EnumsZeroValue.cpp#1)]
 [!code-csharp[FxCop.Design.EnumsZeroValue#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumsZeroValue/cs/FxCop.Design.EnumsZeroValue.cs#1)]
 [!code-vb[FxCop.Design.EnumsZeroValue#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.EnumsZeroValue/vb/FxCop.Design.EnumsZeroValue.vb#1)]

## <a name="related-rules"></a>Regole correlate
 [CA2217: Non contrassegnare le enumerazioni con FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

 [CA1700: Non denominare 'Reserved' i valori di enumerazione](../code-quality/ca1700-do-not-name-enum-values-reserved.md)

 [CA1712: Prefisso nei valori di enumerazione con il nome di tipo](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

 [CA1028: Archivio di enum deve essere Int32](../code-quality/ca1028-enum-storage-should-be-int32.md)

 [CA1027: Contrassegnare le enumerazioni con FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Vedere anche
 <xref:System.Enum?displayProperty=fullName>
