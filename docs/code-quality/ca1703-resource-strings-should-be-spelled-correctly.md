---
title: 'CA1703: Le stringhe di risorsa devono essere digitate correttamente'
ms.date: 03/28/2018
ms.topic: reference
f1_keywords:
- ResourceStringsShouldBeSpelledCorrectly
- CA1703
helpviewer_keywords:
- CA1703
- ResourceStringsShouldBeSpelledCorrectly
ms.assetid: 693f4970-f512-40cb-ae3b-a0f3a5c6d6f1
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2643ff7cb8ce401462be7e5c1e52d5f985896f3a
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55915726"
---
# <a name="ca1703-resource-strings-should-be-spelled-correctly"></a>CA1703: Le stringhe di risorsa devono essere digitate correttamente

|||
|-|-|
|TypeName|ResourceStringsShouldBeSpelledCorrectly|
|CheckId|CA1703|
|Category|Microsoft.Naming|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa

Una stringa di risorsa contiene una o più parole che non sono riconosciute dalla libreria del correttore ortografico Microsoft.

## <a name="rule-description"></a>Descrizione della regola

Questa regola analizza la stringa di risorsa in parole (suddivisione in token le parole composte) e controlla l'ortografia di ciascuna parola/token. Per informazioni sull'algoritmo di analisi, vedere [CA1704: Gli identificatori devono essere digitati correttamente](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, usare parole complete che siano state digitate correttamente o aggiungere le parole in un dizionario personalizzato. Per informazioni su come usare i dizionari personalizzati, vedere [CA1704: Gli identificatori devono essere digitati correttamente](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

## <a name="change-the-dictionary-language"></a>Modificare la lingua di dizionario

Per impostazione predefinita, viene utilizzata la versione inglese (en) del correttore ortografico. Se si desidera modificare la lingua del correttore ortografico, è possibile farlo mediante l'aggiunta di uno dei seguenti attributi per il *AssemblyInfo.cs* oppure *AssemblyInfo* file:

- Usare <xref:System.Reflection.AssemblyCultureAttribute> specificare le impostazioni cultura, se le risorse si trovano in un assembly satellite.
- Uso <xref:System.Resources.NeutralResourcesLanguageAttribute> per specificare il *delle impostazioni cultura neutre* dell'assembly se le risorse sono nello stesso assembly del codice.

> [!IMPORTANT]
> Se si imposta le impostazioni cultura su un valore qualsiasi diverso da una cultura basata su inglese, questa regola di analisi del codice viene disabilitata automaticamente.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

Non escludere un avviso da questa regola. Parole formulate correttamente riducono il tempo necessario per l'apprendimento di nuove librerie software.

## <a name="related-rules"></a>Regole correlate

- [CA1701: Le parole composte di stringa di risorsa devono essere digitate correttamente](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)
- [CA1704: Gli identificatori devono essere digitati correttamente](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)
- [CA2204: Valori letterali devono essere digitati correttamente](../code-quality/ca2204-literals-should-be-spelled-correctly.md)