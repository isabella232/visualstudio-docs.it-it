---
title: 'CA1410: I metodi di registrazione COM devono corrispondere'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1410
- ComRegistrationMethodsShouldBeMatched
helpviewer_keywords:
- CA1410
- ComRegistrationMethodsShouldBeMatched
ms.assetid: f3b2e62d-fd66-4093-9f0c-dba01ad995fd
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: bca9e06c861ab2bcaceead8bf8ee195b64e45c83
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234740"
---
# <a name="ca1410-com-registration-methods-should-be-matched"></a>CA1410: I metodi di registrazione COM devono corrispondere

|||
|-|-|
|TypeName|ComRegistrationMethodsShouldBeMatched|
|CheckId|CA1410|
|Category|Microsoft. interoperabilità|
|Modifica|Senza interruzioni|

## <a name="cause"></a>Causa

Un tipo dichiara un metodo contrassegnato con l' <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> attributo, ma non dichiara un metodo contrassegnato con l' <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> attributo o viceversa.

## <a name="rule-description"></a>Descrizione della regola

Per i client Component Object Model (COM) per la creazione di un tipo .NET, il tipo deve essere prima registrato. Se disponibile, un metodo contrassegnato con l' <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> attributo viene chiamato durante il processo di registrazione per eseguire il codice specificato dall'utente. Un metodo corrispondente contrassegnato con l' <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> attributo viene chiamato durante il processo di annullamento della registrazione per invertire le operazioni del metodo di registrazione.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, aggiungere il metodo di registrazione o annullamento della registrazione corrispondente.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio

Nell'esempio seguente viene illustrato un tipo che viola la regola. Il codice commentato Mostra la correzione per la violazione.

[!code-csharp[FxCop.Interoperability.ComRegistration#1](../code-quality/codesnippet/CSharp/ca1410-com-registration-methods-should-be-matched_1.cs)]
[!code-vb[FxCop.Interoperability.ComRegistration#1](../code-quality/codesnippet/VisualBasic/ca1410-com-registration-methods-should-be-matched_1.vb)]

## <a name="related-rules"></a>Regole correlate

[CA1411: I metodi di registrazione COM non devono essere visibili](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md)

## <a name="see-also"></a>Vedere anche

- <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName>
- [Registrare gli assembly con COM](/dotnet/framework/interop/registering-assemblies-with-com)
- [Regasm.exe (strumento di registrazione di assembly)](/dotnet/framework/tools/regasm-exe-assembly-registration-tool)