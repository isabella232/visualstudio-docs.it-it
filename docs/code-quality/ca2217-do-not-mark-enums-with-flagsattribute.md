---
title: 'CA2217: Non contrassegnare le enumerazioni con FlagsAttribute'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- DoNotMarkEnumsWithFlags
- CA2217
helpviewer_keywords:
- DoNotMarkEnumsWithFlags
- CA2217
dev_langs:
- VB
- CSharp
- CPP
ms.assetid: 1b6f626c-66bf-45b0-a3e2-7c41ee9ceda7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 377188183acdaa9aa86ae3344c8f6d5727b82ccc
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/16/2019
ms.locfileid: "69546846"
---
# <a name="ca2217-do-not-mark-enums-with-flagsattribute"></a>CA2217: Non contrassegnare le enumerazioni con FlagsAttribute

|||
|-|-|
|TypeName|DoNotMarkEnumsWithFlags|
|CheckId|CA2217|
|Category|Microsoft.Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa

Un'enumerazione è contrassegnata <xref:System.FlagsAttribute> con e contiene uno o più valori che non sono potenze di due o una combinazione degli altri valori definiti nell'enumerazione.

Per impostazione predefinita, questa regola esamina solo le enumerazioni visibili esternamente, ma è [configurabile](#configurability).

## <a name="rule-description"></a>Descrizione della regola

Un'enumerazione deve essere <xref:System.FlagsAttribute> presente solo se ogni valore definito nell'enumerazione è una potenza di due o una combinazione di valori definiti.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, rimuovere <xref:System.FlagsAttribute> dall'enumerazione.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

Non escludere un avviso da questa regola.

## <a name="configurability"></a>Configurabilità

Se questa regola viene eseguita da [analizzatori FxCop](install-fxcop-analyzers.md) (e non con analisi legacy), è possibile configurare le parti della codebase su cui eseguire questa regola, in base all'accessibilità. Ad esempio, per specificare che la regola deve essere eseguita solo sulla superficie dell'API non pubblica, aggiungere la coppia chiave-valore seguente a un file con estensione EditorConfig nel progetto:

```ini
dotnet_code_quality.ca2217.api_surface = private, internal
```

È possibile configurare questa opzione solo per questa regola, per tutte le regole o per tutte le regole in questa categoria (utilizzo). Per altre informazioni, vedere [configurare gli analizzatori FxCop](configure-fxcop-analyzers.md).

## <a name="examples"></a>Esempi

Nel codice seguente viene illustrata un' `Color`enumerazione,, che contiene il valore 3. 3 non è una potenza di due o una combinazione di tutti i valori definiti. L' `Color` enumerazione non deve essere contrassegnata con <xref:System.FlagsAttribute>.

[!code-cpp[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/CPP/ca2217-do-not-mark-enums-with-flagsattribute_1.cpp)]
[!code-csharp[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/CSharp/ca2217-do-not-mark-enums-with-flagsattribute_1.cs)]
[!code-vb[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/VisualBasic/ca2217-do-not-mark-enums-with-flagsattribute_1.vb)]

Nel codice seguente viene illustrata un' `Days`enumerazione,, che soddisfa i requisiti per essere <xref:System.FlagsAttribute>contrassegnati con:

[!code-cpp[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/CPP/ca2217-do-not-mark-enums-with-flagsattribute_2.cpp)]
[!code-csharp[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/CSharp/ca2217-do-not-mark-enums-with-flagsattribute_2.cs)]
[!code-vb[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/VisualBasic/ca2217-do-not-mark-enums-with-flagsattribute_2.vb)]

## <a name="related-rules"></a>Regole correlate

[CA1027: Contrassegnare le enumerazioni con FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Vedere anche

- <xref:System.FlagsAttribute?displayProperty=fullName>
