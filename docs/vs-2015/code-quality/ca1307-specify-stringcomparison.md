---
title: 'CA1307: specificare StringComparison | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1307
- SpecifyStringComparison
helpviewer_keywords:
- CA1307
- SpecifyStringComparison
ms.assetid: 9b0d5e71-1683-4a0d-bc4a-68b2fbd8af71
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 033d8f0e22ec040ffb10821993a5a9c647ee401e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85538918"
---
# <a name="ca1307-specify-stringcomparison"></a>CA1307: Specificare StringComparison
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|SpecifyStringComparison|
|CheckId|CA1307|
|Category|Microsoft. globalizzazione|
|Modifica importante|Senza interruzioni|

## <a name="cause"></a>Causa
 Un'operazione di confronto tra stringhe usa un overload del metodo che non imposta un <xref:System.StringComparison> parametro.

## <a name="rule-description"></a>Descrizione della regola
 Molte operazioni di stringa, più importanti <xref:System.String.Compare%2A> dei <xref:System.String.Equals%2A> metodi e, forniscono un overload che accetta un <xref:System.StringComparison> valore di enumerazione come parametro.

 Ogni volta che è presente un overload che accetta un <xref:System.StringComparison> parametro, deve essere usato anziché un overload che non accetta questo parametro. Impostando in modo esplicito questo parametro, il codice viene spesso reso più chiaro e facile da gestire.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, modificare i metodi di confronto tra stringhe in overload che accettano l' <xref:System.StringComparison> enumerazione come parametro. Ad esempio: modificare `String.Compare(str1, str2)` in `String.Compare(str1, str2, StringComparison.Ordinal)` .

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola quando la libreria o l'applicazione è destinata a un gruppo di destinatari locale limitato e pertanto non verrà localizzata.

## <a name="see-also"></a>Vedere anche
 [Avvisi di globalizzazione](../code-quality/globalization-warnings.md) [CA1309: Use StringComparison ordinale](../code-quality/ca1309-use-ordinal-stringcomparison.md)
