---
title: 'CA1309: Utilizza StringComparison ordinale | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- UseOrdinalStringComparison
- CA1309
helpviewer_keywords:
- UseOrdinalStringComparison
- CA1309
ms.assetid: 19be0854-cb6e-4efd-a4c8-a5c1fc6f7a71
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 0666b5db2e72c1adcbee3cb5a601b2eb3bf42b46
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589731"
---
# <a name="ca1309-use-ordinal-stringcomparison"></a>CA1309: Utilizza StringComparison ordinale
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [CA1309: utilizza StringComparison ordinale](https://docs.microsoft.com/visualstudio/code-quality/ca1309-use-ordinal-stringcomparison).

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

 Quando si specifica **StringComparison. Ordinal** oppure **StringComparison. OrdinalIgnoreCase**, nel confronto tra stringhe verrà tipo. Le funzionalità specifiche del linguaggio naturale, ovvero vengono ignorate quando vengono prese decisioni di confronto. Ciò significa prendere le decisioni sono basate su confronti di byte semplici e ignorare le tabelle di maiuscole e minuscole o l'equivalenza parametrizzate dalle impostazioni cultura. Di conseguenza, impostando in modo esplicito il parametro sul **StringComparison. Ordinal** oppure **StringComparison. OrdinalIgnoreCase**, codice spesso snellire, aumenta la correttezza e diventa più affidabile.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, modificare il metodo di confronto di stringhe a un overload che accetta il <xref:System.StringComparison?displayProperty=fullName> enumerazione come parametro, quindi specificare il **ordinale** oppure **OrdinalIgnoreCase**. Ad esempio, modificare `String.Compare(str1, str2)` in `String.Compare(str1, str2, StringComparison.Ordinal)`.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola quando la libreria o l'applicazione è progettata per un numero limitato di utenti locale o quando la semantica delle impostazioni cultura correnti deve essere utilizzata.

## <a name="see-also"></a>Vedere anche
 [Avvisi di globalizzazione](../code-quality/globalization-warnings.md) [CA1307: specificare StringComparison](../code-quality/ca1307-specify-stringcomparison.md)



