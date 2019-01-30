---
title: PF | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: cdc0a094-a986-4629-bd1c-dd5fdca323dc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c339ae070f4f60fc051883ec27ecebba038f1a38
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54966647"
---
# <a name="pf"></a>PF
L'opzione *PF* di **VSPerfCmd.exe** imposta l'evento di profilatura campionato sugli errori di pagina e modifica facoltativamente il numero di errori di pagina in un intervallo di campionamento dal valore predefinito di 10.  
  
> [!NOTE]
>  L'opzione **PF** non può essere usata in sistemi a 64 bit.  
  
**PF** può essere usata solo in una riga di comando che contiene anche l'opzione **Launch** o **Attach**.  
  
 Per impostazione predefinita, l'evento di campionamento è impostato sui cicli del clock del processore non interrotti e l'intervallo di campionamento è impostato su 10.000.000. Le opzioni **Timer**, **PF**, **Sys** e **Counter** consentono di impostare l'evento di campionamento e l'intervallo di campionamento. L'opzione **GC** raccoglie dati di memoria .NET in corrispondenza di ogni evento di allocazione e di Garbage Collection. È possibile specificare solo una di queste opzioni in una riga di comando.  
  
 L'evento di campionamento e l'intervallo di campionamento possono essere impostati solo nella prima riga di comando che include un'opzione **Launch** o **Attach**.  
  
## <a name="syntax"></a>Sintassi  
  
```cmd  
VSPerfCmd.exe {/Launch:AppName|/Attach:PID} /PF[:Events] [Options]  
```  
  
#### <a name="parameters"></a>Parametri  
 `Events`  
 Valore intero che specifica il numero di eventi di errore di pagina in un intervallo di campionamento. Se non si specifica `Events`, l'intervallo viene impostato su 10.  
  
## <a name="required-options"></a>Opzioni obbligatorie  
 L'opzione **PF** può essere specificata solo in una riga di comando che include una delle opzioni seguenti.  
  
 **Launch:** `AppName`  
 Avvia il profiler e l'applicazione specificata da AppName.  
  
 **Attach:** `PID`  
 Collega il profiler al processo specificato da AppName.  
  
## <a name="invalid-options"></a>Opzioni non valide  
 Le opzioni seguenti non possono essere specificate nella stessa riga di comando che include **PF**.  
  
 **Timer**[**:**`Cycles`]  
 Imposta l'evento di campionamento sui cicli di clock del processore e, facoltativamente, imposta l'intervallo di campionamento su `Cycles`. L'intervallo Timer predefinito è 10.000.000.  
  
 **Sys**[**:**`Events`]  
 Imposta l'evento di campionamento per le chiamate dall'applicazione profilata al kernel del sistema operativo (syscall) e imposta facoltativamente l'intervallo di campionamento su `Events`. L'intervallo Sys predefinito è 10.  
  
 **Counter:** `Name`[`,Reload`[`,FriendlyName`]]  
 Imposta l'evento di campionamento sul contatore delle prestazioni della CPU specificato da `Name` e imposta l'intervallo di campionamento su `Reload`.  
  
 **GC**[**:**{**Allocation**&#124;**Lifetime**}]  
 Raccoglie dati di memoria .NET. Per impostazione predefinita, (**Allocation**), i dati vengono raccolti in corrispondenza di ogni evento di allocazione di memoria. Quando si specifica il parametro **Lifetime**, i dati vengono raccolti anche in corrispondenza di ogni evento di Garbage Collection.  
  
## <a name="example"></a>Esempio  
 Questo esempio illustra come impostare l'evento di campionamento di profilatura per gli errori di pagina e imposta l'intervallo di campionamento su 20 errori di pagina.  
  
```cmd  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /PF:20  
```  
  
## <a name="see-also"></a>Vedere anche  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Sottoporre a profilatura applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Sottoporre a profilatura applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Sottoporre a profilatura i servizi](../profiling/command-line-profiling-of-services.md)