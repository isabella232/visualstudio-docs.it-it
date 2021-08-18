---
title: Usare un ambiente lab per DevOps
description: Informazioni sugli ambienti lab e su come usare il cloud con Azure Pipelines o Team Foundation Server build e versione.
ms.custom: SEO-VS-2020
ms.date: 05/02/2017
ms.topic: how-to
helpviewer_keywords:
- lab environment, test lab
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: e411beddb093a75528e2cacd2d3eba945e134b62
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122033018"
---
# <a name="use-a-lab-environment-for-your-devops"></a>Usare un ambiente lab per DevOps

Un ambiente lab è una raccolta di computer virtuali e fisici che è possibile utilizzare per sviluppare e testare le applicazioni. Un ambiente lab può contenere più ruoli necessari per testare le applicazioni a più livelli, come le workstation, i server Web e i server database. Inoltre, è possibile usare un flusso di lavoro compilazione, distribuzione e test con l'ambiente lab per automatizzare il processo di compilazione, distribuzione ed esecuzione di test automatizzati sull'applicazione.

* **Usare un piano di test per eseguire test automatizzati**: è possibile eseguire una raccolta di test automatizzati, denominata *piano di test*, e visualizzarne lo stato.

* **Usare un flusso di lavoro di compilazione/distribuzione/test**: è possibile usare un flusso di lavoro di compilazione/distribuzione/test per testare automaticamente le applicazioni multilivello. Un esempio tipico è un flusso di lavoro che avvia una compilazione, distribuire i file di compilazione sui computer appropriati in un ambiente lab e quindi esegue test automatizzati. È anche possibile pianificare l’esecuzione del flusso di lavoro a intervalli specifici.

* **Raccogliere dati diagnostici da tutti i computer anche durante i test manuali**: è possibile raccogliere simultaneamente test diagnostici da più computer. Ad esempio, durante una singola esecuzione dei test è possibile raccogliere dati IntelliTrace, impatto test e altre forme di dati da un server Web, un server di database e un client.

Ecco alcuni esempi di topologie comuni di ambienti lab:

| Topologia | Descrizione |
|---|---|
|![Topologia solo server](../media/topology_backend.png)| Questo ambiente lab ha una *topologia server*, che è spesso usata per eseguire test manuali su applicazioni server e che consente ai tester di usare i propri computer client per verificare i bug nell'ambiente. In una topologia di back-end, l'ambiente lab contiene solo i server. Quando si usa questo tipo di topologia in genere si esegue la connessione ai server nell’ambiente lab usando un computer client che non fa parte dell’ambiente.|
|![Ambiente lab nel cloud](../media/topology_cloud.png)| Questo ambiente lab presenta caratteristiche e funzionalità simili alla _topologia server_ senza il requisito della presenza di macchine virtuali o computer fisici in un ambiente locale. Ciò può ridurre la durata della configurazione, semplificare la manutenzione e abbassare i costi. La configurazione di più siti Web e più macchine virtuali e la personalizzazione della rete sono semplici e rapide in un ambiente cloud come Microsoft Azure.|
|![Ambiente lab client-server](../media/topology_clientserver.png)| Questo ambiente lab ha una *topologia client/server*, spesso usata per testare un'applicazione dotata di componenti server e client. In una topologia client/server tutti i computer client e server usati per testare l’applicazione si trovano nell’ambiente lab. Quando si usa questa topologia, è possibile raccogliere dati di test da ogni computer che incide sui test.|

:::row:::
    :::column:::
        ![icona della telecamera per un video](../../install/media/video-icon.png)
    :::column-end:::
    :::column:::
        [Guardare un video](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Managing-lab-environments-for-testing) sulla gestione degli ambienti lab per l'esecuzione di test.
    :::column-end:::
:::row-end:::

## <a name="use-the-cloud-with-azure-pipelines-or-team-foundation-server-build-and-release"></a>Usare il cloud con Compilazione e versione di Azure Pipelines o Team Foundation Server

È possibile eseguire test automatizzati e automatizzare le operazioni di compilazione, distribuzione e test usando le funzionalità di [compilazione e versione](/azure/devops/pipelines/index?view=vsts&preserve-view=true) disponibili in Team Foundation Server (TFS) e Azure Test Plans. Ecco alcuni dei vantaggi che offre:

