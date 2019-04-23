---
title: "CA2233: Evitare l'overflow delle operazioni"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- OperationsShouldNotOverflow
- CA2233
helpviewer_keywords:
- OperationsShouldNotOverflow
- CA2233
ms.assetid: 3a2b06ba-6d1b-4666-9eaf-e053ef47ffaa
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 7c07dde4c3b992db30c9fc72a0dfa01f0f13b31e
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60045537"
---
# <a name="ca2233-operations-should-not-overflow"></a>CA2233: Evitare l'overflow delle operazioni

|||
|-|-|
|TypeName|OperationsShouldNotOverflow|
|CheckId|CA2233|
|Category|Microsoft.Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa

Un metodo esegue un'operazione aritmetica e non viene convalidato gli operandi in anticipo per evitare l'overflow.

## <a name="rule-description"></a>Descrizione della regola

Non eseguire operazioni aritmetiche senza prima convalidare gli operandi per assicurarsi che il risultato dell'operazione non è compreso nell'intervallo di valori possibili per i tipi di dati coinvolti. A seconda del contesto di esecuzione e i tipi di dati coinvolti, possa causare un overflow aritmetico in uno una <xref:System.OverflowException?displayProperty=fullName> o eliminati i bit più significativi del risultato.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, convalidare gli operandi prima di eseguire l'operazione.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

È possibile eliminare un avviso da questa regola se i valori possibili degli operandi non causerà mai l'operazione aritmetica genera un overflow.

## <a name="example-of-a-violation"></a>Esempio di violazione

Un metodo nell'esempio seguente modifica un numero intero che violano questa regola. [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] richiede la **rimuovere** opzione overflow di integer deve essere disabilitata per questa attivazione.

[!code-vb[FxCop.Usage.OperationOverflow#1](../code-quality/codesnippet/VisualBasic/ca2233-operations-should-not-overflow_1.vb)]
[!code-csharp[FxCop.Usage.OperationOverflow#1](../code-quality/codesnippet/CSharp/ca2233-operations-should-not-overflow_1.cs)]

Se il metodo in questo esempio viene passato <xref:System.Int32.MinValue?displayProperty=fullName>, l'operazione si verificherà un underflow. In questo modo il bit più significativo del risultato per essere eliminato. Il codice seguente viene illustrata questa operazione.

```csharp
public static void Main()
{
    int value = int.MinValue;    // int.MinValue is -2147483648
    value = Calculator.Decrement(value);
    Console.WriteLine(value);
}
```

```vb
Public Shared Sub Main()
    Dim value = Integer.MinValue    ' Integer.MinValue is -2147483648
    value = Calculator.Decrement(value)
    Console.WriteLine(value)
End Sub
```

Output:

```text
2147483647
```

## <a name="fix-with-input-parameter-validation"></a>Risolvere con la convalida dei parametri di Input

Nell'esempio seguente consente di correggere la violazione precedente convalidando il valore di input.

[!code-csharp[FxCop.Usage.OperationOverflowFixed#1](../code-quality/codesnippet/CSharp/ca2233-operations-should-not-overflow_2.cs)]
[!code-vb[FxCop.Usage.OperationOverflowFixed#1](../code-quality/codesnippet/VisualBasic/ca2233-operations-should-not-overflow_2.vb)]

## <a name="fix-with-a-checked-block"></a>Risolvere con un blocco Checked

Nell'esempio seguente consente di correggere la violazione precedente eseguendo il wrapping dell'operazione in un blocco selezionato. Se l'operazione causa un overflow, una <xref:System.OverflowException?displayProperty=fullName> verrà generata.

I blocchi selezionati non sono supportati in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)].

[!code-csharp[FxCop.Usage.OperationOverflowChecked#1](../code-quality/codesnippet/CSharp/ca2233-operations-should-not-overflow_3.cs)]

## <a name="turn-on-checked-arithmetic-overflowunderflow"></a>Attivare Overflow/Underflow aritmetico selezionato

Se si attiva checked overflow/underflow aritmetico in c#, è equivalente a wrapping di ogni operazione di integer in un blocco selezionato.

Per attivare la verifica overflow/underflow aritmetico in c#:

1. Nelle **Esplora soluzioni**, fare clic sul progetto e scegliere **proprietà**.

2. Nella scheda **Compilazione** scegliere **Avanzate**.

3. Selezionare **Controlla overflow/underflow aritmetico** e fare clic su **OK**.

## <a name="see-also"></a>Vedere anche

- <xref:System.OverflowException?displayProperty=fullName>
- [Operatori C#](/dotnet/csharp/language-reference/operators/index)
- [Checked e Unchecked](/dotnet/csharp/language-reference/keywords/checked-and-unchecked)