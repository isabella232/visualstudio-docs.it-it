---
title: 'Procedura: Filtrare report tramite la riga di comando | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 6e9b140f-b44f-4a5c-bd65-d868ddc94023
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1bd6462f9159a2926c6dfa45dcadff860cce9ca1
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778934"
---
# <a name="how-to-filter-reports-from-the-command-line"></a>Procedura: Filtrare i report dalla riga di comando
Usando le opzioni del comando **VSPerfReport** è possibile filtrare i report per un intervallo di tempo specifico del file dei dati di profilatura o limitare i dati a uno o più processi o thread. Per altre informazioni su questo comando, vedere [VSPerfReport](../profiling/vsperfreport.md).

|Opzioni|Descrizione|
|-------------|-----------------|
|**Ora inizio:**[*Valore*]|Mostra solo i dati raccolti dopo il valore (in millisecondi).|
|**EndTime:**[*Valore*]|Mostra solo i dati raccolti prima del valore (in millisecondi).|
|**FilterFile:** `VSPFFile`|Specifica il percorso di un file di filtro generato dalla finestra Report di prestazioni di **Visual Studio.**|
|**MsFilter:**[*StartTime,Durata*]|Mostra solo i dati da `StartTime` fino alla durata `Duration` (in millisecondi).|
|**Processo:**[*Pid*]|Mostra solo i dati del processo specificato.|
|**Thread:**[*ThreadID*]|Mostra solo i dati del thread specificato.|
|**Thread:**[*ThreadID,IDProcesso*]|Mostra solo i dati del thread specificato associato al processo specificato.|
