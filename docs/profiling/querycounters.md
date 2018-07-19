---
title: QueryCounters | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 8059d4b2-af61-4a47-a6c2-8da5c0741c74
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9f3c3176ea0b865ecf4a433a7a0a22a316720229
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35257709"
---
# <a name="querycounters"></a>QueryCounters
L'opzione **QueryCounters** elenca i contatori delle prestazioni della CPU (hardware) disponibili nel computer.  
  
 **QueryCounters** deve essere l'unica opzione nella riga di comando.  
  
## <a name="syntax"></a>Sintassi  
  
```cmd  
VSPerfCmd.exe /QueryCounters  
```  
  
#### <a name="parameters"></a>Parametri  
 nessuno  
  
## <a name="remarks"></a>Note  
 Quando si usa il metodo di strumentazione, il profiler può raccogliere i valori di uno o più contatori delle prestazioni della CPU per ogni evento di raccolta dati. Quando si usa il metodo di campionamento per la profilatura, è possibile specificare un solo evento di contatore e il numero di occorrenze dell'evento da usare come intervallo di campionamento.  
  
 Processori diversi espongono contatori delle prestazioni della CPU differenti. Il profiler definisce un set di contatori generici utilizzabili per quasi tutti i processori. L'opzione **QueryCounters** elenca sia i nomi dei contatori generici sia i nomi dei contatori specifici del processore.  
  
## <a name="see-also"></a>Vedere anche  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Sottoporre a profilatura applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Sottoporre a profilatura applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Sottoporre a profilatura i servizi](../profiling/command-line-profiling-of-services.md)