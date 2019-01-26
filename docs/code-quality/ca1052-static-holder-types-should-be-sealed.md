---
title: 'CA1052: I tipi che contengono membri statici devono essere sealed'
ms.date: 11/09/2018
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- StaticHolderTypesShouldBeSealed
- CA1052
helpviewer_keywords:
- CA1052
- StaticHolderTypesShouldBeSealed
ms.assetid: 51a3165d-781e-4a55-aa0d-ea25fee7d4f2
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: a8743dc617a7749a81528c8ef5c570f7d52b4a06
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54937087"
---
# <a name="ca1052-static-holder-types-should-be-sealed"></a>CA1052: I tipi che contengono membri statici devono essere sealed

|||
|-|-|
|TypeName|StaticHolderTypesShouldBeSealed|
|CheckId|CA1052|
|Category|Microsoft.Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa

Una pubblica o protetta, non astratta tipo contiene solo membri statici e non è dichiarato con la [sealed](/dotnet/csharp/language-reference/keywords/sealed) ([NotInheritable](/dotnet/visual-basic/language-reference/modifiers/notinheritable)) modificatore.

## <a name="rule-description"></a>Descrizione della regola

CA1052 regola presuppone che un tipo che contiene solo membri statici non è progettato per essere ereditato, poiché il tipo non fornisce alcuna funzionalità che può essere sottoposto a override in un tipo derivato. Un tipo che non è destinato a essere ereditato deve essere contrassegnato con il `sealed` o `NotInheritable` modificatore proibire l'uso come un tipo di base. Questa regola non viene generato per le classi astratte.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, contrassegnare il tipo come `sealed` o `NotInheritable`. Se la destinazione scelta è .NET Framework 2.0 o versioni successive, un approccio migliore consiste nel contrassegnare il tipo come `static` o `Shared`. In questo modo, non è necessario dichiarare un costruttore privato per impedire la creazione di classe.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

Eliminare un avviso da questa regola solo se il tipo è progettato per essere ereditata. L'assenza del `sealed` o `NotInheritable` modificatore suggerisce che il tipo è utile come un tipo di base.

## <a name="example-of-a-violation"></a>Esempio di violazione

Nell'esempio seguente viene illustrato un tipo che viola la regola.

[!code-csharp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_1.cs)]
[!code-vb[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/VisualBasic/ca1052-static-holder-types-should-be-sealed_1.vb)]
[!code-cpp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CPP/ca1052-static-holder-types-should-be-sealed_1.cpp)]

## <a name="fix-with-the-static-modifier"></a>Risolvere con il modificatore static

Nell'esempio seguente viene illustrato come correggere una violazione di questa regola, si contrassegna il tipo con il `static` modificatore in C#.

[!code-csharp[FxCop.Design.StaticMembersFixed#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_2.cs)]

## <a name="related-rules"></a>Regole correlate

[CA1053: I tipi statici non devono avere costruttori](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)