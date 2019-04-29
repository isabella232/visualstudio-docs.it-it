---
title: 'CA1041: Fornire una proprietà ObsoleteAttribute. message | Microsoft Docs'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: fe14ca0c0e917896a2ed5a31a03a8c1a7057d613
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62559898"
---
# <a name="ca1041-provide-obsoleteattribute-message"></a>CA1041: Specificare una proprietà ObsoleteAttribute.Message
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ProvideObsoleteAttributeMessage|
|CheckId|CA1041|
|Category|Microsoft.Design|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa
 Un tipo o membro è contrassegnato utilizzando un <xref:System.ObsoleteAttribute?displayProperty=fullName> attributo che non è relativo <xref:System.ObsoleteAttribute.Message%2A?displayProperty=fullName> proprietà specificata.

## <a name="rule-description"></a>Descrizione della regola
 <xref:System.ObsoleteAttribute> Consente di contrassegnare i membri e tipi di libreria obsoleto. Consumer della libreria è consigliabile evitare l'uso di qualsiasi tipo o membro che è contrassegnato come obsoleto. Si tratta in quanto potrebbero non essere supportata e verranno infine rimosse dalle versioni successive della libreria. Quando un tipo o il membro contrassegnato utilizzando <xref:System.ObsoleteAttribute> viene compilato, la <xref:System.ObsoleteAttribute.Message%2A> proprietà dell'attributo viene visualizzata. In questo modo vengono fornite le informazioni utente sul tipo o sul membro obsoleto. Queste informazioni includono in genere il tempo di tipo obsoleto o membro sarà supportato per le finestre di progettazione di libreria e la sostituzione preferita da usare.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, aggiungere il `message` parametro per il <xref:System.ObsoleteAttribute> costruttore.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola poiché il <xref:System.ObsoleteAttribute.Message%2A> proprietà fornisce informazioni essenziali di tipo o membro obsoleto.

## <a name="example"></a>Esempio
 L'esempio seguente mostra un membro obsoleto che ha dichiarato in modo corretto <xref:System.ObsoleteAttribute>.

 [!code-cpp[FxCop.Design.ObsoleteAttributeOnMember#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.ObsoleteAttributeOnMember/cpp/FxCop.Design.ObsoleteAttributeOnMember.cpp#1)]
 [!code-csharp[FxCop.Design.ObsoleteAttributeOnMember#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ObsoleteAttributeOnMember/cs/FxCop.Design.ObsoleteAttributeOnMember.cs#1)]
 [!code-vb[FxCop.Design.ObsoleteAttributeOnMember#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ObsoleteAttributeOnMember/vb/FxCop.Design.ObsoleteAttributeOnMember.vb#1)]

## <a name="see-also"></a>Vedere anche
 <xref:System.ObsoleteAttribute?displayProperty=fullName>
