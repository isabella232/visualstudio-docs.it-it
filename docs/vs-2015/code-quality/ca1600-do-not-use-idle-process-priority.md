---
title: 'CA1600: non usare la priorità del processo inattivo | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotUseIdleProcessPriority
- CA1600
helpviewer_keywords:
- CA1600
- DoNotUseIdleProcessPriority
ms.assetid: 9b0d073b-78b6-41be-8ef3-14692a735283
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 3f6233136dcf7f1db5d622a02419d33e0eedacf5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545678"
---
# <a name="ca1600-do-not-use-idle-process-priority"></a>CA1600: Non impostare la priorità del processo su Inattivo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|DoNotUseIdleProcessPriority|
|CheckId|CA1600|
|Category|Microsoft. Mobility|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Questa regola si verifica quando i processi sono impostati su `ProcessPriorityClass.Idle` .

## <a name="rule-description"></a>Descrizione della regola
 Non impostare la priorità del processo su Inattivo. I processi che `System.Diagnostics.ProcessPriorityClass.Idle` occupano la CPU quando sarebbero altrimenti inattivi e bloccano quindi la modalità standby.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Impostare i processi su `ProcessPriorityClass.BelowNormal` .

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Questa regola deve essere eliminata solo quando è richiesta la priorità del processo inattivo e le considerazioni sulla mobilità possono essere ignorate in modo sicuro.
