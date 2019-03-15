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
ms.openlocfilehash: 95e2a8892bb7b52122dd34afa3f300123149bb26
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/14/2019
ms.locfileid: "57871850"
---
# <a name="ca1028-enum-storage-should-be-int32"></a>CA1028: Le risorse di archiviazione dell'enumerazione devono essere Int32

|||
|-|-|
|TypeName|EnumStorageShouldBeInt32|
|CheckId|CA1028|
|Category|Microsoft.Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa

Il tipo sottostante di un'enumerazione non <xref:System.Int32?displayProperty=fullName>.

Per impostazione predefinita, questa regola cerca solo in enumerazioni pubbliche, ma si tratta [configurabile](#configurability).

## <a name="rule-description"></a>Descrizione della regola

Un'enumerazione è un tipo di valore che definisce un insieme di costanti denominate correlate. Per impostazione predefinita, il <xref:System.Int32?displayProperty=fullName> tipo di dati viene usato per archiviare il valore costante. Anche se è possibile modificare questo tipo sottostante, non è necessario o consigliabile per la maggior parte degli scenari. Non si ottiene alcun miglioramento significativo delle prestazioni utilizzando un tipo di dati inferiori a quelle <xref:System.Int32>. Se è possibile usare il tipo di dati predefinito, è necessario utilizzare uno del sistema CLS (Common Language)-conforme a tipi integrali <xref:System.Byte>, <xref:System.Int16>, <xref:System.Int32>, o <xref:System.Int64> per assicurarsi che tutti i valori dell'enumerazione possono essere rappresentati in Linguaggi di programmazione conforme a CLS.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, a meno che non esistono problemi di compatibilità o le dimensioni, usare <xref:System.Int32>. Per le situazioni in cui <xref:System.Int32> non è sufficientemente grande da contenere i valori, usare <xref:System.Int64>. Se la compatibilità con le versioni precedenti richiede un tipo di dati più piccolo, utilizzare <xref:System.Byte> o <xref:System.Int16>.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

Eliminare un avviso da questa regola solo se richiesto per problemi di compatibilità con le versioni precedenti. Nelle applicazioni, la mancata conformità con questa regola, in genere non causa problemi. Nelle librerie, in cui è richiesta l'interoperabilità di linguaggio, la mancata conformità con questa regola potrebbe influire negativamente sugli utenti.

## <a name="configurability"></a>Configurabilità

Se si esegue la regola dai [analizzatori FxCop](install-fxcop-analyzers.md) (e non tramite analisi statica del codice), è possibile configurare quali parti della codebase per l'esecuzione di questa regola, in base i criteri di accesso. Ad esempio, per specificare che la regola deve essere eseguito solo per la superficie dell'API non pubblici, aggiungere la coppia chiave-valore seguente a un file con estensione editorconfig nel progetto:

```
dotnet_code_quality.ca1028.api_surface = private, internal
```

È possibile configurare questa opzione per questa regola, per tutte le regole o per tutte le regole in questa categoria (progettazione). Per altre informazioni, vedere [analizzatori FxCop configurare](configure-fxcop-analyzers.md).

## <a name="example-of-a-violation"></a>Esempio di violazione

L'esempio seguente illustra due enumerazioni che non usano il tipo di dati sottostante consigliata.

[!code-vb[FxCop.Design.EnumIntegralType#1](../code-quality/codesnippet/VisualBasic/ca1028-enum-storage-should-be-int32_1.vb)]
[!code-csharp[FxCop.Design.EnumIntegralType#1](../code-quality/codesnippet/CSharp/ca1028-enum-storage-should-be-int32_1.cs)]

## <a name="example-of-how-to-fix"></a>Esempio di come risolvere

Nell'esempio seguente consente di correggere la violazione precedente modificando il tipo di dati sottostante per <xref:System.Int32>.

[!code-csharp[FxCop.Design.EnumIntegralTypeFixed#1](../code-quality/codesnippet/CSharp/ca1028-enum-storage-should-be-int32_2.cs)]
[!code-vb[FxCop.Design.EnumIntegralTypeFixed#1](../code-quality/codesnippet/VisualBasic/ca1028-enum-storage-should-be-int32_2.vb)]

## <a name="related-rules"></a>Regole correlate

- [CA1008: Le enumerazioni devono avere valore zero](../code-quality/ca1008-enums-should-have-zero-value.md)
- [CA1027: Contrassegnare le enumerazioni con FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)
- [CA2217: Non contrassegnare le enumerazioni con FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)
- [CA1700: Non denominare 'Reserved' i valori di enumerazione](../code-quality/ca1700-do-not-name-enum-values-reserved.md)
- [CA1712: Prefisso nei valori di enumerazione con il nome di tipo](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

## <a name="see-also"></a>Vedere anche

- <xref:System.Byte?displayProperty=fullName>
- <xref:System.Int16?displayProperty=fullName>
- <xref:System.Int32?displayProperty=fullName>
- <xref:System.Int64?displayProperty=fullName>