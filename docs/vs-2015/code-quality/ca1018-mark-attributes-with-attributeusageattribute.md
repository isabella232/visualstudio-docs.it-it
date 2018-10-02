---
title: 'CA1018: Contrassegnare gli attributi con AttributeUsageAttribute | Microsoft Docs'
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
- CA1018
- MarkAttributesWithAttributeUsage
helpviewer_keywords:
- CA1018
- MarkAttributesWithAttributeUsage
ms.assetid: 6ab70ec0-220f-4880-af31-45067703133c
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: bfb9e7d954697fab554749dbd42155f92030ce88
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589285"
---
# <a name="ca1018-mark-attributes-with-attributeusageattribute"></a>CA1018: Contrassegnare gli attributi con AttributeUsageAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [CA1018: contrassegnare gli attributi con AttributeUsageAttribute](https://docs.microsoft.com/visualstudio/code-quality/ca1018-mark-attributes-with-attributeusageattribute).

|||
|-|-|
|TypeName|MarkAttributesWithAttributeUsage|
|CheckId|CA1018|
|Category|Microsoft.Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Il <xref:System.AttributeUsageAttribute?displayProperty=fullName> attributo non è presente nell'attributo personalizzato.

## <a name="rule-description"></a>Descrizione della regola
 Quando si definisce un attributo personalizzato, contrassegnarlo tramite <xref:System.AttributeUsageAttribute> per indicare la posizione nel codice sorgente può essere applicato l'attributo personalizzato. Il significato e l'utilizzo previsto di un attributo ne determinano le posizioni valide nel codice. Ad esempio, si potrebbe definire un attributo che identifica la persona responsabile della manutenzione e miglioramento di ogni tipo in una libreria, e che responsabilità viene sempre assegnata a livello di tipo. In questo caso, i compilatori devono abilitare l'attributo su classi, enumerazioni e le interfacce, ma non consigliabile abilitarlo in metodi, eventi o proprietà. Le procedure e i criteri dell'organizzazione indicano se l'attributo deve essere abilitato su assembly.

 Il <xref:System.AttributeTargets?displayProperty=fullName> enumerazione definisce le destinazioni che è possibile specificare per un attributo personalizzato. Se si omette <xref:System.AttributeUsageAttribute>, l'attributo personalizzato sarà valido per tutte le destinazioni, come definito per il `All` pari a <xref:System.AttributeTargets> enumerazione.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, specificare le destinazioni per l'attributo utilizzando <xref:System.AttributeUsageAttribute>. Vedere l'esempio seguente.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È necessario correggere una violazione di questa regola invece di escludere il messaggio. Anche se l'attributo eredita <xref:System.AttributeUsageAttribute>, l'attributo deve essere presente per semplificare la manutenzione del codice.

## <a name="example"></a>Esempio
 L'esempio seguente definisce due attributi. `BadCodeMaintainerAttribute` in modo non corretto vengono omessi il <xref:System.AttributeUsageAttribute> istruzione e `GoodCodeMaintainerAttribute` implementa correttamente l'attributo che è descritti in precedenza in questa sezione. Si noti che la proprietà `DeveloperName` è richiesto dalla regola di progettazione [CA1019: definire funzioni di accesso per gli argomenti degli attributi](../code-quality/ca1019-define-accessors-for-attribute-arguments.md) ed è incluso per motivi di completezza.

 [!code-csharp[FxCop.Design.AttributeUsage#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeUsage/cs/FxCop.Design.AttributeUsage.cs#1)]
 [!code-vb[FxCop.Design.AttributeUsage#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeUsage/vb/FxCop.Design.AttributeUsage.vb#1)]

## <a name="related-rules"></a>Regole correlate
 [CA1019: Definire le funzioni di accesso per gli argomenti degli attributi](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)

 [CA1813: Evitare attributi non sealed](../code-quality/ca1813-avoid-unsealed-attributes.md)

## <a name="see-also"></a>Vedere anche
 [Attributi](http://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b)



