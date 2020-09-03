---
title: 'CA1026: i parametri predefiniti non devono essere usati | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1026
- DefaultParametersShouldNotBeUsed
helpviewer_keywords:
- CA1026
- DefaultParametersShouldNotBeUsed
ms.assetid: 09643415-36ef-4d0f-9411-5721e14e2512
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a63d6e788dd1722d0c593469b225a4f1aeb4738d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85548445"
---
# <a name="ca1026-default-parameters-should-not-be-used"></a>CA1026: Evitare l'uso di parametri predefiniti
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|DefaultParametersShouldNotBeUsed|
|CheckId|CA1026|
|Category|Microsoft. Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un tipo visibile esternamente contiene un metodo visibile esternamente che usa un parametro predefinito.

## <a name="rule-description"></a>Descrizione della regola
 I metodi che utilizzano parametri predefiniti sono consentiti nel Common Language Specification (CLS); Tuttavia, la CLS consente ai compilatori di ignorare i valori assegnati a questi parametri. Il codice scritto per i compilatori che ignorano i valori dei parametri predefiniti deve fornire in modo esplicito gli argomenti per ogni parametro predefinito. Per mantenere il comportamento desiderato tra i linguaggi di programmazione, i metodi che utilizzano parametri predefiniti devono essere sostituiti con overload del metodo che forniscono i parametri predefiniti.

 Il compilatore ignora i valori dei parametri predefiniti per l'estensione gestita per C++ quando accede a codice gestito. Il compilatore Visual Basic supporta i metodi con parametri predefiniti che usano la parola chiave [Optional](https://msdn.microsoft.com/library/4571ce88-a539-4115-b230-54eb277c6aa7) .

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, sostituire il metodo che usa parametri predefiniti con overload del metodo che forniscono i parametri predefiniti.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un metodo che utilizza parametri predefiniti e i metodi di overload che forniscono una funzionalità equivalente.

 [!code-vb[FxCop.Design.DefaultParameters#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.DefaultParameters/vb/FxCop.Design.DefaultParameters.vb#1)]

## <a name="related-rules"></a>Regole correlate
 [CA1025: Sostituire gli argomenti ripetitivi con una matrice di parametri](../code-quality/ca1025-replace-repetitive-arguments-with-params-array.md)

## <a name="see-also"></a>Vedere anche
 [Indipendenza del linguaggio e componenti indipendenti dal linguaggio](https://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)
