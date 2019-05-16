---
title: "CA2233: Evitare l'overflow delle operazioni | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- OperationsShouldNotOverflow
- CA2233
helpviewer_keywords:
- OperationsShouldNotOverflow
- CA2233
ms.assetid: 3a2b06ba-6d1b-4666-9eaf-e053ef47ffaa
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 0531a739ec00c3e6224ef5caa7b1c0bf71f0e4e4
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65697943"
---
# <a name="ca2233-operations-should-not-overflow"></a>CA2233: Evitare l'overflow delle operazioni
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OperationsShouldNotOverflow|
|CheckId|CA2233|
|Category|Microsoft.Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Un metodo esegue un'operazione aritmetica e non viene convalidato gli operandi in anticipo per evitare l'overflow.

## <a name="rule-description"></a>Descrizione della regola
 Operazioni aritmetiche non devono essere eseguite solo dopo aver convalidato gli operandi per assicurarsi che il risultato dell'operazione non è compreso nell'intervallo di valori possibili per i tipi di dati coinvolti. A seconda del contesto di esecuzione e i tipi di dati coinvolti, possa causare un overflow aritmetico in uno una <xref:System.OverflowException?displayProperty=fullName> o eliminati i bit più significativi del risultato.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, convalidare gli operandi prima di eseguire l'operazione.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola se i valori possibili degli operandi non causerà mai l'operazione aritmetica genera un overflow.

## <a name="example-of-a-violation"></a>Esempio di violazione

### <a name="description"></a>Descrizione
 Un metodo nell'esempio seguente modifica un numero intero che violano questa regola. [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] richiede la **rimuovere** opzione overflow di integer deve essere disabilitata per questa attivazione.

### <a name="code"></a>Codice
 [!code-csharp[FxCop.Usage.OperationOverflow#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflow/cs/FxCop.Usage.OperationOverflow.cs#1)]
 [!code-vb[FxCop.Usage.OperationOverflow#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflow/vb/FxCop.Usage.OperationOverflow.vb#1)]

### <a name="comments"></a>Commenti
 Se il metodo in questo esempio viene passato <xref:System.Int32.MinValue?displayProperty=fullName>, l'operazione si verificherà un underflow. In questo modo il bit più significativo del risultato per essere eliminato. Il codice seguente viene illustrata questa operazione.

 [C#]

```
public static void Main()
{
    int value = int.MinValue;    // int.MinValue is -2147483648
    value = Calculator.Decrement(value);
    Console.WriteLine(value);
}
```

 [VB]

```
Public Shared Sub Main()
    Dim value = Integer.MinValue    ' Integer.MinValue is -2147483648
    value = Calculator.Decrement(value)
    Console.WriteLine(value)
End Sub
```

### <a name="output"></a>Output

```
2147483647
```

## <a name="fix-with-input-parameter-validation"></a>Risolvere con la convalida dei parametri di Input

### <a name="description"></a>Descrizione
 Nell'esempio seguente consente di correggere la violazione precedente convalidando il valore di input.

### <a name="code"></a>Codice
 [!code-csharp[FxCop.Usage.OperationOverflowFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflowFixed/cs/FxCop.Usage.OperationOverflowFixed.cs#1)]
 [!code-vb[FxCop.Usage.OperationOverflowFixed#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflowFixed/vb/FxCop.Usage.OperationOverflowFixed.vb#1)]

## <a name="fix-with-a-checked-block"></a>Risolvere con un blocco Checked

### <a name="description"></a>Descrizione
 Nell'esempio seguente consente di correggere la violazione precedente eseguendo il wrapping dell'operazione in un blocco selezionato. Se l'operazione causa un overflow, una <xref:System.OverflowException?displayProperty=fullName> verrà generata.

 Si noti che i blocchi selezionati non sono supportati [!INCLUDE[vbprvb](../includes/vbprvb-md.md)].

### <a name="code"></a>Codice
 [!code-csharp[FxCop.Usage.OperationOverflowChecked#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflowChecked/cs/FxCop.Usage.OperationOverflowChecked.cs#1)]

## <a name="turn-on-checked-arithmetic-overflowunderflow"></a>Attivare Overflow/Underflow aritmetico selezionato
 Se si attiva checked overflow/underflow aritmetico in c#, è equivalente a wrapping di ogni operazione di integer in un blocco selezionato.

 **Per attivare overflow/underflow aritmetico nel linguaggio c# selezionata**

1. Nelle **Esplora soluzioni**, fare clic sul progetto e scegliere **proprietà**.

2. Nella scheda **Compilazione** scegliere **Avanzate**.

3. Selezionare **Controlla overflow/underflow aritmetico** e fare clic su **OK**.

## <a name="see-also"></a>Vedere anche
 <xref:System.OverflowException?displayProperty=fullName> [Operatori di c#](https://msdn.microsoft.com/library/0301e31f-22ad-49af-ac3c-d5eae7f0ac43) [Checked e Unchecked](https://msdn.microsoft.com/library/a84bc877-2c7f-4396-8735-1ce97c42f35e)
