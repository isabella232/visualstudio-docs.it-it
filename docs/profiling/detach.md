---
title: Detach | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: d9d1b52c-7f28-467d-b1e0-512afc4e46c9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 91b93eb99b1068e1695e26136eacc6abf2886774
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/05/2018
ms.locfileid: "34764491"
---
# <a name="detach"></a>Detach
L'opzione **Detach** di VSPerfCmd.exe disconnette il profiler dai processi specificati o da tutti i processi se non ne vengono specificati. La profilatura deve essere inizializzata usando il metodo di campionamento.  
  
 La profilatura avviata con l'opzione **Launch** o **Attach** può essere disconnessa con **Detach**. Il profiler può essere connesso nuovamente usando comandi **Attach** successivi.  
  
 **Detach** non consente di chiudere il file di dati di profilatura. Usare l'opzione **Shutdown** per terminare la profilatura e chiudere il file di dati.  
  
> [!NOTE]
>  Se l'opzione **Start** è stata specificata con l'opzione **Crosssession**, eventuali chiamate a **VSPerfCmd /Attach** o a **VSPerfCmd /Detach** devono specificare anche **Crosssession**.  
  
## <a name="syntax"></a>Sintassi  
  
```cmd  
VSPerfCmd.exe /Detach[:PIDs|ProcessNames]  
```  
  
#### <a name="parameters"></a>Parametri  
 `PIDs|ProcessNames`  
 `PID` - Identificatore numerico del sistema di uno o più processi.  
  
 `ProcessNames` - Nome del processo. Se si eseguono più istanze del processo denominato, i risultati sono imprevedibili.  
  
 Se si specificano più processi, separarli con virgole.  
  
 Se non viene specificato alcun processo, il profiler viene disconnesso da tutti i processi profilati.  
  
## <a name="valid-options"></a>Opzioni valide  
 Le seguenti opzioni di **VSPerfCmd** possono essere combinate con l'opzione **Attach** in una singola riga di comando.  
  
 **Crosssession**  
 Consente la profilatura delle applicazioni in sessioni diverse da quella di accesso. Obbligatoria se l'opzione **Start** è stata specificata con l'opzione **Crosssession**.  
  
## <a name="example"></a>Esempio  
 In questo esempio il comando **Detach** sospende la profilatura e il comando **Shutdown** chiude il file di dati del profiler.  
  
```cmd  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
;REM Excercise the application  
VSPerfCmd.exe /Detach  
VSPerfCmd.exe /Shutdown  
```  
  
## <a name="see-also"></a>Vedere anche  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Sottoporre a profilatura applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Sottoporre a profilatura applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Sottoporre a profilatura i servizi](../profiling/command-line-profiling-of-services.md)