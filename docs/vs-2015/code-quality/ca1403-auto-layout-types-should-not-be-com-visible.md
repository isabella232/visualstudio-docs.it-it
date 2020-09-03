---
title: 'CA1403: i tipi di layout automatici non devono essere visibili a COM | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AutoLayoutTypesShouldNotBeComVisible
- CA1403
helpviewer_keywords:
- CA1403
- AutoLayoutTypesShouldNotBeComVisible
ms.assetid: a7007714-f9b4-4730-94e0-67d3dc68991f
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1752efb5be1828f62703e1fe1a1130b37ff80503
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85534927"
---
# <a name="ca1403-auto-layout-types-should-not-be-com-visible"></a>CA1403: I tipi layout automatici non devono essere visibili a COM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|AutoLayoutTypesShouldNotBeComVisible|
|CheckId|CA1403|
|Category|Microsoft. interoperabilità|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un tipo di valore visibile Component Object Model (COM) è contrassegnato con l' <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=fullName> attributo impostato su <xref:System.Runtime.InteropServices.LayoutKind?displayProperty=fullName> .

## <a name="rule-description"></a>Descrizione della regola
 <xref:System.Runtime.InteropServices.LayoutKind> i tipi di layout vengono gestiti dal Common Language Runtime. Il layout di questi tipi può variare tra le versioni del .NET Framework, in modo da interrompere i client COM che prevedono un layout specifico. Si noti che se l' <xref:System.Runtime.InteropServices.StructLayoutAttribute> attributo non è specificato, i [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] compilatori C#, e C++ specificano il <xref:System.Runtime.InteropServices.LayoutKind> layout per i tipi di valore.

 A meno che non sia contrassegnato diversamente, tutti i tipi non generici pubblici sono visibili a COM; tutti i tipi non pubblici e generici sono invisibili a COM. Tuttavia, per ridurre i falsi positivi, questa regola richiede che la visibilità COM del tipo venga dichiarata in modo esplicito; l'assembly contenitore deve essere contrassegnato con <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> impostato su `false` e il tipo deve essere contrassegnato con <xref:System.Runtime.InteropServices.ComVisibleAttribute> impostato su `true` .

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, modificare il valore dell' <xref:System.Runtime.InteropServices.StructLayoutAttribute> attributo in <xref:System.Runtime.InteropServices.LayoutKind> o oppure <xref:System.Runtime.InteropServices.LayoutKind> rendere il tipo invisibile a com.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo che viola la regola e un tipo che soddisfa la regola.

 [!code-csharp[FxCop.Interoperability.AutoLayout#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.AutoLayout/cs/FxCop.Interoperability.AutoLayout.cs#1)]
 [!code-vb[FxCop.Interoperability.AutoLayout#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.AutoLayout/vb/FxCop.Interoperability.AutoLayout.vb#1)]

## <a name="related-rules"></a>Regole correlate
 [CA1408: Non usare AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)

## <a name="see-also"></a>Vedere anche
 [Introduzione all'interfaccia della classe per la](https://msdn.microsoft.com/733c0dd2-12e5-46e6-8de1-39d5b25df024) [qualificazione di tipi .NET per](https://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd) l' [interoperabilità dell'interazione con codice non gestito](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
