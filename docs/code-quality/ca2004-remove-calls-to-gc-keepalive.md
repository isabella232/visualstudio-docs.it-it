---
title: 'CA2004: Rimuovere le chiamate a GC.KeepAlive'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
helpviewer_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
ms.assetid: bc543b5b-23eb-4b45-abc2-9325cd254ac2
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c495357b837c4ae10d4dfe1e25237d6caaefcc4c
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233110"
---
# <a name="ca2004-remove-calls-to-gckeepalive"></a>CA2004: Rimuovere le chiamate a GC.KeepAlive

|||
|-|-|
|TypeName|RemoveCallsToGCKeepAlive|
|CheckId|CA2004|
|Category|Microsoft.Reliability|
|Modifica|Senza interruzioni|

## <a name="cause"></a>Causa
Le classi `SafeHandle` usano, ma contengono ancora `GC.KeepAlive`chiamate a.

## <a name="rule-description"></a>Descrizione della regola
Se si esegue la conversione `SafeHandle` in utilizzo, rimuovere tutte le `GC.KeepAlive` chiamate a (oggetto). In questo caso, le classi non devono chiamare `GC.KeepAlive`, supponendo che non dispongano di un finalizzatore, ma si basano su `SafeHandle` per completare l'handle del sistema operativo.  Sebbene il costo dell'uscita in una chiamata a `GC.KeepAlive` possa essere trascurabile in base alle prestazioni, la percezione che una chiamata `GC.KeepAlive` a sia necessaria o sufficiente per risolvere un problema di durata che potrebbe non esistere più rende più difficile il codice mantenere.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
Rimuovere le chiamate `GC.KeepAlive`a.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
È possibile eliminare questo avviso solo se non è tecnicamente corretto per la conversione a `SafeHandle` utilizzo nella classe.