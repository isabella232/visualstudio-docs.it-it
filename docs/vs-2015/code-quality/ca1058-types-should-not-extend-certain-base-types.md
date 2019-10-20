---
title: 'CA1058: i tipi non devono estendere determinati tipi di base | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- TypesShouldNotExtendCertainBaseTypes
- CA1058
helpviewer_keywords:
- CA1058
- TypesShouldNotExtendCertainBaseTypes
ms.assetid: 8446ee40-beb1-49fa-8733-4d8e813471c0
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 9a4663fe3bc09b27bad9eeec05e325f07a3de6f3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72603058"
---
# <a name="ca1058-types-should-not-extend-certain-base-types"></a>CA1058: I tipi non devono estendere tipi di base specifici
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TypesShouldNotExtendCertainBaseTypes|
|CheckId|CA1058|
|Category|Microsoft. Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un tipo visibile esternamente estende tipi di base specifici. Attualmente questa regola segnala i tipi che derivano dai tipi seguenti:

- <xref:System.ApplicationException?displayProperty=fullName>

- <xref:System.Xml.XmlDocument?displayProperty=fullName>

- <xref:System.Collections.CollectionBase?displayProperty=fullName>

- <xref:System.Collections.DictionaryBase?displayProperty=fullName>

- <xref:System.Collections.Queue?displayProperty=fullName>

- <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>

- <xref:System.Collections.SortedList?displayProperty=fullName>

- <xref:System.Collections.Stack?displayProperty=fullName>

## <a name="rule-description"></a>Descrizione della regola
 Per [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] versione 1, è consigliabile derivare nuove eccezioni da <xref:System.ApplicationException>. La raccomandazione è stata modificata e le nuove eccezioni dovrebbero derivare da <xref:System.Exception?displayProperty=fullName> o una delle relative sottoclassi nello spazio dei nomi <xref:System>.

 Non creare una sottoclasse di <xref:System.Xml.XmlDocument> se si desidera creare una vista XML di un modello a oggetti sottostante o di un'origine dati.

### <a name="non-generic-collections"></a>Raccolte non generiche
 Quando possibile, utilizzare e/o estendere le raccolte generiche. Non estendere le raccolte non generiche nel codice, a meno che non sia stato spedito in precedenza.

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
 Per correggere una violazione di questa regola, derivare il tipo da un diverso tipo di base o da una raccolta generica.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non eliminare un avviso da questa regola per violazioni circa <xref:System.ApplicationException>. È possibile eliminare un avviso da questa regola per eventuali violazioni circa <xref:System.Xml.XmlDocument>. Se il codice è stato rilasciato in precedenza, è possibile evitare l'eliminazione di un avviso relativo a una raccolta non generica.
