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
ms.openlocfilehash: f567fa1d1f793395532efac5991b01c5087b638a
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55908530"
---
# <a name="ca1804-remove-unused-locals"></a>CA1804: Rimuovere variabili locali non usate

|||
|-|-|
|TypeName|RemoveUnusedLocals|
|CheckId|CA1804|
|Category|Microsoft.Performance|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa
 Un metodo dichiara una variabile locale ma non usa la variabile, ad eccezione forse come destinatario di un'istruzione di assegnazione. Per l'analisi da questa regola, l'assembly testata deve essere compilato con le informazioni di debug e il file di database (con estensione pdb) del programma associato deve essere disponibile.

## <a name="rule-description"></a>Descrizione della regola
 Le variabili locali inutilizzate e le assegnazioni non necessarie comportano un aumento delle dimensioni dell'assembly e una riduzione delle prestazioni.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, rimuovere o usare la variabile locale. Si noti che il compilatore c# che è accluso [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] rimuove le variabili locali inutilizzate quando il `optimize` opzione è abilitata.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 Eliminare un avviso da questa regola se la variabile è stata creata dal compilatore. È inoltre sicura per eliminare un avviso da questa regola, o disabilitare la regola, se le prestazioni e manutenzione del codice non sono aspetti più importanti.

## <a name="example"></a>Esempio
 Nell'esempio seguente mostra alcune variabili locali inutilizzate.

 [!code-vb[FxCop.Performance.UnusedLocals#1](../code-quality/codesnippet/VisualBasic/ca1804-remove-unused-locals_1.vb)]
 [!code-csharp[FxCop.Performance.UnusedLocals#1](../code-quality/codesnippet/CSharp/ca1804-remove-unused-locals_1.cs)]

## <a name="related-rules"></a>Regole correlate
 [CA1809: Evitare un numero eccessivo di variabili locali](../code-quality/ca1809-avoid-excessive-locals.md)

 [CA1811: Evitare il codice privato](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1812: Evitare classi interne prive di istanze](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1801: Controllare i parametri inutilizzati](../code-quality/ca1801-review-unused-parameters.md)