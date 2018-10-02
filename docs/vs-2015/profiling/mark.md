---
title: Mark | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1d72cef3-bb09-4bbb-8864-6ea0ab623ff9
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fb1b5d35e11cd3317db473330d908e0f7300d576
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47540880"
---
# <a name="mark"></a>Contrassegno
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [Mark](https://docs.microsoft.com/visualstudio/profiling/mark).  
  
L'opzione **Mark** di VSPerfCmd.exe consente di inserire le informazioni specificate nel file di dati di profilatura. L'opzione Mark può essere elencata in un report di VSPerfReport separato o nella visualizzazione Contrassegni dell'interfaccia utente del profiler. È possibile usare **Mark** per specificare i punti di inizio e fine nel report e visualizzare i filtri.  
  
 L'opzione **Mark** deve essere l'unica opzione specificata nella riga di comando.  
  
## <a name="syntax"></a>Sintassi  
  
```  
VSPerfCmd.exe /Mark:MarkID,[MarkName]  
```  
  
#### <a name="parameters"></a>Parametri  
 `MarkID`  
 Intero definito dall'utente elencato come ID contrassegno nelle visualizzazioni e nei report del profiler. `MarkID` non deve essere univoco.  
  
 `MarkName`  
 (Facoltativo) Stringa definita dall'utente elencata come Nome contrassegno nelle visualizzazioni e nei report del profiler. Se non si specifica `MarkName`, il campo Nome contrassegno dell'elenco dei contrassegni sarà vuoto. Racchiudere le stringhe che contengono spazi o barre ("/") tra virgolette.  
  
## <a name="example"></a>Esempio  
 Questo esempio inserisce un contrassegno con ID 123 e il nome di contrassegno "TestMark".  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
VSPerfCmd.exe /Mark:123,TestMark  
```  
  
## <a name="see-also"></a>Vedere anche  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilatura di applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilatura di applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilatura di servizi](../profiling/command-line-profiling-of-services.md)



