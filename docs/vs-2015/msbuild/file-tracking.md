---
title: Rilevamento di file | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- msbuild, file tracking
ms.assetid: e6c66ac0-3464-451f-9192-3b98dca21b4a
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 40598ba8fbe693d44ee49228a36be75a9e851eea
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47519567"
---
# <a name="file-tracking"></a>Rilevamento di file
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [rilevamento File](https://docs.microsoft.com/visualstudio/msbuild/file-tracking).  
  
  
Il rilevamento di file registra le chiamate al file system di Windows per un processo e i relativi processi figlio. Chiamando le funzioni elencate di seguito, i programmi stabiliscono quando attivare e disattivare la registrazione e quale file di log usare.  
  
## <a name="in-this-section"></a>In questa sezione  
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


