---
title: 'CA1813: evitare attributi non sealed | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1813
- AvoidUnsealedAttributes
helpviewer_keywords:
- CA1813
- AvoidUnsealedAttributes
ms.assetid: f5e31b4c-9f8b-49e1-a2a8-bb5f1140729a
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8d86f4a9ecbdfff451fed21f93c0fe6a7679d471
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543949"
---
# <a name="ca1813-avoid-unsealed-attributes"></a>CA1813: Evitare attributi unsealed
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|AvoidUnsealedAttributes|
|CheckId|CA1813|
|Category|Microsoft. performance|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un tipo pubblico eredita da <xref:System.Attribute?displayProperty=fullName> , non è astratto e non è sealed ( `NotInheritable` in Visual Basic).

## <a name="rule-description"></a>Descrizione della regola
 La libreria di classi [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] fornisce metodi per recuperare attributi personalizzati. Per impostazione predefinita, questi metodi cercano la gerarchia di ereditarietà dell'attributo; ad esempio <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=fullName> , Cerca il tipo di attributo specificato o qualsiasi tipo di attributo che estende il tipo di attributo specificato. La chiusura dell'attributo elimina la ricerca attraverso la gerarchia di ereditarietà e può migliorare le prestazioni.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, bloccare il tipo di attributo o renderlo astratto.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola in modo sicuro. È consigliabile eseguire questa operazione solo se si definisce una gerarchia dell'attributo e non è possibile bloccare l'attributo o renderlo astratto.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un attributo personalizzato che soddisfa questa regola.

 [!code-csharp[FxCop.Performance.AttributesSealed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.AttributesSealed/cs/FxCop.Performance.AttributesSealed.cs#1)]
 [!code-vb[FxCop.Performance.AttributesSealed#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.AttributesSealed/vb/FxCop.Performance.AttributesSealed.vb#1)]

## <a name="related-rules"></a>Regole correlate
 [CA1019: Definire le funzioni di accesso per gli argomenti degli attributi](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)

 [CA1018: Contrassegnare gli attributi con AttributeUsageAttribute](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)

## <a name="see-also"></a>Vedere anche
 [Attributes (Attributi)](https://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b)
