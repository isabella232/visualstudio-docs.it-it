---
title: 'CA1821: Rimuovere i finalizzatori vuoti'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- RemoveEmptyFinalizers
- CA1821
helpviewer_keywords:
- CA1821
ms.assetid: 3f4855a0-e4a0-46e6-923c-4c3b7074048d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9c8c4d4ca04c7a9a21cd1e80e4dc06e8d5a92c2f
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921364"
---
# <a name="ca1821-remove-empty-finalizers"></a>CA1821: Rimuovere i finalizzatori vuoti

|||
|-|-|
|TypeName|RemoveEmptyFinalizers|
|CheckId|CA1821|
|Category|Microsoft.Performance|
|Modifica importante|Senza interruzioni|

## <a name="cause"></a>Causa
Un tipo implementa un finalizzatore vuoto, chiama solo il finalizzatore del tipo di base o chiama solo metodi creati in modo condizionale.

## <a name="rule-description"></a>Descrizione della regola
Quando possibile, evitare di utilizzare i finalizzatori per non sovraccaricare ulteriormente le prestazioni durante il rilevamento della durata dell'oggetto. Prima di raccogliere l'oggetto, il Garbage Collector eseguirà il finalizzatore. Ciò significa che saranno necessarie due raccolte per la raccolta dell'oggetto. Un finalizzatore vuoto comporta questo sovraccarico aggiuntivo senza alcun vantaggio.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
Rimuovere il finalizzatore vuoto. Se è necessario un finalizzatore per il debug, racchiudere l'intero finalizzatore `#if DEBUG / #endif` nelle direttive.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
Non eliminare un messaggio da questa regola. La mancata eliminazione della finalizzazione comporta una riduzione delle prestazioni e non offre alcun vantaggio.

## <a name="example"></a>Esempio
Nell'esempio seguente viene illustrato un finalizzatore vuoto da rimuovere, un finalizzatore che deve essere racchiuso tra `#if DEBUG / #endif` direttive e un finalizzatore che utilizza correttamente le `#if DEBUG / #endif` direttive.

[!code-csharp[FxCop.Performance.RemoveEmptyFinalizers#1](../code-quality/codesnippet/CSharp/ca1821-remove-empty-finalizers_1.cs)]