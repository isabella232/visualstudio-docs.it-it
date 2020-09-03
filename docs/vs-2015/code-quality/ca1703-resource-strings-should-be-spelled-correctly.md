---
title: 'CA1703: le stringhe di risorsa devono essere digitate correttamente | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ResourceStringsShouldBeSpelledCorrectly
- CA1703
helpviewer_keywords:
- CA1703
- ResourceStringsShouldBeSpelledCorrectly
ms.assetid: 693f4970-f512-40cb-ae3b-a0f3a5c6d6f1
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 2e720c1c491e88b6d89fb4b1f0175e8bc8a56e27
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544053"
---
# <a name="ca1703-resource-strings-should-be-spelled-correctly"></a>CA1703: Le stringhe di risorsa devono essere digitate correttamente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|ResourceStringsShouldBeSpelledCorrectly|
|CheckId|CA1703|
|Category|Microsoft. Naming|
|Modifica importante|Senza interruzioni|

## <a name="cause"></a>Causa
 Una stringa di risorsa contiene una o più parole che non sono riconosciute dalla libreria del correttore ortografico Microsoft.

## <a name="rule-description"></a>Descrizione della regola
 Questa regola analizza la stringa di risorsa in parole (parole composte suddivisione in token) e controlla l'ortografia di ogni parola/token. Per informazioni sull'algoritmo di analisi, vedere [CA1704: gli identificatori devono essere digitati correttamente](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

 Per impostazione predefinita, viene utilizzata la versione inglese (en) del correttore ortografico.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, usare parole complete che sono state digitate correttamente o aggiungere parole a un dizionario personalizzato. Per informazioni sull'uso dei dizionari personalizzati, vedere [CA1704: gli identificatori devono essere digitati correttamente](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola. Le parole con ortografia corretta consentono di ridurre il tempo necessario per apprendere nuove librerie software.

## <a name="related-rules"></a>Regole correlate
 [CA1701: Le parole composte di una stringa di risorsa devono essere digitate correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

 [CA1704: Gli identificatori devono essere digitati correttamente](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

 [CA2204: I valori letterali devono essere digitati correttamente](../code-quality/ca2204-literals-should-be-spelled-correctly.md)
