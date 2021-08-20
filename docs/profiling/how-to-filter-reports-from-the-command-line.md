---
title: Filtrare report tramite la riga di comando | Microsoft Docs
description: Usare VSPerfReport.exe per limitare la creazione di report a un periodo di tempo specifico o a processi e thread selezionati. Questo articolo elenca le opzioni, con le descrizioni.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 6e9b140f-b44f-4a5c-bd65-d868ddc94023
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 39471e7006cfe49a8c03c0d4d0f34bb3b149aad6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122060999"
---
# <a name="how-to-filter-reports-from-the-command-line"></a>Procedura: Filtrare i report dalla riga di comando
Usando le opzioni del comando **VSPerfReport** è possibile filtrare i report per un intervallo di tempo specifico del file dei dati di profilatura o limitare i dati a uno o più processi o thread. Per altre informazioni su questo comando, vedere [VSPerfReport](../profiling/vsperfreport.md).

|Opzioni|Descrizione|
|-------------|-----------------|
|**StartTime:**[*Valore*]|Mostra solo i dati raccolti dopo il valore (in millisecondi).|
|**EndTime:**[*Valore*]|Mostra solo i dati raccolti prima del valore (in millisecondi).|
|**FilterFile:** `VSPFFile`|Specifica il percorso di un file di filtro generato dalla finestra Visual Studio **report di** prestazioni.|
|**MsFilter:**[*StartTime,Duration*]|Mostra solo i dati da `StartTime` fino alla durata `Duration` (in millisecondi).|
|**Processo:**[*Pid*]|Mostra solo i dati del processo specificato.|
|**Thread:**[*ThreadID*]|Mostra solo i dati del thread specificato.|
|**Thread:**[*ThreadID, ProcessID*]|Mostra solo i dati del thread specificato associato al processo specificato.|
