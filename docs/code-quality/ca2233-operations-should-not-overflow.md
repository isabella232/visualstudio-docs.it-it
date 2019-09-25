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
ms.openlocfilehash: b99aae681dbe7bbeece557a15d78aed0b3f07f6f
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71230826"
---
# <a name="ca2233-operations-should-not-overflow"></a>CA2233: Evitare l'overflow delle operazioni

|||
|-|-|
|TypeName|OperationsShouldNotOverflow|
|CheckId|CA2233|
|Category|Microsoft.Usage|
|Modifica|Senza interruzioni|

## <a name="cause"></a>Causa

Un metodo esegue un'operazione aritmetica e non convalida gli operandi in anticipo per evitare l'overflow.

## <a name="rule-description"></a>Descrizione della regola

Non eseguire operazioni aritmetiche senza prima convalidare gli operandi per assicurarsi che il risultato dell'operazione non sia al di fuori dell'intervallo di valori possibili per i tipi di dati necessari. A seconda del contesto di esecuzione e dei tipi di dati necessari, l'overflow aritmetico può comportare l'eliminazione di un oggetto <xref:System.OverflowException?displayProperty=fullName> o dei bit più significativi del risultato.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, convalidare gli operandi prima di eseguire l'operazione.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

È possibile eliminare un avviso da questa regola se i valori possibili degli operandi non provocheranno mai l'overflow dell'operazione aritmetica.

## <a name="example-of-a-violation"></a>Esempio di violazione

Un metodo nell'esempio seguente modifica un intero che viola questa regola. [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]per attivare questa opzione, è necessario disabilitare l'opzione **Rimuovi** intero overflow.

[!code-vb[FxCop.Usage.OperationOverflow#1](../code-quality/codesnippet/VisualBasic/ca2233-operations-should-not-overflow_1.vb)]
[!code-csharp[FxCop.Usage.OperationOverflow#1](../code-quality/codesnippet/CSharp/ca2233-operations-should-not-overflow_1.cs)]

Se viene passato <xref:System.Int32.MinValue?displayProperty=fullName>il metodo in questo esempio, l'operazione risulterebbe underflow. In questo modo il bit più significativo del risultato viene eliminato. Il codice seguente illustra come si verifica questa situazione.

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

## <a name="fix-with-input-parameter-validation"></a>Correzione con convalida dei parametri di input

Nell'esempio seguente viene corretta la violazione precedente convalidando il valore di input.

[!code-csharp[FxCop.Usage.OperationOverflowFixed#1](../code-quality/codesnippet/CSharp/ca2233-operations-should-not-overflow_2.cs)]
[!code-vb[FxCop.Usage.OperationOverflowFixed#1](../code-quality/codesnippet/VisualBasic/ca2233-operations-should-not-overflow_2.vb)]

## <a name="fix-with-a-checked-block"></a>Correzione con un blocco checked

Nell'esempio seguente viene corretta la violazione precedente eseguendo il wrapping dell'operazione in un blocco checked. Se l'operazione causa un overflow, verrà <xref:System.OverflowException?displayProperty=fullName> generata un'eccezione.

I blocchi controllati non sono supportati [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]in.

[!code-csharp[FxCop.Usage.OperationOverflowChecked#1](../code-quality/codesnippet/CSharp/ca2233-operations-should-not-overflow_3.cs)]

## <a name="turn-on-checked-arithmetic-overflowunderflow"></a>Attiva overflow/underflow aritmetico selezionato

Se si attiva l'overflow/underflow aritmetico controllato C#in, è equivalente al wrapping di ogni operazione Integer in un blocco checked.

Per attivare l'overflow/underflow aritmetico controllato C#in:

1. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul progetto e scegliere **Proprietà**.

2. Nella scheda **Compilazione** scegliere **Avanzate**.

3. Selezionare **Controlla overflow/underflow aritmetico** e fare clic su **OK**.

## <a name="see-also"></a>Vedere anche

- <xref:System.OverflowException?displayProperty=fullName>
- [Operatori C#](/dotnet/csharp/language-reference/operators/index)
- [Checked e Unchecked](/dotnet/csharp/language-reference/keywords/checked-and-unchecked)