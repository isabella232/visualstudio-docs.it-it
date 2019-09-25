---
title: 'CA1809: Evitare un numero eccessivo di variabili locali'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1809
- AvoidExcessiveLocals
helpviewer_keywords:
- AvoidExcessiveLocals
- CA1809
ms.assetid: 5c81ea43-cb49-448f-980f-a1dd9764043c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 89d6ee4d1a53f63cffb31439a124d3d9358e976f
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233652"
---
# <a name="ca1809-avoid-excessive-locals"></a>CA1809: Evitare un numero eccessivo di variabili locali

|||
|-|-|
|TypeName|AvoidExcessiveLocals|
|CheckId|CA1809|
|Category|Microsoft.Performance|
|Modifica|Senza interruzioni|

## <a name="cause"></a>Causa
Un membro contiene più di 64 variabili locali, alcune delle quali potrebbero essere generate dal compilatore.

## <a name="rule-description"></a>Descrizione della regola
Un'ottimizzazione delle prestazioni comune consiste nell'archiviare un valore in un registro del processore anziché in memoria, a cui viene fatto *riferimento come registrazione* del valore. Il Common Language Runtime considera fino a 64 variabili locali per l'iscrizione. Le variabili non registrate vengono inserite nello stack e devono essere spostate in un registro prima della manipolazione. Per consentire la registrazione di tutte le variabili locali, limitare il numero di variabili locali a 64.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
Per correggere una violazione di questa regola, effettuare il refactoring dell'implementazione in modo che non utilizzi più di 64 variabili locali.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
È possibile eliminare un avviso da questa regola o disabilitare la regola se le prestazioni non sono un problema.

## <a name="related-rules"></a>Regole correlate
[CA1804: Rimuovi variabili locali non usate](../code-quality/ca1804-remove-unused-locals.md)