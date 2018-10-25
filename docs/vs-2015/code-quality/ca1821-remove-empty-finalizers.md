---
title: 'CA1821: Rimuovere i finalizzatori vuoti | Microsoft Docs'
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
- RemoveEmptyFinalizers
- CA1821
helpviewer_keywords:
- CA1821
ms.assetid: 3f4855a0-e4a0-46e6-923c-4c3b7074048d
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 0ea2ca64009071538848c71f5bf9a825250cb82e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49900085"
---
# <a name="ca1821-remove-empty-finalizers"></a>CA1821: Rimuovere i finalizzatori vuoti
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non eliminare un messaggio da questa regola. Tentativo di eliminare la finalizzazione riduce le prestazioni e non offre alcun vantaggio.

## <a name="example"></a>Esempio
 L'esempio seguente mostra un finalizzatore vuoto che deve essere rimosso, un finalizzatore che deve essere racchiuso tra parentesi `#if DEBUG / #endif` direttive e un finalizzatore che usa il `#if DEBUG / #endif` direttive correttamente.

 [!code-csharp[FxCop.Performance.RemoveEmptyFinalizers#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.RemoveEmptyFinalizers/cs/FxCop.Performance.RemoveEmptyFinalizers.cs#1)]



