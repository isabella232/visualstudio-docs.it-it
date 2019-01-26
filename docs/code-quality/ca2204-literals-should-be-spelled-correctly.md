---
title: 'CA2204: I valori letterali devono essere digitati correttamente'
ms.date: 03/28/2018
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- Literals should be spelled correctly
- CA2204
- LiteralsShouldBeSpelledCorrectly
helpviewer_keywords:
- CA2204
ms.assetid: b0bbcbb6-c92d-4c14-8ef7-9c8b38c791a6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 62ad30516720a843d519a9e514cd325a957b3cff
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55017123"
---
# <a name="ca2204-literals-should-be-spelled-correctly"></a>CA2204: I valori letterali devono essere digitati correttamente

|||
|-|-|
|TypeName|LiteralsShouldBeSpelledCorrectly|
|CheckId|CA2204|
|Category|Microsoft.Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa

Una valore letterale stringa viene passata come argomento per un parametro localizzabile, o a una proprietà localizzabile e la stringa contiene uno o più parole che non sono riconosciute dalla libreria del correttore ortografico Microsoft.

## <a name="rule-description"></a>Descrizione della regola

Questa regola consente di controllare una stringa letterale che viene passata come un valore per un parametro o una proprietà quando per uno o più delle seguenti condizioni sono true:

- Il <xref:System.ComponentModel.LocalizableAttribute> attributi del parametro o della proprietà sono impostato su true.

- Il nome di parametro o una proprietà contiene "Text", "Messaggio" o "Caption".

- Il nome della variabile di stringa che viene passato a un <xref:System.Console.Write%2A> o <xref:System.Console.WriteLine> è "value" o "format".

Questa regola analizza la stringa letterale in parole, suddivisione in token le parole composte e controlla l'ortografia di ogni parola o il token. Per informazioni sull'algoritmo di analisi, vedere [CA1704: Gli identificatori devono essere digitati correttamente](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

## <a name="language"></a>Linguaggio

Il correttore ortografico attualmente verifica solo a dizionari le impostazioni cultura basate su inglese. È possibile modificare le impostazioni cultura del progetto nel file di progetto, aggiungendo il **CodeAnalysisCulture** elemento.

Ad esempio:

```xml
<Project ...>
  <PropertyGroup>
    <CodeAnalysisCulture>en-AU</CodeAnalysisCulture>
```

> [!IMPORTANT]
> Se si imposta le impostazioni cultura su un valore qualsiasi diverso da una cultura basata su inglese, questa regola di analisi del codice viene disabilitata automaticamente.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, correggere l'ortografia del termine o aggiungere la parola al dizionario personalizzato. Per informazioni su come usare i dizionari personalizzati, vedere [come: Personalizzare il dizionario di analisi codice](../code-quality/how-to-customize-the-code-analysis-dictionary.md).

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

Non escludere un avviso da questa regola. Correttamente ortografia consente di ridurre la curva di apprendimento necessaria per le nuove librerie software.

## <a name="related-rules"></a>Regole correlate

- [CA1704: Gli identificatori devono essere digitati correttamente](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)
- [CA1703: Le stringhe di risorsa devono essere digitate correttamente](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)