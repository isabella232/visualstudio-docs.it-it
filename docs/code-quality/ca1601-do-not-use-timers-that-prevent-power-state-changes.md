---
title: 'CA1601: Non usare i timer che impediscono le modifiche allo stato di potenza'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1601
- DoNotUseTimersThatPreventPowerStateChanges
helpviewer_keywords:
- CA1601
- DoNotUseTimersThatPreventPowerStateChanges
ms.assetid: b8028c92-0696-4c54-9773-0028f29bda9a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6b3c3fe41332d488d180ddafbedfe29da1a3855e
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921784"
---
# <a name="ca1601-do-not-use-timers-that-prevent-power-state-changes"></a>CA1601: Non usare i timer che impediscono le modifiche allo stato di potenza

|||
|-|-|
|TypeName|DoNotUseTimersThatPreventPowerStateChanges|
|CheckId|CA1601|
|Category|Microsoft.Mobility|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
Un timer ha un intervallo impostato in modo che venga eseguito più di una volta al secondo.

## <a name="rule-description"></a>Descrizione della regola
Non eseguire il polling più spesso di una volta al secondo o usare i timer che si verificano più frequentemente di una volta al secondo. Una frequenza maggiore per l'attività periodica occupa la CPU e interferisce con i timer di inattività per il risparmio di energia tramite cui vengono disattivati lo schermo e i dischi rigidi.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
Impostare gli intervalli del timer in modo che si verifichino meno di una volta al secondo.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
Questa regola deve essere eliminata solo se è richiesto l'attivazione del timer più di una volta al secondo e le considerazioni sulla mobilità possono essere ignorate in modo sicuro.