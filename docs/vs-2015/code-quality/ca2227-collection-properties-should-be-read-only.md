---
title: 'CA2227: Le proprietà della raccolta devono essere di sola lettura | Microsoft Docs'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 3182a254ed5e22c560523911f87dc852708a9eb1
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58967557"
---
# <a name="ca2227-collection-properties-should-be-read-only"></a>CA2227: Le proprietà di raccolte devono essere in sola lettura
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|CollectionPropertiesShouldBeReadOnly|
|CheckId|CA2227|
|Category|Microsoft.Usage|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Una proprietà scrivibile visibile esternamente è un tipo che implementa <xref:System.Collections.ICollection?displayProperty=fullName>. Le matrici, gli indicizzatori (proprietà con il nome 'Item') e i set di autorizzazioni vengono ignorati dalla regola.

## <a name="rule-description"></a>Descrizione della regola
 Una proprietà di raccolta scrivibile consente a un utente di sostituire la raccolta con una raccolta completamente diversa. Una proprietà di sola lettura interrompe la sostituzione della raccolta ma consente ancora l'impostazione dei singoli membri. Se la sostituzione della raccolta è un obiettivo, lo schema progettuale preferito è includere un metodo per rimuovere tutti gli elementi dalla raccolta e un metodo per popolare nuovamente la raccolta. Vedere le <xref:System.Collections.ArrayList.Clear%2A> e <xref:System.Collections.ArrayList.AddRange%2A> metodi del <xref:System.Collections.ArrayList?displayProperty=fullName> per un esempio di questo modello di classe.

 La serializzazione XML e binaria supportano le proprietà di sola lettura che vengono raccolte. Il <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> classe presenta requisiti specifici per i tipi che implementano <xref:System.Collections.ICollection> e <xref:System.Collections.IEnumerable?displayProperty=fullName> per poter essere serializzabili.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, impostare la proprietà di sola lettura e, se richiede la progettazione, aggiungere i metodi per cancellare e ripopolare la raccolta.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo con una proprietà di raccolta scrivibile e Mostra come la raccolta può essere sostituita direttamente. Inoltre, il modo preferito di sostituzione di una proprietà di raccolta di sola lettura usando `Clear` e `AddRange` metodi viene visualizzato.

 [!code-cpp[FxCop.Usage.PropertiesReturningCollections#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.PropertiesReturningCollections/cpp/FxCop.Usage.PropertiesReturningCollections.cpp#1)]
 [!code-csharp[FxCop.Usage.PropertiesReturningCollections#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.PropertiesReturningCollections/cs/FxCop.Usage.PropertiesReturningCollections.cs#1)]
 [!code-vb[FxCop.Usage.PropertiesReturningCollections#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.PropertiesReturningCollections/vb/FxCop.Usage.PropertiesReturningCollections.vb#1)]

## <a name="related-rules"></a>Regole correlate
 [CA1819: Proprietà non devono restituire matrici](../code-quality/ca1819-properties-should-not-return-arrays.md)
