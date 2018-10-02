---
title: 'CA1059: I membri non devono esporre tipi concreti specifici | Microsoft Docs'
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
- CA1059
- MembersShouldNotExposeCertainConcreteTypes
helpviewer_keywords:
- MembersShouldNotExposeCertainConcreteTypes
- CA1059
ms.assetid: 59f61f52-8d6c-49cb-aefb-191910523a3c
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 073d55a9a5ae6caa573a2c3db282aaa5e5ea4e57
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2018
ms.locfileid: "47590052"
---
# <a name="ca1059-members-should-not-expose-certain-concrete-types"></a>CA1059: I membri non devono esporre tipi concreti specifici
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [CA1059: i membri non devono esporre tipi concreti specifici](https://docs.microsoft.com/visualstudio/code-quality/ca1059-members-should-not-expose-certain-concrete-types).

|||
|-|-|
|TypeName|MembersShouldNotExposeCertainConcreteTypes|
|CheckId|CA1059|
|Category|Microsoft.Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un membro visibile esternamente è un certo tipo concreto o espone tipi concreti specifici tramite uno dei relativi parametri o valore restituito. Attualmente, questa regola segnala l'esposizione dei tipi concreti seguenti:

-   Un tipo derivato da <xref:System.Xml.XmlNode?displayProperty=fullName>.

## <a name="rule-description"></a>Descrizione della regola
 Un tipo concreto è un tipo con implementazione completa, pertanto è possibile crearne un'istanza. Per consentire un utilizzo esteso del membro, sostituire il tipo concreto con l'interfaccia suggerita. In questo modo il membro accettare qualsiasi tipo che implementa l'interfaccia oppure essere usato in cui è previsto un tipo che implementa l'interfaccia.

 La tabella seguente elenca i tipi concreti di destinazione e le relative sostituzioni consigliate.

|Tipo concreto|Sostituzione|
|-------------------|-----------------|
|<xref:System.Xml.XPath.XPathDocument>|<xref:System.Xml.XPath.IXPathNavigable?displayProperty=fullName>.<br /><br /> Tramite l'interfaccia consente di disaccoppiare il membro da un'implementazione specifica di un'origine dati XML.|

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, modificare il tipo concreto per l'interfaccia suggerita.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un messaggio da questa regola se la funzionalità specifica fornita dal tipo concreto è obbligatorio.

## <a name="related-rules"></a>Regole correlate
 [CA1011: Considerare il passaggio di tipi di base come parametri](../code-quality/ca1011-consider-passing-base-types-as-parameters.md)



