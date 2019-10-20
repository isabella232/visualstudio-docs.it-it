---
title: 'CA1041: specificare un messaggio di ObsoleteAttribute | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1041
- ProvideObsoleteAttributeMessage
helpviewer_keywords:
- ProvideObsoleteAttributeMessage
- CA1041
ms.assetid: be5bee69-d2d2-44e1-be2e-3ea451969003
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: dd1799f67036ab55de5b136d746ce938835de87f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668318"
---
# <a name="ca1041-provide-obsoleteattribute-message"></a>CA1041: Fornire una proprietà ObsoleteAttribute.Message
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ProvideObsoleteAttributeMessage|
|CheckId|CA1041|
|Category|Microsoft. Design|
|Modifica importante|Senza interruzioni|

## <a name="cause"></a>Causa
 Un tipo o un membro è contrassegnato con un attributo <xref:System.ObsoleteAttribute?displayProperty=fullName> che non ha la relativa proprietà <xref:System.ObsoleteAttribute.Message%2A?displayProperty=fullName> specificata.

## <a name="rule-description"></a>Descrizione della regola
 <xref:System.ObsoleteAttribute> viene usato per contrassegnare i tipi e i membri della libreria deprecata. I consumer della libreria devono evitare l'uso di qualsiasi tipo o membro contrassegnato come obsoleto. Questo perché potrebbe non essere supportato e verrà rimosso da versioni successive della libreria. Quando un tipo o un membro contrassegnato con <xref:System.ObsoleteAttribute> viene compilato, viene visualizzata la proprietà <xref:System.ObsoleteAttribute.Message%2A> dell'attributo. In questo modo vengono fornite le informazioni utente sul tipo o sul membro obsoleto. Queste informazioni includono generalmente per quanto tempo il tipo o il membro obsoleto sarà supportato dalle finestre di progettazione della libreria e dalla sostituzione preferita da usare.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, aggiungere il parametro `message` al costruttore <xref:System.ObsoleteAttribute>.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non eliminare un avviso da questa regola perché la proprietà <xref:System.ObsoleteAttribute.Message%2A> fornisce informazioni critiche sul tipo o sul membro obsoleto.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un membro obsoleto con una dichiarata correttamente <xref:System.ObsoleteAttribute>.

 [!code-cpp[FxCop.Design.ObsoleteAttributeOnMember#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.ObsoleteAttributeOnMember/cpp/FxCop.Design.ObsoleteAttributeOnMember.cpp#1)]
 [!code-csharp[FxCop.Design.ObsoleteAttributeOnMember#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ObsoleteAttributeOnMember/cs/FxCop.Design.ObsoleteAttributeOnMember.cs#1)]
 [!code-vb[FxCop.Design.ObsoleteAttributeOnMember#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ObsoleteAttributeOnMember/vb/FxCop.Design.ObsoleteAttributeOnMember.vb#1)]

## <a name="see-also"></a>Vedere anche
 <xref:System.ObsoleteAttribute?displayProperty=fullName>
