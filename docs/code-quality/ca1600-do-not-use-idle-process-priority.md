---
title: 'CA1600: Non impostare la priorità del processo su Inattivo'
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c37affc585653807912d00c1cfe365853fd6260b
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921816"
---
# <a name="ca1600-do-not-use-idle-process-priority"></a>CA1600: Non impostare la priorità del processo su Inattivo

|||
|-|-|
|TypeName|DoNotUseIdleProcessPriority|
|CheckId|CA1600|
|Category|Microsoft.Mobility|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
Questa regola si verifica quando i processi sono `ProcessPriorityClass.Idle`impostati su.

## <a name="rule-description"></a>Descrizione della regola
Non impostare la priorità del processo su Inattivo. I processi che `System.Diagnostics.ProcessPriorityClass.Idle` occupano la CPU quando sarebbero altrimenti inattivi e bloccano quindi la modalità standby.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
Impostare i processi `ProcessPriorityClass.BelowNormal`su.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
Questa regola deve essere eliminata solo quando è richiesta la priorità del processo inattivo e le considerazioni sulla mobilità possono essere ignorate in modo sicuro.