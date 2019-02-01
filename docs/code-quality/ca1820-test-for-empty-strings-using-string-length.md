---
title: 'CA1820: Testare le stringhe vuote usando la lunghezza di stringa'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- TestForEmptyStringsUsingStringLength
- CA1820
helpviewer_keywords:
- TestForEmptyStringsUsingStringLength
- CA1820
ms.assetid: da1e70c8-b1dc-46b9-8b8f-4e6e48339681
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e290fa29f27638c327565825872e0de96bbd8bb7
ms.sourcegitcommit: e3d96b20381916bf4772f9db52b22275763bb603
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/31/2019
ms.locfileid: "55483890"
---
# <a name="ca1820-test-for-empty-strings-using-string-length"></a>CA1820: Testare le stringhe vuote usando la lunghezza di stringa

|||
|-|-|
|TypeName|TestForEmptyStringsUsingStringLength|
|CheckId|CA1820|
|Category|Microsoft.Performance|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa

Una stringa viene confrontato con una stringa vuota usando <xref:System.Object.Equals%2A?displayProperty=nameWithType>.

## <a name="rule-description"></a>Descrizione della regola

Il confronto di stringhe usando il <xref:System.String.Length%2A?displayProperty=nameWithType> proprietà o il <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType> metodo è più veloce rispetto all'uso di <xref:System.Object.Equals%2A>. Infatti <xref:System.Object.Equals%2A> esegue le istruzioni MSIL significativamente maggiore rispetto al metodo <xref:System.String.IsNullOrEmpty%2A> o il numero di istruzioni eseguite per recuperare il <xref:System.String.Length%2A> proprietà valore e confrontarla con zero.

Per le stringhe null, <xref:System.Object.Equals%2A> e <xref:System.String.Length%2A> = = 0 si comportano in modo diverso. Se si prova a ottenere il valore della <xref:System.String.Length%2A> su una stringa null, common language runtime, viene generata una <xref:System.NullReferenceException?displayProperty=fullName>. Se si esegue un confronto tra una stringa null e una stringa vuota, common language runtime non viene generata un'eccezione e restituisce `false`. Verifica dei valori null non interessano in modo significativo le prestazioni relative di questi due approcci. Quando la destinazione è .NET Framework 2.0 o versione successiva, usare il <xref:System.String.IsNullOrEmpty%2A> (metodo). In caso contrario, usare il <xref:System.String.Length%2A> = = 0 confronto laddove possibile.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, impostare il confronto da utilizzare il <xref:System.String.Length%2A> proprietà ed eseguire test per la stringa null. Se la destinazione è .NET Framework 2.0 o versione successiva, usare il <xref:System.String.IsNullOrEmpty%2A> (metodo).

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

È possibile eliminare un avviso da questa regola se le prestazioni non sono un problema.

## <a name="example"></a>Esempio

L'esempio seguente illustra le diverse tecniche che consentono di cercare una stringa vuota.

[!code-csharp[FxCop.Performance.StringTest#1](../code-quality/codesnippet/CSharp/ca1820-test-for-empty-strings-using-string-length_1.cs)]