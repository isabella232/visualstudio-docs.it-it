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
ms.openlocfilehash: 4bb79d2944bdb49c59fd53fb30e1497c57c5c516
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62779652"
---
# <a name="ca1008-enums-should-have-zero-value"></a>CA1008: Le enumerazioni devono avere valore zero

|||
|-|-|
|TypeName|EnumsShouldHaveZeroValue|
|CheckId|CA1008|
|Category|Microsoft.Design|
|Modifica importante|Non sostanziale - Quando viene richiesto di aggiungere un **None** in un'enumerazione di flag di non valore. Rilievo - quando viene richiesto di rinominare o rimuovere eventuali valori di enumerazione.|

## <a name="cause"></a>Causa

Un'enumerazione senza un applicato <xref:System.FlagsAttribute?displayProperty=fullName> non definisce un membro che ha un valore pari a zero. O, un'enumerazione con un applicato <xref:System.FlagsAttribute> definisce un membro che ha un valore pari a zero, ma non il relativo nome è 'Nessuno'. In alternativa, l'enumerazione definisce più membri con valore zero.

Per impostazione predefinita, questa regola solo esamina le enumerazioni visibile esternamente, ma si tratta [configurabile](#configurability).

## <a name="rule-description"></a>Descrizione della regola

Il valore predefinito di un'enumerazione non inizializzata, come altri tipi di valore, è zero. Un'enumerazione senza attributi flag definisce un membro con il valore pari a zero, in modo che il valore predefinito è un valore valido dell'enumerazione. Se appropriato, denominare il membro 'None'. In caso contrario, assegna zero per i membri usati più di frequente. Per impostazione predefinita, se il valore del primo membro di enumerazione non è impostato nella dichiarazione, il relativo valore è zero.

Se un'enumerazione contenente il <xref:System.FlagsAttribute> applicato definisce un membro con valore zero, il relativo nome deve essere 'None' per indicare che è stato impostato alcun valore nell'enumerazione. Utilizzando un membro con valore zero per altri scopi sono contrario all'utilizzo del <xref:System.FlagsAttribute> in quanto l'operatore AND e OR operatori bit per bit sono inutili con il membro. Ciò implica che solo un membro deve essere assegnato il valore zero. Se si verificano più membri con valore zero in un'enumerazione flags con attributi, `Enum.ToString()` restituisce risultati non corretti per i membri che non sono uguali a zero.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola per le enumerazioni senza attributi flag, definire un membro con il valore pari a 0. si tratta di una modifica non sostanziale. Per le enumerazioni flags con attributi che definiscono un membro con valore zero, nome di questo membro 'None' ed eliminare eventuali altri membri che hanno un valore pari a 0. si tratta di una modifica sostanziale.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

Non escludere un avviso da questa regola, ad eccezione delle enumerazioni flags attributi fornite in precedenza.

## <a name="configurability"></a>Configurabilità

Se si esegue la regola dai [analizzatori FxCop](install-fxcop-analyzers.md) (e non tramite analisi statica del codice), è possibile configurare quali parti della codebase per l'esecuzione di questa regola, in base i criteri di accesso. Ad esempio, per specificare che la regola deve essere eseguito solo per la superficie dell'API non pubblici, aggiungere la coppia chiave-valore seguente a un file con estensione editorconfig nel progetto:

```
dotnet_code_quality.ca1008.api_surface = private, internal
```

È possibile configurare questa opzione per questa regola, per tutte le regole o per tutte le regole in questa categoria (progettazione). Per altre informazioni, vedere [analizzatori FxCop configurare](configure-fxcop-analyzers.md).

## <a name="example"></a>Esempio

L'esempio seguente mostra due enumerazioni che soddisfano la regola e un'enumerazione, `BadTraceOptions`, che viola la regola.

[!code-cpp[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/CPP/ca1008-enums-should-have-zero-value_1.cpp)]
[!code-csharp[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/CSharp/ca1008-enums-should-have-zero-value_1.cs)]
[!code-vb[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/VisualBasic/ca1008-enums-should-have-zero-value_1.vb)]

## <a name="related-rules"></a>Regole correlate

- [CA2217: Non contrassegnare le enumerazioni con FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)
- [CA1700: Non denominare 'Reserved' i valori di enumerazione](../code-quality/ca1700-do-not-name-enum-values-reserved.md)
- [CA1712: Prefisso nei valori di enumerazione con il nome di tipo](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)
- [CA1028: Archivio di enum deve essere Int32](../code-quality/ca1028-enum-storage-should-be-int32.md)
- [CA1027: Contrassegnare le enumerazioni con FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Vedere anche

- <xref:System.Enum?displayProperty=fullName>