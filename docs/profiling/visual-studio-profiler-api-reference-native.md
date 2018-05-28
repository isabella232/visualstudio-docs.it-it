---
title: Riferimenti per le API del profiler di Visual Studio (native) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- performance tools, API
- Profiler, API
ms.assetid: a0c3be92-c263-4678-9fb9-bafead3bd5f5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 53c8caa101b51a9d26d555787e710408cf315a0e
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/22/2018
---
# <a name="visual-studio-profiler-api-reference-native"></a>Riferimenti per le API del profiler di Visual Studio (native)
Le API del profiler di Visual Studio consentono di controllare a livello di codice la quantità di dati raccolti e di inserire contrassegni sia per il timestamp che per il profilo durante la profilatura. Per usare le API native, è necessario includere il file di intestazione VSPerf.h e aggiungere il file VSPerf.lib nel progetto.  
  
> [!NOTE]
>  Per impostazione predefinita, VSPerf.h e VSPerf.lib si trovano in una cartella denominata PerfSDK. Ad esempio, la directory \<unità>:\Programmi\Microsoft Visual Studio 14.0\Team Tools\Performance Tools\PerfSDK.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [CommentMarkAtProfile](../profiling/commentmarkatprofile.md)  
  
 [CommentMarkProfile](../profiling/commentmarkprofile.md)  
  
 [MarkProfile](../profiling/markprofile.md)  
  
 [NameProfile](../profiling/nameprofile.md)  
  
 [ResumeProfile](../profiling/resumeprofile.md)  
  
 [StartProfile](../profiling/startprofile.md)  
  
 [StopProfile](../profiling/stopprofile.md)  
  
 [SuspendProfile](../profiling/suspendprofile.md)  
  
 [PROFILE_CURRENTID](../profiling/profile-currentid.md)  
  
## <a name="see-also"></a>Vedere anche  
 [API degli strumenti di profilatura](../profiling/profiling-tools-apis.md)   
 [Procedura dettagliata: Uso delle API del profiler](../profiling/walkthrough-using-profiler-apis.md)
