---
title: Filtro delle visualizzazioni dei rapporti di prestazioni | Microsoft Docs
description: Informazioni su come la finestra Filtro visualizzazione report del profiler si trova nella parte superiore della finestra Report di prestazioni.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, Profiler Report view filter
- Profiler Report View filter, profiling tools
ms.assetid: 35f89d86-4683-4db1-aa0c-ae0ce65fa524
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: e7ac70b0b84bb9425f64123f11bfb6fac9127d9da38c35107bfa59a5df941962
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121354580"
---
# <a name="performance-report-view-filter"></a>Filtro delle visualizzazioni dei rapporti di prestazioni
La **finestra Profiler Report View Filter (Filtro** visualizzazione report profiler) si trova nella parte superiore della **finestra Report di** prestazioni. Se non è visibile, fare clic sul pulsante **Mostra filtro**.

 È possibile modificare ogni clausola filtro per perfezionare i risultati. Nel generatore di filtri sono disponibili le colonne seguenti.

|Elemento del filtro|Descrizione|
|-----------------|-----------------|
|And/Or|Scegliere **And** se questa clausola e la successiva devono essere entrambe vere (true) per restituire un risultato. Scegliere **Or** se questa clausola o la successiva può essere vera (true) per restituire un risultato.|
|Campo|Selezionare il campo da usare nella clausola filtro dall'elenco dei campi dati disponibili nel file di rapporto corrente.|
|Operatore|Scegliere l'operatore che specifica la relazione da impostare tra il campo e il valore.<br /><br /> =    Uguale a<br /><br /> <>  Non uguale a<br /><br /> <    Minore di<br /><br /> >    Maggiore di<br /><br /> <=  Minore o uguale a<br /><br /> >=  Maggiore o uguale a|
|Valore|Selezionare o immettere il valore da cercare. Per alcuni campi è presente l'elenco dei valori disponibili.|

 È possibile aggiungere clausole filtro fino a ottenere risultati ottimali. Fare clic su **Esegui filtro** per applicare il filtro al file di dati.

 Dalla visualizzazione del rapporto **Contrassegni** è possibile generare clausole filtro per limitare i dati da includere nelle visualizzazioni dei rapporti ai dati raccolti tra due contrassegni. Selezionare i contrassegni da usare come inizio e fine dei dati per il rapporto, quindi fare clic con il pulsante destro del mouse e selezionare **Aggiungi filtro in contrassegni** o **Aggiungi filtro in timestamp**. Entrambi i filtri limitano i dati nel file di dati corrente allo stesso intervallo. L'opzione **Aggiungi filtro in contrassegni** può essere applicata ad altri file con estensione vsp.

 Per salvare il filtro, fare clic **su Esporta** filtro sulla barra degli strumenti **Report** di prestazioni e quindi specificare un percorso e un nome file per . *File vspf.* Per caricare un filtro salvato in precedenza, fare clic su **Importa filtro** e individuare il file del filtro salvato. I file di filtro possono essere usati anche per filtrare file di dati nei computer in cui sono installati gli strumenti di profilatura autonomi. Per altre informazioni, vedere [VSPerfReport](../profiling/vsperfreport.md).

## <a name="see-also"></a>Vedi anche
- [Analizzare i dati degli strumenti per le prestazioni](../profiling/analyzing-performance-tools-data.md)
- [VSPerfReport](../profiling/vsperfreport.md)
