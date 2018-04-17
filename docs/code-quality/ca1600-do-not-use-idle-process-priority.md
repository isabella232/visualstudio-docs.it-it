---
title: ': Non CA1600 processo inattivo priorità | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- DoNotUseIdleProcessPriority
- CA1600
helpviewer_keywords:
- CA1600
- DoNotUseIdleProcessPriority
ms.assetid: 9b0d073b-78b6-41be-8ef3-14692a735283
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 93255488efa84f553d61aaedb0474c69a4bbb8d0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="ca1600-do-not-use-idle-process-priority"></a>CA1600: Non impostare la priorità del processo su Inattivo
|||  
|-|-|  
|TypeName|DoNotUseIdleProcessPriority|  
|CheckId|CA1600|  
|Category|Microsoft.Mobility|  
|Modifica importante|Interruzione|  
  
## <a name="cause"></a>Causa  
 Questa regola si verifica quando i processi sono impostati su `ProcessPriorityClass.Idle`.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Non impostare la priorità del processo su Inattivo. I processi con `System.Diagnostics.ProcessPriorityClass.Idle` . Idle occupano la CPU diversamente sarebbe inattiva e blocca quindi la modalità standby.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Impostare i processi su `ProcessPriorityClass.BelowNormal`.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Questa regola deve essere eliminata solo quando è necessaria una priorità di processo su inattivo e le considerazioni sulla mobilità possono essere ignorati.