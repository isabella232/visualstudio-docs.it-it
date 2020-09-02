---
title: Come filtrare i report dalla riga di comando | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 6e9b140f-b44f-4a5c-bd65-d868ddc94023
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 3461965f0944200c44570cff5362aeeb143ed43c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85332250"
---
# <a name="how-to-filter-reports-from-the-command-line"></a>Procedura: Filtrare i report dalla riga di comando
Usando le opzioni del comando **VSPerfReport** è possibile filtrare i report per un intervallo di tempo specifico del file dei dati di profilatura o limitare i dati a uno o più processi o thread. Per altre informazioni su questo comando, vedere [VSPerfReport](../profiling/vsperfreport.md).

|Opzioni|Descrizione|
|-------------|-----------------|
|**StartTime:**[*valore*]|Mostra solo i dati raccolti dopo il valore (in millisecondi).|
|**EndTime:**[*valore*]|Mostra solo i dati raccolti prima del valore (in millisecondi).|
|**FilterFile:** `VSPFFile`|Specifica il percorso di un file di filtro generato dalla finestra **rapporto di prestazioni di Visual Studio** .|
|**MsFilter:**[*StartTime, Duration*]|Mostra solo i dati da `StartTime` fino alla durata `Duration` (in millisecondi).|
|**Processo:**[*PID*]|Mostra solo i dati del processo specificato.|
|**Thread:**[*ThreadID*]|Mostra solo i dati del thread specificato.|
|**Thread:**[*ThreadID, ProcessId*]|Mostra solo i dati del thread specificato associato al processo specificato.|
