---
title: CrossSession | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b9fcb9c3-7903-478c-9b7c-dbd94092fcba
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 196107019a43f8f76beeb55cde6a56034375b9d9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="crosssession"></a>CrossSession
L'opzione **CrossSession** di VSPerfCmd.exe consente al profiler di raccogliere dati da qualsiasi sessione della console. L'opzione **CrossSession** deve essere usata con l'opzione **Start**.  
  
 È possibile usare l'abbreviazione **CS** al posto di **CrossSession**.  
  
## <a name="syntax"></a>Sintassi  
  
```  
VSPerfCmd.exe /Start:Method /CrossSession [Options]  
```  
  
#### <a name="parameters"></a>Parametri  
 Nessuno  
  
## <a name="valid-options"></a>Opzioni valide  
 Per abilitare la profilatura in un'altra sessione, l'opzione **CrossSession** deve essere specificata con l'opzione **Start**. **CrossSession** deve essere specificata anche in tutti i comandi **Attach e Detach** di **VSPerfCmd**.  
  
 **Start:** `Method`  
 L'opzione **Start** inizializza il profiler sul metodo di profilatura specificato.  
  
 **Attach:** *PID*[**,***PID*]  
 Avvia la profilatura dei processi specificati.  
  
 **Detach**[**:***PID*[,*PID*]]  
 Interrompe la profilatura dei processi specificati.  
  
## <a name="example"></a>Esempio  
 In questo esempio l'opzione **CrossSession** viene usata per connettersi a un'applicazione che è stata avviata in un'altra sessione di console.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /CrossSession  
VSPerfCmd.exe /Attach:12345 /CS  
```  
  
## <a name="see-also"></a>Vedere anche  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilatura di applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilatura di applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilatura di servizi](../profiling/command-line-profiling-of-services.md)