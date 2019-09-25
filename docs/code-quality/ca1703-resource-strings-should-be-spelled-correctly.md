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
ms.openlocfilehash: edd3945953a07b10aee5c2690a25aafe446e2c10
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234319"
---
# <a name="ca1703-resource-strings-should-be-spelled-correctly"></a>CA1703: Le stringhe di risorsa devono essere digitate correttamente

|||
|-|-|
|TypeName|ResourceStringsShouldBeSpelledCorrectly|
|CheckId|CA1703|
|Category|Microsoft.Naming|
|Modifica|Senza interruzioni|

## <a name="cause"></a>Causa

Una stringa di risorsa contiene una o più parole che non sono riconosciute dalla libreria del correttore ortografico Microsoft.

## <a name="rule-description"></a>Descrizione della regola

Questa regola analizza la stringa di risorsa in parole (parole composte suddivisione in token) e controlla l'ortografia di ogni parola/token. Per informazioni sull'algoritmo di analisi, vedere [CA1704: Gli identificatori devono essere digitati correttamente](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, usare parole complete che sono state digitate correttamente o aggiungere parole a un dizionario personalizzato. Per informazioni sull'uso dei dizionari personalizzati, vedere [CA1704: Gli identificatori devono essere digitati correttamente](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

## <a name="change-the-dictionary-language"></a>Modificare la lingua del dizionario

Per impostazione predefinita, viene utilizzata la versione inglese (en) del correttore ortografico. Se si desidera modificare la lingua del correttore ortografico, è possibile aggiungere uno degli attributi seguenti al file *AssemblyInfo.cs* o *AssemblyInfo. vb* :

- Usare <xref:System.Reflection.AssemblyCultureAttribute> per specificare le impostazioni cultura se le risorse si trovano in un assembly satellite.
- Usare <xref:System.Resources.NeutralResourcesLanguageAttribute> per specificare le *impostazioni cultura non associate ad alcun paese* dell'assembly se le risorse si trovano nello stesso assembly del codice.

> [!IMPORTANT]
> Se si impostano le impostazioni cultura su un valore diverso da una lingua inglese, questa regola di analisi del codice viene disabilitata automaticamente.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

Non escludere un avviso da questa regola. Le parole con ortografia corretta consentono di ridurre il tempo necessario per apprendere nuove librerie software.

## <a name="related-rules"></a>Regole correlate

- [CA1701 Le parole composte della stringa di risorsa devono essere configurate correttamente](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)
- [CA1704: Gli identificatori devono essere digitati correttamente](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)
- [CA2204: I valori letterali devono essere digitati correttamente](../code-quality/ca2204-literals-should-be-spelled-correctly.md)