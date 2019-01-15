---
title: 'Procedura: Filtrare report tramite la riga di comando | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 6e9b140f-b44f-4a5c-bd65-d868ddc94023
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2d53af6417a4eb3b78c6063455bf44e7243a13d7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53933515"
---
# <a name="how-to-filter-reports-from-the-command-line"></a>Procedura: Filtrare report tramite la riga di comando
Usando le opzioni del comando **VSPerfReport** è possibile filtrare i report per un intervallo di tempo specifico del file dei dati di profilatura o limitare i dati a uno o più processi o thread. Per altre informazioni su questo comando, vedere [VSPerfReport](../profiling/vsperfreport.md).  
  
|Opzioni|Description|  
|-------------|-----------------|  
|**StartTime:**[*Valore*]|Mostra solo i dati raccolti dopo il valore (in millisecondi).|  
|**EndTime:**[*Valore*]|Mostra solo i dati raccolti prima del valore (in millisecondi).|  
|**FilterFile:** `VSPFFile`|Specifica il percorso di un file di filtro generato dalla finestra **Visual Studio Performance Report**.|  
|**MsFilter:**[*OraInizio,Durata*]|Mostra solo i dati di `StartTime` fino alla lunghezza di `Duration` (in millisecondi).|  
|**Process:**[*IDprocesso*]|Mostra solo i dati del processo specificato.|  
|**Thread:**[*IDthread*]|Mostra solo i dati del thread specificato.|  
|**Thread:**[*IDthread,IDprocesso*]|Mostra solo i dati del thread specificato associato al processo specificato.|