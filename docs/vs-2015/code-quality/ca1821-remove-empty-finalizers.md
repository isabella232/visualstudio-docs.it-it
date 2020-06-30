---
title: 'CA1821: rimuovere i finalizzatori vuoti | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- RemoveEmptyFinalizers
- CA1821
helpviewer_keywords:
- CA1821
ms.assetid: 3f4855a0-e4a0-46e6-923c-4c3b7074048d
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a2e704202773447e353f041df66b05cb5f648c00
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545353"
---
# <a name="ca1821-remove-empty-finalizers"></a>CA1821: Rimuovere i finalizzatori vuoti
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|RemoveEmptyFinalizers|
|CheckId|CA1821|
|Category|Microsoft. performance|
|Modifica importante|Senza interruzioni|

## <a name="cause"></a>Causa
 Un tipo implementa un finalizzatore vuoto, chiama solo il finalizzatore del tipo di base o chiama solo metodi creati in modo condizionale.

## <a name="rule-description"></a>Descrizione della regola
 Quando possibile, evitare di utilizzare i finalizzatori per non sovraccaricare ulteriormente le prestazioni durante il rilevamento della durata dell'oggetto. Prima di raccogliere l'oggetto, il Garbage Collector eseguirà il finalizzatore. Ciò significa che saranno necessarie due raccolte per la raccolta dell'oggetto. Un finalizzatore vuoto comporta questo sovraccarico aggiuntivo senza alcun vantaggio.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Rimuovere il finalizzatore vuoto. Se è necessario un finalizzatore per il debug, racchiudere l'intero finalizzatore nelle `#if DEBUG / #endif` direttive.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non eliminare un messaggio da questa regola. La mancata eliminazione della finalizzazione comporta una riduzione delle prestazioni e non offre alcun vantaggio.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un finalizzatore vuoto da rimuovere, un finalizzatore che deve essere racchiuso tra `#if DEBUG / #endif` direttive e un finalizzatore che utilizza correttamente le `#if DEBUG / #endif` direttive.

 [!code-csharp[FxCop.Performance.RemoveEmptyFinalizers#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.RemoveEmptyFinalizers/cs/FxCop.Performance.RemoveEmptyFinalizers.cs#1)]
