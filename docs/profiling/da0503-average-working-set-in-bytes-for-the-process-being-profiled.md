---
title: DA0503 - Working set medio in byte per il processo profilato | Microsoft Docs
description: Questo messaggio indica la quantità media di memoria fisica, in byte, usata attualmente dal processo espressa in byte (il working set).
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.503
- vs.performance.DA0503
- vs.performance.rules.DA0503
ms.assetid: 9047a494-eaaf-4679-b422-c64e8bde77a4
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: dbfee079945441f41069d34d1bc3cd36e4b9896a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122142143"
---
# <a name="da0503-average-working-set-in-bytes-for-the-process-being-profiled"></a>DA0503: Working set medio in byte del processo sottoposto a profilatura

|Elemento|valore|
|-|-|
|ID regola|DA0503|
|Category|Monitoraggio risorse|
|Metodo di profilatura|Tutti|
|Message|Dati raccolti a solo scopo informativo. Il contatore working set di processo misura l'utilizzo della memoria fisica da parte del processo sottoposto a profilatura. Il valore restituito corrisponde al valore medio rilevato per tutti gli intervalli di misurazione.|
|Tipo regola|Informazioni|

 Quando si esegue la profilatura tramite i metodi di campionamento, memoria .NET o conflitto di risorse, è necessario raccogliere almeno 10 campioni per attivare questa regola.

## <a name="rule-description"></a>Descrizione della regola
 Questo messaggio indica la quantità media di memoria fisica, in byte, usata attualmente dal processo espressa in byte (il working set). Il working set del processo rappresenta pagine dallo spazio degli indirizzi del processo che attualmente risiedono nella memoria fisica.

 Il valore indicato include pagine residenti da segmenti di memoria condivisa a cui ha fatto riferimento il processo. Le DLL condivise a cui fa riferimento il processo sono incluse nei segmenti di memoria condivisa contati. Il valore del working set del processo può essere maggiore della quantità di memoria virtuale allocata dal processo a causa dei segmenti di memoria condivisa.

 Il valore indicato è il valore medio fra tutti gli intervalli di misurazione nei quali il processo sottoposto a profilatura era attivo.

 La dimensione del working set del processo riflette la quantità di memoria virtuale attivamente usata dal processo stesso. Dipende anche dalla quantità di memoria fisica (o RAM) disponibile per eseguire l'applicazione e dai conflitti tra altri processi in esecuzione per tale memoria fisica. Se la memoria fisica è vincolata, il valore del working set del processo è soggetto a variazioni significative in quanto il sistema operativo tenta di bilanciare l'utilizzo della memoria tra i processi attivi rimuovendo periodicamente le pagine quasi inattive dai working set del processo.

 Per altre informazioni sui working set di processo, vedere [Working Set](/windows/win32/memory/working-set) nella documentazione relativa alla gestione della memoria di Windows in MSDN.

## <a name="how-to-use-rule-data"></a>Come usare i dati della regola
 Usare il valore della regola per confrontare le prestazioni di versioni o build diverse del programma o per ottenere informazioni sulle prestazioni dell'applicazione in scenari di profilatura diversi.

 Fare doppio clic sul messaggio nella finestra Elenco errori per passare alla [visualizzazione Contrassegni](../profiling/marks-view.md) dei dati di profilatura. Individuare le colonne **Processo\Working Set** e **Memoria\Pagine/sec**. Confrontare le due colonne e determinare se sono presenti fasi specifiche di esecuzione del programma che sembrano associate ad attività I/O di paging aumentate.
