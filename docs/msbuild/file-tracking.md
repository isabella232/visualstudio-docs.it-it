---
title: Rilevamento di file | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, file tracking
ms.assetid: e6c66ac0-3464-451f-9192-3b98dca21b4a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7770da734143b2b6185b266137eeb46ba25bd32a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62968067"
---
# <a name="file-tracking"></a>Rilevamento file
Il rilevamento di file registra le chiamate al file system di Windows per un processo e i relativi processi figlio. Chiamando le funzioni elencate di seguito, i programmi stabiliscono quando attivare e disattivare la registrazione e quale file di log usare.

- [EndTrackingContext](../msbuild/endtrackingcontext.md) Arresta il rilevamento nel contesto corrente.

- [ResumeTracking](../msbuild/resumetracking.md) Riprende il rilevamento dopo una chiamata a [SuspendTracking](../msbuild/suspendtracking.md).

- [SetThreadCount](../msbuild/setthreadcount.md) Imposta il numero di thread da usare per il rilevamento.

- [StartTrackingContext](../msbuild/starttrackingcontext.md) Avvia un nuovo contesto di rilevamento.

- [StartTrackingContextWithRoot](../msbuild/starttrackingcontextwithroot.md) Avvia un nuovo contesto di rilevamento con una radice specificata.

- [StopTrackingAndCleanup](../msbuild/stoptrackingandcleanup.md) Termina il rilevamento e rilascia le risorse usate.

- [SuspendTracking](../msbuild/suspendtracking.md) Sospende temporaneamente il rilevamento.

- [WriteAllTLogs](../msbuild/writealltlogs.md) Scrive i log di rilevamento per tutti i contesti.

- [WriteContextTLogs](../msbuild/writecontexttlogs.md) Scrive il log di rilevamento per il contesto corrente.