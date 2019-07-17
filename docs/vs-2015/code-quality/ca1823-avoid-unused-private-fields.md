---
title: 'CA1823: Evitare campi privati non utilizzati | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidUnusedPrivateFields
- CA1823
helpviewer_keywords:
- AvoidUnusedPrivateFields
- CA1823
ms.assetid: 614f94f6-0dc7-430f-8124-cb889a4a720f
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 32bf1596e4994f3cfdb2df179bb5d7f1a743f289
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68201648"
---
# <a name="ca1823-avoid-unused-private-fields"></a>CA1823: Evitare campi privati non usati
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidUnusedPrivateFields|
|CheckId|CA1823|
|Category|Microsoft.Performance|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa
 Questa regola viene segnalata quando un campo privato nel codice esiste ma non viene usato da qualsiasi percorso di codice.

## <a name="rule-description"></a>Descrizione della regola
 Sono stati rilevati campi privati che non sembrano essere utilizzati all'interno dell'assembly.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, rimuovere il campo o aggiungere codice che lo usa.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola.

## <a name="related-rules"></a>Regole correlate
 [CA1812: Evitare classi interne prive di istanze](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1801: Controllare i parametri inutilizzati](../code-quality/ca1801-review-unused-parameters.md)

 [CA1804: Rimuovere locali non utilizzati](../code-quality/ca1804-remove-unused-locals.md)

 [CA1811: Evitare il codice privato](../code-quality/ca1811-avoid-uncalled-private-code.md)
