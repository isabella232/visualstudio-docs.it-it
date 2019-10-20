---
title: 'CA2004: rimuovere le chiamate a GC. KeepAlive | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
helpviewer_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
ms.assetid: bc543b5b-23eb-4b45-abc2-9325cd254ac2
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e34a8e7d4860a599155554410e13df5a6eb3bfe1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672486"
---
# <a name="ca2004-remove-calls-to-gckeepalive"></a>CA2004: Rimuovere le chiamate a GC.KeepAlive
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|RemoveCallsToGCKeepAlive|
|CheckId|CA2004|
|Category|Microsoft. affidabilità|
|Modifica importante|Senza interruzioni|

## <a name="cause"></a>Causa
 Le classi usano `SafeHandle`, ma contengono ancora chiamate a `GC.KeepAlive`.

## <a name="rule-description"></a>Descrizione della regola
 Se si esegue la conversione nell'utilizzo `SafeHandle`, rimuovere tutte le chiamate a `GC.KeepAlive` (oggetto). In questo caso, le classi non devono chiamare `GC.KeepAlive`, supponendo che non dispongano di un finalizzatore, ma si basano su `SafeHandle` per completare l'handle del sistema operativo.  Sebbene il costo di una chiamata a `GC.KeepAlive` possa essere trascurabile come misurato dalle prestazioni, la percezione che una chiamata a `GC.KeepAlive` sia necessaria o sufficiente per risolvere un problema di durata che potrebbe non esistere rende più difficile la gestione del codice.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Rimuovere le chiamate a `GC.KeepAlive`.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare questo avviso solo se non è tecnicamente corretto per la conversione nell'utilizzo `SafeHandle` nella classe.
