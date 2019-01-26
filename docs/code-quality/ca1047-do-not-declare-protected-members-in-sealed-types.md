---
title: 'CA1047: Non dichiarare membri protected nei tipi sealed'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 77277c093396ddbfdf458e93f468ad5ce5775bd2
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54928399"
---
# <a name="ca1047-do-not-declare-protected-members-in-sealed-types"></a>CA1047: Non dichiarare membri protected nei tipi sealed

|||
|-|-|
|TypeName|DoNotDeclareProtectedMembersInSealedTypes|
|CheckId|CA1047|
|Category|Microsoft.Design|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa
 È un tipo pubblico `sealed` (`NotInheritable` in Visual basic) e dichiara un membro protetto o un tipo annidato protetto. Questa regola segnala le violazioni per <xref:System.Object.Finalize%2A> metodi, che devono seguire questo modello.

## <a name="rule-description"></a>Descrizione della regola
 I tipi dichiarano membri protetti in modo che i tipi che ereditano possano accedere al membro o eseguirne l'override. Per definizione, è possibile ereditare da un tipo sealed, ovvero metodi protetti su tipi sealed non può essere chiamato.

 Il compilatore c# genera un avviso per questo errore.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, impostare il livello di accesso del membro privato o rendere ereditabile il tipo.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 Non escludere un avviso da questa regola. Lasciare il tipo nello stato corrente può causare problemi di manutenzione e non offre alcun vantaggio.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo che viola la regola.

 [!code-vb[FxCop.Design.SealedNoProtected#1](../code-quality/codesnippet/VisualBasic/ca1047-do-not-declare-protected-members-in-sealed-types_1.vb)]
 [!code-csharp[FxCop.Design.SealedNoProtected#1](../code-quality/codesnippet/CSharp/ca1047-do-not-declare-protected-members-in-sealed-types_1.cs)]