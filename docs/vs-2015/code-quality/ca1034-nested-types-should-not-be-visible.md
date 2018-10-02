---
title: 'CA1034: I tipi annidati non devono essere visibili | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- NestedTypesShouldNotBeVisible
- CA1034
helpviewer_keywords:
- NestedTypesShouldNotBeVisible
- CA1034
ms.assetid: e9789a2c-2540-42a1-8705-ae7104011194
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5edfdca7fe3834160a7120528b56a2770924bf83
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589723"
---
# <a name="ca1034-nested-types-should-not-be-visible"></a>CA1034: I tipi annidati non devono essere visibili
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [CA1034: i tipi annidati non devono essere visibili](https://docs.microsoft.com/visualstudio/code-quality/ca1034-nested-types-should-not-be-visible).

|||
|-|-|
|TypeName|NestedTypesShouldNotBeVisible|
|CheckId|CA1034|
|Category|Microsoft.Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un tipo visibile esternamente contiene una dichiarazione del tipo visibile esternamente. Enumerazioni annidate e i tipi protetti sono esclusi da questa regola.

## <a name="rule-description"></a>Descrizione della regola
 Un tipo annidato è un tipo dichiarato nell'ambito di un altro tipo. I tipi annidati sono utili per incapsulare i dettagli di implementazione privati del tipo contenitore. I tipi annidati utilizzati per questo scopo non devono essere visibili esternamente.

 Non usare i tipi annidati visibili esternamente per il raggruppamento logico o per evitare conflitti di nome; Usare invece gli spazi dei nomi.

 I tipi annidati includono la nozione di accessibilità del membro, che alcuni programmatori non supportano in modo chiaro.

 Tipi protetti possono essere utilizzati nelle sottoclassi e i tipi annidati in scenari di personalizzazione avanzate.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Se non si intende il tipo annidato da essere visibili esternamente, modificare l'accessibilità del tipo. In caso contrario, rimuovere il tipo annidato dal relativo elemento padre. Se lo scopo dell'annidamento è per classificare il tipo annidato, usare uno spazio dei nomi per creare invece una gerarchia.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo che viola la regola.

 [!code-cpp[FxCop.Design.NestedTypes#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.NestedTypes/cpp/FxCop.Design.NestedTypes.cpp#1)]
 [!code-csharp[FxCop.Design.NestedTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NestedTypes/cs/FxCop.Design.NestedTypes.cs#1)]
 [!code-vb[FxCop.Design.NestedTypes#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.NestedTypes/vb/FxCop.Design.NestedTypes.vb#1)]



