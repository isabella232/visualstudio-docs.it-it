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
ms.openlocfilehash: 2c528266c54bbb2f3f0d9420461d700a46b09bd5
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922276"
---
# <a name="ca1309-use-ordinal-stringcomparison"></a>CA1309: Usare StringComparison ordinale

|||
|-|-|
|TypeName|UseOrdinalStringComparison|
|CheckId|CA1309|
|Category|Microsoft. globalizzazione|
|Modifica importante|Senza interruzioni|

## <a name="cause"></a>Causa

Un'operazione di confronto tra stringhe non linguistiche non imposta il <xref:System.StringComparison> parametro su **ordinal** o **OrdinalIgnoreCase**.

## <a name="rule-description"></a>Descrizione della regola
Molte operazioni sulle stringhe, soprattutto i <xref:System.String.Compare%2A?displayProperty=fullName> metodi e <xref:System.String.Equals%2A?displayProperty=fullName> , forniscono ora un overload che accetta un <xref:System.StringComparison?displayProperty=fullName> valore di enumerazione come parametro.

Quando si specifica **StringComparison. Ordinal** o **StringComparison. OrdinalIgnoreCase**, il confronto tra stringhe non è linguistico. In altre parole, le funzionalità specifiche del linguaggio naturale vengono ignorate quando vengono prese decisioni di confronto. Se si ignorano le funzionalità del linguaggio naturale, le decisioni sono basate su confronti di byte semplici e non sulle tabelle di maiuscole e minuscole o di equivalenza parametrizzate dalle impostazioni cultura. Di conseguenza, impostando in modo esplicito il parametro su **StringComparison. Ordinal** o **StringComparison. OrdinalIgnoreCase**, il codice ottiene spesso una velocità, aumenta la correttezza e diventa più affidabile.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
Per correggere una violazione di questa regola, modificare il metodo di confronto tra stringhe in un overload che <xref:System.StringComparison?displayProperty=fullName> accetta l'enumerazione come parametro e specificare **ordinal** o **OrdinalIgnoreCase**. Ad esempio, modificare `String.Compare(str1, str2)` in `String.Compare(str1, str2, StringComparison.Ordinal)`.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
È possibile eliminare un avviso da questa regola quando la libreria o l'applicazione è destinata a un gruppo di destinatari locale limitato oppure quando è necessario usare la semantica delle impostazioni cultura correnti.

## <a name="see-also"></a>Vedere anche

- [Avvisi di globalizzazione](../code-quality/globalization-warnings.md)
- [CA1307: Specificare StringComparison](../code-quality/ca1307-specify-stringcomparison.md)