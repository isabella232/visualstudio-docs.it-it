---
title: "CA1028: l'archivio di enum deve essere Int32 | Microsoft Docs"
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: fc1039cb547a48c4f2dd3ea869b46d4706e9c3a2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661910"
---
# <a name="ca1028-enum-storage-should-be-int32"></a>CA1028: L'archivio di enum deve essere Int32
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|EnumStorageShouldBeInt32|
|CheckId|CA1028|
|Category|Microsoft. Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Il tipo sottostante di un'enumerazione pubblica non è <xref:System.Int32?displayProperty=fullName>.

## <a name="rule-description"></a>Descrizione della regola
 Un'enumerazione è un tipo di valore che definisce un insieme di costanti denominate correlate. Per impostazione predefinita, viene usato il tipo di dati <xref:System.Int32?displayProperty=fullName> per archiviare il valore costante. Anche se è possibile modificare questo tipo sottostante, non è necessario o consigliato per la maggior parte degli scenari. Si noti che non è possibile ottenere un miglioramento significativo delle prestazioni utilizzando un tipo di dati inferiore a <xref:System.Int32>. Se non è possibile utilizzare il tipo di dati predefinito, è necessario utilizzare uno dei tipi integrali conformi a CLS (Common Language System), <xref:System.Byte>, <xref:System.Int16>, <xref:System.Int32> o <xref:System.Int64> per assicurarsi che tutti i valori dell'enumerazione possano essere rappresentati nella programmazione conforme a CLS Lingue.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, a meno che non esistano problemi di dimensione o compatibilità, usare <xref:System.Int32>. Per le situazioni in cui <xref:System.Int32> non è sufficiente per mantenere i valori, usare <xref:System.Int64>. Se la compatibilità con le versioni precedenti richiede un tipo di dati più piccolo, utilizzare <xref:System.Byte> o <xref:System.Int16>.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Eliminare un avviso da questa regola solo se i problemi di compatibilità con le versioni precedenti lo richiedono. Nelle applicazioni, la mancata conformità a questa regola in genere non provoca problemi. Nelle librerie, in cui è necessaria l'interoperabilità del linguaggio, la mancata conformità a questa regola potrebbe influire negativamente sugli utenti.

## <a name="example-of-a-violation"></a>Esempio di violazione

### <a name="description"></a>Descrizione
 Nell'esempio seguente vengono illustrate due enumerazioni che non utilizzano il tipo di dati sottostante consigliato.

### <a name="code"></a>Codice
 [!code-csharp[FxCop.Design.EnumIntegralType#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumIntegralType/cs/FxCop.Design.EnumIntegralType.cs#1)]
 [!code-vb[FxCop.Design.EnumIntegralType#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.EnumIntegralType/vb/FxCop.Design.EnumIntegralType.vb#1)]

## <a name="example-of-how-to-fix"></a>Esempio di correzione

### <a name="description"></a>Descrizione
 Nell'esempio seguente viene corretta la violazione precedente modificando il tipo di dati sottostante in <xref:System.Int32>.

### <a name="code"></a>Codice
 [!code-csharp[FxCop.Design.EnumIntegralTypeFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumIntegralTypeFixed/cs/FxCop.Design.EnumIntegralTypeFixed.cs#1)]
 [!code-vb[FxCop.Design.EnumIntegralTypeFixed#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.EnumIntegralTypeFixed/vb/FxCop.Design.EnumIntegralTypeFixed.vb#1)]

## <a name="related-rules"></a>Regole correlate
 [CA1008: Gli enum devono avere valore zero](../code-quality/ca1008-enums-should-have-zero-value.md)

 [CA1027: Contrassegnare le enumerazioni con FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217: Non contrassegnare le enumerazioni con FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

 [CA1700: Non denominare 'Reserved' i valori di enumerazione](../code-quality/ca1700-do-not-name-enum-values-reserved.md)

 [CA1712: Non usare nomi di tipo come prefisso nei valori di enumerazione](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

## <a name="see-also"></a>Vedere anche
 <xref:System.Byte?displayProperty=fullName> <xref:System.Int16?displayProperty=fullName>
 <xref:System.Int32?displayProperty=fullName>
 <xref:System.Int64?displayProperty=fullName>