* Non è necessario alcun controller di compilazione o di test.
* L'agente di test viene installato tramite un'attività compresa nella compilazione o nella versione.
* È facile personalizzare i passaggi di distribuzione. È ora possibile usare più di uno script. È anche possibile usufruire delle numerose attività disponibili nel prodotto e in Visual Studio Marketplace.
* Non è necessario gestire gruppi di test. È possibile eseguire i test direttamente dai file binari.
* Per i test eseguiti all'interno di ogni compilazione o di ogni versione è possibile ottenere un'esperienza di report inline più esaustiva.
* È possibile tenere traccia delle risorse (versione, compilazione, elementi di lavoro, commit) distribuite e sottoposte a test in ogni ambiente.
* È possibile personalizzare ed estendere l'automazione per distribuire con facilità più ambienti di test e persino l'ambiente di produzione.
* È possibile pianificare l'automazione in modo che venga eseguita ogni volta che viene effettuata un'archiviazione o un commit oppure ogni giorno a un'ora specifica.

Per altre informazioni, vedere [Usare la gestione di compilazione o versione](use-build-or-rm-instead-of-lab-management.md).

::: moniker range="vs-2017"
## <a name="use-the-visual-studio-lab-management-features-of-microsoft-test-manager"></a>Usare le funzionalità di Visual Studio Lab Management di Microsoft Test Manager

È possibile creare e gestire ambienti lab con le funzionalità di Visual Studio Lab Management di Microsoft Test Manager quando si usa Visual Studio Enterprise.

Lab Management installa automaticamente agenti di test in ogni computer dell'ambiente.

Se si usa il servizio Lab Management in combinazione con System Center Virtual Machine Manager (SCVMM), si ottengono anche questi vantaggi quando si usano gli ambienti lab:

* **Riprodurre rapidamente le configurazioni dei computer**: è possibile archiviare raccolte di macchine virtuali configurate in modo da ricreare tipici ambienti di produzione. Sarà quindi possibile procedere a ciascuna esecuzione dei test in una nuova copia di un ambiente archiviato.

* **Riprodurre esattamente le condizioni di un bug**: quando l'esecuzione dei test ha esito negativo, è possibile archiviare una copia dello stato dell'ambiente lab e accedervi dai risultati di compilazione o da un elemento di lavoro.

* **Eseguire più copie di un ambiente lab allo stesso tempo**: è possibile eseguire più copie dell'ambiente lab contemporaneamente senza conflitti di denominazione.

### <a name="standard-environments-and-scvmm-environments"></a>Ambienti standard e ambienti SCVMM

Con Visual Studio Lab Management è possibile creare due tipi di ambiente lab: **ambienti standard** e **ambienti SCVMM**. Tuttavia, le funzionalità di ogni tipo di ambiente sono diverse.

**Ambienti standard:** possono contenere una combinazione di computer fisici e macchine virtuali. È anche possibile aggiungere macchine virtuali a un ambiente standard, gestite da framework di virtualizzazione di terze parti. Inoltre, gli ambienti standard non richiedono risorse server aggiuntive, come un server SCVMM.

**Ambienti SCVMM:** possono contenere solo macchine virtuali gestite da SCVMM (System Center Virtual Machine Manager), quindi le macchine virtuali in ambienti SCVMM possono essere eseguite solo su framework di virtualizzazione Hyper-V. Tuttavia, gli ambienti SCVMM forniscono le seguenti funzionalità di gestione e di automazione non disponibili in ambienti standard:

- **Snapshot dell'ambiente:** gli snapshot dell'ambiente contengono lo stato di un ambiente lab. È quindi possibile ripristinare rapidamente un ambiente pulito o salvare lo stato di un ambiente modificato. È anche possibile usare un flusso di lavoro di compilazione-distribuzione-test per automatizzare il processo di salvataggio e ripristino degli snapshot dell'ambiente.

- **Ambienti archiviati:** è possibile archiviare una copia di un ambiente SCVMM e quindi distribuirne più copie.

- **Isolamento rete:** l'isolamento rete consente di eseguire contemporaneamente più copie identiche di un ambiente SCVMM senza conflitti di nomi computer.

- **Modelli di macchina virtuale:** un modello di macchina virtuale è una macchina virtuale il cui nome e altri identificatori sono stati rimossi. Quando un modello di macchina virtuale viene distribuito in un ambiente SCVMM, Microsoft Test Manager genera nuovi identificatori. Ciò consente di distribuire più copie di una macchina virtuale nello stesso ambiente o in più ambienti e quindi eseguire le macchine virtuali contemporaneamente.

