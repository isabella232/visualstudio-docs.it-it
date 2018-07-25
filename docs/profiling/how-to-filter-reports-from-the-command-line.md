---
title: 'Procedura: Filtrare report tramite la riga di comando | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 6e9b140f-b44f-4a5c-bd65-d868ddc94023
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2c173fb5cdea4c18f3d470bd1e92bd7f9b68a62e
ms.sourcegitcommit: 1b9c1e333c2f096d35cfc77e846116f8e5054557
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/06/2018
ms.locfileid: "34814567"
---
# <a name="how-to-filter-reports-from-the-command-line"></a>Procedura: Filtrare i report dalla riga di comando
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