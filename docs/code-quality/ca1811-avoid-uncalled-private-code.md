---
title: 'CA1811: Evitare il codice privato non chiamato'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidUncalledPrivateCode
- CA1811
helpviewer_keywords:
- CA1811
- AvoidUncalledPrivateCode
ms.assetid: aadbba74-7821-475f-8980-34d17c0a0a8b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f37ef9cdc76b86d3ad3c18489f63fb5c340aa6a7
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="ca1811-avoid-uncalled-private-code"></a>CA1811: Evitare il codice privato non chiamato
|||
|-|-|
|TypeName|AvoidUncalledPrivateCode|
|CheckId|CA1811|
|Category|Microsoft.Performance|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa
 Membro privato o interno (a livello di assembly) non presenta chiamanti nell'assembly, non viene richiamato da common language runtime e non viene richiamato da un delegato. I membri seguenti non sono controllati da questa regola:

-   Membri di interfaccia esplicita.

-   Costruttori statici.

-   Costruttori di serializzazione.

-   I metodi contrassegnati con <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> o <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName>.

-   Membri che corrispondono alle sostituzioni.

## <a name="rule-description"></a>Descrizione della regola
 Questa regola può segnalare falsi positivi se si verificano i punti di ingresso che non sono attualmente identificate dalla logica della regola. Inoltre, un compilatore può creare codice non chiamabile in un assembly.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, rimuovere il codice non chiamabile o aggiungere codice che lo chiama.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola.

## <a name="related-rules"></a>Regole correlate
 [CA1812: Evitare classi interne prive di istanze](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1801: Rivedere i parametri non usati](../code-quality/ca1801-review-unused-parameters.md)

 [CA1804: Rimuovere locali non usati](../code-quality/ca1804-remove-unused-locals.md)