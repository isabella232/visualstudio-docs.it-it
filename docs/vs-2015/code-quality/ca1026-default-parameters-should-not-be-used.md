---
title: 'CA1026: I parametri predefiniti non devono essere utilizzati | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1026
- DefaultParametersShouldNotBeUsed
helpviewer_keywords:
- CA1026
- DefaultParametersShouldNotBeUsed
ms.assetid: 09643415-36ef-4d0f-9411-5721e14e2512
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5ab5fd842363c39f23981bdec93635974e2b2582
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49894365"
---
# <a name="ca1026-default-parameters-should-not-be-used"></a>CA1026: Evitare l'utilizzo di parametri predefiniti
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DefaultParametersShouldNotBeUsed|
|CheckId|CA1026|
|Category|Microsoft.Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un tipo visibile esternamente contiene un metodo visibile esternamente che usa un parametro predefinito.

## <a name="rule-description"></a>Descrizione della regola
 I metodi che utilizzano parametri predefiniti sono consentiti con la specifica CLS (Common Language); Tuttavia, la specifica CLS consente ai compilatori di ignorare i valori assegnati a questi parametri. Il codice scritto per i compilatori che ignorano i valori predefiniti dei parametri deve fornire esplicitamente gli argomenti per ogni parametro predefinito. Per mantenere il comportamento desiderato tra diversi linguaggi di programmazione, i metodi che utilizzano parametri predefiniti devono essere sostituiti con overload di metodi che forniscono i parametri predefiniti.

 Il compilatore ignora i valori dei parametri predefiniti per estensioni gestite per C++ durante l'accesso al codice gestito. Il compilatore Visual Basic supporta metodi che hanno parametri predefiniti che utilizzano le [facoltativo](http://msdn.microsoft.com/library/4571ce88-a539-4115-b230-54eb277c6aa7) (parola chiave).

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, sostituire il metodo che usa i parametri predefiniti con overload di metodi che forniscono i parametri predefiniti.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un metodo che usa i parametri predefiniti e i metodi di overload che forniscono una funzionalità equivalente.

 [!code-vb[FxCop.Design.DefaultParameters#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.DefaultParameters/vb/FxCop.Design.DefaultParameters.vb#1)]

## <a name="related-rules"></a>Regole correlate
 [CA1025: Sostituire gli argomenti ripetitivi con una matrice di parametri](../code-quality/ca1025-replace-repetitive-arguments-with-params-array.md)

## <a name="see-also"></a>Vedere anche
 [Indipendenza del linguaggio e componenti indipendenti dal linguaggio](http://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)



