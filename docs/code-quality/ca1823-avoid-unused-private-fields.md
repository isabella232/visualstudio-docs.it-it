---
title: 'CA1823: Evitare campi privati non usati'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AvoidUnusedPrivateFields
- CA1823
helpviewer_keywords:
- AvoidUnusedPrivateFields
- CA1823
ms.assetid: 614f94f6-0dc7-430f-8124-cb889a4a720f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 68d7f521927497a50779d77c4d7bdd8520ac222f
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55953711"
---
# <a name="ca1823-avoid-unused-private-fields"></a>CA1823: Evitare campi privati non usati

|||
|-|-|
|TypeName|AvoidUnusedPrivateFields|
|CheckId|CA1823|
|Category|Microsoft.Performance|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa
 Questa regola viene segnalata quando un campo privato nel codice esiste ma non viene usato da qualsiasi percorso di codice.

## <a name="rule-description"></a>Descrizione della regola
 Sono stati rilevati campi privati che non sembrano essere utilizzati all'interno dell'assembly.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, rimuovere il campo o aggiungere codice che lo usa.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 È possibile eliminare un avviso da questa regola.

## <a name="related-rules"></a>Regole correlate
 [CA1812: Evitare classi interne prive di istanze](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1801: Controllare i parametri inutilizzati](../code-quality/ca1801-review-unused-parameters.md)

 [CA1804: Rimuovere locali non utilizzati](../code-quality/ca1804-remove-unused-locals.md)

 [CA1811: Evitare il codice privato](../code-quality/ca1811-avoid-uncalled-private-code.md)