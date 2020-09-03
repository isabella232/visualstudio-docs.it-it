---
title: 'CA1408: non utilizzare AutoDual ClassInterfaceType | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotUseAutoDualClassInterfaceType
- CA1408
helpviewer_keywords:
- CA1408
- DoNotUseAutoDualClassInterfaceType
ms.assetid: 60ca5e02-3c51-42dd-942b-4f950eecfa0f
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: b953a97d557e28cce50f554acc03797d4be38220
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85534875"
---
# <a name="ca1408-do-not-use-autodual-classinterfacetype"></a>CA1408: Non usare AutoDual ClassInterfaceType
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|DoNotUseAutoDualClassInterfaceType|
|CheckId|CA1408|
|Category|Microsoft. interoperabilità|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un tipo visibile Component Object Model (COM) è contrassegnato con l' <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> attributo impostato sul `AutoDual` valore di <xref:System.Runtime.InteropServices.ClassInterfaceType> .

## <a name="rule-description"></a>Descrizione della regola
 I tipi che utilizzano un'interfaccia duale consentono l'associazione dei client a uno specifico layout di interfaccia. Eventuali modifiche apportate in una versione futura al layout del tipo o ai tipi base interromperanno l'associazione dei client COM all'interfaccia. Per impostazione predefinita, se l' <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> attributo non è specificato, viene utilizzata un'interfaccia di solo dispatch.

 A meno che non sia contrassegnato diversamente, tutti i tipi non generici pubblici sono visibili a COM; tutti i tipi non pubblici e generici sono invisibili a COM.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, modificare il valore dell' <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> attributo con il `None` valore di <xref:System.Runtime.InteropServices.ClassInterfaceType> e definire in modo esplicito l'interfaccia.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non eliminare un avviso da questa regola a meno che non si sia certi che il layout del tipo e dei relativi tipi di base non verrà modificato in una versione futura.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrata una classe che viola la regola e una nuova dichiarazione della classe per l'utilizzo di un'interfaccia esplicita.

 [!code-csharp[FxCop.Interoperability.AutoDual#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.AutoDual/cs/FxCop.Interoperability.AutoDual.cs#1)]
 [!code-vb[FxCop.Interoperability.AutoDual#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.AutoDual/vb/FxCop.Interoperability.AutoDual.vb#1)]

## <a name="related-rules"></a>Regole correlate
 [CA1403: I tipi layout automatici non devono essere visibili a COM](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)

 [CA1412: Contrassegnare le interfacce ComSource come IDispatch](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md)

## <a name="see-also"></a>Vedere anche
 [Introduzione all'interfaccia della classe per la](https://msdn.microsoft.com/733c0dd2-12e5-46e6-8de1-39d5b25df024) [qualificazione di tipi .NET per](https://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd) l' [interoperabilità dell'interazione con codice non gestito](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
