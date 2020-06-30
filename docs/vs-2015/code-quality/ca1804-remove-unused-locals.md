---
title: 'CA1804: rimuovere variabili locali non usate | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1804
- RemoveUnusedLocals
helpviewer_keywords:
- RemoveUnusedLocals
- CA1804
ms.assetid: cc332e67-6543-4813-bd8a-6f6fc75bf22a
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 4bd57d76acd0c46e39bb2c01449146715abc0666
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543884"
---
# <a name="ca1804-remove-unused-locals"></a>CA1804: Rimuovere variabili locali non usate
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|RemoveUnusedLocals|
|CheckId|CA1804|
|Category|Microsoft. performance|
|Modifica importante|Senza interruzioni|

## <a name="cause"></a>Causa
 Un metodo dichiara una variabile locale, ma non usa la variabile, tranne possibilmente come destinatario di un'istruzione di assegnazione. Per l'analisi da parte di questa regola, l'assembly testato deve essere compilato con le informazioni di debug e il file di database di programma (con estensione pdb) associato deve essere disponibile.

## <a name="rule-description"></a>Descrizione della regola
 Le variabili locali inutilizzate e le assegnazioni non necessarie comportano un aumento delle dimensioni dell'assembly e una riduzione delle prestazioni.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, rimuovere o usare la variabile locale. Si noti che il compilatore C# incluso in [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] rimuove le variabili locali non usate quando l' `optimize` opzione è abilitata.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Eliminare un avviso da questa regola se la variabile è stata emessa dal compilatore. È anche possibile eliminare un avviso da questa regola oppure disabilitare la regola se le prestazioni e la manutenzione del codice non rappresentano problemi principali.

## <a name="example"></a>Esempio
 Nell'esempio seguente vengono illustrate diverse variabili locali non utilizzate.

 [!code-csharp[FxCop.Performance.UnusedLocals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UnusedLocals/cs/FxCop.Performance.UnusedLocals.cs#1)]
 [!code-vb[FxCop.Performance.UnusedLocals#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.UnusedLocals/vb/FxCop.Performance.UnusedLocals.vb#1)]

## <a name="related-rules"></a>Regole correlate
 [CA1809: Evitare un numero eccessivo di variabili locali](../code-quality/ca1809-avoid-excessive-locals.md)

 [CA1811: Evitare il codice privato non chiamato](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1812: Evitare classi interne prive di istanze](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1801: Controllare i parametri non usati](../code-quality/ca1801-review-unused-parameters.md)
