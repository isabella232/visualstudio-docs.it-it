---
title: 'CA2230: usare params per gli argomenti variabili | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseParamsForVariableArguments
- CA2230
helpviewer_keywords:
- CA2230
- UseParamsForVariableArguments
ms.assetid: bf98b733-4855-4110-9f16-eba5a9e79421
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a690544a7ed03094587a2aaf1c44b7ed68e8f2a9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662836"
---
# <a name="ca2230-use-params-for-variable-arguments"></a>CA2230: Utilizzare params per argomenti variabili
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseParamsForVariableArguments|
|CheckId|CA2230|
|Category|Microsoft. Usage|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un tipo pubblico o protetto contiene un metodo pubblico o protetto che usa la convenzione di chiamata `VarArgs`.

## <a name="rule-description"></a>Descrizione della regola
 La convenzione di chiamata `VarArgs` viene utilizzata con determinate definizioni di metodo che accettano un numero variabile di parametri. Un metodo che usa la convenzione di chiamata `VarArgs` non è conforme a CLS (Common Language Specification) e potrebbe non essere accessibile nei linguaggi di programmazione.

 In C#, la convenzione di chiamata `VarArgs` viene utilizzata quando l'elenco di parametri di un metodo termina con la parola chiave `__arglist`. Visual Basic non supporta la convenzione di chiamata `VarArgs` e l'oggetto C++ visivo ne consente l'utilizzo solo nel codice non gestito che utilizza la notazione `...` ellisse.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola in C#, utilizzare la parola chiave [params](https://msdn.microsoft.com/library/1690815e-b52b-4967-8380-5780aff08012) anziché `__arglist`.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 Nell'esempio seguente vengono illustrati due metodi, uno che viola la regola e uno che soddisfa la regola.

 [!code-csharp[FxCop.Usage.UseParams#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.UseParams/cs/FxCop.Usage.UseParams.cs#1)]

## <a name="see-also"></a>Vedere anche
 [indipendenza dal linguaggio <xref:System.Reflection.CallingConventions?displayProperty=fullName> e componenti indipendenti dal linguaggio](https://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)
