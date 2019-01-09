---
title: QueryCounters | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 8059d4b2-af61-4a47-a6c2-8da5c0741c74
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a9a4e3c9f80ed437eb4476833776c5c19689c69a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53866920"
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