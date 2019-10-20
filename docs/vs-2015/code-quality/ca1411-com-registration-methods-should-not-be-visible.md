---
title: 'CA1411: i metodi di registrazione COM non devono essere visibili | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1411
- ComRegistrationMethodsShouldNotBeVisible
helpviewer_keywords:
- ComRegistrationMethodsShouldNotBeVisible
- CA1411
ms.assetid: a59f96f1-1f38-4596-b656-947df5c55311
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f3ddd2c90d23884bd08a90560dcc5ed0fe700aaf
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652718"
---
# <a name="ca1411-com-registration-methods-should-not-be-visible"></a>CA1411: I metodi di registrazione COM non devono essere visibili
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ComRegistrationMethodsShouldNotBeVisible|
|CheckId|CA1411|
|Category|Microsoft. interoperabilità|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un metodo contrassegnato con l'attributo <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> o <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> è visibile esternamente.

## <a name="rule-description"></a>Descrizione della regola
 Quando un assembly viene registrato con Component Object Model (COM), le voci vengono aggiunte al registro di sistema per ogni tipo visibile a COM nell'assembly. I metodi contrassegnati con gli attributi <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> e <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> vengono chiamati rispettivamente durante i processi di registrazione e annullamento della registrazione per eseguire codice utente specifico per la registrazione e l'annullamento della registrazione di questi tipi. Questo codice non deve essere chiamato al di fuori di questi processi.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, modificare l'accessibilità del metodo in `private` o `internal` (`Friend` in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]).

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 Nell'esempio seguente vengono illustrati due metodi che violano la regola.

 [!code-csharp[FxCop.Interoperability.ComRegistration2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComRegistration2/cs/FxCop.Interoperability.ComRegistration2.cs#1)]
 [!code-vb[FxCop.Interoperability.ComRegistration2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComRegistration2/vb/FxCop.Interoperability.ComRegistration2.vb#1)]

## <a name="related-rules"></a>Regole correlate
 [CA1410: I metodi di registrazione COM devono corrispondere](../code-quality/ca1410-com-registration-methods-should-be-matched.md)

## <a name="see-also"></a>Vedere anche
 <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName> [la registrazione degli assembly con com](https://msdn.microsoft.com/library/87925795-a3ae-4833-b138-125413478551) [regasm. exe (strumento di registrazione degli assembly)](https://msdn.microsoft.com/library/e190e342-36ef-4651-a0b4-0e8c2c0281cb)
