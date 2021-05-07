---
title: Compilazione e creazione di build
description: Questo articolo descrive come creare e compilare progetti e soluzioni in Visual Studio per Mac
ms.topic: overview
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/03/2021
ms.assetid: FB253757-DB00-4889-A6BF-E44722E25BD1
ms.openlocfilehash: a24c57907afedb4f02068a071d2c9f81eb8962bb
ms.sourcegitcommit: dd2fc6e03a789c044f8438096b8f112e4dba5557
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/06/2021
ms.locfileid: "108640974"
---
# <a name="compiling-and-building-in-visual-studio-for-mac"></a>Compilazione e creazione di build in Visual Studio per Mac

Visual Studio per Mac consente di compilare applicazioni e creare assembly durante lo sviluppo del progetto. È importante compilare spesso il codice per consentire di identificare rapidamente tipi non corrispondenti, sintassi errata, parole chiave non digitate correttamente e altri errori in fase di compilazione. Con la compilazione e successivamente il debug, è anche possibile individuare e correggere errori di run-time, ad esempio errori di logica, I/O e divisione per zero.

Una compilazione riuscita conferma che la sintassi del codice sorgente è corretta e che tutti i riferimenti statici a librerie, assembly e altri componenti possono essere risolti. Il processo di compilazione genera un eseguibile dell'applicazione. Questo eseguibile può quindi essere testato tramite debug e diversi tipi di test manuali e automatizzati per convalidare la qualità del codice. Dopo aver testato completamente l'applicazione, è possibile compilare una versione finale da distribuire ai clienti.

Nel Mac è possibile usare uno dei metodi seguenti per compilare l'applicazione: Visual Studio per Mac, strumenti da riga di comando di MSBuild o Azure Pipelines.

| Metodo di compilazione | Vantaggi |
| --- |--- | --- |
| Visual Studio per Mac |- Creazione immediata di build e test in un debugger.<br />- Esecuzione di compilazioni multiprocessore per progetti C#.<br />- Personalizzazione di vari aspetti del sistema di compilazione. |
| Riga di comando MSBuild| - Compilazione di progetti senza l'installazione di Visual Studio per Mac.<br />- Esecuzione di compilazioni multiprocessore per tutti i tipi di progetto.<br />- Personalizzazione della maggior parte delle aree del sistema di compilazione.|
| Azure Pipelines | - Automazione della compilazione come parte di un processo di integrazione continua/recapito continuo.<br />- Implementazione di test automatizzati con ogni compilazione.<br />- Uso di risorse di codice praticamente illimitate per i processi di compilazione.<br />- Modifica del flusso di lavoro di compilazione e creazione di attività di compilazione per eseguire attività personalizzate specifiche.|

La documentazione di questa sezione approfondisce i dettagli del processo di compilazione basato su IDE. Per compilare applicazioni dalla riga di comando senza installare Visual Studio per Mac, è possibile installare la versione [più recente .NET Core SDK](https://dotnet.microsoft.com/download). Per altre informazioni sulla compilazione di applicazioni tramite la riga di comando, vedere [MSBuild](/visualstudio/msbuild/msbuild). Per informazioni dettagliate sulla compilazione di applicazioni con Azure Pipelines, vedere [Azure Pipelines](/azure/devops/pipelines).


> [!NOTE]
> Questo argomento si applica a Visual Studio per Mac. Per Visual Studio in Windows, vedere [Compilare e creare in Visual Studio](/visualstudio/ide/compiling-and-building-in-visual-studio).


## <a name="building-from-the-ide"></a>Compilazione nell'IDE

Visual Studio per Mac consente di creare ed eseguire compilazioni immediatamente, mantenendo al contempo il controllo della funzionalità di compilazione. Quando si crea un progetto, Visual Studio per Mac definisce una configurazione di compilazione predefinita che imposta il contesto per le compilazioni. È possibile modificare le configurazioni di compilazione predefinite e crearne di personalizzate. La creazione e la modifica di queste configurazioni aggiorna automaticamente il file di progetto, che viene quindi usato da MSBuild per la compilazione.

Per altre informazioni su come compilare progetti e soluzioni nell'IDE, vedere la guida [Compilazione e pulizia di progetti e soluzioni](building-and-cleaning-projects-and-solutions.md).

Visual Studio per Mac consente anche di eseguire le operazioni seguenti:

* Modificare il percorso di output. È possibile eseguire questa operazione nelle opzioni del progetto:

    ![Modificare il percorso di output](media/compiling-and-building-image4.png)

* Modificare il livello di dettaglio dell'output di compilazione:

    ![Modificare il livello di dettaglio della compilazione](media/compiling-and-building-image5.png)

* Aggiungere comandi personalizzati prima, durante o dopo la compilazione o la pulizia:

    ![Aggiungere comandi personalizzati](media/compiling-and-building-image6.png)


## <a name="see-also"></a>Vedi anche

- [Compilazione e creazione (Visual Studio in Windows)](/visualstudio/ide/compiling-and-building-in-visual-studio)
