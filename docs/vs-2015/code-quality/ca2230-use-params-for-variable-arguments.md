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
ms.openlocfilehash: ce66e04272618b9df2ab1957af305bb9bf40ee9c
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85540361"
---
# <a name="ca2230-use-params-for-variable-arguments"></a>CA2230: Usare params per argomenti variabili
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|UseParamsForVariableArguments|
|CheckId|CA2230|
|Category|Microsoft. Usage|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un tipo pubblico o protetto contiene un metodo pubblico o protetto che usa la `VarArgs` convenzione di chiamata.

## <a name="rule-description"></a>Descrizione della regola
 La `VarArgs` convenzione di chiamata viene utilizzata con determinate definizioni di metodo che accettano un numero variabile di parametri. Un metodo che usa la `VarArgs` convenzione di chiamata non è conforme a CLS (Common Language Specification) e potrebbe non essere accessibile nei linguaggi di programmazione.

 In C#, la `VarArgs` convenzione di chiamata viene usata quando l'elenco di parametri di un metodo termina con la `__arglist` parola chiave. Visual Basic non supporta la `VarArgs` convenzione di chiamata e Visual C++ ne consente l'utilizzo solo nel codice non gestito che utilizza la notazione ellisse `...` .

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola in C#, usare la parola chiave [params](https://msdn.microsoft.com/library/1690815e-b52b-4967-8380-5780aff08012) invece di `__arglist` .

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 Nell'esempio seguente vengono illustrati due metodi, uno che viola la regola e uno che soddisfa la regola.

 [!code-csharp[FxCop.Usage.UseParams#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.UseParams/cs/FxCop.Usage.UseParams.cs#1)]

## <a name="see-also"></a>Vedere anche
 <xref:System.Reflection.CallingConventions?displayProperty=fullName>[Indipendenza del linguaggio e componenti indipendenti dal linguaggio](https://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)
