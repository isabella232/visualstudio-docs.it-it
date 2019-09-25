---
title: 'CA2230: Usare params per argomenti variabili'
ms.date: 11/04/2016
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
ms.openlocfilehash: 0639d30771b3a6bb288ddbf9644dda2efcd5f90d
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231353"
---
# <a name="ca2230-use-params-for-variable-arguments"></a>CA2230: Usare params per argomenti variabili

|||
|-|-|
|TypeName|UseParamsForVariableArguments|
|CheckId|CA2230|
|Category|Microsoft.Usage|
|Modifica|Interruzione|

## <a name="cause"></a>Causa
Un tipo pubblico o protetto contiene un metodo pubblico o protetto che usa la `VarArgs` convenzione di chiamata.

## <a name="rule-description"></a>Descrizione della regola
La `VarArgs` convenzione di chiamata viene utilizzata con determinate definizioni di metodo che accettano un numero variabile di parametri. Un metodo che usa `VarArgs` la convenzione di chiamata non è conforme a CLS (Common Language Specification) e potrebbe non essere accessibile nei linguaggi di programmazione.

In C#, la `VarArgs` convenzione di chiamata viene utilizzata quando l'elenco di parametri di un metodo `__arglist` termina con la parola chiave. Visual Basic non supporta la convenzione `VarArgs` di chiamata e l'oggetto C++ visivo ne consente l'utilizzo solo nel codice non gestito che utilizza la `...` notazione ellisse.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
Per correggere una violazione di questa regola in C#, utilizzare la parola chiave [params](/dotnet/csharp/language-reference/keywords/params) anziché `__arglist`.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
Nell'esempio seguente vengono illustrati due metodi, uno che viola la regola e uno che soddisfa la regola.

[!code-csharp[FxCop.Usage.UseParams#1](../code-quality/codesnippet/CSharp/ca2230-use-params-for-variable-arguments_1.cs)]

## <a name="see-also"></a>Vedere anche

- <xref:System.Reflection.CallingConventions?displayProperty=fullName>
- [Indipendenza del linguaggio e componenti indipendenti dal linguaggio](/dotnet/standard/language-independence-and-language-independent-components)