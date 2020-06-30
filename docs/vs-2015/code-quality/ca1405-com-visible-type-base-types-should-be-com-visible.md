---
title: 'CA1405: i tipi di base del tipo visibile a COM devono essere visibili a COM | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1405
- ComVisibleTypeBaseTypesShouldBeComVisible
helpviewer_keywords:
- CA1405
- ComVisibleTypeBaseTypesShouldBeComVisible
ms.assetid: a762ea2f-5285-4f73-bfb9-9eb10aea4290
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 779d3ec1ed520d5d48043f90e7cb6272553012a6
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85535044"
---
# <a name="ca1405-com-visible-type-base-types-should-be-com-visible"></a>CA1405: I tipi di base del tipo visibile a COM devono essere visibili a COM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|ComVisibleTypeBaseTypesShouldBeComVisible|
|CheckId|CA1405|
|Category|Microsoft. interoperabilità|
|Modifica importante|DependsOnFix|

## <a name="cause"></a>Causa
 Un tipo visibile di Component Object Model (COM) deriva da un tipo non visibile a COM.

## <a name="rule-description"></a>Descrizione della regola
 Quando un tipo visibile a COM aggiunge membri in una nuova versione, deve attenersi alle linee guida rigorose per evitare di suddividere i client COM che si associano alla versione corrente. Un tipo invisibile a COM presume che non debba seguire queste regole di controllo delle versioni COM quando aggiunge nuovi membri. Tuttavia, se un tipo visibile a COM deriva dal tipo COM invisibile ed espone un'interfaccia di classe di <xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=fullName> o <xref:System.Runtime.InteropServices.ClassInterfaceType> (impostazione predefinita), tutti i membri pubblici del tipo di base (a meno che non siano contrassegnati in modo esplicito come com invisibile, che sarebbe ridondante) vengono esposti a com. Se il tipo di base aggiunge nuovi membri in una versione successiva, eventuali client COM che si associano all'interfaccia della classe del tipo derivato potrebbero interrompersi. I tipi visibili a COM dovrebbero derivare solo da tipi visibili a COM per ridurre la possibilità di suddividere i client COM.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, rendere visibili i tipi di base o il tipo derivato COM invisibile.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo che viola la regola.

 [!code-csharp[FxCop.Interoperability.ComBaseTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComBaseTypes/cs/FxCop.Interoperability.ComBaseTypes.cs#1)]
 [!code-vb[FxCop.Interoperability.ComBaseTypes#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComBaseTypes/vb/FxCop.Interoperability.ComBaseTypes.vb#1)]

## <a name="see-also"></a>Vedere anche
 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute?displayProperty=fullName>[Introduzione all'interfaccia della classe](https://msdn.microsoft.com/733c0dd2-12e5-46e6-8de1-39d5b25df024) [interoperabilità con codice non gestito](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
