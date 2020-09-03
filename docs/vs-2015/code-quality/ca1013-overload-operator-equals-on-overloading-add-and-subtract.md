---
title: "CA1013: l'operatore di overload è uguale all'overload di Add e Subtract | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- OverrideOperatorEqualsOnOverridingAddAndSubtract
- OverrideOperatorEqualsOnOverloadingAddAndSubtract
- CA1013
- OverloadOperatorEqualsOnOverloadingAddAndSubtract
helpviewer_keywords:
- OverrideOperatorEqualsOnOverloadingAddAndSubtract
- OverrideOperatorEqualsOnOverridingAddAndSubtract
- CA1013
- OverloadOperatorEqualsOnOverloadingAddAndSubtract
ms.assetid: 5bd28d68-c179-49ff-af47-5250b8b18a10
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 2304b78073b806dfc4aec9686f061d946b379ded
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545418"
---
# <a name="ca1013-overload-operator-equals-on-overloading-add-and-subtract"></a>CA1013: Eseguire l'overload dell'operatore "uguale a" all'overload degli operatori di addizione e sottrazione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|OverloadOperatorEqualsOnOverloadingAddAndSubtract|
|CheckId|CA1013|
|Category|Microsoft. Design|
|Modifica importante|Senza interruzioni|

## <a name="cause"></a>Causa
 Un membro pubblico o protetto implementa gli operatori di addizione o sottrazione senza implementare l'operatore di uguaglianza.

## <a name="rule-description"></a>Descrizione della regola
 Quando le istanze di un tipo possono essere combinate usando operazioni quali l'addizione e la sottrazione, è necessario definire quasi sempre l'uguaglianza per restituire `true` per due istanze con gli stessi valori costitutivi.

 Non è possibile usare l'operatore di uguaglianza predefinito in un'implementazione di overload dell'operatore di uguaglianza. Questa operazione provocherà un overflow dello stack. Per implementare l'operatore di uguaglianza, usare il metodo Object. Equals nell'implementazione. Vedere l'esempio seguente.

```vb
If (Object.ReferenceEquals(left, Nothing)) Then
    Return Object.ReferenceEquals(right, Nothing)
Else
    Return left.Equals(right)
End If
```

```csharp
if (Object.ReferenceEquals(left, null))
    return Object.ReferenceEquals(right, null);
return left.Equals(right);
```

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, implementare l'operatore di uguaglianza in modo che sia matematicamente coerente con gli operatori di addizione e sottrazione.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola quando l'implementazione predefinita dell'operatore di uguaglianza fornisce il comportamento corretto per il tipo.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene definito un tipo ( `BadAddableType` ) che viola questa regola. Questo tipo deve implementare l'operatore di uguaglianza per far verificare l'uguaglianza di due istanze con lo stesso valore `true` di campo. Il tipo `GoodAddableType` Mostra l'implementazione corretta. Si noti che questo tipo implementa anche l'operatore di disuguaglianza e le sostituzioni <xref:System.Object.Equals%2A> per soddisfare altre regole. Verrà inoltre implementata un'implementazione completa di <xref:System.Object.GetHashCode%2A> .

 [!code-csharp[FxCop.Design.AddAndSubtract#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AddAndSubtract/cs/FxCop.Design.AddAndSubtract.cs#1)]

## <a name="example"></a>Esempio
 Nell'esempio seguente viene verificata l'uguaglianza utilizzando istanze dei tipi definiti in precedenza in questo argomento per illustrare il comportamento predefinito e corretto per l'operatore di uguaglianza.

 [!code-csharp[FxCop.Design.TestAddAndSubtract#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestAddAndSubtract/cs/FxCop.Design.TestAddAndSubtract.cs#1)]

 Questo esempio produce il seguente output:

 **Tipo non valido: {2,2} {2,2} sono uguali? Nessun** 
 **tipo valido: {3,3} {3,3} è uguale? Sì** 
 **, tipo valido: {3,3} {3,3} è = =?   Sì** 
 **tipo non valido: {2,2} {9,9} sono uguali? Nessun** 
 **tipo valido: {3,3} {9,9} è = =?   No**
## <a name="see-also"></a>Vedere anche
 [Operatori di uguaglianza](https://msdn.microsoft.com/library/bc496a91-fefb-4ce0-ab4c-61f09964119a)
