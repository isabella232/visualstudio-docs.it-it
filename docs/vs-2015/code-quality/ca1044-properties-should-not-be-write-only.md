---
title: 'CA1044: Le proprietà non devono essere in sola scrittura | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- PropertiesShouldNotBeWriteOnly
- CA1044
helpviewer_keywords:
- CA1044
- PropertiesShouldNotBeWriteOnly
ms.assetid: 8386bf3a-b161-4841-bf8b-92591595aea9
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 732af1dcdeff669723f717dabe035a38640a8bf3
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2018
ms.locfileid: "47590346"
---
# <a name="ca1044-properties-should-not-be-write-only"></a>CA1044: Le proprietà non devono essere in sola scrittura
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [CA1044: le proprietà non devono essere in sola scrittura](https://docs.microsoft.com/visualstudio/code-quality/ca1044-properties-should-not-be-write-only).

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

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È consigliabile che non viene eliminato un messaggio di avviso da questa regola.

## <a name="example"></a>Esempio
 Nell'esempio seguente, `BadClassWithWriteOnlyProperty` è un tipo con una proprietà di sola scrittura. `GoodClassWithReadWriteProperty` contiene il codice corretto.

 [!code-csharp[FxCop.Design.PropertiesNotWriteOnly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.PropertiesNotWriteOnly/cs/FxCop.Design.PropertiesNotWriteOnly.cs#1)]
 [!code-vb[FxCop.Design.PropertiesNotWriteOnly#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.PropertiesNotWriteOnly/vb/PropertiesNotWriteOnly.vb#1)]



