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
ms.openlocfilehash: 3845826ef1c88eaa40c8cf05936080eb320bdecc
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2018
ms.locfileid: "45546811"
---
# <a name="ca2004-remove-calls-to-gckeepalive"></a>CA2004: Rimuovere le chiamate a GC.KeepAlive
|||
|-|-|
|TypeName|RemoveCallsToGCKeepAlive|
|CheckId|CA2004|
|Category|Microsoft.Reliability|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa
 Le classi di uso `SafeHandle` ma comunque contenere chiamate ad `GC.KeepAlive`.

## <a name="rule-description"></a>Descrizione della regola
 Se sta convertendo `SafeHandle` sull'utilizzo, rimuovere tutte le chiamate a `GC.KeepAlive` (oggetto). In questo caso, le classi non necessario chiamare `GC.KeepAlive`, supponendo che non è un finalizzatore ma si basano su `SafeHandle` per completare l'handle del sistema operativo per loro.  Anche se i costi di uscita in una chiamata a `GC.KeepAlive` potrebbe essere trascurabile in termini di prestazioni, la percezione che una chiamata a `GC.KeepAlive` sia necessaria o sufficiente per risolvere un problema che potrebbe non esistere più rende più difficile per il codice di durata Consente di gestire.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Rimuovere le chiamate a `GC.KeepAlive`.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 È possibile eliminare questo avviso solo se non è tecnicamente corretto da convertire in `SafeHandle` utilizzo nella classe.