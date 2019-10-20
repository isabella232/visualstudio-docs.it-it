---
title: 'CA1309: usare StringComparison ordinale | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseOrdinalStringComparison
- CA1309
helpviewer_keywords:
- UseOrdinalStringComparison
- CA1309
ms.assetid: 19be0854-cb6e-4efd-a4c8-a5c1fc6f7a71
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 34054f6f444e503077c1e81da9f08ae2832d635a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661423"
---
# <a name="ca1309-use-ordinal-stringcomparison"></a>CA1309: Utilizza StringComparison ordinale
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseOrdinalStringComparison|
|CheckId|CA1309|
|Category|Microsoft. globalizzazione|
|Modifica importante|Senza interruzioni|

## <a name="cause"></a>Causa
 Un'operazione di confronto tra stringhe non linguistiche non imposta il parametro <xref:System.StringComparison> su **ordinal** o **OrdinalIgnoreCase**.

## <a name="rule-description"></a>Descrizione della regola
 Molte operazioni di stringa, più importanti i metodi <xref:System.String.Compare%2A?displayProperty=fullName> e <xref:System.String.Equals%2A?displayProperty=fullName>, forniscono ora un overload che accetta un <xref:System.StringComparison?displayProperty=fullName> valore di enumerazione come parametro.

 Quando si specifica **StringComparison. Ordinal** o **StringComparison. OrdinalIgnoreCase**, il confronto tra stringhe sarà di tipo non linguistico. In altre parole, le funzionalità specifiche del linguaggio naturale vengono ignorate quando vengono prese decisioni di confronto. Ciò significa che le decisioni sono basate su semplici confronti di byte e ignorano le tabelle di maiuscole e minuscole parametrizzate in base alle impostazioni cultura. Di conseguenza, impostando in modo esplicito il parametro su **StringComparison. Ordinal** o **StringComparison. OrdinalIgnoreCase**, il codice ottiene spesso una velocità, aumenta la correttezza e diventa più affidabile.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, modificare il metodo di confronto tra stringhe in un overload che accetta l'enumerazione <xref:System.StringComparison?displayProperty=fullName> come parametro e specificare **ordinal** o **OrdinalIgnoreCase**. Ad esempio, modificare `String.Compare(str1, str2)` in `String.Compare(str1, str2, StringComparison.Ordinal)`.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola quando la libreria o l'applicazione è destinata a un gruppo di destinatari locale limitato o quando è necessario usare la semantica delle impostazioni cultura correnti.

## <a name="see-also"></a>Vedere anche
 [Avvisi di globalizzazione](../code-quality/globalization-warnings.md) [Ca1307: specificare StringComparison](../code-quality/ca1307-specify-stringcomparison.md)
