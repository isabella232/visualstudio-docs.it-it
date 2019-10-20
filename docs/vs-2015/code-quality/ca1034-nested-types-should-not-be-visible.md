---
title: 'CA1034: i tipi annidati non devono essere visibili | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- NestedTypesShouldNotBeVisible
- CA1034
helpviewer_keywords:
- NestedTypesShouldNotBeVisible
- CA1034
ms.assetid: e9789a2c-2540-42a1-8705-ae7104011194
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 33e7ea6aaefcaf5b6cbf0bf8c52ade0b9e68a549
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661861"
---
# <a name="ca1034-nested-types-should-not-be-visible"></a>CA1034: I tipi annidati non devono essere visibili
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|NestedTypesShouldNotBeVisible|
|CheckId|CA1034|
|Category|Microsoft. Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un tipo visibile esternamente contiene una dichiarazione di tipo visibile esternamente. Le enumerazioni annidate e i tipi protetti sono esenti da questa regola.

## <a name="rule-description"></a>Descrizione della regola
 Un tipo annidato è un tipo dichiarato all'interno dell'ambito di un altro tipo. I tipi annidati sono utili per incapsulare i dettagli di implementazione privata del tipo che lo contiene. I tipi annidati utilizzati per questo scopo non devono essere visibili esternamente.

 Non usare tipi annidati visibili esternamente per il raggruppamento logico o per evitare conflitti di nomi; usare invece gli spazi dei nomi.

 I tipi annidati includono la nozione di accessibilità dei membri, che alcuni programmatori non conoscono chiaramente.

 I tipi protetti possono essere utilizzati nelle sottoclassi e nei tipi annidati in scenari di personalizzazione avanzati.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Se non si desidera che il tipo annidato sia visibile esternamente, modificare l'accessibilità del tipo. In caso contrario, rimuovere il tipo annidato dall'elemento padre. Se lo scopo dell'annidamento consiste nel categorizzare il tipo annidato, usare uno spazio dei nomi per creare la gerarchia.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo che viola la regola.

 [!code-cpp[FxCop.Design.NestedTypes#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.NestedTypes/cpp/FxCop.Design.NestedTypes.cpp#1)]
 [!code-csharp[FxCop.Design.NestedTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NestedTypes/cs/FxCop.Design.NestedTypes.cs#1)]
 [!code-vb[FxCop.Design.NestedTypes#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.NestedTypes/vb/FxCop.Design.NestedTypes.vb#1)]
