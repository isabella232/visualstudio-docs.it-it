---
title: LineOff | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76082063-20ef-47ae-ad64-81b43b654865
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cf55f34b1ced4d76dcd45ea08514dfbb04ca582b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47526853"
---
# <a name="lineoff"></a>LineOff
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [LineOff](https://docs.microsoft.com/visualstudio/profiling/lineoff).  
  
Per impostazione predefinita, il profiler raccoglie i dati dei numeri di riga del codice sorgente e i dati di offset dei numeri di riga quando si usa il metodo di campionamento per la profilatura. L'opzione **LineOff** di VSPerfCmd disabilita la raccolta dei dati dei numeri di riga quando VSPerfCmd viene usato per avviare l'applicazione. I dati di profilatura vengono raccolti a livello di funzione quando si specifica l'opzione **LineOff**.  
  
 È possibile usare **LineOff** solo con l'opzione **Launch** e solo quando il profiler è stato inizializzato per eseguire il campionamento tramite l'opzione **Start**:**Sample**.  
  
## <a name="syntax"></a>Sintassi  
  
```  
VSPerfCmd.exe /Launch:AppName /LineOff [Options]  
```  
  
#### <a name="parameters"></a>Parametri  
 nessuno  
  
## <a name="required-options"></a>Opzioni obbligatorie  
 L'opzione **LineOff** può essere usata solo su una riga di comando che contiene l'opzione **Launch**.  
  
 **Launch:** `AppName`  
 Avvia l'applicazione specificata e inizia la profilatura con il metodo di campionamento.  
  
## <a name="example"></a>Esempio  
 Questo esempio illustra come avviare l'applicazione e il profiler e quindi disabilitare il campionamento a livello di riga.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /LineOff  
```  
  
## <a name="see-also"></a>Vedere anche  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilatura di applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilatura di applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilatura di servizi](../profiling/command-line-profiling-of-services.md)



