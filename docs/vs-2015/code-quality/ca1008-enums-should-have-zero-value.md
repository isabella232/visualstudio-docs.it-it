---
title: 'CA1008: le enumerazioni devono avere valore zero | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0ca58938a55330243315529e9c7990b59d1a6fe5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85548343"
---
# <a name="ca1008-enums-should-have-zero-value"></a>CA1008: Le enumerazioni devono avere valore zero
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|EnumsShouldHaveZeroValue|
|CheckId|CA1008|
|Category|Microsoft. Design|
|Modifica importante|Senza interruzioni: quando viene richiesto di aggiungere un valore **None** a un'enumerazione non flag. Suddivisione: quando viene richiesto di rinominare o rimuovere i valori di enumerazione.|

## <a name="cause"></a>Causa
 Un'enumerazione senza applicato <xref:System.FlagsAttribute?displayProperty=fullName> non definisce un membro con un valore pari a zero oppure un'enumerazione con un oggetto applicato <xref:System.FlagsAttribute> definisce un membro con un valore pari a zero, ma il cui nome non è' none ' o l'enumerazione definisce più membri con valori zero.

## <a name="rule-description"></a>Descrizione della regola
 Il valore predefinito di un'enumerazione non inizializzata, analogamente ad altri tipi di valore, è zero. Un'enumerazione non con attributi di flag deve definire un membro con valore zero, in modo che il valore predefinito sia un valore valido dell'enumerazione. Se appropriato, denominare il membro ' none '. In caso contrario, assegnare zero al membro usato più di frequente. Si noti che, per impostazione predefinita, se il valore del primo membro di enumerazione non è impostato nella dichiarazione, il valore è zero.

 Se un'enumerazione con l'oggetto <xref:System.FlagsAttribute> applicato definisce un membro con valore zero, il nome deve essere ' none ' per indicare che non è stato impostato alcun valore nell'enumerazione. L'uso di un membro a valore zero per qualsiasi altro scopo è contrario all'uso di <xref:System.FlagsAttribute> in quanto gli operatori and e OR bit per bit sono inutili con il membro. Questo implica che a un solo membro deve essere assegnato il valore zero. Si noti che se più membri con valore zero si verificano in un'enumerazione con attributi flag, `Enum.ToString()` restituisce risultati non corretti per i membri che non sono zero.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola per le enumerazioni senza attributi, definire un membro con valore pari a zero; si tratta di una modifica senza interruzioni. Per le enumerazioni con attributi di flag che definiscono un membro con valore zero, denominare il membro ' none ' ed eliminare tutti gli altri membri che hanno un valore pari a zero; si tratta di una modifica di rilievo.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non eliminare un avviso da questa regola, ad eccezione delle enumerazioni con attributi di flag precedentemente spedite.

## <a name="example"></a>Esempio
 Nell'esempio seguente vengono illustrate due enumerazioni che soddisfano la regola e un'enumerazione, `BadTraceOptions` , che viola la regola.

 [!code-cpp[FxCop.Design.EnumsZeroValue#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumsZeroValue/cpp/FxCop.Design.EnumsZeroValue.cpp#1)]
 [!code-csharp[FxCop.Design.EnumsZeroValue#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumsZeroValue/cs/FxCop.Design.EnumsZeroValue.cs#1)]
 [!code-vb[FxCop.Design.EnumsZeroValue#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.EnumsZeroValue/vb/FxCop.Design.EnumsZeroValue.vb#1)]

## <a name="related-rules"></a>Regole correlate
 [CA2217: Non contrassegnare le enumerazioni con FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

 [CA1700: Non denominare 'Reserved' i valori di enumerazione](../code-quality/ca1700-do-not-name-enum-values-reserved.md)

 [CA1712: Non usare nomi di tipo come prefisso nei valori di enumerazione](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

 [CA1028: Le risorse di archiviazione dell'enumerazione devono essere Int32](../code-quality/ca1028-enum-storage-should-be-int32.md)

 [CA1027: Contrassegnare le enumerazioni con FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Vedere anche
 <xref:System.Enum?displayProperty=fullName>
