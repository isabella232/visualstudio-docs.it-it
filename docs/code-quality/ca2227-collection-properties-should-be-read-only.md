---
title: 'CA2227: Le proprietà di raccolte devono essere in sola lettura'
ms.date: 09/28/2018
ms.topic: reference
f1_keywords:
- CA2227
- CollectionPropertiesShouldBeReadOnly
helpviewer_keywords:
- CA2227
- CollectionPropertiesShouldBeReadOnly
ms.assetid: 26967aaf-6fbe-438a-b4d3-ac579b5dc0f9
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.openlocfilehash: 8a6ced277aa442450418ce55f4e1db56ad5d8af1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62806537"
---
# <a name="ca2227-collection-properties-should-be-read-only"></a>CA2227: Le proprietà di raccolte devono essere in sola lettura

|||
|-|-|
|TypeName|CollectionPropertiesShouldBeReadOnly|
|CheckId|CA2227|
|Category|Microsoft.Usage|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa

È una proprietà scrivibile, visibile esternamente di un tipo che implementa <xref:System.Collections.ICollection?displayProperty=fullName>. Questa regola ignora le matrici, gli indicizzatori (proprietà con il nome 'Item') e i set di autorizzazioni.

## <a name="rule-description"></a>Descrizione della regola

Una proprietà di raccolta scrivibile consente a un utente di sostituire la raccolta con una raccolta completamente diversa. Una proprietà di sola lettura interrompe la sostituzione della raccolta, ma consente ancora i singoli membri da impostare. Se la sostituzione della raccolta è un obiettivo, lo schema progettuale preferito è possibile includere un metodo per rimuovere tutti gli elementi dalla raccolta e un metodo per ripopolare la raccolta. Vedere le <xref:System.Collections.ArrayList.Clear%2A> e <xref:System.Collections.ArrayList.AddRange%2A> metodi del <xref:System.Collections.ArrayList?displayProperty=fullName> per un esempio di questo modello di classe.

La serializzazione XML e binaria supportano le proprietà di sola lettura che vengono raccolte. Il <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> classe presenta requisiti specifici per i tipi che implementano <xref:System.Collections.ICollection> e <xref:System.Collections.IEnumerable?displayProperty=fullName> per poter essere serializzabili.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, impostare la proprietà di sola lettura. Se la struttura richiede, aggiungere i metodi per cancellare e ripopolare la raccolta.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

È possibile eliminare l'avviso se la proprietà fa parte di un [i dati oggetto di trasferimento](/previous-versions/msp-n-p/ff649585(v=pandp.10)) classe.

In caso contrario, non eliminare gli avvisi da questa regola.

## <a name="example"></a>Esempio

Nell'esempio seguente viene illustrato un tipo con una proprietà di raccolta scrivibile e Mostra come la raccolta può essere sostituita direttamente. Inoltre, viene spiegato il modo preferito di sostituzione di una proprietà di raccolta di sola lettura usando `Clear` e `AddRange` metodi.

[!code-csharp[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/CSharp/ca2227-collection-properties-should-be-read-only_1.cs)]
[!code-vb[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/VisualBasic/ca2227-collection-properties-should-be-read-only_1.vb)]
[!code-cpp[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/CPP/ca2227-collection-properties-should-be-read-only_1.cpp)]

## <a name="related-rules"></a>Regole correlate

- [CA1819: Proprietà non devono restituire matrici](../code-quality/ca1819-properties-should-not-return-arrays.md)