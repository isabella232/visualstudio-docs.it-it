---
title: 'CA1703: Le stringhe di risorsa devono essere digitate correttamente | Microsoft Docs'
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
- ResourceStringsShouldBeSpelledCorrectly
- CA1703
helpviewer_keywords:
- CA1703
- ResourceStringsShouldBeSpelledCorrectly
ms.assetid: 693f4970-f512-40cb-ae3b-a0f3a5c6d6f1
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: fc83d109666c98718b1a4b1196db11a81424c911
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589691"
---
# <a name="ca1703-resource-strings-should-be-spelled-correctly"></a>CA1703: Le stringhe di risorsa devono essere digitate correttamente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [CA1703: le stringhe di risorsa devono essere digitate correttamente](https://docs.microsoft.com/visualstudio/code-quality/ca1703-resource-strings-should-be-spelled-correctly).

|||
|-|-|
|TypeName|ResourceStringsShouldBeSpelledCorrectly|
|CheckId|CA1703|
|Category|Microsoft.Naming|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa
 Una stringa di risorsa contiene una o più parole che non sono riconosciute dalla libreria del correttore ortografico Microsoft.

## <a name="rule-description"></a>Descrizione della regola
 Questa regola analizza la stringa di risorsa in parole (suddivisione in token le parole composte) e controlla l'ortografia di ciascuna parola/token. Per informazioni sull'algoritmo di analisi, vedere [CA1704: gli identificatori devono essere digitati correttamente](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

 Per impostazione predefinita, viene utilizzata la versione inglese (en) del correttore ortografico.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, usare parole complete che siano state digitate correttamente o aggiungere le parole in un dizionario personalizzato. Per informazioni su come usare i dizionari personalizzati, vedere [CA1704: gli identificatori devono essere digitati correttamente](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola. Parole formulate correttamente riducono il tempo necessario per l'apprendimento di nuove librerie software.

## <a name="related-rules"></a>Regole correlate
 [CA1701: Le parole composte di una stringa di risorsa devono essere digitate correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

 [CA1704: Gli identificatori devono essere digitati correttamente](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

 [CA2204: I valori letterali devono essere digitati in modo corretto](../code-quality/ca2204-literals-should-be-spelled-correctly.md)



