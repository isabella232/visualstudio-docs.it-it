---
title: "CA1013: Uguale a operatore di Overload all'overload degli operatori addizione e sottrazione | Microsoft Docs"
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 277f0c880ba9a3043744cf1c558ea8487062bd12
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49922000"
---
# <a name="ca1013-overload-operator-equals-on-overloading-add-and-subtract"></a>CA1013: Eseguire l'overload dell'operatore "uguale a" all'overload degli operatori di addizione e sottrazione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OverloadOperatorEqualsOnOverloadingAddAndSubtract|
|CheckId|CA1013|
|Category|Microsoft.Design|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa
 Un membro pubblico o protetto implementa gli operatori di addizione o sottrazione senza implementare l'operatore di uguaglianza.

## <a name="rule-description"></a>Descrizione della regola
 Quando le istanze di un tipo possono essere combinate usando operazioni quali l'addizione e sottrazione, è quasi sempre necessario definire l'uguaglianza per restituire `true` per due istanze che presentano gli stessi valori che lo costituiscono.

 È possibile usare l'operatore di uguaglianza predefinito in un'implementazione di overload dell'operatore di uguaglianza. Questa operazione causerà un overflow dello stack. Per implementare l'operatore di uguaglianza, usare il metodo di Object. Equals nell'implementazione. Vedere l'esempio seguente.

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
 Per correggere una violazione di questa regola, implementare l'operatore di uguaglianza, in modo che sia matematicamente coerenza con gli operatori di addizione e sottrazione.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola quando l'implementazione predefinita dell'operatore di uguaglianza fornisce il comportamento corretto per il tipo.

## <a name="example"></a>Esempio
 L'esempio seguente definisce un tipo (`BadAddableType`) che violano questa regola. Questo tipo deve implementare l'operatore di uguaglianza affinché due istanze in cui gli stessi valori di campo di test `true` per verificarne l'uguaglianza. Il tipo `GoodAddableType` Mostra l'implementazione corretta. Si noti che questo tipo implementa l'operatore di disuguaglianza anche che esegue l'override <xref:System.Object.Equals%2A> per soddisfare le altre regole. Un'implementazione completa è necessario implementare anche <xref:System.Object.GetHashCode%2A>.

 [!code-csharp[FxCop.Design.AddAndSubtract#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AddAndSubtract/cs/FxCop.Design.AddAndSubtract.cs#1)]

## <a name="example"></a>Esempio
 Nell'esempio seguente testa l'uguaglianza con istanze dei tipi definiti in precedenza in questo argomento per illustrare il comportamento predefinito e il comportamento corretto per l'operatore di uguaglianza.

 [!code-csharp[FxCop.Design.TestAddAndSubtract#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestAddAndSubtract/cs/FxCop.Design.TestAddAndSubtract.cs#1)]

 Questo esempio produce il seguente output:

 **Tipo non valido: {2,2} {2,2} sono uguali? No**
**tipo ottima: {3,3} {3,3} sono uguali? Sì**
**tipo ottima: {3,3} {3,3} sono = =?   Sì**
**tipo non valido: {2,2} {9,9} sono uguali? No**
**tipo ottima: {3,3} {9,9} sono = =?   No**
## <a name="see-also"></a>Vedere anche
 [Operatori di uguaglianza](http://msdn.microsoft.com/library/bc496a91-fefb-4ce0-ab4c-61f09964119a)



