---
title: 'CA2204: i valori letterali devono essere digitati correttamente | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- Literals should be spelled correctly
- CA2204
- LiteralsShouldBeSpelledCorrectly
helpviewer_keywords:
- CA2204
ms.assetid: b0bbcbb6-c92d-4c14-8ef7-9c8b38c791a6
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ecf829251cbeab600cb95f8f0c0b0173cd7338d4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546276"
---
# <a name="ca2204-literals-should-be-spelled-correctly"></a>CA2204: I valori letterali devono essere digitati correttamente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|LiteralsShouldBeSpelledCorrectly|
|CheckId|CA2204|
|Category|Microsoft. Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Un metodo passa una stringa letterale a utilizzata in un parametro o in una proprietà che richiede una stringa localizzata e la stringa letterale contiene una o più parole che non sono riconosciute dalla libreria del correttore ortografico Microsoft.

## <a name="rule-description"></a>Descrizione della regola
 Questa regola consente di controllare una stringa letterale passata come valore a un parametro o a una proprietà quando uno o più dei seguenti casi è true:

- L' <xref:System.ComponentModel.LocalizableAttribute> attributo del parametro o della proprietà è impostato su true.

- Il nome del parametro o della proprietà contiene "Text", "message" o "Caption".

- Il nome del parametro stringa passato a un metodo Console. Write o console. WriteLine può essere "value" o "Format".

  Questa regola analizza la stringa letterale in parole, suddivisione in token parole composte e controlla l'ortografia di ogni parola/token. Per informazioni sull'algoritmo di analisi, vedere [CA1704: gli identificatori devono essere digitati correttamente](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

  Per impostazione predefinita, viene utilizzata la versione inglese (en) del correttore ortografico.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, correggere l'ortografia della parola o aggiungere la parola a un dizionario personalizzato. Per informazioni sull'uso dei dizionari personalizzati, vedere [procedura: personalizzare il dizionario di analisi del codice](../code-quality/how-to-customize-the-code-analysis-dictionary.md).

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola. Le parole con ortografia corretta riducono la curva di apprendimento necessaria per le nuove librerie software.

## <a name="related-rules"></a>Regole correlate
 [CA1704: Gli identificatori devono essere digitati correttamente](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

 [CA1703: Le stringhe di risorsa devono essere digitate correttamente](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)
