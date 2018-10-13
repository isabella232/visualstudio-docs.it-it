---
title: Creazione di logger di inoltro | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MSBuild, forwarding loggers
- MSBuild, logging
ms.assetid: 3aebf9c8-b62c-4cb2-b2d6-8cdfcd369a24
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 46cff57e8238e00f914f8437fbc81d1887e7d629
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49281242"
---
# <a name="creating-forwarding-loggers"></a>Creazione di logger di inoltro
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
I logger di inoltro migliorano l'efficienza della registrazione, perché consentono di scegliere gli eventi da monitorare quando si compilano progetti in un sistema multiprocessore. L'abilitazione dei logger di inoltro impedisce che gli eventi indesiderati sovraccarichino il logger centrale, rallentando le compilazioni e occupando spazio nel log.  
  
 Per creare un logger di inoltro è possibile implementare l'interfaccia <xref:Microsoft.Build.Framework.IForwardingLogger>, quindi implementare manualmente i metodi corrispondenti oppure usare la classe <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger> e i metodi preconfigurati corrispondenti. La seconda soluzione è in genere sufficiente per la maggior parte delle applicazioni.  
  
## <a name="register-events-and-respond-to-them"></a>Registrare gli eventi e adottare misure  
 Un logger di inoltro raccoglie informazioni sugli eventi di compilazione man mano che vengono segnalati dal motore di compilazione secondario, un processo di lavoro creato dal processo di compilazione principale durante una compilazione in un sistema multiprocessore. Il logger di inoltro seleziona gli eventi da inoltrare al logger centrale, in base alle istruzioni impostate.  
  
 È necessario registrare i logger di inoltro per la gestione degli eventi da monitorare. Per eseguire la registrazione per gli eventi, i logger devono eseguire l'override del metodo <xref:Microsoft.Build.Utilities.Logger.Initialize%2A>. Questo metodo ora include il parametro facoltativo `nodecount`, che può essere impostato sul numero di processori del sistema. Per impostazione predefinita, il valore è 1.  
  
 Ad esempio è possibile monitorare eventi quali <xref:Microsoft.Build.Framework.IEventSource.TargetStarted>, <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted> e <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished>.  
  
 In un ambiente multiprocessore, è probabile che i messaggi di evento non vengano ricevuti in ordine. Pertanto è necessario valutare gli eventi usando il gestore eventi nel logger di inoltro e programmarlo per determinare gli eventi da passare al redirector per l'inoltro al logger centrale. A tale scopo è possibile usare la classe <xref:Microsoft.Build.Framework.BuildEventContext> collegata a ogni messaggio per identificare gli eventi da inoltrare, quindi passare i nomi degli eventi alla classe <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger> (o a una sottoclasse). Se si usa questo metodo, non è necessario altro codice specifico per inoltrare gli eventi.  
  
## <a name="specify-a-forwarding-logger"></a>Specificare un logger di inoltro  
 Dopo avere compilato il logger di inoltro in un assembly, è necessario richiedere a [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] di usarlo durante le compilazioni. A tale scopo usare le opzioni `/FileLogger`, `/FileLoggerParameters`, e `/DistributedFileLogger` insieme a MSBuild.exe. L'opzione `/FileLogger` comunica a MSBuild.exe che il logger è collegato direttamente. L'opzione `/DistributedFileLogger` indica che è presente un file di log per ogni nodo. L'opzione `/FileLoggerParameters` consente di impostare parametri per il logger di inoltro. Per informazioni sul queste e altre opzioni disponibili per MSBuild.exe, vedere [Riferimenti alla riga di comando](../msbuild/msbuild-command-line-reference.md).  
  
## <a name="multi-processor-aware-loggers"></a>Logger compatibili con più processori  
 Quando si compila un progetto in un sistema multiprocessore, i messaggi di compilazione di ogni processore non vengono disposti automaticamente in una sequenza unificata. È necessario stabilire una priorità di raggruppamento dei messaggi usando la classe <xref:Microsoft.Build.Framework.BuildEventContext> associata a ogni messaggio. Per altre informazioni sulla compilazione in ambienti a più processori, vedere [Registrazione in un ambiente a più processori](../msbuild/logging-in-a-multi-processor-environment.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Obtaining Build Logs](../msbuild/obtaining-build-logs-with-msbuild.md)  (Recupero di log di compilazione)  
 [Logger di compilazione](../msbuild/build-loggers.md)   
 [Registrazione in un ambiente a più processori](../msbuild/logging-in-a-multi-processor-environment.md)



