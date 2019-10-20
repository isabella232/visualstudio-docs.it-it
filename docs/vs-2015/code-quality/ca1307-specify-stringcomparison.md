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
ms.openlocfilehash: 111f0b85a601d931ac17bde46f7170fa81e71815
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661404"
---
# <a name="ca1307-specify-stringcomparison"></a>CA1307: Specificare StringComparison
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SpecifyStringComparison|
|CheckId|CA1307|
|Category|Microsoft. globalizzazione|
|Modifica importante|Senza interruzioni|

## <a name="cause"></a>Causa
 Un'operazione di confronto tra stringhe usa un overload del metodo che non imposta un parametro <xref:System.StringComparison>.

## <a name="rule-description"></a>Descrizione della regola
 Molte operazioni di stringa, più importanti i metodi <xref:System.String.Compare%2A> e <xref:System.String.Equals%2A>, forniscono un overload che accetta un <xref:System.StringComparison> valore di enumerazione come parametro.

 Quando esiste un overload che accetta un parametro <xref:System.StringComparison>, deve essere usato al posto di un overload che non accetta questo parametro. Impostando in modo esplicito questo parametro, il codice viene spesso reso più chiaro e facile da gestire.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, modificare i metodi di confronto tra stringhe in overload che accettano l'enumerazione <xref:System.StringComparison> come parametro. Ad esempio: sostituire `String.Compare(str1, str2)` con `String.Compare(str1, str2, StringComparison.Ordinal)`.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola quando la libreria o l'applicazione è destinata a un gruppo di destinatari locale limitato e pertanto non verrà localizzata.

## <a name="see-also"></a>Vedere anche
 [Avvisi di globalizzazione](../code-quality/globalization-warnings.md) [CA1309: Use StringComparison ordinale](../code-quality/ca1309-use-ordinal-stringcomparison.md)
