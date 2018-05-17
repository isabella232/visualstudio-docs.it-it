---
title: AutoMark | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: c4de965e-0364-4f78-9936-1f509e85df74
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 922f6f40389277bed7da7b960fae341d7afe70da
ms.sourcegitcommit: eefffa7ebe339d1297cdc12f51a813e7849d7e95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/14/2018
---
# <a name="automark"></a>AutoMark
L'opzione **AutoMark** specifica il numero di millisecondi tra diverse raccolte di eventi del contatore delle prestazioni del software Windows. I contatori delle prestazioni di Windows sono specificati nell'opzione **WinCounter**.  
  
 Nella riga di comando può essere specificata una sola opzione **AutoMark**. Si noti che l'intervallo di campionamento di **WinCounter** specificato da **AutoMark** è indipendente dell'intervallo di campionamento principale.  
  
## <a name="syntax"></a>Sintassi  
  
```cmd  
VSPerfCmd.exe /Start:Method /WinCounter:Path /AutoMark:Milliseconds  
```  
  
#### <a name="parameters"></a>Parametri  
 `Milliseconds`  
 Specifica il numero di millisecondi tra le raccolte di eventi dei contatori delle prestazioni di Windows.  
  
## <a name="required-options"></a>Opzioni obbligatorie  
 **WinCounter:** `Path`  
 Specifica il contatore delle prestazioni di Windows da raccogliere. Quando si usa il metodo di strumentazione è possibile specificare più contatori di Windows. Quando si usa il metodo di campionamento è possibile specificare solo un contatore del software. L'opzione **WinCounter** deve essere specificata in una riga di comando che contiene l'opzione **Start**.  
  
## <a name="example"></a>Esempio  
 In questo esempio viene impostato un intervallo di campionamento di 1000 millisecondi per due contatori delle prestazioni di Windows.  
  
```cmd  
VSPerfCmd.exe /Start:Trace /Output:TestApp.exe.vsp /WinCounter:"\Process(*)\% Processor Time" /WinCounter:"\ASP.NET\Pages/sec" /AutoMark:1000  
VSPerfCmd.exe /Launch:TestApp.exe  
```  
  
## <a name="see-also"></a>Vedere anche  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilatura di applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilatura di applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilatura di servizi](../profiling/command-line-profiling-of-services.md)