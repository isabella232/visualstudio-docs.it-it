---
title: 'CA2204: I valori letterali devono essere digitati correttamente'
ms.date: 03/28/2018
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
ms.openlocfilehash: 6763fd9f8999bd590511026f6571db6a747c43bc
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231853"
---
# <a name="ca2204-literals-should-be-spelled-correctly"></a>CA2204: I valori letterali devono essere digitati correttamente

|||
|-|-|
|TypeName|LiteralsShouldBeSpelledCorrectly|
|CheckId|CA2204|
|Category|Microsoft.Usage|
|Modifica|Senza interruzioni|

## <a name="cause"></a>Causa

Una stringa letterale viene passata come argomento per un parametro localizzabile o a una proprietà localizzabile e la stringa contiene una o più parole che non sono riconosciute dalla libreria del correttore ortografico Microsoft.

## <a name="rule-description"></a>Descrizione della regola

Questa regola consente di controllare una stringa letterale passata come valore a un parametro o a una proprietà quando uno o più dei seguenti casi è true:

- L' <xref:System.ComponentModel.LocalizableAttribute> attributo del parametro o della proprietà è impostato su true.

- Il nome del parametro o della proprietà contiene "Text", "message" o "Caption".

- Il nome della variabile stringa passata a un <xref:System.Console.Write%2A> metodo o <xref:System.Console.WriteLine> è "value" o "Format".

Questa regola analizza la stringa letterale in parole, suddivisione in token parole composte e controlla l'ortografia di ogni parola o token. Per informazioni sull'algoritmo di analisi, vedere [CA1704: Gli identificatori devono essere digitati correttamente](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

## <a name="language"></a>Linguaggio

Il controllo ortografico attualmente controlla solo i dizionari delle impostazioni cultura in lingua inglese. È possibile modificare le impostazioni cultura del progetto nel file di progetto aggiungendo l'elemento **CodeAnalysisCulture** .

Ad esempio:

```xml
<Project ...>
  <PropertyGroup>
    <CodeAnalysisCulture>en-AU</CodeAnalysisCulture>
```

> [!IMPORTANT]
> Se si impostano le impostazioni cultura su un valore diverso da una lingua inglese, questa regola di analisi del codice viene disabilitata automaticamente.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, correggere l'ortografia della parola o aggiungere la parola a un dizionario personalizzato. Per informazioni sull'uso dei dizionari personalizzati, vedere [procedura: Personalizzare il dizionario](../code-quality/how-to-customize-the-code-analysis-dictionary.md)di analisi del codice.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

Non escludere un avviso da questa regola. Le parole con ortografia corretta riducono la curva di apprendimento necessaria per le nuove librerie software.

## <a name="related-rules"></a>Regole correlate

- [CA1704: Gli identificatori devono essere digitati correttamente](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)
- [CA1703 Le stringhe di risorsa devono essere digitate correttamente](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)