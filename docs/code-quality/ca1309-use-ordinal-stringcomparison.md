---
title: 'CA1309: Usare StringComparison ordinale'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- UseOrdinalStringComparison
- CA1309
helpviewer_keywords:
- UseOrdinalStringComparison
- CA1309
ms.assetid: 19be0854-cb6e-4efd-a4c8-a5c1fc6f7a71
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b00accdbdb08e4267bbca2b7e5fab8002f539f1d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62546479"
---
# <a name="ca1309-use-ordinal-stringcomparison"></a>CA1309: Usare StringComparison ordinale

|||
|-|-|
|TypeName|UseOrdinalStringComparison|
|CheckId|CA1309|
|Category|Microsoft.Globalization|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa

Un'operazione di confronto di stringhe linguistico non viene impostata la <xref:System.StringComparison> parametro a **ordinale** o **OrdinalIgnoreCase**.

## <a name="rule-description"></a>Descrizione della regola
 Molte operazioni stringa, soprattutto il <xref:System.String.Compare%2A?displayProperty=fullName> e <xref:System.String.Equals%2A?displayProperty=fullName> metodi forniscono ora un overload che accetta un <xref:System.StringComparison?displayProperty=fullName> come parametro un valore di enumerazione.

 Quando si specifica **StringComparison. Ordinal** oppure **StringComparison. OrdinalIgnoreCase**, nel confronto tra stringhe non è linguistico. Le funzionalità specifiche del linguaggio naturale, ovvero vengono ignorate quando vengono prese decisioni di confronto. Ignorando le funzionalità del linguaggio naturale, significa che le decisioni sono basate su confronti di byte semplici e non su maiuscole e minuscole o tabelle di equivalenza parametrizzate dalle impostazioni cultura. Di conseguenza, impostando in modo esplicito il parametro sul **StringComparison. Ordinal** oppure **StringComparison. OrdinalIgnoreCase**, codice spesso snellire, aumenta la correttezza e diventa più affidabile.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, modificare il metodo di confronto di stringhe a un overload che accetta il <xref:System.StringComparison?displayProperty=fullName> enumerazione come parametro, quindi specificare il **ordinale** oppure **OrdinalIgnoreCase**. Ad esempio, modificare `String.Compare(str1, str2)` in `String.Compare(str1, str2, StringComparison.Ordinal)`.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 È possibile eliminare un avviso da questa regola quando la libreria o l'applicazione è destinata a un numero limitato di utenti locale o quando la semantica delle impostazioni cultura correnti deve essere utilizzata.

## <a name="see-also"></a>Vedere anche

- [Avvisi di globalizzazione](../code-quality/globalization-warnings.md)
- [CA1307: Specificare StringComparison](../code-quality/ca1307-specify-stringcomparison.md)