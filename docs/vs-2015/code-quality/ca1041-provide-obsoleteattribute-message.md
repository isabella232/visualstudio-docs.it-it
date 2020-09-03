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
ms.openlocfilehash: d738cf15ebe734cb74e553f38f6eb26af17e8cfd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85542311"
---
# <a name="ca1041-provide-obsoleteattribute-message"></a>CA1041: Specificare una proprietà ObsoleteAttribute.Message
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|ProvideObsoleteAttributeMessage|
|CheckId|CA1041|
|Category|Microsoft. Design|
|Modifica importante|Senza interruzioni|

## <a name="cause"></a>Causa
 Un tipo o un membro è contrassegnato con un <xref:System.ObsoleteAttribute?displayProperty=fullName> attributo che non ha la relativa <xref:System.ObsoleteAttribute.Message%2A?displayProperty=fullName> proprietà specificata.

## <a name="rule-description"></a>Descrizione della regola
 <xref:System.ObsoleteAttribute> viene utilizzato per contrassegnare i tipi e i membri della libreria deprecata. I consumer della libreria devono evitare l'uso di qualsiasi tipo o membro contrassegnato come obsoleto. Questo perché potrebbe non essere supportato e verrà rimosso da versioni successive della libreria. Quando un tipo o un membro contrassegnato mediante <xref:System.ObsoleteAttribute> viene compilato, <xref:System.ObsoleteAttribute.Message%2A> viene visualizzata la proprietà dell'attributo. In questo modo vengono fornite le informazioni utente sul tipo o sul membro obsoleto. Queste informazioni includono generalmente per quanto tempo il tipo o il membro obsoleto sarà supportato dalle finestre di progettazione della libreria e dalla sostituzione preferita da usare.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, aggiungere il `message` parametro al <xref:System.ObsoleteAttribute> costruttore.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non eliminare un avviso da questa regola perché la <xref:System.ObsoleteAttribute.Message%2A> proprietà fornisce informazioni critiche sul tipo o sul membro obsoleto.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un membro obsoleto con una dichiarata correttamente <xref:System.ObsoleteAttribute> .

 [!code-cpp[FxCop.Design.ObsoleteAttributeOnMember#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.ObsoleteAttributeOnMember/cpp/FxCop.Design.ObsoleteAttributeOnMember.cpp#1)]
 [!code-csharp[FxCop.Design.ObsoleteAttributeOnMember#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ObsoleteAttributeOnMember/cs/FxCop.Design.ObsoleteAttributeOnMember.cs#1)]
 [!code-vb[FxCop.Design.ObsoleteAttributeOnMember#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ObsoleteAttributeOnMember/vb/FxCop.Design.ObsoleteAttributeOnMember.vb#1)]

## <a name="see-also"></a>Vedere anche
 <xref:System.ObsoleteAttribute?displayProperty=fullName>
