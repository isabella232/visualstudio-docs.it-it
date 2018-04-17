---
title: 'CA1820: Testare le stringhe vuote utilizzando la lunghezza della stringa | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- TestForEmptyStringsUsingStringLength
- CA1820
helpviewer_keywords:
- TestForEmptyStringsUsingStringLength
- CA1820
ms.assetid: da1e70c8-b1dc-46b9-8b8f-4e6e48339681
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0b70f2579a7c5afb0baa24cf1c6ad9b33ec5a47d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="ca1820-test-for-empty-strings-using-string-length"></a>CA1820: Testare le stringhe vuote utilizzando la lunghezza di stringa
|||  
|-|-|  
|TypeName|TestForEmptyStringsUsingStringLength|  
|CheckId|CA1820|  
|Category|Microsoft.Performance|  
|Modifica importante|Non sostanziale|  
  
## <a name="cause"></a>Causa  
 Una stringa viene confrontata con la stringa vuota usando <xref:System.Object.Equals%2A?displayProperty=fullName>.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Confronto tra stringhe mediante la <xref:System.String.Length%2A?displayProperty=fullName> proprietà o <xref:System.String.IsNullOrEmpty%2A?displayProperty=fullName> metodo è notevolmente più veloce rispetto all'utilizzo di <xref:System.Object.Equals%2A>. In questo modo <xref:System.Object.Equals%2A> esegue istruzioni MSIL significativamente maggiore rispetto al metodo <xref:System.String.IsNullOrEmpty%2A> o il numero di istruzioni eseguite per recuperare il <xref:System.String.Length%2A> proprietà valore e lo confrontano con zero.  
  
 È necessario essere consapevoli che <xref:System.Object.Equals%2A> e <xref:System.String.Length%2A> = = 0 si comportano in modo diverso per le stringhe null. Se si tenta di ottenere il valore della <xref:System.String.Length%2A> su una stringa null, common language runtime, viene generata una <xref:System.NullReferenceException?displayProperty=fullName>. Se si esegue un confronto tra una stringa null e una stringa vuota, common language runtime non genera un'eccezione. il confronto restituisce `false`. Verifica dei valori null non in modo significativo le prestazioni relative di questi due approcci. Quando la destinazione [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)], utilizzare il <xref:System.String.IsNullOrEmpty%2A> metodo. In caso contrario, utilizzare il <xref:System.String.Length%2A> confronto = = quando possibile.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere una violazione di questa regola, modificare il confronto affinché venga utilizzato il <xref:System.String.Length%2A> proprietà e i test per la stringa null. Se la destinazione [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)], utilizzare il <xref:System.String.IsNullOrEmpty%2A> metodo.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 È possibile eliminare un avviso da questa regola se le prestazioni non è un problema.  
  
## <a name="example"></a>Esempio  
 L'esempio seguente illustra le diverse tecniche che consentono di cercare una stringa vuota.  
  
 [!code-csharp[FxCop.Performance.StringTest#1](../code-quality/codesnippet/CSharp/ca1820-test-for-empty-strings-using-string-length_1.cs)]