---
title: Rilevamento di file | Microsoft Docs
description: Usare MSBuild funzioni di rilevamento file per registrare le chiamate al Windows file system per un processo e i relativi processi figlio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, file tracking
ms.assetid: e6c66ac0-3464-451f-9192-3b98dca21b4a
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: fbff31884c3aa6539b286772f1517b1594462579a5992f8fa750a8e5b7b03729
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121428081"
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
