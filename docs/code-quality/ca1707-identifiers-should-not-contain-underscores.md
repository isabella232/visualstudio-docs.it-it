---
title: 'CA1707: Gli identificatori non devono contenere caratteri di sottolineatura'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotContainUnderscores
- CA1707
helpviewer_keywords:
- CA1707
- IdentifiersShouldNotContainUnderscores
ms.assetid: 5fb539ef-c304-4323-90c0-b14386da9774
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: adfa0ccd63d0433d367b0e7278693608bb83d685
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234276"
---
# <a name="ca1707-identifiers-should-not-contain-underscores"></a>CA1707: Gli identificatori non devono contenere caratteri di sottolineatura

|||
|-|-|
|TypeName|IdentifiersShouldNotContainUnderscores|
|CheckId|CA1707|
|Category|Microsoft.Naming|
|Modifica|Suddivisione in caso di generazione di assembly<br /><br /> Senza interruzioni: quando viene generato un parametro di tipo|

## <a name="cause"></a>Causa

Il nome di un identificatore contiene il carattere di sottolineatura (\_).

## <a name="rule-description"></a>Descrizione della regola

Per convenzione, i nomi degli identificatori non contengono il carattere\_di sottolineatura (). La regola controlla gli spazi dei nomi, i tipi, i membri e i parametri.

Le convenzioni di denominazione forniscono un aspetto comune per le librerie destinate al Common Language Runtime. In questo modo si riduce la curva di apprendimento necessaria per le nuove librerie software e si aumenta la fiducia dei clienti che la libreria è stata sviluppata da un utente esperto nello sviluppo di codice gestito.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Rimuovere tutti i caratteri di sottolineatura dal nome.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

Non escludere un avviso da questa regola.

## <a name="related-rules"></a>Regole correlate

- [CA1709 Gli identificatori devono essere configurati correttamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708 Gli identificatori devono differire più di case](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)
