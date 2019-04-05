---
title: 'CA1600: Non utilizzare la priorità del processo inattivo | Microsoft Docs'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 4002e17e3988ca3b449e141394ce762f95ffc78b
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2019
ms.locfileid: "58963844"
---
# <a name="ca1600-do-not-use-idle-process-priority"></a>CA1600: Non impostare la priorità del processo su Inattivo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Questa regola deve essere eliminata solo quando è necessaria una priorità processo inattivo e le considerazioni sulla mobilità può essere ignorati in modo sicuro.
