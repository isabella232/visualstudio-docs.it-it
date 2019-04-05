---
title: 'CA1411: Metodi di registrazione COM non devono essere visibili | Microsoft Docs'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a332139caec707c593614c7cf1b07733d533ac87
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58967558"
---
# <a name="ca1411-com-registration-methods-should-not-be-visible"></a>CA1411: I metodi di registrazione COM non devono essere visibili
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ComRegistrationMethodsShouldNotBeVisible|
|CheckId|CA1411|
|Category|Microsoft.Interoperability|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un metodo contrassegnato con il <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> o il <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> attributo è visibile esternamente.

## <a name="rule-description"></a>Descrizione della regola
 Quando un assembly viene registrato con modello COM (Component Object), vengono aggiunte voci nel Registro di sistema per ogni tipo visibile a COM nell'assembly. I metodi contrassegnati con il <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> e <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> attributi vengono chiamati durante i processi di registrazione e annullamento della registrazione, rispettivamente, per eseguire il codice utente specifico per la registrazione/annullamento della registrazione di questi tipi. Questo codice non deve essere chiamato all'esterno di questi processi.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, modificare l'accessibilità del metodo `private` oppure `internal` (`Friend` in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]).

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 L'esempio seguente illustra due metodi che violano la regola.

 [!code-csharp[FxCop.Interoperability.ComRegistration2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComRegistration2/cs/FxCop.Interoperability.ComRegistration2.cs#1)]
 [!code-vb[FxCop.Interoperability.ComRegistration2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComRegistration2/vb/FxCop.Interoperability.ComRegistration2.vb#1)]

## <a name="related-rules"></a>Regole correlate
 [CA1410: I metodi di registrazione COM devono corrispondere](../code-quality/ca1410-com-registration-methods-should-be-matched.md)

## <a name="see-also"></a>Vedere anche
 <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName> [Registrazione di assembly presso COM](http://msdn.microsoft.com/library/87925795-a3ae-4833-b138-125413478551) [Regasm.exe (strumento di registrazione di Assembly)](http://msdn.microsoft.com/library/e190e342-36ef-4651-a0b4-0e8c2c0281cb)
