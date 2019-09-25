---
title: 'CA1008: Le enumerazioni devono avere valore zero'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1008
- EnumsShouldHaveZeroValue
helpviewer_keywords:
- CA1008
- EnumsShouldHaveZeroValue
ms.assetid: 3503a73c-360c-416d-8ee4-c2aa44365a05
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: c9b6e48fb82be5a41c420827a32926630bb725ed
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236497"
---
# <a name="ca1008-enums-should-have-zero-value"></a>CA1008: Le enumerazioni devono avere valore zero

|||
|-|-|
|TypeName|EnumsShouldHaveZeroValue|
|CheckId|CA1008|
|Category|Microsoft.Design|
|Modifica|Senza interruzioni: quando viene richiesto di aggiungere un valore **None** a un'enumerazione non flag. Suddivisione: quando viene richiesto di rinominare o rimuovere i valori di enumerazione.|

## <a name="cause"></a>Causa

Un'enumerazione senza applicato <xref:System.FlagsAttribute?displayProperty=fullName> non definisce un membro con un valore pari a zero. In alternativa, un'enumerazione con applicato <xref:System.FlagsAttribute> definisce un membro che ha un valore pari a zero, ma il cui nome non è' none '. In alternativa, l'enumerazione definisce più membri con valore zero.

Per impostazione predefinita, questa regola esamina solo le enumerazioni visibili esternamente, ma è [configurabile](#configurability).

## <a name="rule-description"></a>Descrizione della regola

Il valore predefinito di un'enumerazione non inizializzata, analogamente ad altri tipi di valore, è zero. Un'enumerazione non con attributi di flag deve definire un membro con valore zero, in modo che il valore predefinito sia un valore valido dell'enumerazione. Se appropriato, denominare il membro ' none '. In caso contrario, assegnare zero al membro usato più di frequente. Per impostazione predefinita, se il valore del primo membro di enumerazione non è impostato nella dichiarazione, il valore è zero.

Se un'enumerazione con l'oggetto <xref:System.FlagsAttribute> applicato definisce un membro con valore zero, il nome deve essere ' none ' per indicare che non è stato impostato alcun valore nell'enumerazione. L'uso di un membro a valore zero per qualsiasi altro scopo è contrario all'uso di <xref:System.FlagsAttribute> in quanto gli operatori and e OR bit per bit sono inutili con il membro. Questo implica che a un solo membro deve essere assegnato il valore zero. Se più membri con valore zero si verificano in un'enumerazione con attributi flag, `Enum.ToString()` restituisce risultati non corretti per i membri che non sono zero.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola per le enumerazioni non con attributi di flag, definire un membro con valore pari a zero; si tratta di una modifica senza interruzioni. Per le enumerazioni con attributi di flag che definiscono un membro con valore zero, denominare il membro ' none ' ed eliminare tutti gli altri membri che hanno un valore pari a zero; si tratta di una modifica di rilievo.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

Non eliminare un avviso da questa regola, ad eccezione delle enumerazioni con attributi di flag precedentemente spedite.

## <a name="configurability"></a>Configurabilità

Se questa regola viene eseguita da [analizzatori FxCop](install-fxcop-analyzers.md) (e non con analisi legacy), è possibile configurare le parti della codebase su cui eseguire questa regola, in base all'accessibilità. Ad esempio, per specificare che la regola deve essere eseguita solo sulla superficie dell'API non pubblica, aggiungere la coppia chiave-valore seguente a un file con estensione EditorConfig nel progetto:

```ini
dotnet_code_quality.ca1008.api_surface = private, internal
```

È possibile configurare questa opzione solo per questa regola, per tutte le regole o per tutte le regole in questa categoria (progettazione). Per altre informazioni, vedere [configurare gli analizzatori FxCop](configure-fxcop-analyzers.md).

## <a name="example"></a>Esempio

Nell'esempio seguente vengono illustrate due enumerazioni che soddisfano la regola e `BadTraceOptions`un'enumerazione,, che viola la regola.

[!code-cpp[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/CPP/ca1008-enums-should-have-zero-value_1.cpp)]
[!code-csharp[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/CSharp/ca1008-enums-should-have-zero-value_1.cs)]
[!code-vb[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/VisualBasic/ca1008-enums-should-have-zero-value_1.vb)]

## <a name="related-rules"></a>Regole correlate

- [CA2217 Non contrassegnare le enumerazioni con FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)
- [CA1700 Non denominare i valori enum ' Reserved '](../code-quality/ca1700-do-not-name-enum-values-reserved.md)
- [CA1712 Non anteporre i valori enum al nome del tipo](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)
- [CA1028: L'archiviazione enum deve essere Int32](../code-quality/ca1028-enum-storage-should-be-int32.md)
- [CA1027: Contrassegnare le enumerazioni con FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Vedere anche

- <xref:System.Enum?displayProperty=fullName>