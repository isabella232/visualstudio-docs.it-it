---
title: 'CA1804: Rimuovere variabili locali non usate'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1804
- RemoveUnusedLocals
helpviewer_keywords:
- RemoveUnusedLocals
- CA1804
ms.assetid: cc332e67-6543-4813-bd8a-6f6fc75bf22a
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 0a83d0afffc50c7697fad98c4dc49e31770d63d4
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233745"
---
# <a name="ca1804-remove-unused-locals"></a>CA1804: Rimuovere variabili locali non usate

|||
|-|-|
|TypeName|RemoveUnusedLocals|
|CheckId|CA1804|
|Category|Microsoft.Performance|
|Modifica|Senza interruzioni|

## <a name="cause"></a>Causa
Un metodo dichiara una variabile locale, ma non usa la variabile, tranne possibilmente come destinatario di un'istruzione di assegnazione. Per l'analisi da parte di questa regola, l'assembly testato deve essere compilato con le informazioni di debug e il file di database di programma (con estensione pdb) associato deve essere disponibile.

## <a name="rule-description"></a>Descrizione della regola
Le variabili locali inutilizzate e le assegnazioni non necessarie comportano un aumento delle dimensioni dell'assembly e una riduzione delle prestazioni.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, rimuovere o usare la variabile locale.

> [!NOTE]
> Il C# compilatore rimuove le variabili locali inutilizzate `optimize` quando l'opzione è abilitata.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
Eliminare un avviso da questa regola se la variabile è stata emessa dal compilatore. È anche possibile eliminare un avviso da questa regola oppure disabilitare la regola se le prestazioni e la manutenzione del codice non rappresentano problemi principali.

## <a name="example"></a>Esempio
Nell'esempio seguente vengono illustrate diverse variabili locali non utilizzate.

[!code-vb[FxCop.Performance.UnusedLocals#1](../code-quality/codesnippet/VisualBasic/ca1804-remove-unused-locals_1.vb)]
[!code-csharp[FxCop.Performance.UnusedLocals#1](../code-quality/codesnippet/CSharp/ca1804-remove-unused-locals_1.cs)]

## <a name="related-rules"></a>Regole correlate
[CA1809 Evitare un numero eccessivo di variabili locali](../code-quality/ca1809-avoid-excessive-locals.md)

[CA1811: Evitare il codice privato non chiamato](../code-quality/ca1811-avoid-uncalled-private-code.md)

[CA1812 Evitare classi interne prive di istanze](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

[CA1801 Verifica parametri inutilizzati](../code-quality/ca1801-review-unused-parameters.md)