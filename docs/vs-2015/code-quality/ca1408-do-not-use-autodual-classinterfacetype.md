---
title: 'CA1408: Non utilizzare AutoDual ClassInterfaceType | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DoNotUseAutoDualClassInterfaceType
- CA1408
helpviewer_keywords:
- CA1408
- DoNotUseAutoDualClassInterfaceType
ms.assetid: 60ca5e02-3c51-42dd-942b-4f950eecfa0f
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 67b22f74ece23420bf47b8607d5b7a875501765a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49942446"
---
# <a name="ca1408-do-not-use-autodual-classinterfacetype"></a>CA1408: Non utilizzare AutoDual ClassInterfaceType
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotUseAutoDualClassInterfaceType|
|CheckId|CA1408|
|Category|Microsoft.Interoperability|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un tipo visibile modello COM (Component Object) è contrassegnato con il <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> attributo impostato il `AutoDual` pari a <xref:System.Runtime.InteropServices.ClassInterfaceType>.

## <a name="rule-description"></a>Descrizione della regola
 I tipi che utilizzano un'interfaccia duale consentono l'associazione dei client a uno specifico layout di interfaccia. Eventuali modifiche apportate in una versione futura al layout del tipo o ai tipi base interromperanno l'associazione dei client COM all'interfaccia. Per impostazione predefinita, se il <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> attributo viene omesso, viene usata un'interfaccia solo dispatch.

 Se non diversamente specificato, tutti i tipi generici pubblici sono visibili a COM. tutti i tipi generici e non pubblici non sono visibili a COM.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, modificare il valore della <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> dell'attributo per il `None` pari a <xref:System.Runtime.InteropServices.ClassInterfaceType> e definire in modo esplicito l'interfaccia.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola a meno che non è certo che il layout del tipo e i relativi tipi di base non verrà modificati in una versione futura.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrata una classe che viola la regola e una nuova dichiarazione della classe per utilizzare un'interfaccia esplicita.

 [!code-csharp[FxCop.Interoperability.AutoDual#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.AutoDual/cs/FxCop.Interoperability.AutoDual.cs#1)]
 [!code-vb[FxCop.Interoperability.AutoDual#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.AutoDual/vb/FxCop.Interoperability.AutoDual.vb#1)]

## <a name="related-rules"></a>Regole correlate
 [CA1403: I tipi layout automatici non devono essere visibili a COM](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)

 [CA1412: Contrassegnare le interfacce ComSource come IDispatch](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md)

## <a name="see-also"></a>Vedere anche
 [Introduzione all'interfaccia della classe](http://msdn.microsoft.com/en-us/733c0dd2-12e5-46e6-8de1-39d5b25df024) [qualificazione di tipi .NET per l'interoperatività](http://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd) [interoperabilità con codice non gestito](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)



