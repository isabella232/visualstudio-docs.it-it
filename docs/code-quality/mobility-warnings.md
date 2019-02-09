---
title: avvisi di mobilità
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.MobilityRules
helpviewer_keywords:
- managed code analysis warnings, mobility warnings
- mobility warnings
- warnings, mobility
ms.assetid: 9808054c-593b-4fc3-92cc-1fc45f41569c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 170caf52999fb687c040c2e9212d1a1ed2e154a0
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55908414"
---
# <a name="mobility-warnings"></a>avvisi di mobilità
Avvisi di mobilità supportano l'utilizzo di risparmio energetico.

## <a name="in-this-section"></a>In questa sezione

|Regola|Descrizione|
|----------|-----------------|
|[CA1600: Non utilizzare priorità del processo su inattivo](../code-quality/ca1600-do-not-use-idle-process-priority.md)|Non impostare la priorità del processo su Inattivo. I processi con System.Diagnostics.ProcessPriorityClass.Idle occupano la CPU, che diversamente sarebbe inattiva, e bloccano quindi la modalità standby.|
|[CA1601: Non usare i timer che impediscono le modifiche dello stato di alimentazione](../code-quality/ca1601-do-not-use-timers-that-prevent-power-state-changes.md)|Una frequenza maggiore per l'attività periodica occupa la CPU e interferisce con i timer di inattività per il risparmio di energia tramite cui vengono disattivati lo schermo e i dischi rigidi.|