- **Macchine virtuali archiviate:** una macchina virtuale archiviata nella libreria del progetto che include identificatori univoci.

> [!NOTE]
> Lab Management non supporta SCVMM 2016.

Per informazioni su SCVMM, vedere [Virtual Machine Manager](/azure/devops/pipelines/?view=vsts&preserve-view=true).

Gli ambienti standard e gli ambienti SCVMM supportano molte delle stesse funzionalità. Esistono tuttavia alcune importanti differenze da considerare. Nella tabella seguente vengono confrontate le funzionalità disponibili per gli ambienti standard e gli ambienti SCVMM.

|Funzionalità|Ambienti SCVMM|Ambienti standard|
|-|------------------------|-|
|**Test**|||
|Eseguire test manuali|Supportato|Supportato|
|Eseguire il test codificato dell'interfaccia utente e altri test automatizzati|Supportato|Supportato|
|Archiviare bug dettagliati usando gli adattatori diagnostici|Supportato|Supportato|
|**Distribuzione della compilazione**|||
|Flussi di lavoro compilazione, distribuzione e test automatici|Supportato|Supportato|
|**Creazione e gestione dell'ambiente**|||
|Usare computer fisici oltre alle macchine virtuali|Non supportato|Supportato|
|Usare macchine virtuali di terze parti|Non supportato|Supportato|
|Installazione automatica degli agenti di test nei computer nell'ambiente lab|Supportato|Supportato|
|Salvare e distribuire lo stato di un ambiente lab tramite snapshot dell'ambiente|Supportato|Non supportato|
|Creare ambienti lab dai modelli di macchina virtuale|Supportato|Non supportato|
|Avviare, arrestare e creare lo snapshot dell'ambiente|Supportato|Non supportato|
|Connettersi all'ambiente usando Visualizzatore ambiente|Supportato|Supportato|
|Eseguire più copie di un ambiente nello stesso momento usando l'isolamento della rete|Supportato|Non supportato|

### <a name="lab-management-concepts"></a>Concetti di Lab Management

Di seguito sono riportati alcuni concetti aggiuntivi che è necessario conoscere prima di continuare:

|Termine|Descrizione|
|-|-----------------|
|Centro Lab|L'area di Microsoft Test Manager in cui creare e gestire ambienti lab.|
|Lab del progetto Azure DevOps|La raccolta di ambienti lab che sono stati configurati in modo da connettersi a essi ed eseguire le macchine virtuali.|
|Libreria del progetto Azure DevOps|Archivio di macchine virtuali, modelli e ambienti lab archiviati che sono stati importati nel gruppo host del progetto. È possibile usare gli elementi della raccolta con ambienti SCVMM, tuttavia non è possibile aggiungerli direttamente in un ambiente standard. Non è possibile eseguire gli elementi della raccolta, ma è possibile usarli per implementare un nuovo ambiente.|
|Ambiente distribuito|Ambiente che è stato distribuito nel lab del progetto per connessione e l'esecuzione dei relativi computer.|

Per altre informazioni su Lab Management, vedere:

* [Pianificare il lab](/previous-versions/ff756575(v=vs.140))
* [Configurazione e amministrazione di Lab Management](/previous-versions/dd936084(v=vs.140))
* [Configurazione di Lab Management per ambienti SCVMM](/previous-versions/dd380687(v=vs.140))
* [Gestione autorizzazioni](/previous-versions/dd380760(v=vs.140))
* [Modifica della configurazione](/previous-versions/ee704508(v=vs.140))
* [Risoluzione dei problemi](/previous-versions/ee853230(v=vs.140))

Per informazioni sulla configurazione degli ambienti, vedere:

* [Ambienti cloud di compilazione e versione](use-build-or-rm-instead-of-lab-management.md)
* [Ambienti lab standard](/previous-versions/ee390842(v=vs.140))
* [Ambienti SCVMM (virtuali)](/previous-versions/ee943322(v=vs.140))
* [Creazione e uso di un ambiente di isolamento rete](/previous-versions/ee518924(v=vs.140))
::: moniker-end

## <a name="see-also"></a>Vedi anche

* [Installare e configurare agenti di test](../../test/lab-management/install-configure-test-agents.md)
* [Visual Studio Lab Management Guide](/archive/blogs/visualstudioalmrangers/library-of-tooling-and-guidance-solutions-aka-msvsarsolutions) (Guida di Visual Studio Lab Management)
* [Blog di Microsoft DevOps](https://devblogs.microsoft.com/devops/)