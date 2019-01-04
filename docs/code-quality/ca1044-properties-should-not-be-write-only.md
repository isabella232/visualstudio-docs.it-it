---
title: 'CA1044: Proprietà non devono essere in sola scrittura'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- PropertiesShouldNotBeWriteOnly
- CA1044
helpviewer_keywords:
- CA1044
- PropertiesShouldNotBeWriteOnly
ms.assetid: 8386bf3a-b161-4841-bf8b-92591595aea9
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: e9d543c915cecbaa4f37a694786e80876bdf06cd
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53959092"
---
# <a name="ca1044-properties-should-not-be-write-only"></a>CA1044: Proprietà non devono essere in sola scrittura

|||
|-|-|
|TypeName|PropertiesShouldNotBeWriteOnly|
|CheckId|CA1044|
|Category|Microsoft.Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 La proprietà pubblica o protetta è una funzione di accesso set, ma non ha una funzione di accesso get.

## <a name="rule-description"></a>Descrizione della regola
 Ottenere le funzioni di accesso forniscono accesso in lettura a una proprietà e funzioni di accesso set fornisce accesso in scrittura. Sebbene la presenza di proprietà di sola lettura sia accettabile e spesso necessaria, le linee guida di progettazione proibiscono l'utilizzo di proprietà di sola scrittura. Infatti, consentire a un utente di impostare un valore e quindi impedire all'utente di visualizzare il valore non fornisce alcuna garanzia di sicurezza. Inoltre, senza accesso in lettura, lo stato degli oggetti condivisi non può essere visualizzato, il che ne limita l'utilità.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, aggiungere una funzione di accesso get della proprietà. In alternativa, se è necessario il comportamento di una proprietà di sola scrittura, è consigliabile convertire questa proprietà a un metodo.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 È consigliabile che non viene eliminato un messaggio di avviso da questa regola.

## <a name="example"></a>Esempio
 Nell'esempio seguente, `BadClassWithWriteOnlyProperty` è un tipo con una proprietà di sola scrittura. `GoodClassWithReadWriteProperty` contiene il codice corretto.

 [!code-vb[FxCop.Design.PropertiesNotWriteOnly#1](../code-quality/codesnippet/VisualBasic/ca1044-properties-should-not-be-write-only_1.vb)]
 [!code-csharp[FxCop.Design.PropertiesNotWriteOnly#1](../code-quality/codesnippet/CSharp/ca1044-properties-should-not-be-write-only_1.cs)]