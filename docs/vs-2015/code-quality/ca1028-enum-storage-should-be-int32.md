---
title: 'CA1028: Archivio di enum deve essere Int32 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1028
- EnumStorageShouldBeInt32
helpviewer_keywords:
- EnumStorageShouldBeInt32
- CA1028
ms.assetid: 87160825-9f39-4142-8d7f-a31fe7ac7b84
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: e79eb7e0ed33184103cc772c13515959cf973ecc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68192803"
---
# <a name="ca1028-enum-storage-should-be-int32"></a>CA1028: Le risorse di archiviazione dell'enumerazione devono essere Int32
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|EnumStorageShouldBeInt32|
|CheckId|CA1028|
|Category|Microsoft.Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Non è il tipo sottostante di un'enumerazione pubblica <xref:System.Int32?displayProperty=fullName>.

## <a name="rule-description"></a>Descrizione della regola
 Un'enumerazione è un tipo di valore che definisce un insieme di costanti denominate correlate. Per impostazione predefinita, il <xref:System.Int32?displayProperty=fullName> tipo di dati viene usato per archiviare il valore costante. Anche se è possibile modificare questo tipo sottostante, non è necessario o consigliabile per la maggior parte degli scenari. Si noti che non si ottiene alcun miglioramento significativo delle prestazioni utilizzando un tipo di dati inferiori a quelle <xref:System.Int32>. Se è possibile usare il tipo di dati predefinito, è necessario utilizzare uno del sistema CLS (Common Language)-conforme a tipi integrali <xref:System.Byte>, <xref:System.Int16>, <xref:System.Int32>, o <xref:System.Int64> per assicurarsi che tutti i valori dell'enumerazione possono essere rappresentati in Linguaggi di programmazione conforme a CLS.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, a meno che non esistono problemi di compatibilità o le dimensioni, usare <xref:System.Int32>. Per le situazioni in cui <xref:System.Int32> non è sufficientemente grande da contenere i valori, usare <xref:System.Int64>. Se la compatibilità con le versioni precedenti richiede un tipo di dati più piccolo, utilizzare <xref:System.Byte> o <xref:System.Int16>.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Eliminare un avviso da questa regola solo se richiesto per problemi di compatibilità con le versioni precedenti. Nelle applicazioni, la mancata conformità con questa regola, in genere non causa problemi. Nelle librerie, in cui è richiesta l'interoperabilità di linguaggio, la mancata conformità con questa regola potrebbe influire negativamente sugli utenti.

## <a name="example-of-a-violation"></a>Esempio di violazione

### <a name="description"></a>Descrizione
 L'esempio seguente illustra due enumerazioni che non usano il tipo di dati sottostante consigliata.

### <a name="code"></a>Codice
 [!code-csharp[FxCop.Design.EnumIntegralType#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumIntegralType/cs/FxCop.Design.EnumIntegralType.cs#1)]
 [!code-vb[FxCop.Design.EnumIntegralType#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.EnumIntegralType/vb/FxCop.Design.EnumIntegralType.vb#1)]

## <a name="example-of-how-to-fix"></a>Esempio di procedura di correzione

### <a name="description"></a>DESCRIZIONE
 Nell'esempio seguente consente di correggere la violazione precedente modificando il tipo di dati sottostante per <xref:System.Int32>.

### <a name="code"></a>Codice
 [!code-csharp[FxCop.Design.EnumIntegralTypeFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumIntegralTypeFixed/cs/FxCop.Design.EnumIntegralTypeFixed.cs#1)]
 [!code-vb[FxCop.Design.EnumIntegralTypeFixed#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.EnumIntegralTypeFixed/vb/FxCop.Design.EnumIntegralTypeFixed.vb#1)]

## <a name="related-rules"></a>Regole correlate
 [CA1008: Le enumerazioni devono avere valore zero](../code-quality/ca1008-enums-should-have-zero-value.md)

 [CA1027: Contrassegnare le enumerazioni con FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217: Non contrassegnare le enumerazioni con FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

 [CA1700: Non denominare 'Reserved' i valori di enumerazione](../code-quality/ca1700-do-not-name-enum-values-reserved.md)

 [CA1712: Prefisso nei valori di enumerazione con il nome di tipo](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

## <a name="see-also"></a>Vedere anche
 <xref:System.Byte?displayProperty=fullName> <xref:System.Int16?displayProperty=fullName>
 <xref:System.Int32?displayProperty=fullName>
 <xref:System.Int64?displayProperty=fullName>
