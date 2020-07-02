---
title: 'CA1059: i membri non devono esporre tipi concreti specifici | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1059
- MembersShouldNotExposeCertainConcreteTypes
helpviewer_keywords:
- MembersShouldNotExposeCertainConcreteTypes
- CA1059
ms.assetid: 59f61f52-8d6c-49cb-aefb-191910523a3c
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 792426615dd78241ade1d38a24ec1f4d5702cede
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545379"
---
# <a name="ca1059-members-should-not-expose-certain-concrete-types"></a>CA1059: I membri non devono esporre tipi concreti specifici
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|MembersShouldNotExposeCertainConcreteTypes|
|CheckId|CA1059|
|Category|Microsoft. Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un membro visibile esternamente è un determinato tipo concreto o espone determinati tipi concreti tramite uno dei relativi parametri o valori restituiti. Attualmente questa regola segnala l'esposizione dei tipi concreti seguenti:

- Tipo derivato dall'oggetto <xref:System.Xml.XmlNode?displayProperty=fullName>.

## <a name="rule-description"></a>Descrizione della regola
 Un tipo concreto è un tipo con implementazione completa, pertanto è possibile crearne un'istanza. Per consentire un uso generalizzato del membro, sostituire il tipo concreto con l'interfaccia suggerita. In questo modo il membro può accettare qualsiasi tipo che implementa l'interfaccia o essere utilizzato quando è previsto un tipo che implementa l'interfaccia.

 Nella tabella seguente sono elencati i tipi concreti di destinazione e le sostituzioni consigliate.

|Tipo concreto|Sostituzione|
|-------------------|-----------------|
|<xref:System.Xml.XPath.XPathDocument>|<xref:System.Xml.XPath.IXPathNavigable?displayProperty=fullName>.<br /><br /> L'utilizzo dell'interfaccia separa il membro da un'implementazione specifica di un'origine dati XML.|

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, modificare il tipo concreto nell'interfaccia consigliata.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un messaggio da questa regola in modo sicuro se è necessaria la funzionalità specifica fornita dal tipo concreto.

## <a name="related-rules"></a>Regole correlate
 [CA1011: Provare a passare tipi di base come parametri](../code-quality/ca1011-consider-passing-base-types-as-parameters.md)
