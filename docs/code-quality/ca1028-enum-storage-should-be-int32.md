---
title: "CA1028: Le risorse di archiviazione dell'enumerazione devono essere Int32"
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1028
- EnumStorageShouldBeInt32
helpviewer_keywords:
- EnumStorageShouldBeInt32
- CA1028
ms.assetid: 87160825-9f39-4142-8d7f-a31fe7ac7b84
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 47a934a6e35296927eea64465ff8e7007219bec5
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236089"
---
# <a name="ca1028-enum-storage-should-be-int32"></a>CA1028: Le risorse di archiviazione dell'enumerazione devono essere Int32

|||
|-|-|
|TypeName|EnumStorageShouldBeInt32|
|CheckId|CA1028|
|Category|Microsoft.Design|
|Modifica|Interruzione|

## <a name="cause"></a>Causa

Il tipo sottostante di un'enumerazione non <xref:System.Int32?displayProperty=fullName>è.

Per impostazione predefinita, questa regola esamina solo le enumerazioni pubbliche, ma è [configurabile](#configurability).

## <a name="rule-description"></a>Descrizione della regola

Un'enumerazione è un tipo di valore che definisce un insieme di costanti denominate correlate. Per impostazione predefinita, <xref:System.Int32?displayProperty=fullName> il tipo di dati viene utilizzato per archiviare il valore costante. Anche se è possibile modificare questo tipo sottostante, non è necessario o consigliato per la maggior parte degli scenari. Non è possibile ottenere un miglioramento significativo delle prestazioni utilizzando un tipo <xref:System.Int32>di dati inferiore a. Se non è possibile utilizzare il tipo di dati predefinito, è necessario utilizzare uno dei tipi integrali conformi a CLS (Common Language System <xref:System.Byte>) <xref:System.Int16>, <xref:System.Int32>,, <xref:System.Int64> o per assicurarsi che tutti i valori dell'enumerazione possano essere rappresentati in Linguaggi di programmazione conformi a CLS.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, a meno che non esistano problemi di dimensione <xref:System.Int32>o compatibilità, usare. Per le situazioni <xref:System.Int32> in cui non è sufficiente conservare i valori, usare <xref:System.Int64>. Se la compatibilità con le versioni precedenti richiede un tipo <xref:System.Byte> di <xref:System.Int16>dati più piccolo, utilizzare o.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

Eliminare un avviso da questa regola solo se i problemi di compatibilità con le versioni precedenti lo richiedono. Nelle applicazioni, la mancata conformità a questa regola in genere non provoca problemi. Nelle librerie, in cui è necessaria l'interoperabilità del linguaggio, la mancata conformità a questa regola potrebbe influire negativamente sugli utenti.

## <a name="configurability"></a>Configurabilità

Se questa regola viene eseguita da [analizzatori FxCop](install-fxcop-analyzers.md) (e non con analisi legacy), è possibile configurare le parti della codebase su cui eseguire questa regola, in base all'accessibilità. Ad esempio, per specificare che la regola deve essere eseguita solo sulla superficie dell'API non pubblica, aggiungere la coppia chiave-valore seguente a un file con estensione EditorConfig nel progetto:

```ini
dotnet_code_quality.ca1028.api_surface = private, internal
```

È possibile configurare questa opzione solo per questa regola, per tutte le regole o per tutte le regole in questa categoria (progettazione). Per altre informazioni, vedere [configurare gli analizzatori FxCop](configure-fxcop-analyzers.md).

## <a name="example-of-a-violation"></a>Esempio di violazione

Nell'esempio seguente vengono illustrate due enumerazioni che non utilizzano il tipo di dati sottostante consigliato.

[!code-vb[FxCop.Design.EnumIntegralType#1](../code-quality/codesnippet/VisualBasic/ca1028-enum-storage-should-be-int32_1.vb)]
[!code-csharp[FxCop.Design.EnumIntegralType#1](../code-quality/codesnippet/CSharp/ca1028-enum-storage-should-be-int32_1.cs)]

## <a name="example-of-how-to-fix"></a>Esempio di correzione

Nell'esempio seguente viene corretta la violazione precedente modificando il tipo di dati <xref:System.Int32>sottostante in.

[!code-csharp[FxCop.Design.EnumIntegralTypeFixed#1](../code-quality/codesnippet/CSharp/ca1028-enum-storage-should-be-int32_2.cs)]
[!code-vb[FxCop.Design.EnumIntegralTypeFixed#1](../code-quality/codesnippet/VisualBasic/ca1028-enum-storage-should-be-int32_2.vb)]

## <a name="related-rules"></a>Regole correlate

- [CA1008 Le enumerazioni devono avere valore zero](../code-quality/ca1008-enums-should-have-zero-value.md)
- [CA1027: Contrassegnare le enumerazioni con FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)
- [CA2217 Non contrassegnare le enumerazioni con FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)
- [CA1700 Non denominare i valori enum ' Reserved '](../code-quality/ca1700-do-not-name-enum-values-reserved.md)
- [CA1712 Non anteporre i valori enum al nome del tipo](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

## <a name="see-also"></a>Vedere anche

- <xref:System.Byte?displayProperty=fullName>
- <xref:System.Int16?displayProperty=fullName>
- <xref:System.Int32?displayProperty=fullName>
- <xref:System.Int64?displayProperty=fullName>