---
title: 'CA2227: le proprietà della raccolta devono essere di sola lettura | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2227
- CollectionPropertiesShouldBeReadOnly
helpviewer_keywords:
- CA2227
- CollectionPropertiesShouldBeReadOnly
ms.assetid: 26967aaf-6fbe-438a-b4d3-ac579b5dc0f9
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 17c4e2336a5c8bd8905d857dc8189a11f9fb6181
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85540530"
---
# <a name="ca2227-collection-properties-should-be-read-only"></a>CA2227: Le proprietà di raccolte devono essere in sola lettura
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|CollectionPropertiesShouldBeReadOnly|
|CheckId|CA2227|
|Category|Microsoft. Usage|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Una proprietà scrivibile visibile esternamente è un tipo che implementa <xref:System.Collections.ICollection?displayProperty=fullName> . Le matrici, gli indicizzatori (proprietà con il nome "Item") e i set di autorizzazioni vengono ignorati dalla regola.

## <a name="rule-description"></a>Descrizione della regola
 Una proprietà di raccolta scrivibile consente a un utente di sostituire la raccolta con una raccolta completamente diversa. Una proprietà di sola lettura interrompe la sostituzione della raccolta ma consente ancora l'impostazione dei singoli membri. Se la sostituzione della raccolta è un obiettivo, il modello di progettazione preferito consiste nell'includere un metodo per rimuovere tutti gli elementi dalla raccolta e un metodo per ripopolare la raccolta. <xref:System.Collections.ArrayList.Clear%2A> <xref:System.Collections.ArrayList.AddRange%2A> <xref:System.Collections.ArrayList?displayProperty=fullName> Per un esempio di questo modello, vedere i metodi e della classe.

 Sia la serializzazione binaria che quella XML supportano le proprietà di sola lettura che sono raccolte. La <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> classe presenta requisiti specifici per i tipi che implementano <xref:System.Collections.ICollection> e per <xref:System.Collections.IEnumerable?displayProperty=fullName> essere serializzabili.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, rendere la proprietà di sola lettura e, se richiesto dalla progettazione, aggiungere metodi per cancellare e ripopolare la raccolta.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo con una proprietà di raccolta scrivibile e viene illustrato come la raccolta può essere sostituita direttamente. Viene inoltre illustrato il modo migliore per sostituire una proprietà di raccolta di sola lettura usando i `Clear` `AddRange` metodi e.

 [!code-cpp[FxCop.Usage.PropertiesReturningCollections#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.PropertiesReturningCollections/cpp/FxCop.Usage.PropertiesReturningCollections.cpp#1)]
 [!code-csharp[FxCop.Usage.PropertiesReturningCollections#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.PropertiesReturningCollections/cs/FxCop.Usage.PropertiesReturningCollections.cs#1)]
 [!code-vb[FxCop.Usage.PropertiesReturningCollections#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.PropertiesReturningCollections/vb/FxCop.Usage.PropertiesReturningCollections.vb#1)]

## <a name="related-rules"></a>Regole correlate
 [CA1819: Le proprietà non devono restituire matrici](../code-quality/ca1819-properties-should-not-return-arrays.md)
