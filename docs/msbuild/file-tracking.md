---
title: Rilevamento di file | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- msbuild, file tracking
ms.assetid: e6c66ac0-3464-451f-9192-3b98dca21b4a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 394b40a304d2aba3b79c5878befe33a8a1aaf8b8
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2018
ms.locfileid: "37945559"
---
# <a name="file-tracking"></a>Rilevamento file
Il rilevamento di file registra le chiamate al file system di Windows per un processo e i relativi processi figlio. Chiamando le funzioni elencate di seguito, i programmi stabiliscono quando attivare e disattivare la registrazione e quale file di log usare.  
  
 [EndTrackingContext](../msbuild/endtrackingcontext.md)  
 Interrompe il rilevamento nel contesto corrente.  
  
 [ResumeTracking](../msbuild/resumetracking.md)  
 Riprende il rilevamento dopo una chiamata a [SuspendTracking](../msbuild/suspendtracking.md).  
  
 [SetThreadCount](../msbuild/setthreadcount.md)  
 Imposta il numero di thread da usare per il rilevamento.  
  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)  
 Avvia un nuovo contesto di rilevamento.  
  
 [StartTrackingContextWithRoot](../msbuild/starttrackingcontextwithroot.md)  
 Avvia un nuovo contesto di rilevamento con una radice specificata.  
  
 [StopTrackingAndCleanup](../msbuild/stoptrackingandcleanup.md)  
 Termina il rilevamento e rilascia le risorse usate.  
  
 [SuspendTracking](../msbuild/suspendtracking.md)  
 Sospende temporaneamente il rilevamento.  
  
 [WriteAllTLogs](../msbuild/writealltlogs.md)  
 Scrive i log di rilevamento per tutti i contesti.  
  
 [WriteContextTLogs](../msbuild/writecontexttlogs.md)  
 Scrive il log di rilevamento per il contesto corrente.