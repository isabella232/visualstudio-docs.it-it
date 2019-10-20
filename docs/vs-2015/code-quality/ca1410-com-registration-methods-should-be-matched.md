---
title: 'CA1410: i metodi di registrazione COM devono corrispondere | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1410
- ComRegistrationMethodsShouldBeMatched
helpviewer_keywords:
- CA1410
- ComRegistrationMethodsShouldBeMatched
ms.assetid: f3b2e62d-fd66-4093-9f0c-dba01ad995fd
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 30f507f07de858dc222b4824ac6da633c76812ab
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652736"
---
# <a name="ca1410-com-registration-methods-should-be-matched"></a>CA1410: I metodi di registrazione COM devono corrispondere
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ComRegistrationMethodsShouldBeMatched|
|CheckId|CA1410|
|Category|Microsoft. interoperabilità|
|Modifica importante|Senza interruzioni|

## <a name="cause"></a>Causa
 Un tipo dichiara un metodo contrassegnato con l'attributo <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName>, ma non dichiara un metodo contrassegnato con l'attributo <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> o viceversa.

## <a name="rule-description"></a>Descrizione della regola
 Per Component Object Model client (COM) per la creazione di un tipo di [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], il tipo deve essere prima registrato. Se è disponibile, durante il processo di registrazione viene chiamato un metodo contrassegnato con l'attributo <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> per eseguire il codice specificato dall'utente. Un metodo corrispondente contrassegnato con l'attributo <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> viene chiamato durante il processo di annullamento della registrazione per invertire le operazioni del metodo di registrazione.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, aggiungere il metodo di registrazione o annullamento della registrazione corrispondente.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo che viola la regola. Il codice commentato Mostra la correzione per la violazione.

 [!code-csharp[FxCop.Interoperability.ComRegistration#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComRegistration/cs/FxCop.Interoperability.ComRegistration.cs#1)]
 [!code-vb[FxCop.Interoperability.ComRegistration#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComRegistration/vb/FxCop.Interoperability.ComRegistration.vb#1)]

## <a name="related-rules"></a>Regole correlate
 [CA1411: I metodi di registrazione COM non devono essere visibili](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md)

## <a name="see-also"></a>Vedere anche
 <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName> [la registrazione degli assembly con com](https://msdn.microsoft.com/library/87925795-a3ae-4833-b138-125413478551) [regasm. exe (strumento di registrazione degli assembly)](https://msdn.microsoft.com/library/e190e342-36ef-4651-a0b4-0e8c2c0281cb)
