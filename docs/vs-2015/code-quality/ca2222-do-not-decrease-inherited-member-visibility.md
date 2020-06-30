---
title: 'CA2222: non diminuire la visibilità del membro ereditato | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotDecreaseInheritedMemberVisibility
- CA2222
helpviewer_keywords:
- DoNotDecreaseInheritedMemberVisibility
- CA2222
ms.assetid: 066c8675-381f-43cc-956c-d757cc494028
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 04109e821d3a739b96ad63e1a441089a5d479cd8
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85540777"
---
# <a name="ca2222-do-not-decrease-inherited-member-visibility"></a>CA2222: Non diminuire la visibilità di membri ereditati
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|DoNotDecreaseInheritedMemberVisibility|
|CheckId|CA2222|
|Category|Microsoft. Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Un metodo privato in un tipo non sealed ha una firma identica a un metodo pubblico dichiarato in un tipo di base. Il metodo privato non è finale.

## <a name="rule-description"></a>Descrizione della regola
 Non modificare il modificatore di accesso per i membri ereditati. La modifica in privato di un membro ereditato non impedisce ai chiamanti di accedere all'implementazione della classe base del metodo. Se il membro viene reso privato e il tipo è non sealed, i tipi che ereditano possono chiamare l'ultima implementazione pubblica del metodo nella gerarchia di ereditarietà. Se è necessario modificare il modificatore di accesso, il metodo deve essere contrassegnato come Final o il tipo deve essere sealed per impedire che il metodo venga sottoposto a override.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, modificare l'accesso in modo che non sia privato. In alternativa, se il linguaggio di programmazione lo supporta, è possibile rendere il metodo finale.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo che viola questa regola.

 [!code-csharp[FxCop.Usage.InheritedPublic#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.InheritedPublic/cs/FxCop.Usage.InheritedPublic.cs#1)]
 [!code-vb[FxCop.Usage.InheritedPublic#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.InheritedPublic/vb/FxCop.Usage.InheritedPublic.vb#1)]
