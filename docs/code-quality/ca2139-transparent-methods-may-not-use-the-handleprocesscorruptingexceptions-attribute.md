---
title: "CA2139: I metodi Transparent non possono usare l'attributo HandleProcessCorruptingExceptions"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2139
ms.assetid: 45a0328a-add7-40f9-8934-dff59beb02b3
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4d7f680107790143f4022722ed60e2a7f1000a06
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232183"
---
# <a name="ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute"></a>CA2139: I metodi Transparent non possono usare l'attributo HandleProcessCorruptingExceptions

|||
|-|-|
|TypeName|TransparentMethodsMustNotHandleProcessCorruptingExceptions|
|CheckId|CA2139|
|Category|Microsoft.Security|
|Modifica|Interruzione|

## <a name="cause"></a>Causa
Un metodo trasparente è contrassegnato con l' <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> attributo.

## <a name="rule-description"></a>Descrizione della regola
Questa regola attiva qualsiasi metodo trasparente e tenta di gestire un'eccezione che danneggia il processo tramite l' <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> attributo. Un'eccezione che danneggia il processo è una classificazione di eccezione CLR versione 4,0 di <xref:System.AccessViolationException>eccezioni di questo tipo. L'attributo HandleProcessCorruptedStateExceptionsAttribute può essere usato solo dai metodi critici per la sicurezza e sarà ignorato se applicato a un metodo trasparente. Per gestire le eccezioni che danneggiano il processo, questo metodo deve diventare critico per la sicurezza o critico per la sicurezza.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
Per correggere una violazione di questa regola, rimuovere l' <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> attributo o contrassegnare il metodo con l' <xref:System.Security.SecurityCriticalAttribute> <xref:System.Security.SecuritySafeCriticalAttribute> attributo o.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
In questo esempio, un metodo trasparente è contrassegnato con l' <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> attributo e non avrà esito positivo per la regola. Anche il metodo deve essere contrassegnato con l' <xref:System.Security.SecurityCriticalAttribute> <xref:System.Security.SecuritySafeCriticalAttribute> attributo o.

[!code-csharp[FxCop.Security.CA2139.TransparentMethodsMustNotHandleProcessCorruptingExceptions#1](../code-quality/codesnippet/CSharp/ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute_1.cs)]