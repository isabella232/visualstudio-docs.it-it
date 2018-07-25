---
title: Mark | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 1d72cef3-bb09-4bbb-8864-6ea0ab623ff9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 89a26a3a3729241cb4ec9180e6cb16f131194b86
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/07/2018
ms.locfileid: "34844794"
---
# <a name="mark"></a>Contrassegno
In *VSPerfCmd.exe* l'opzione **Mark** consente di inserire le informazioni specificate nel file di dati di profilatura. L'opzione Mark può essere elencata in un report di VSPerfReport separato o nella visualizzazione Contrassegni dell'interfaccia utente del profiler. È possibile usare **Mark** per specificare i punti di inizio e fine nel report e visualizzare i filtri.  
  
 L'opzione **Mark** deve essere l'unica opzione specificata nella riga di comando.  
  
## <a name="syntax"></a>Sintassi  
  
```cmd  
VSPerfCmd.exe /Mark:MarkID,[MarkName]  
```  
  
#### <a name="parameters"></a>Parametri  
 `MarkID`  
 Intero definito dall'utente elencato come ID contrassegno nelle visualizzazioni e nei report del profiler. `MarkID` non deve essere univoco.  
  
 `MarkName`  
 (Facoltativo) Stringa definita dall'utente elencata come Nome contrassegno nelle visualizzazioni e nei report del profiler. Se non si specifica `MarkName`, il campo Nome contrassegno dell'elenco dei contrassegni sarà vuoto. Racchiudere le stringhe che contengono spazi o barre ("/") tra virgolette.  
  
## <a name="example"></a>Esempio  
 Questo esempio inserisce un contrassegno con ID 123 e il nome di contrassegno "TestMark".  
  
```cmd  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
VSPerfCmd.exe /Mark:123,TestMark  
```  
  
## <a name="see-also"></a>Vedere anche  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Sottoporre a profilatura applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Sottoporre a profilatura applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Sottoporre a profilatura i servizi](../profiling/command-line-profiling-of-services.md)