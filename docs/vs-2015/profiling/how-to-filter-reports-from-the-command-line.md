---
title: 'Procedura: Filtrare report tramite la riga di comando | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6e9b140f-b44f-4a5c-bd65-d868ddc94023
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 14be02ecf293cfb141b671917a715c8013009d2e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47519754"
---
# <a name="how-to-filter-reports-from-the-command-line"></a>Procedura: filtrare rapporti tramite la riga di comando
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [procedura: filtrare i report dalla riga di comando](https://docs.microsoft.com/visualstudio/profiling/how-to-filter-reports-from-the-command-line).  
  
Usando le opzioni del comando **VSPerfReport** è possibile filtrare i report per un intervallo di tempo specifico del file dei dati di profilatura o limitare i dati a uno o più processi o thread. Per altre informazioni su questo comando, vedere [VSPerfReport](../profiling/vsperfreport.md).  
  
|Opzioni|Descrizione|  
|-------------|-----------------|  
|**StartTime:**[*Valore*]|Mostra solo i dati raccolti dopo il valore (in millisecondi).|  
|**EndTime:**[*Valore*]|Mostra solo i dati raccolti prima del valore (in millisecondi).|  
|**FilterFile:** `VSPFFile`|Specifica il percorso di un file di filtro generato dalla finestra **Visual Studio Performance Report**.|  
|**MsFilter:**[*OraInizio,Durata*]|Mostra solo i dati di `StartTime` fino alla lunghezza di `Duration` (in millisecondi).|  
|**Process:**[*IDprocesso*]|Mostra solo i dati del processo specificato.|  
|**Thread:**[*IDthread*]|Mostra solo i dati del thread specificato.|  
|**Thread:**[*IDthread,IDprocesso*]|Mostra solo i dati del thread specificato associato al processo specificato.|



