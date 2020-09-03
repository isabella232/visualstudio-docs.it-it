---
title: 'CA2233: le operazioni non devono essere overflow | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: eff09fb8f4423560c4681c94507d909f5864c69e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545236"
---
# <a name="ca2233-operations-should-not-overflow"></a>CA2233: Evitare l'overflow delle operazioni
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|OperationsShouldNotOverflow|
|CheckId|CA2233|
|Category|Microsoft. Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Un metodo esegue un'operazione aritmetica e non convalida gli operandi in anticipo per evitare l'overflow.

## <a name="rule-description"></a>Descrizione della regola
 Le operazioni aritmetiche non devono essere eseguite senza prima convalidare gli operandi per assicurarsi che il risultato dell'operazione non sia compreso nell'intervallo dei valori possibili per i tipi di dati implicati. A seconda del contesto di esecuzione e dei tipi di dati necessari, l'overflow aritmetico può comportare l' <xref:System.OverflowException?displayProperty=fullName> eliminazione di un oggetto o dei bit più significativi del risultato.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, convalidare gli operandi prima di eseguire l'operazione.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola se i valori possibili degli operandi non provocheranno mai l'overflow dell'operazione aritmetica.

## <a name="example-of-a-violation"></a>Esempio di violazione

### <a name="description"></a>Descrizione
 Un metodo nell'esempio seguente modifica un intero che viola questa regola. [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] per attivare questa opzione, è necessario disabilitare l'opzione **Rimuovi** intero overflow.

### <a name="code"></a>Codice
 [!code-csharp[FxCop.Usage.OperationOverflow#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflow/cs/FxCop.Usage.OperationOverflow.cs#1)]
 [!code-vb[FxCop.Usage.OperationOverflow#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflow/vb/FxCop.Usage.OperationOverflow.vb#1)]

### <a name="comments"></a>Commenti
 Se viene passato il metodo in questo esempio <xref:System.Int32.MinValue?displayProperty=fullName> , l'operazione risulterebbe underflow. In questo modo il bit più significativo del risultato viene eliminato. Il codice seguente illustra come si verifica questa situazione.

 [C#]

```
public static void Main()
{
    int value = int.MinValue;    // int.MinValue is -2147483648
    value = Calculator.Decrement(value);
    Console.WriteLine(value);
}
```

 VB

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

## <a name="fix-with-input-parameter-validation"></a>Correzione con convalida dei parametri di input

### <a name="description"></a>Descrizione
 Nell'esempio seguente viene corretta la violazione precedente convalidando il valore di input.

### <a name="code"></a>Codice
 [!code-csharp[FxCop.Usage.OperationOverflowFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflowFixed/cs/FxCop.Usage.OperationOverflowFixed.cs#1)]
 [!code-vb[FxCop.Usage.OperationOverflowFixed#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflowFixed/vb/FxCop.Usage.OperationOverflowFixed.vb#1)]

## <a name="fix-with-a-checked-block"></a>Correzione con un blocco checked

### <a name="description"></a>Descrizione
 Nell'esempio seguente viene corretta la violazione precedente eseguendo il wrapping dell'operazione in un blocco checked. Se l'operazione causa un overflow, <xref:System.OverflowException?displayProperty=fullName> verrà generata un'eccezione.

 Si noti che i blocchi controllati non sono supportati in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] .

### <a name="code"></a>Codice
 [!code-csharp[FxCop.Usage.OperationOverflowChecked#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflowChecked/cs/FxCop.Usage.OperationOverflowChecked.cs#1)]

## <a name="turn-on-checked-arithmetic-overflowunderflow"></a>Attiva overflow/underflow aritmetico selezionato
 Se si attiva l'overflow/underflow aritmetico controllato in C#, è equivalente al wrapping di ogni operazione Integer in un blocco checked.

 **Per attivare l'overflow/underflow aritmetico controllato in C #**

1. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul progetto e scegliere **Proprietà**.

2. Nella scheda **Compilazione** scegliere **Avanzate**.

3. Selezionare **Controlla overflow/underflow aritmetico** e fare clic su **OK**.

## <a name="see-also"></a>Vedere anche
 <xref:System.OverflowException?displayProperty=fullName>[Operatori C#](https://msdn.microsoft.com/library/0301e31f-22ad-49af-ac3c-d5eae7f0ac43) [selezionati e deselezionati](https://msdn.microsoft.com/library/a84bc877-2c7f-4396-8735-1ce97c42f35e)
