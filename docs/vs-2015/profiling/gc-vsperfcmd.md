---
title: GC (VSPerfCmd) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7c81e88b-a748-4cf5-a7a1-3429608e1b54
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4d13193ea49a2d96bb1bd6d4058457e48a58e5ff
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49213031"
---
# <a name="gc-vsperfcmd"></a>GC (VSPerfCmd)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L'opzione **GC** abilita la raccolta dei dati di allocazione della memoria e dei dati di durata degli oggetti di .NET Framework. L'opzione **GC** può essere usata solo con il metodo di profilatura del campionamento e solo con l'opzione **Launch**.  
  
 Quando si usa l'opzione **GC** il comando **/sampleon** di VSPerfClrEnv non è necessario.  
  
 Se non vengono specificati parametri o viene specificato il parametro **Allocation**, vengono raccolti solo i dati di allocazione della memoria di .NET Framework. Se viene specificato il parametro **Lifetime**, vengono raccolti sia i dati di allocazione della memoria di .NET Framework sia i dati di durata degli oggetti di .NET Framework.  
  
## <a name="syntax"></a>Sintassi  
  
```  
VSPerfCmd.exe /Launch:AppName /GC[:{Allocation|Lifetime}] [Options]  
```  
  
#### <a name="parameters"></a>Parametri  
 **Allocation**  
 Predefinita. Raccoglie i dati di allocazione della memoria di .NET Framework.  
  
 **Durata**  
 Raccoglie sia i dati di allocazione della memoria di .NET Framework, sia i dati di durata degli oggetti di .NET Framework.  
  
## <a name="required-options"></a>Opzioni obbligatorie  
 L'opzione **GC** può essere usata solo con l'opzione **Launch**.  
  
 **Launch:** `AppName`  
 Avvia l'applicazione specificata e inizia la profilatura con il metodo di campionamento.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene avviata un'applicazione e vengono raccolti i dati di allocazione della memoria di .NET Framework.  
  
```  
VSPerfCmd.exe /Launch:TestApp.exe /gc  
```  
  
## <a name="see-also"></a>Vedere anche  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilatura di applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilatura di applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilatura di servizi](../profiling/command-line-profiling-of-services.md)



