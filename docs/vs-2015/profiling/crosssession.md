---
title: CrossSession | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: b9fcb9c3-7903-478c-9b7c-dbd94092fcba
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 05e1f2360b3257e44fde1af8be3554dd7fd95115
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2019
ms.locfileid: "54790337"
---
# <a name="crosssession"></a>CrossSession
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L'opzione **CrossSession** di VSPerfCmd.exe consente al profiler di raccogliere dati da qualsiasi sessione della console. L'opzione **CrossSession** deve essere usata con l'opzione **Start**.  
  
 È possibile usare l'abbreviazione **CS** al posto di **CrossSession**.  
  
## <a name="syntax"></a>Sintassi  
  
```  
VSPerfCmd.exe /Start:Method /CrossSession [Options]  
```  
  
#### <a name="parameters"></a>Parametri  
 nessuno  
  
## <a name="valid-options"></a>Opzioni valide  
 Per abilitare la profilatura in un'altra sessione, l'opzione **CrossSession** deve essere specificata con l'opzione **Start**. **CrossSession** deve essere specificata anche in tutti i comandi **Attach e Detach** di **VSPerfCmd**.  
  
 **Start:** `Method`  
 L'opzione **Start** inizializza il profiler sul metodo di profilatura specificato.  
  
 **Attach:** _PID_[**,**_PID_]  
 Avvia la profilatura dei processi specificati.  
  
 **Detach**[**:**_PID_[,_PID_]]  
 Arresta la profilatura dei processi specificati.  
  
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
