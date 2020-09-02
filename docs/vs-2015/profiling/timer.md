---
title: Timer | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 1971868e-89fa-4452-8ee7-76e4daf31b66
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1e5f6c6db903b3ecced2ac3ebc4aaa0a3e60910c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68145506"
---
# <a name="timer"></a>Timer
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L'opzione **Timer** di VSPerfCmd.exe imposta l'evento di profilatura campionato su cicli del clock del processore e, facoltativamente, modifica il numero di cicli in un intervallo di campionamento dal valore predefinito di 10.000.000. In un processore da 1 GH (un gigahertz), un valore di 10.000.000 cicli di clock è pari a circa 100 campioni al secondo. Il numero minimo di cicli che è possibile specificare è 50.000.  
  
 L'opzione **Timer** può essere usata solo quando si usa il metodo di profilatura del campionamento e può essere usata solo in una riga di comando che include anche l'opzione **Launch** o **Attach**.  
  
 Per impostazione predefinita, l'evento di campionamento del profiler è impostato sui cicli del clock del processore e l'intervallo di campionamento è impostato su 10.000.000. Le opzioni **Timer**, **PF**, **Sys** e **Counter** consentono di impostare l'evento di campionamento e l'intervallo di campionamento. L'opzione **GC** raccoglie dati di memoria .NET in corrispondenza di ogni evento di allocazione e di Garbage Collection. È possibile specificare solo una di queste opzioni in una riga di comando.  
  
 L'evento di campionamento e l'intervallo di campionamento possono essere impostati solo nella prima riga di comando che include un'opzione **Launch** o **Attach**.  
  
## <a name="syntax"></a>Sintassi  
  
```  
VSPerfCmd.exe {/Launch:AppName|/Attach:PID} /Timer[:Cycles] [Options]  
```  
  
#### <a name="parameters"></a>Parametri  
 `Cycles`  
 Un valore di tipo Integer che specifica il numero di cicli del clock del processore in un intervallo di campionamento. Se `Cycles` non è specificato, l'intervallo sarà impostato su 10.000.000. Specificare il valore senza virgole.  
  
## <a name="required-options"></a>Opzioni obbligatorie  
 L'opzione **Timer** può essere specificata solo in una riga di comando che include una delle opzioni seguenti.  
  
 **Avvia:**`AppName`  
 Avvia il profiler e l'applicazione specificata da `AppName`.  
  
 **Connetti:**`PID`  
 Collega il profiler al processo specificato dall'ID di processo (`PID`).  
  
## <a name="invalid-options"></a>Opzioni non valide  
 Le opzioni seguenti non possono essere specificate nella stessa riga di comando che include **Timer**.  
  
 **PF**[**:** `Events` ]  
 Imposta l'evento di campionamento sugli errori di pagina e, facoltativamente, imposta l'intervallo di campionamento su `Events`. L'intervallo PF predefinito è 10.  
  
 **Sys**[**:** `Events` ]  
 Imposta l'evento di campionamento su chiamate del sistema operativo e, facoltativamente, imposta l'intervallo di campionamento su `Events`. L'intervallo Sys predefinito è 10.  
  
 **Contatore**[**:** `Name,Reload,FriendlyName` ]  
 Imposta l'evento di campionamento sul contatore delle prestazioni della CPU specificato da `Name` e imposta l'intervallo di campionamento su `Reload`.  
  
 **GC**[**:**{**Allocation**&#124;**Lifetime**}]  
 Raccoglie dati di memoria .NET. Per impostazione predefinita (**allocazione**), i dati vengono raccolti a ogni evento di allocazione della memoria. Quando viene specificato il parametro **Lifetime** , i dati vengono raccolti anche in corrispondenza di ogni evento Garbage Collection.  
  
## <a name="example"></a>Esempio  
 Questo esempio illustra come impostare l'intervallo di campionamento del profiler su 1.000.000 cicli del processore.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /Timer:1000000  
```  
  
## <a name="see-also"></a>Vedere anche  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilatura di applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilatura di applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilatura di servizi](../profiling/command-line-profiling-of-services.md)
