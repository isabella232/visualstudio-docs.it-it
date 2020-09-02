---
title: TargetCLR | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: f9732480-287f-40f1-a4ff-b112e143b940
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1e4ca52f631b3e2de9c01daab7e6268c42f20268
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68145615"
---
# <a name="targetclr"></a>TargetCLR
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L'opzione **TargetCLR** specifica la versione di Common Language Runtime (CLR) da sottoporre a profilatura quando in un'applicazione è caricata più di una versione di CLR.  
  
 Per impostazione predefinita, gli strumenti di profilatura di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] vengono applicati alla prima versione di CLR caricata dall'applicazione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
VSPerfCmd.exe {/Launch:AppName | /Attach:PID} /TargetCLR[:ClrVersion] [Options]   
```  
  
#### <a name="parameters"></a>Parametri  
 `ClrVersion`  
 Numero di versione di CLR. Usare il formato di versione **vN.N.NNNNN**.  
  
## <a name="required-options"></a>Opzioni obbligatorie  
 L'opzione **TargetCLR** può essere usata solo con le opzioni **Launch** o **Attach**.  
  
 **Avvia:**`AppName`  
 Avvia l'applicazione specificata e avvia la profilatura.  
  
 **Connetti:**`PID`  
 Avvia la profilatura del processo specificato.  
  
## <a name="example"></a>Esempio  
 In questo esempio, l'opzione TargetCLR viene usata per assicurarsi che venga sottoposta a profilatura la versione di CLR 4.0.11003.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /TargetCLR:v4.0.11003  
```
