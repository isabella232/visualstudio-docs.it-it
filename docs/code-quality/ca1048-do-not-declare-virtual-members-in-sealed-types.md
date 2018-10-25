---
title: 'CA1048: Non dichiarare membri virtuali nei tipi sealed'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotDeclareVirtualMembersInSealedTypes
- CA1048
helpviewer_keywords:
- DoNotDeclareVirtualMembersInSealedTypes
- CA1048
ms.assetid: 5dcf4a30-6f98-48a8-b8cc-7b89ea757262
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6cb38b089b432d65d74032b5ceb5ef820685557c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49891921"
---
# <a name="ca1048-do-not-declare-virtual-members-in-sealed-types"></a>CA1048: Non dichiarare membri virtuali nei tipi sealed

|||
|-|-|
|TypeName|DoNotDeclareVirtualMembersInSealedTypes|
|CheckId|CA1048|
|Category|Microsoft.Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un tipo pubblico è bloccato e dichiara un metodo che è sia `virtual` (`Overridable` in Visual Basic) e non finale. Questa regola segnala le violazioni per i tipi di delegato, che devono seguire questo modello.

## <a name="rule-description"></a>Descrizione della regola
 I tipi dichiarano metodi come virtuali in modo che l'ereditarietà di tipi possa eseguire l'override dell'implementazione del metodo virtuale. Per definizione, è possibile ereditare da un tipo sealed, rendere un metodo virtuale su un tipo sealed privo di significato.

 I compilatori Visual Basic e c# non consentono tipi violano questa regola.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, impostare il metodo non virtuale o rendere ereditabile il tipo.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 Non escludere un avviso da questa regola. Lasciare il tipo nello stato corrente può causare problemi di manutenzione e non offre alcun vantaggio.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo che viola la regola.

 [!code-cpp[FxCop.Design.SealedVirtual#1](../code-quality/codesnippet/CPP/ca1048-do-not-declare-virtual-members-in-sealed-types_1.cpp)]