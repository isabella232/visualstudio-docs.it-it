---
title: 'CA2004: Rimuovere le chiamate a GC.KeepAlive'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fa59c6797d81202637f44799327e6b2802d822eb
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
ms.locfileid: "31917189"
---
# <a name="ca2004-remove-calls-to-gckeepalive"></a>CA2004: Rimuovere le chiamate a GC.KeepAlive
|||
|-|-|
|TypeName|RemoveCallsToGCKeepAlive|
|CheckId|CA2004|
|Category|Microsoft.Reliability|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa
 Utilizzo di classi `SafeHandle` ma contengono ancora chiamate a `GC.KeepAlive`.

## <a name="rule-description"></a>Descrizione della regola
 Se si desidera convertire in `SafeHandle` utilizzo, rimuovere tutte le chiamate a `GC.KeepAlive` (oggetto). In questo caso, le classi non necessario chiamare `GC.KeepAlive`, supponendo che non dispone di un finalizzatore, ma si basano su `SafeHandle` per completare l'handle del sistema operativo per loro.  Anche se il costo di lasciare in una chiamata a `GC.KeepAlive` potrebbe essere trascurabile in termini di prestazioni, la percezione che una chiamata a `GC.KeepAlive` sia necessaria o sufficiente per risolvere un problema che potrebbe non esistere più difficile il codice di durata Gestisci.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Rimuovere le chiamate a `GC.KeepAlive`.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare questo avviso solo se non è tecnicamente corretto convertire in `SafeHandle` utilizzo della classe.