---
title: Args | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 20c35949-1f29-4282-ac75-4e6c237d71bc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 40de97d134f24832c56b0cda7b8462a3f8f8c937
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53845538"
---
# <a name="args"></a>Args
L'opzione **Args** di VSPerfCmd.exe specifica un elenco di argomenti passati all'applicazione di destinazione del sottocomando **Launch**.  
  
 **Args** può essere usata solo quando è specificato anche **Launch** nella riga di comando. **Args** è facoltativa quando è specificato **Launch**.  
  
## <a name="syntax"></a>Sintassi  
  
```cmd  
VSPerfCmd.exe /Launch:AppName /Args:Arguments [Options]  
```  
  
#### <a name="parameters"></a>Parametri  
 `Arguments`  
 Un elenco di argomenti per l'applicazione di destinazione del comando **Launch**.  
  
## <a name="required-options"></a>Opzioni obbligatorie  
 **Launch:** `AppName`  
 Avvia l'applicazione specificata e inizia la profilatura con il metodo di campionamento.  
  
## <a name="example"></a>Esempio  
 L'esempio seguente usa l'opzione **Args** per passare gli argomenti a TestApp.exe.  
  
```cmd  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /Args:"123, 'Hello World'"  
```  
  
## <a name="see-also"></a>Vedere anche  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilatura di applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilatura di applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilatura di servizi](../profiling/command-line-profiling-of-services.md)