---
title: Report Traccia eventi per Windows (ETW) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Event tracing for Windows profiling report
- ETW profiling report
ms.assetid: 81e88162-b88a-40b6-8b85-a232c8096a47
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 49ea37f6830c7e4fdf8c8d94b0f323c6337329c5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47533109"
---
# <a name="event-tracing-for-windows-etw-report"></a>Rapporto Traccia eventi per Windows (ETW)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [Report di Event Tracing for Windows (ETW)](https://docs.microsoft.com/visualstudio/profiling/event-tracing-for-windows-etw-report).  
  
Il report Traccia eventi per Windows (ETW) indica gli eventi ETW registrati in una sessione di prestazioni degli strumenti di profilatura di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. I dati ETW vengono raccolti in un file binario (ETL).  
  
> [!NOTE]
>  Non è possibile visualizzare i report ETW nell'interfaccia di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
-   Per informazioni su come raccogliere dati ETW usando gli strumenti di profilatura dall'interfaccia di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], vedere [Procedura: Raccogliere dati ETW (Event Tracing for Windows)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md).  
  
-   Per informazioni su come raccogliere dati ETW usando gli strumenti della riga di comando di [VSPerfCmd](../profiling/vsperfcmd.md), vedere [Eventi](../profiling/events-vsperfcmd.md).  
  
-   Per generare il report ETW, usare il comando **VSReport/Summary:ETW**. Per altre informazioni, vedere [VSPerfReport](../profiling/vsperfreport.md).  
  
|Colonna|Descrizione|  
|------------|-----------------|  
|**Timestamp**|Identifica il momento in cui si è verificato l'evento.|  
|**ID processo**|Identifica il processo che ha generato l'evento.|  
|**ID thread**|Identifica il thread che ha generato l'evento.|  
|**Descrizione**|Identifica il provider di eventi.|  
|**Type**|Identifica il tipo di evento.|  
|**Proprietà**|Le proprietà dell'evento. Ogni evento è una coppia nome-valore separata da virgola e racchiusa tra parentesi.|


