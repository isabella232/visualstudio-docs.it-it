---
title: Avvisi di mobilità | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.MobilityRules
helpviewer_keywords:
- managed code analysis warnings, mobility warnings
- mobility warnings
- warnings, mobility
ms.assetid: 9808054c-593b-4fc3-92cc-1fc45f41569c
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: e67be4e501cb2d0dd9d584250fcea91af13fe657
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58966999"
---
# <a name="mobility-warnings"></a>avvisi di mobilità
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Avvisi di mobilità supportano l'utilizzo di risparmio energetico.  
  
## <a name="in-this-section"></a>In questa sezione  
  
|Regola|Descrizione|  
|----------|-----------------|  
|[CA1600: Non utilizzare priorità del processo su inattivo](../code-quality/ca1600-do-not-use-idle-process-priority.md)|Non impostare la priorità del processo su Inattivo. I processi con System.Diagnostics.ProcessPriorityClass.Idle occupano la CPU, che diversamente sarebbe inattiva, e bloccano quindi la modalità standby.|  
|[CA1601: Non usare i timer che impediscono le modifiche dello stato di alimentazione](../code-quality/ca1601-do-not-use-timers-that-prevent-power-state-changes.md)|Una frequenza maggiore per l'attività periodica occupa la CPU e interferisce con i timer di inattività per il risparmio di energia tramite cui vengono disattivati lo schermo e i dischi rigidi.|
