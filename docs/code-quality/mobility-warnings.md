---
title: avvisi di mobilità
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8f40803e4e491382e958c1954d2608cb712ad82b
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="mobility-warnings"></a>avvisi di mobilità
Avvisi di mobilità supportano l'utilizzo di risparmio energetico.

## <a name="in-this-section"></a>In questa sezione

|Regola|Descrizione|
|----------|-----------------|
|[CA1600: Non impostare la priorità del processo su Inattivo](../code-quality/ca1600-do-not-use-idle-process-priority.md)|Non impostare la priorità del processo su Inattivo. I processi con System.Diagnostics.ProcessPriorityClass.Idle occupano la CPU, che diversamente sarebbe inattiva, e bloccano quindi la modalità standby.|
|[CA1601: Non usare i timer che impediscono le modifiche allo stato di potenza](../code-quality/ca1601-do-not-use-timers-that-prevent-power-state-changes.md)|Una frequenza maggiore per l'attività periodica occupa la CPU e interferisce con i timer di inattività per il risparmio di energia tramite cui vengono disattivati lo schermo e i dischi rigidi.|