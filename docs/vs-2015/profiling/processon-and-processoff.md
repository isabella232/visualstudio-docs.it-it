---
title: ProcessOn e ProcessOff | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d3dc6a7e-bc0f-48a6-a4ec-f386348bb296
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cd2d33a6d0e333600c31e540f03d6140853e796d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47529244"
---
# <a name="processon-and-processoff"></a>ProcessOn e ProcessOff
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [ProcessOn e ProcessOff](https://docs.microsoft.com/visualstudio/profiling/processon-and-processoff).  
  
I sottocomandi **ProcessOff** e **ProcessOn** di VSPerfCmd.exe sospendono e riprendono la profilatura per il processo specificato in una sessione di profilatura da riga di comando. **ProcessOff** arresta la profilatura del processo e **ProcessOn** avvia la profilatura del processo.  
  
 Nella maggior parte dei casi si specifica **ProcessOn** o **ProcessOff** come unica opzione in una riga di comando di VSPerfCmd.exe, ma questi sottocomandi possono anche essere combinati con i sottocomandi **GlobalOn**, **GlobalOff**, **ThreadOn** e **ThreadOff**.  
  
 I sottocomandi **ProcessOn** e **ProcessOff** interagiscono con i sottocomandi **GlobalOn** e **GlobalOff** che controllano la raccolta dei dati per tutti i processi in una sessione di profilatura da riga di comando e i sottocomandi **ThreadOn** e **ThreadOff** che controllano la raccolta dei dati per un processo specificato.  
  
 I sottocomandi **ProcessOff** e **ProcessOn** influenzano anche il conteggio Start/Stop per il processo, gestito dalle funzioni API del profiler.  
  
-   **ProcessOff** imposta immediatamente il conteggio Start/Stop per il processo su 0 e sospende quindi la profilatura.  
  
-   **ProcessOn** imposta immediatamente il conteggio Start/Stop per il processo su 1 e riprende quindi la profilatura.  
  
 Per altre informazioni, vedere [API per strumenti di profilatura](../profiling/profiling-tools-apis.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
VSPerfCmd.exe /{ProcessOff|ProcessOn}:PID [Options]  
  
```  
  
#### <a name="parameters"></a>Parametri  
 `PID`  
 Identificatore integer del processo da avviare o arrestare. Gli ID di processo sono elencati nella scheda Processi di Gestione attività di Windows.  
  
## <a name="required-subcommands"></a>Sottocomandi obbligatori  
 nessuno  
  
## <a name="valid-subcommands"></a>Sottocomandi validi  
 **ProcessOn** e **ProcessOff** possono essere specificati su righe di comando che contengono anche i sottocomandi seguenti.  
  
 **Start:** `Method`  
 Inizializza la sessione di profilatura da riga di comando e imposta il metodo di profilatura specificato.  
  
 **Launch:** `AppName`  
 Avvia l'applicazione specificata e inizia la profilatura con il metodo di campionamento.  
  
 **Attach:** `PID`  
 Avvia la profilatura del processo specificato.  
  
 **GlobalOff**&#124;**GlobalOn**  
 Arresta o avvia la profilatura per tutti i processi in una sessione di profilatura da riga di comando.  
  
 {**ThreadOff**&#124;**ThreadOn**}**:**`TID`  
 Arresta o avvia la profilatura per il thread specificato (solo metodo di strumentazione).  
  
## <a name="example"></a>Esempio  
 In questo esempio, il sottocomando **ProcessOff** viene usato per raccogliere dati di profilatura per l'avvio dell'applicazione.  
  
```  
; Initialize the profiler.  
VSPerfCmd.exe /Start:Trace /Output:Instrument.vsp   
; Start the instrumented application.  
; Stop profiling the process after startup.  
VSPerfCmd.exe /ProcessOff:12345  
; Shut down the target application.  
; Close the profiler.  
VSPerfCmd /Shutdown  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilatura di applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilatura di applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilatura di servizi](../profiling/command-line-profiling-of-services.md)



