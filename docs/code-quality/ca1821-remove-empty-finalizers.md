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
ms.openlocfilehash: 16bb2786c4c7b0ca94fe60a9577e4b462d663bfc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62545713"
---
# <a name="ca1821-remove-empty-finalizers"></a>CA1821: Rimuovere i finalizzatori vuoti

|||
|-|-|
|TypeName|RemoveEmptyFinalizers|
|CheckId|CA1821|
|Category|Microsoft.Performance|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa
 Un tipo implementa un finalizzatore è vuoto, chiama solo il finalizzatore del tipo di base o chiama solo metodi emessi in modo condizionale.

## <a name="rule-description"></a>Descrizione della regola
 Quando possibile, evitare di utilizzare i finalizzatori per non sovraccaricare ulteriormente le prestazioni durante il rilevamento della durata dell'oggetto. Prima di raccogliere l'oggetto, il garbage collector eseguirà il finalizzatore. Ciò significa che due raccolte verrà richiesto di raccogliere l'oggetto. Un finalizzatore vuoto provoca questo sovraccarico senza alcun vantaggio.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Rimuovere il finalizzatore è vuoto. Se è necessario per il debug di un finalizzatore, racchiudere l'intero finalizzatore in `#if DEBUG / #endif` direttive.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 Non eliminare un messaggio da questa regola. Tentativo di eliminare la finalizzazione riduce le prestazioni e non offre alcun vantaggio.

## <a name="example"></a>Esempio
 L'esempio seguente mostra un finalizzatore vuoto che deve essere rimosso, un finalizzatore che deve essere racchiuso tra parentesi `#if DEBUG / #endif` direttive e un finalizzatore che usa il `#if DEBUG / #endif` direttive correttamente.

 [!code-csharp[FxCop.Performance.RemoveEmptyFinalizers#1](../code-quality/codesnippet/CSharp/ca1821-remove-empty-finalizers_1.cs)]