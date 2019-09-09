---
title: 'CA1058: I tipi non devono estendere tipi di base specifici'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- TypesShouldNotExtendCertainBaseTypes
- CA1058
helpviewer_keywords:
- CA1058
- TypesShouldNotExtendCertainBaseTypes
ms.assetid: 8446ee40-beb1-49fa-8733-4d8e813471c0
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 38d92194a5aa2b46a0cb65a1525bc01d9de67b86
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547364"
---
# <a name="ca1058-types-should-not-extend-certain-base-types"></a>CA1058: I tipi non devono estendere tipi di base specifici

|||
|-|-|
|TypeName|TypesShouldNotExtendCertainBaseTypes|
|CheckId|CA1058|
|Category|Microsoft.Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa

Un tipo estende uno dei tipi di base seguenti:

- <xref:System.ApplicationException?displayProperty=fullName>
- <xref:System.Xml.XmlDocument?displayProperty=fullName>
- <xref:System.Collections.CollectionBase?displayProperty=fullName>
- <xref:System.Collections.DictionaryBase?displayProperty=fullName>
- <xref:System.Collections.Queue?displayProperty=fullName>
- <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>
- <xref:System.Collections.SortedList?displayProperty=fullName>
- <xref:System.Collections.Stack?displayProperty=fullName>

Per impostazione predefinita, questa regola esamina solo i tipi visibili esternamente, ma è [configurabile](#configurability).

## <a name="rule-description"></a>Descrizione della regola

<xref:System.Exception?displayProperty=fullName> Le<xref:System> eccezioni devono derivare da o da una delle relative sottoclassi nello spazio dei nomi.

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

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

Non eliminare un avviso da questa regola per violazioni relative <xref:System.ApplicationException>a. È possibile eliminare un avviso da questa regola per le violazioni relative <xref:System.Xml.XmlDocument>a. Se il codice è stato rilasciato in precedenza, è possibile evitare l'eliminazione di un avviso relativo a una raccolta non generica.

## <a name="configurability"></a>Configurabilità

Se questa regola viene eseguita da [analizzatori FxCop](install-fxcop-analyzers.md) (e non con analisi legacy), è possibile configurare le parti della codebase su cui eseguire questa regola, in base all'accessibilità. Ad esempio, per specificare che la regola deve essere eseguita solo sulla superficie dell'API non pubblica, aggiungere la coppia chiave-valore seguente a un file con estensione EditorConfig nel progetto:

```ini
dotnet_code_quality.ca1058.api_surface = private, internal
```

È possibile configurare questa opzione solo per questa regola, per tutte le regole o per tutte le regole in questa categoria (progettazione). Per altre informazioni, vedere [configurare gli analizzatori FxCop](configure-fxcop-analyzers.md).