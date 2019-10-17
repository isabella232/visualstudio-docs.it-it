---
title: 'CA1047: Non dichiarare membri protetti nei tipi sealed'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotDeclareProtectedMembersInSealedTypes
- CA1047
helpviewer_keywords:
- CA1047
- DoNotDeclareProtectedMembersInSealedTypes
ms.assetid: 829033b5-a9d8-4f26-a719-45494c9dd035
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: b55da06cdaee07e0d5c30dc6c5220ef2d50f8d0b
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72449098"
---
# <a name="ca1047-do-not-declare-protected-members-in-sealed-types"></a>CA1047: Non dichiarare membri protetti nei tipi sealed

|||
|-|-|
|TypeName|DoNotDeclareProtectedMembersInSealedTypes|
|CheckId|CA1047|
|Category|Microsoft. Design|
|Modifica|Senza interruzioni|

## <a name="cause"></a>Causa
Un tipo pubblico è `sealed` (`NotInheritable` in Visual Basic) e dichiara un membro protetto o un tipo annidato protetto. Questa regola non segnala le violazioni per i metodi <xref:System.Object.Finalize%2A>, che devono seguire questo modello.

## <a name="rule-description"></a>Descrizione della regola
I tipi dichiarano membri protetti in modo che i tipi che ereditano possano accedere al membro o eseguirne l'override. Per definizione, non è possibile ereditare da un tipo sealed, il che significa che non è possibile chiamare metodi protetti su tipi sealed.

Il C# compilatore genera un avviso per l'errore.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
Per correggere una violazione di questa regola, impostare il livello di accesso del membro su privato o rendere il tipo ereditabile.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
Non escludere un avviso da questa regola. Lasciare il tipo nello stato corrente può causare problemi di manutenzione e non fornisce alcun vantaggio.

## <a name="example"></a>Esempio
Nell'esempio seguente viene illustrato un tipo che viola questa regola.

[!code-vb[FxCop.Design.SealedNoProtected#1](../code-quality/codesnippet/VisualBasic/ca1047-do-not-declare-protected-members-in-sealed-types_1.vb)]
[!code-csharp[FxCop.Design.SealedNoProtected#1](../code-quality/codesnippet/CSharp/ca1047-do-not-declare-protected-members-in-sealed-types_1.cs)]
