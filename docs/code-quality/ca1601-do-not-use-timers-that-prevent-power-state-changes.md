---
title: 'CA1601: Non utilizzare i timer che impediscono le modifiche allo stato di potenza'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 033c7a73c404a2bd5146a17a1a7b4f2fa8b9c540
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2018
ms.locfileid: "45545713"
---
# <a name="ca1601-do-not-use-timers-that-prevent-power-state-changes"></a>CA1601: Non utilizzare i timer che impediscono le modifiche allo stato di potenza
|||
|-|-|
|TypeName|DoNotUseTimersThatPreventPowerStateChanges|
|CheckId|CA1601|
|Category|Microsoft.Mobility|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un timer ha un intervallo impostato su si verificano più di una volta al secondo.

## <a name="rule-description"></a>Descrizione della regola
 Non eseguire il polling più spesso di una volta al secondo o utilizzare i timer che si verificano più frequentemente una volta al secondo. Una frequenza maggiore per l'attività periodica occupa la CPU e interferisce con i timer di inattività per il risparmio di energia tramite cui vengono disattivati lo schermo e i dischi rigidi.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Impostare gli intervalli di timer in presenti meno di una volta al secondo.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 Questa regola deve essere eliminata solo se è richiesta l'attivazione di più di una volta al secondo il timer e le considerazioni sulla mobilità può essere ignorati.