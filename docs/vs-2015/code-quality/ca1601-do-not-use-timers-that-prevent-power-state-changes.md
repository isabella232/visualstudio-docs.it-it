---
title: 'CA1601: non utilizzare i timer che impediscono le modifiche allo stato di alimentazione | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1601
- DoNotUseTimersThatPreventPowerStateChanges
helpviewer_keywords:
- CA1601
- DoNotUseTimersThatPreventPowerStateChanges
ms.assetid: b8028c92-0696-4c54-9773-0028f29bda9a
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7928b2fff8c12ca3f0cc3c58bee31fe5809517e5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545639"
---
# <a name="ca1601-do-not-use-timers-that-prevent-power-state-changes"></a>CA1601: Non usare i timer che impediscono le modifiche allo stato di potenza
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|DoNotUseTimersThatPreventPowerStateChanges|
|CheckId|CA1601|
|Category|Microsoft. Mobility|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un timer ha un intervallo impostato in modo che venga eseguito più di una volta al secondo.

## <a name="rule-description"></a>Descrizione della regola
 Non eseguire il polling più spesso di una volta al secondo o usare i timer che si verificano più frequentemente di una volta al secondo. Una frequenza maggiore per l'attività periodica occupa la CPU e interferisce con i timer di inattività per il risparmio di energia tramite cui vengono disattivati lo schermo e i dischi rigidi.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Impostare gli intervalli del timer in modo che si verifichino meno di una volta al secondo.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Questa regola deve essere eliminata solo se è richiesto l'attivazione del timer più di una volta al secondo e le considerazioni sulla mobilità possono essere ignorate in modo sicuro.
