---
title: 'CA1809: Evitare un numero eccessivo di variabili locali | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1809
- AvoidExcessiveLocals
helpviewer_keywords:
- AvoidExcessiveLocals
- CA1809
ms.assetid: 5c81ea43-cb49-448f-980f-a1dd9764043c
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 1e019c79138ab635e056852df426c5060d46da0b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49223893"
---
# <a name="ca1809-avoid-excessive-locals"></a>CA1809: Evitare un numero eccessivo di variabili locali
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|AvoidExcessiveLocals|
|CheckId|CA1809|
|Category|Microsoft.Performance|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa
 Un membro contiene più di 64 variabili locali, alcune delle quali potrebbe essere generato dal compilatore.

## <a name="rule-description"></a>Descrizione della regola
 Ottimizzazione delle prestazioni più comuni consiste nell'archiviare un valore in un registro del processore anziché in memoria che si intende *comportando così una riduzione* il valore. Common language runtime considera un massimo di 64 variabili locali per la registrazione. Le variabili non registrate vengono inserite nello stack e devono essere spostate in un registro prima della modifica. Per consentire la possibilità che tutte le variabili locali, ottenere registrate, limitare il numero di variabili a 64.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, eseguire il refactoring dell'implementazione per usare non più di 64 variabili locali.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È sicuro per eliminare un avviso da questa regola, o disabilitare la regola, se le prestazioni non sono un problema.

## <a name="related-rules"></a>Regole correlate
 [CA1804: Rimuovere locali non usati](../code-quality/ca1804-remove-unused-locals.md)



