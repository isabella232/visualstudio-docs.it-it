---
title: Gestire i risultati dei test di carico
description: Informazioni su come gestire i dati raccolti durante un test di carico, archiviati nel database del Risultati test di SQL carico.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, results repository
- results, load test
- load test results, repository
- Load Test Results Repository
ms.assetid: 1cd63c4b-4f74-4133-b675-5e8fbeab25f3
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: 407e265424863d7018fc6b3e12fc23bddd0a9812
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122139907"
---
# <a name="manage-load-test-results-in-the-load-test-results-repository"></a>Gestire i risultati dei test di carico nel repository dei risultati del test di carico

Quando si eseguono i test di carico, le informazioni raccolte durante l'esecuzione possono essere memorizzate nel *repository dei risultati del test di carico*, che è un database SQL. Il repository dei risultati del test di carico contiene i dati del contatore delle prestazioni e tutte le informazioni sugli errori registrati. Il database che funge da repository dei risultati viene creato durante l'installazione dei controller o automaticamente alla prima esecuzione locale di un test di carico. Per un'esecuzione locale, il database verrà creato automaticamente se lo schema del test di carico non è presente.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Se si modifica la stringa di connessione del database dei risultati del controller per utilizzare un altro server, sarà necessario che sul nuovo server venga eseguito lo *script loadtestresultsrepository.sql* per creare lo schema.

Visual Studio Enterprise fornisce insiemi di contatori denominati che raccolgono contatori delle prestazioni comuni basati su una tecnologia. Tali insiemi sono utili quando si analizza un server IIS, un server ASP.NET o un server SQL. Tutti i dati raccolti con gli insiemi di contatori vengono memorizzati nel repository dei risultati del test di carico.

> [!IMPORTANT]
> Esiste una differenza tra un insieme di contatori e i dati del contatore delle prestazioni. Un insieme di contatori rappresenta dei metadati. Definisce un gruppo di contatori delle prestazioni da raccogliere da un computer che sta eseguendo un determinato ruolo, come un server IIS o SQL Server. L'insieme di contatori fa parte della definizione del test di carico. I dati del contatore delle prestazioni vengono raccolti in base agli insiemi di contatori, al mapping dell'insieme dei contatori a un determinato computer e alla velocità di campionamento.

## <a name="sql-server-versions"></a>Versioni di SQL Server

Per usare i test di carico, è possibile utilizzare SQL Server Express LocalDB, che viene installato con Visual Studio. È il server di database predefinito per i test di carico (inclusa l'integrazione di Microsoft Excel). SQL Server Express LocalDB è una modalità di esecuzione di SQL Server Express destinata agli sviluppatori di programmi. L'installazione di SQL Server Express LocalDB comporta la copia di un set minimo di file necessari ad avviare il motore di database di SQL Server.

Se il team prevede un uso intensivo del database o i progetti diventano troppo grandi per SQL Server Express LocalDB, considerare la possibilità di eseguire l'aggiornamento a SQL Express o alla versione completa di SQL Server per aumentare il potenziale di scalabilità. Se si esegue l'aggiornamento di SQL Server, i file LDF e MDF di SQL Server Express LocalDB vengono archiviati nella cartella del profilo utente. Questi file possono essere utilizzati per importare il database del test di carico in SQL Server Express o SQL Server.

## <a name="load-test-results-store-considerations"></a>Considerazioni sull'archivio dei risultati del test di carico

Quando è installato Visual Studio Enterprise, l'archivio dei risultati dei test di carico viene configurato per l'uso di un'istanza di SQL Express installata nel computer. SQL Express è limitato all'utilizzo di un massimo di 4 GB di spazio su disco. Se si prevede di eseguire molti test di carico in un lungo periodo di tempo, è consigliabile considerare la possibilità di configurare l'archivio dei risultati del test di carico in modo che venga utilizzata un'istanza del prodotto SQL Server completo, se disponibile.

## <a name="load-test-analyzer-tasks"></a>Attività dell'Analizzatore test di carico

|Attività|Argomenti correlati|
|-|-----------------------|
|**Configurare un repository dei risultati del test di carico**: è possibile configurare un repository dei risultati del test di carico in un database SQL. **Nota:** un repository del test di carico può essere creato anche quando si installa un test controller. Per altre informazioni, vedere [Installare e configurare agenti di test](../test/lab-management/install-configure-test-agents.md).||
|**Selezione e visualizzazione di un repository dei risultati:** è possibile selezionare un repository dei risultati specifico. La scelta non è limitata a un archivio dei risultati locale. Spesso i test di carico vengono eseguiti su un insieme remoto di computer agente. I risultati ottenuti dai computer agente o locale possono essere memorizzati in qualsiasi server SQL in cui sia stato creato un archivio dei risultati del test di carico. In entrambi i casi è necessario identificare la posizione in cui archiviare i risultati del test di carico utilizzando la finestra **Gestisci controller test**.|-   [Procedura: Selezionare un repository dei risultati del test di carico](../test/how-to-select-a-load-test-results-repository.md)<br />-   [Procedura: Accedere ai risultati dei test di carico per l'analisi](../test/how-to-access-load-test-results-for-analysis.md)|
|**Eliminare un risultato del test di carico dal repository**: è possibile rimuovere un risultato del test di carico dall'**Editor test di carico** utilizzando la finestra di dialogo **Apri e gestisci risultati test di carico**.|-   [Procedura: Eliminare i risultati del test di carico da un repository](../test/how-to-delete-load-test-results-from-a-repository.md)|
|**Importare ed esportare risultati in un repository:** è possibile importare ed esportare risultati del test di carico dall'**Editor test di carico**.|-   [Procedura: Importare i risultati del test di carico in un repository](../test/how-to-import-load-test-results-into-a-repository.md)<br />-   [Procedura: Esportare i risultati dei test di carico da un repository](../test/how-to-export-load-test-results-from-a-repository.md)|

## <a name="related-tasks"></a>Attività correlate

[Analizzare i risultati dei test di carico](../test/analyze-load-test-results-using-the-load-test-analyzer.md)

È possibile visualizzare i risultati di un test di carico in esecuzione e di un test di carico completato tramite l'**analizzatore test di carico**.

## <a name="see-also"></a>Vedi anche

- [Analizzare i risultati dei test di carico](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Procedura: Accedere ai risultati dei test di carico per l'analisi](../test/how-to-access-load-test-results-for-analysis.md)
