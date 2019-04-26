---
title: 'Procedura: Filtrare report tramite la riga di comando | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 6e9b140f-b44f-4a5c-bd65-d868ddc94023
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1c90ca0bea8126308b1260258044cece53218fb3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62973786"
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