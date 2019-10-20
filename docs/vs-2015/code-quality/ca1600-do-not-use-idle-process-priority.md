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
ms.openlocfilehash: d4260db808d9c50f78388cf6ba976f7ace52e6a3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669289"
---
# <a name="ca1600-do-not-use-idle-process-priority"></a>CA1600: Non impostare la priorità del processo su Inattivo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotUseIdleProcessPriority|
|CheckId|CA1600|
|Category|Microsoft. Mobility|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Questa regola si verifica quando i processi sono impostati su `ProcessPriorityClass.Idle`.

## <a name="rule-description"></a>Descrizione della regola
 Non impostare la priorità del processo su Inattivo. I processi con `System.Diagnostics.ProcessPriorityClass.Idle` occupano la CPU quando altrimenti sarebbero inattivi e bloccano quindi la modalità standby.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Impostare i processi su `ProcessPriorityClass.BelowNormal`.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Questa regola deve essere eliminata solo quando è richiesta la priorità del processo inattivo e le considerazioni sulla mobilità possono essere ignorate in modo sicuro.
