---
title: 'CA1018: contrassegnare gli attributi con AttributeUsageAttribute | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1018
- MarkAttributesWithAttributeUsage
helpviewer_keywords:
- CA1018
- MarkAttributesWithAttributeUsage
ms.assetid: 6ab70ec0-220f-4880-af31-45067703133c
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 256fc281b27c483f1dda0317f7d2695fa36c47f8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85535057"
---
# <a name="ca1018-mark-attributes-with-attributeusageattribute"></a>CA1018: Contrassegnare gli attributi con AttributeUsageAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|MarkAttributesWithAttributeUsage|
|CheckId|CA1018|
|Category|Microsoft. Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 L' <xref:System.AttributeUsageAttribute?displayProperty=fullName> attributo non è presente nell'attributo personalizzato.

## <a name="rule-description"></a>Descrizione della regola
 Quando si definisce un attributo personalizzato, contrassegnarlo utilizzando <xref:System.AttributeUsageAttribute> per indicare la posizione del codice sorgente a cui è possibile applicare l'attributo personalizzato. Il significato e l'utilizzo previsto di un attributo ne determinano le posizioni valide nel codice. È possibile, ad esempio, definire un attributo che identifichi la persona responsabile della gestione e del miglioramento di ogni tipo in una libreria e che la responsabilità venga sempre assegnata a livello di tipo. In questo caso, i compilatori devono abilitare l'attributo su classi, enumerazioni e interfacce, ma non devono abilitarlo su metodi, eventi o proprietà. I criteri e le procedure aziendali stabiliscono se l'attributo deve essere abilitato negli assembly.

 L' <xref:System.AttributeTargets?displayProperty=fullName> enumerazione definisce le destinazioni che è possibile specificare per un attributo personalizzato. Se si omette <xref:System.AttributeUsageAttribute> , l'attributo personalizzato sarà valido per tutte le destinazioni, come definito dal `All` valore di <xref:System.AttributeTargets> Enumeration.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, specificare le destinazioni per l'attributo tramite <xref:System.AttributeUsageAttribute> . Vedere l'esempio seguente.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È necessario correggere una violazione di questa regola anziché escludere il messaggio. Anche se l'attributo eredita <xref:System.AttributeUsageAttribute> , l'attributo deve essere presente per semplificare la manutenzione del codice.

## <a name="example"></a>Esempio
 Nell'esempio seguente vengono definiti due attributi. `BadCodeMaintainerAttribute` omette erroneamente l' <xref:System.AttributeUsageAttribute> istruzione e `GoodCodeMaintainerAttribute` implementa correttamente l'attributo descritto in precedenza in questa sezione. Si noti che la proprietà `DeveloperName` è richiesta dalle funzioni di accesso della regola di progettazione [CA1019: define per gli argomenti dell'attributo](../code-quality/ca1019-define-accessors-for-attribute-arguments.md) ed è inclusa per completezza.

 [!code-csharp[FxCop.Design.AttributeUsage#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeUsage/cs/FxCop.Design.AttributeUsage.cs#1)]
 [!code-vb[FxCop.Design.AttributeUsage#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeUsage/vb/FxCop.Design.AttributeUsage.vb#1)]

## <a name="related-rules"></a>Regole correlate
 [CA1019: Definire le funzioni di accesso per gli argomenti degli attributi](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)

 [CA1813: Evitare attributi unsealed](../code-quality/ca1813-avoid-unsealed-attributes.md)

## <a name="see-also"></a>Vedere anche
 [Attributes (Attributi)](https://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b)
