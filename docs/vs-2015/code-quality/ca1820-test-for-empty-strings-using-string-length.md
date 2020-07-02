---
title: 'CA1820: testare le stringhe vuote utilizzando la lunghezza della stringa | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- TestForEmptyStringsUsingStringLength
- CA1820
helpviewer_keywords:
- TestForEmptyStringsUsingStringLength
- CA1820
ms.assetid: da1e70c8-b1dc-46b9-8b8f-4e6e48339681
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 296eb6407e3ce63b0eb28ff86c215c12ec724ce9
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545314"
---
# <a name="ca1820-test-for-empty-strings-using-string-length"></a>CA1820: Testare le stringhe vuote usando la lunghezza di stringa
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|TestForEmptyStringsUsingStringLength|
|CheckId|CA1820|
|Category|Microsoft. performance|
|Modifica importante|Senza interruzioni|

## <a name="cause"></a>Causa
 Una stringa viene confrontata con la stringa vuota utilizzando <xref:System.Object.Equals%2A?displayProperty=fullName> .

## <a name="rule-description"></a>Descrizione della regola
 Il confronto di stringhe tramite la <xref:System.String.Length%2A?displayProperty=fullName> proprietà o il <xref:System.String.IsNullOrEmpty%2A?displayProperty=fullName> metodo è notevolmente più veloce rispetto all'utilizzo di <xref:System.Object.Equals%2A> . Questo perché <xref:System.Object.Equals%2A> esegue in modo significativo più istruzioni MSIL rispetto a <xref:System.String.IsNullOrEmpty%2A> o al numero di istruzioni eseguite per recuperare il <xref:System.String.Length%2A> valore della proprietà e confrontarlo con zero.

 È necessario tenere presente che <xref:System.Object.Equals%2A> e <xref:System.String.Length%2A> = = 0 si comportano in modo diverso per le stringhe null. Se si tenta di ottenere il valore della <xref:System.String.Length%2A> Proprietà in una stringa null, il Common Language Runtime genera un'eccezione <xref:System.NullReferenceException?displayProperty=fullName> . Se si esegue un confronto tra una stringa null e una stringa vuota, il Common Language Runtime non genera un'eccezione. il confronto restituisce `false` . Il testing di null non influisce in modo significativo sulle prestazioni relative di questi due approcci. Quando la destinazione è [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] , usare il <xref:System.String.IsNullOrEmpty%2A> metodo. In caso contrario, usare il <xref:System.String.Length%2A> confronto = = laddove possibile.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, modificare il confronto per utilizzare la <xref:System.String.Length%2A> proprietà e verificare la stringa null. Se la destinazione è [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] , usare il <xref:System.String.IsNullOrEmpty%2A> metodo.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola se le prestazioni non sono un problema.

## <a name="example"></a>Esempio
 Nell'esempio seguente vengono illustrate le diverse tecniche utilizzate per cercare una stringa vuota.

 [!code-csharp[FxCop.Performance.StringTest#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.StringTest/cs/FxCop.Performance.StringTest.cs#1)]
