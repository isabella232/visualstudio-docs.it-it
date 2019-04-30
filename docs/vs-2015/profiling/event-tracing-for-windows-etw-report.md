---
title: Report Traccia eventi per Windows (ETW) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Event tracing for Windows profiling report
- ETW profiling report
ms.assetid: 81e88162-b88a-40b6-8b85-a232c8096a47
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bc0e139644a0b3df29109c1543140e57c5378f31
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63444006"
---
# <a name="event-tracing-for-windows-etw-report"></a>Rapporto Traccia eventi per Windows (ETW)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il report Traccia eventi per Windows (ETW) indica gli eventi ETW registrati in una sessione di prestazioni degli strumenti di profilatura di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. I dati ETW vengono raccolti in un file binario (ETL).  
  
> [!NOTE]
> Non è possibile visualizzare i report ETW nell'interfaccia di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
- Per informazioni su come raccogliere dati ETW usando gli strumenti di profilatura dall'interfaccia di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], vedere [Procedura: Raccogliere Event Tracing for Windows (ETW) Data](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md).  
  
- Per informazioni su come raccogliere dati ETW usando gli strumenti della riga di comando di [VSPerfCmd](../profiling/vsperfcmd.md), vedere [Eventi](../profiling/events-vsperfcmd.md).  
  
- Per generare il report ETW, usare il comando **VSReport/Summary:ETW**. Per altre informazioni, vedere [VSPerfReport](../profiling/vsperfreport.md).  
  
|Colonna|Descrizione|  
|------------|-----------------|  
|**Timestamp**|Identifica il momento in cui si è verificato l'evento.|  
|**ID processo**|Identifica il processo che ha generato l'evento.|  
|**ID thread**|Identifica il thread che ha generato l'evento.|  
|**Descrizione**|Identifica il provider di eventi.|  
|**Type**|Identifica il tipo di evento.|  
|**Proprietà**|Le proprietà dell'evento. Ogni evento è una coppia nome-valore separata da virgola e racchiusa tra parentesi.|
