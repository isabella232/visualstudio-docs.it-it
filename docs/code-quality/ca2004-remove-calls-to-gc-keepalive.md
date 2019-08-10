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
ms.openlocfilehash: a716da8eb0fb1b741c302ed32408e63a4933567b
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921142"
---
# <a name="ca2004-remove-calls-to-gckeepalive"></a>CA2004: Rimuovere le chiamate a GC.KeepAlive

|||
|-|-|
|TypeName|RemoveCallsToGCKeepAlive|
|CheckId|CA2004|
|Category|Microsoft.Reliability|
|Modifica importante|Senza interruzioni|

## <a name="cause"></a>Causa
Le classi `SafeHandle` usano, ma contengono ancora `GC.KeepAlive`chiamate a.

## <a name="rule-description"></a>Descrizione della regola
Se si esegue la conversione `SafeHandle` in utilizzo, rimuovere tutte le `GC.KeepAlive` chiamate a (oggetto). In questo caso, le classi non devono chiamare `GC.KeepAlive`, supponendo che non dispongano di un finalizzatore, ma si basano su `SafeHandle` per completare l'handle del sistema operativo.  Sebbene il costo dell'uscita in una chiamata a `GC.KeepAlive` possa essere trascurabile in base alle prestazioni, la percezione che una chiamata `GC.KeepAlive` a sia necessaria o sufficiente per risolvere un problema di durata che potrebbe non esistere più rende più difficile il codice mantenere.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
Rimuovere le chiamate `GC.KeepAlive`a.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
È possibile eliminare questo avviso solo se non è tecnicamente corretto per la conversione a `SafeHandle` utilizzo nella classe.