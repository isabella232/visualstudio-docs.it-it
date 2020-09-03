---
title: Output | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 5e286e61-4548-42cf-a635-e608c5edbe2b
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 26a9532bcf0e641d9ad27522f207493b905dc471
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179553"
---
# <a name="output"></a>Output
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L'opzione **Output** specifica il nome del file di dati di profilatura per la sessione di prestazioni. L'opzione **Output** deve essere usata con l'opzione **Start**.  
  
## <a name="syntax"></a>Sintassi  
  
```  
VSPerfCmd.exe /Start:Method /Output:FileName [Options]  
```  
  
#### <a name="parameters"></a>Parametri  
 `FileName`  
 Nome del file di dati. Sono accettati percorsi completi e parziali. Se non viene specificato un percorso, il file viene creato nella directory corrente.  
  
## <a name="required-options"></a>Opzioni obbligatorie  
 L'opzione **Output** deve essere usata con l'opzione **Start**.  
  
 **Inizio:**`Method`  
 Specifica il nome del file di output.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente il file di dati di profilatura viene creato nella directory corrente.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
```  
  
## <a name="see-also"></a>Vedere anche  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilatura di applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilatura di applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilatura di servizi](../profiling/command-line-profiling-of-services.md)
