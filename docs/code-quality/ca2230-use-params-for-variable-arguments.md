---
title: 'CA2230: Usare params per argomenti variabili'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- UseParamsForVariableArguments
- CA2230
helpviewer_keywords:
- CA2230
- UseParamsForVariableArguments
ms.assetid: bf98b733-4855-4110-9f16-eba5a9e79421
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: db6c66e65ed89e53d0cbbed671004c88bdbaed95
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54982975"
---
# <a name="ca2230-use-params-for-variable-arguments"></a>CA2230: Usare params per argomenti variabili

|||
|-|-|
|TypeName|UseParamsForVariableArguments|
|CheckId|CA2230|
|Category|Microsoft.Usage|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un tipo pubblico o protetto contiene un metodo pubblico o protetto che utilizza il `VarArgs` convenzione di chiamata.

## <a name="rule-description"></a>Descrizione della regola
 Il `VarArgs` convenzione di chiamata viene usato con alcune definizioni di metodi che accettano un numero variabile di parametri. Un metodo tramite la `VarArgs` convenzione di chiamata non Common Language Specification (conforme a CLS) e potrebbe non essere accessibile in linguaggi di programmazione.

 In c#, il `VarArgs` convenzione di chiamata viene utilizzato quando l'elenco dei parametri del metodo termina con il `__arglist` (parola chiave). Visual Basic non supporta il `VarArgs` convenzione di chiamata e Visual C++ consente l'utilizzo solo nel codice non gestito che utilizza l'ellisse `...` notation.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione della regola nel linguaggio c#, usare il [params](/dotnet/csharp/language-reference/keywords/params) parola chiave anziché `__arglist`.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 L'esempio seguente illustra due metodi, uno che viola la regola e uno che soddisfa la regola.

 [!code-csharp[FxCop.Usage.UseParams#1](../code-quality/codesnippet/CSharp/ca2230-use-params-for-variable-arguments_1.cs)]

## <a name="see-also"></a>Vedere anche

- <xref:System.Reflection.CallingConventions?displayProperty=fullName>
- [Indipendenza del linguaggio e componenti indipendenti dal linguaggio](/dotnet/standard/language-independence-and-language-independent-components)