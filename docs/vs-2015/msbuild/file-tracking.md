---
title: Rilevamento di file | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- msbuild, file tracking
ms.assetid: e6c66ac0-3464-451f-9192-3b98dca21b4a
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d8d999d65b207f72542b732842f6eb984df40764
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156464"
---
# <a name="file-tracking"></a>Rilevamento di file
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il rilevamento di file registra le chiamate al file system di Windows per un processo e i relativi processi figlio. Chiamando le funzioni elencate di seguito, i programmi stabiliscono quando attivare e disattivare la registrazione e quale file di log usare.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
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
