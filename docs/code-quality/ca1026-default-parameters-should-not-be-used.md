---
title: "CA1026: Evitare l'uso di parametri predefiniti"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1026
- DefaultParametersShouldNotBeUsed
helpviewer_keywords:
- CA1026
- DefaultParametersShouldNotBeUsed
ms.assetid: 09643415-36ef-4d0f-9411-5721e14e2512
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 62de7654083f3fd64f95401f95e5ee593effb27d
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236125"
---
# <a name="ca1026-default-parameters-should-not-be-used"></a>CA1026: Evitare l'uso di parametri predefiniti

|||
|-|-|
|TypeName|DefaultParametersShouldNotBeUsed|
|CheckId|CA1026|
|Category|Microsoft.Design|
|Modifica|Interruzione|

## <a name="cause"></a>Causa
Un tipo visibile esternamente contiene un metodo visibile esternamente che usa un parametro predefinito.

## <a name="rule-description"></a>Descrizione della regola
I metodi che utilizzano parametri predefiniti sono consentiti nel Common Language Specification (CLS); Tuttavia, la CLS consente ai compilatori di ignorare i valori assegnati a questi parametri. Il codice scritto per i compilatori che ignorano i valori dei parametri predefiniti deve fornire in modo esplicito gli argomenti per ogni parametro predefinito. Per mantenere il comportamento desiderato tra i linguaggi di programmazione, i metodi che utilizzano parametri predefiniti devono essere sostituiti con overload del metodo che forniscono i parametri predefiniti.

Il compilatore ignora i valori dei parametri predefiniti per l'estensione gestita per C++ quando accede al codice gestito. Il compilatore Visual Basic supporta i metodi con parametri predefiniti che usano la parola chiave [Optional](/dotnet/visual-basic/language-reference/modifiers/optional) .

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
Per correggere una violazione di questa regola, sostituire il metodo che usa parametri predefiniti con overload del metodo che forniscono i parametri predefiniti.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
Nell'esempio seguente viene illustrato un metodo che utilizza parametri predefiniti e i metodi di overload che forniscono una funzionalità equivalente.

[!code-vb[FxCop.Design.DefaultParameters#1](../code-quality/codesnippet/VisualBasic/ca1026-default-parameters-should-not-be-used_1.vb)]

## <a name="related-rules"></a>Regole correlate
[CA1025: Sostituisci argomenti ripetitivi con la matrice params](../code-quality/ca1025-replace-repetitive-arguments-with-params-array.md)

## <a name="see-also"></a>Vedere anche
[Indipendenza del linguaggio e componenti indipendenti dal linguaggio](/dotnet/standard/language-independence-and-language-independent-components)