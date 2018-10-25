---
title: ': CA1600 non priorità del processo su inattivo | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
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
ms.openlocfilehash: f077774f67ca398d26746d0c375545e0cb641454
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49941854"
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



