---
title: 'CA1405: I tipi di base tipo visibile a COM devono essere visibili a COM | Microsoft Docs'
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
- CA1405
- ComVisibleTypeBaseTypesShouldBeComVisible
helpviewer_keywords:
- CA1405
- ComVisibleTypeBaseTypesShouldBeComVisible
ms.assetid: a762ea2f-5285-4f73-bfb9-9eb10aea4290
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 1d912466c4823357f8614f22083ab2e1d93109fe
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589114"
---
# <a name="ca1405-com-visible-type-base-types-should-be-com-visible"></a>CA1405: I tipi di base del tipo visibile a COM devono essere visibili a COM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [CA1405: i tipi di base tipo visibile a COM devono essere visibili a COM](https://docs.microsoft.com/visualstudio/code-quality/ca1405-com-visible-type-base-types-should-be-com-visible).

|||
|-|-|
|TypeName|ComVisibleTypeBaseTypesShouldBeComVisible|
|CheckId|CA1405|
|Category|Microsoft.Interoperability|
|Modifica importante|DependsOnFix|

## <a name="cause"></a>Causa
 Un tipo visibile modello COM (Component Object) deriva da un tipo che non è visibile a COM.

## <a name="rule-description"></a>Descrizione della regola
 Quando un tipo visibile a COM consente di aggiungere membri in una nuova versione, deve attenersi alle indicazioni rigorose per evitare di interrompere l'associazione alla versione corrente dei client COM. Un tipo che non è visibile a COM si presuppone che non è necessario rispettare queste regole di controllo delle versioni di COM durante l'aggiunta di nuovi membri. Tuttavia, se un visibili a COM tipo deriva dal tipo visibile a COM ed espone un'interfaccia di classe <xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=fullName> o <xref:System.Runtime.InteropServices.ClassInterfaceType> (impostazione predefinita), tutti i membri pubblici del tipo di base (a meno che non siano specificamente contrassegnati come COM invisibili, che potrebbero essere ridondanti) sono esposte a COM. Se il tipo di base consente di aggiungere nuovi membri in una versione successiva, potrebbero interrompere qualsiasi client COM che sono associati all'interfaccia di classe del tipo derivato. Tipi visibili a COM devono derivare solo da tipi visibili a COM per ridurre il rischio di interrompere i client COM.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, rendere invisibile il tipo derivato, COM o i tipi di base visibile a COM.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo che viola la regola.

 [!code-csharp[FxCop.Interoperability.ComBaseTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComBaseTypes/cs/FxCop.Interoperability.ComBaseTypes.cs#1)]
 [!code-vb[FxCop.Interoperability.ComBaseTypes#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComBaseTypes/vb/FxCop.Interoperability.ComBaseTypes.vb#1)]

## <a name="see-also"></a>Vedere anche
 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute?displayProperty=fullName> [Introduzione all'interfaccia della classe](http://msdn.microsoft.com/en-us/733c0dd2-12e5-46e6-8de1-39d5b25df024) [interoperabilità con codice non gestito](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)



