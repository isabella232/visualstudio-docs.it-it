---
title: 'CA1052: I tipi statici devono essere sealed | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- StaticHolderTypesShouldBeSealed
- CA1052
helpviewer_keywords:
- CA1052
- StaticHolderTypesShouldBeSealed
ms.assetid: 51a3165d-781e-4a55-aa0d-ea25fee7d4f2
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: d973d7ff5464b76228e917c83b3e62116e115718
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65693796"
---
# <a name="ca1052-static-holder-types-should-be-sealed"></a>CA1052: I tipi che contengono membri statici devono essere sealed
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|StaticHolderTypesShouldBeSealed|
|CheckId|CA1052|
|Category|Microsoft.Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un tipo pubblico o protetto contiene solo membri statici e non è dichiarato con la [sealed](https://msdn.microsoft.com/library/8e4ed5d3-10be-47db-9488-0da2008e6f3f) ([NotInheritable](https://msdn.microsoft.com/library/5c4da7c9-9562-4653-a947-1972e992f9f9)) modificatore.

## <a name="rule-description"></a>Descrizione della regola
 Questa regola presuppone che un tipo che contiene solo membri statici non è progettato per essere ereditato, poiché il tipo non fornisce alcuna funzionalità che può essere sottoposto a override in un tipo derivato. Un tipo che non è destinato a essere ereditato deve essere contrassegnato con il `sealed` modificatore proibire l'uso come un tipo di base.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, contrassegnare il tipo come `sealed`. Se la destinazione [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 2.0 o versioni precedenti, un approccio migliore consiste nel contrassegnare il tipo come `static`. In questo modo, evitare di dichiarare un costruttore privato per impedire la creazione di classe.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Eliminare un avviso da questa regola solo se il tipo è progettato per essere ereditata. L'assenza del `sealed` modificatore suggerisce che il tipo è utile come un tipo di base.

## <a name="example-of-a-violation"></a>Esempio di violazione

### <a name="description"></a>Descrizione
 Nell'esempio seguente viene illustrato un tipo che viola la regola.

### <a name="code"></a>Codice
 [!code-cpp[FxCop.Design.StaticMembers#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.StaticMembers/cpp/FxCop.Design.StaticMembers.cpp#1)]
 [!code-csharp[FxCop.Design.StaticMembers#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.StaticMembers/cs/FxCop.Design.StaticMembers.cs#1)]
 [!code-vb[FxCop.Design.StaticMembers#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.StaticMembers/vb/FxCop.Design.StaticMembers.vb#1)]

## <a name="fix-with-the-static-modifier"></a>Risolvere con il modificatore Static

### <a name="description"></a>Descrizione
 Nell'esempio seguente viene illustrato come correggere una violazione di questa regola, si contrassegna il tipo con il `static` modificatore.

### <a name="code"></a>Codice
 [!code-csharp[FxCop.Design.StaticMembersFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.StaticMembersFixed/cs/FxCop.Design.StaticMembersFixed.cs#1)]

## <a name="related-rules"></a>Regole correlate
 [CA1053: I tipi statici non devono avere costruttori](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)
