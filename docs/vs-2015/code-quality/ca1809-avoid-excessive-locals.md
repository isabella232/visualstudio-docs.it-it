---
title: 'CA1809: evitare un numero eccessivo di variabili locali | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1809
- AvoidExcessiveLocals
helpviewer_keywords:
- AvoidExcessiveLocals
- CA1809
ms.assetid: 5c81ea43-cb49-448f-980f-a1dd9764043c
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d39c8d9d09cf457738df87e3c2e6e109f7bc1696
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543858"
---
# <a name="ca1809-avoid-excessive-locals"></a>CA1809: Evitare un numero eccessivo di variabili locali
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|AvoidExcessiveLocals|
|CheckId|CA1809|
|Category|Microsoft. performance|
|Modifica importante|Senza interruzioni|

## <a name="cause"></a>Causa
 Un membro contiene più di 64 variabili locali, alcune delle quali potrebbero essere generate dal compilatore.

## <a name="rule-description"></a>Descrizione della regola
 Un'ottimizzazione delle prestazioni comune consiste nell'archiviare un valore in un registro del processore anziché in memoria, a cui viene fatto *riferimento come registrazione* del valore. Il Common Language Runtime considera fino a 64 variabili locali per l'iscrizione. Le variabili non registrate vengono inserite nello stack e devono essere spostate in un registro prima della manipolazione. Per consentire la registrazione di tutte le variabili locali, limitare il numero di variabili locali a 64.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, effettuare il refactoring dell'implementazione in modo che non utilizzi più di 64 variabili locali.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola o disabilitare la regola se le prestazioni non sono un problema.

## <a name="related-rules"></a>Regole correlate
 [CA1804: Rimuovere variabili locali non usate](../code-quality/ca1804-remove-unused-locals.md)
