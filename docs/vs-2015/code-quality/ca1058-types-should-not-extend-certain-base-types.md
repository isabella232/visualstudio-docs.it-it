---
title: 'CA1058: I tipi non devono estendere tipi di base specifici | Microsoft Docs'
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
- TypesShouldNotExtendCertainBaseTypes
- CA1058
helpviewer_keywords:
- CA1058
- TypesShouldNotExtendCertainBaseTypes
ms.assetid: 8446ee40-beb1-49fa-8733-4d8e813471c0
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: d4eb5b13813ca8bf06a64c638f399186a88a17c4
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589192"
---
# <a name="ca1058-types-should-not-extend-certain-base-types"></a>CA1058: I tipi non devono estendere tipi di base specifici
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [CA1058: i tipi non devono estendere tipi di base specifici](https://docs.microsoft.com/visualstudio/code-quality/ca1058-types-should-not-extend-certain-base-types).

|||
|-|-|
|TypeName|TypesShouldNotExtendCertainBaseTypes|
|CheckId|CA1058|
|Category|Microsoft.Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un tipo visibile esternamente estende tipi di base specifici. Attualmente, questa regola segnala i tipi che derivano dai tipi seguenti:

-   <xref:System.ApplicationException?displayProperty=fullName>

-   <xref:System.Xml.XmlDocument?displayProperty=fullName>

-   <xref:System.Collections.CollectionBase?displayProperty=fullName>

-   <xref:System.Collections.DictionaryBase?displayProperty=fullName>

-   <xref:System.Collections.Queue?displayProperty=fullName>

-   <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>

-   <xref:System.Collections.SortedList?displayProperty=fullName>

-   <xref:System.Collections.Stack?displayProperty=fullName>

## <a name="rule-description"></a>Descrizione della regola
 Per la [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] versione 1, era consigliabile derivare nuove eccezioni da <xref:System.ApplicationException>. La raccomandazione è stato modificato e nuove eccezioni devono derivare da <xref:System.Exception?displayProperty=fullName> o una delle sue sottoclassi nel <xref:System> dello spazio dei nomi.

 Non creare una sottoclasse di <xref:System.Xml.XmlDocument> se si desidera creare una vista XML di un'origine dati o del modello di oggetto sottostante.

### <a name="non-generic-collections"></a>Raccolte non generiche
 Usare e/o di estendere le raccolte generiche, laddove possibile. Non si estendono le raccolte non generiche nel codice, a meno che non sono stati inviati in precedenza.

 **Esempi di utilizzo non corretto**

```csharp
public class MyCollection : CollectionBase
{
}

public class MyReadOnlyCollection : ReadOnlyCollectionBase
{
}
```

 **Esempi di utilizzo corretto**

```csharp
public class MyCollection : Collection<T>
{
}

public class MyReadOnlyCollection : ReadOnlyCollection<T>
{
}
```

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, derivare il tipo da un tipo di base diverso o una raccolta generica.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non eliminare un avviso da questa regola per le violazioni sulle <xref:System.ApplicationException>. È possibile eliminare un avviso da questa regola per le violazioni su <xref:System.Xml.XmlDocument>. È possibile eliminare un avviso relativo a una raccolta non generiche se il codice è stato rilasciato in precedenza.



