---
title: 'CA1600: Non utilizzare priorità del processo su inattivo'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
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
ms.openlocfilehash: e606850298841d1d1c77435d83dbbe12c4e55d64
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53921043"
---
# <a name="ca1600-do-not-use-idle-process-priority"></a>CA1600: Non utilizzare priorità del processo su inattivo

|||
|-|-|
|TypeName|DoNotUseIdleProcessPriority|
|CheckId|CA1600|
|Category|Microsoft.Mobility|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Questa regola si verifica quando i processi sono impostati su `ProcessPriorityClass.Idle`.

## <a name="rule-description"></a>Descrizione della regola
 Non impostare la priorità del processo su Inattivo. I processi con `System.Diagnostics.ProcessPriorityClass.Idle` occupano la CPU diversamente sarebbe inattiva e blocca quindi la modalità standby.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Impostare i processi su `ProcessPriorityClass.BelowNormal`.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 Questa regola deve essere eliminata solo quando è necessaria una priorità processo inattivo e le considerazioni sulla mobilità può essere ignorati in modo sicuro.