---
title: Test delle prestazioni di un servizio cloud | Microsoft Docs
description: Test delle prestazioni di un servizio cloud con il profiler di Visual Studio
author: mikejo5000
manager: douge
ms.assetid: 7a5501aa-f92c-457c-af9b-92ea50914e24
ms.topic: conceptual
ms.tgt_pltfrm: multiple
ms.workload: na
ms.date: 11/11/2016
ms.author: mikejo
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.openlocfilehash: 25b60e5e4072a0523d17082a5c5646e5bb1ade6a
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002410"
---
# <a name="testing-the-performance-of-a-cloud-service"></a>Test delle prestazioni di un servizio cloud
## <a name="overview"></a>Panoramica
È possibile testare le prestazioni di un servizio cloud nei modi seguenti:

* Usare la diagnostica di Azure per raccogliere informazioni sulle richieste e connessioni ed esaminare le statistiche del sito che mostrano le prestazioni del servizio dalla prospettiva del cliente. Per un'introduzione, vedere [configurazione della diagnostica per servizi Cloud di Azure e macchine virtuali](http://go.microsoft.com/fwlink/p/?LinkId=623009).
* Usare il profiler di Visual Studio per ottenere un'analisi approfondita degli aspetti computazionali dell'esecuzione del servizio. Come descritto in questo argomento, è possibile usare il profiler per misurare le prestazioni durante l'esecuzione di un servizio in Azure. Per informazioni su come usare il profiler per misurare le prestazioni durante l'esecuzione di un servizio localmente in un emulatore di calcolo, vedere [test delle prestazioni di un Azure Cloud Service localmente nell'emulatore di calcolo tramite il Visual Studio Profiler](http://go.microsoft.com/fwlink/p/?LinkId=262845).

## <a name="choosing-a-performance-testing-method"></a>Scelta di una metodo di test delle prestazioni
### <a name="use-azure-diagnostics-to-collect"></a>Usare diagnostica di Azure per raccogliere:
* Statistiche su pagine web o servizi, ad esempio le richieste e connessioni.
* Statistiche sui ruoli, ad esempio la frequenza con cui un ruolo viene riavviato.
* Informazioni sull'utilizzo della memoria, ad esempio la percentuale di tempo impiegato dal garbage collector o la memoria set complessivo di un ruolo in esecuzione.

### <a name="use-the-visual-studio-profiler-to"></a>Usare il profiler di Visual Studio per:
* Determinare le funzioni che richiedono più tempo.
* Quanto tempo ogni parte di un programma con calcoli complessi di misure.
* Confrontare rapporti dettagliati sulle prestazioni per due versioni di un servizio.
* Analizzare l'allocazione di memoria in modo più dettagliato rispetto al livello delle singole allocazioni di memoria.
* Analizzare i problemi di concorrenza nel codice a thread multipli.

Quando si usa il profiler, è possibile raccogliere i dati quando un servizio cloud viene eseguito localmente o in Azure.

### <a name="collect-profiling-data-locally-to"></a>Raccogliere dati di profilatura in locale per:
* Test delle prestazioni di una parte di un servizio cloud, ad esempio l'esecuzione del ruolo di lavoro specifico, che non richiede un carico simulato realistico.
* Test delle prestazioni di un servizio cloud in isolamento, in condizioni controllate.
* Test delle prestazioni di un servizio cloud prima di distribuirla in Azure.
* Test delle prestazioni di un servizio cloud privatamente, senza interferire con le distribuzioni esistenti.
* Test delle prestazioni del servizio senza incorrere in addebiti per l'esecuzione in Azure.

### <a name="collect-profiling-data-in-azure-to"></a>Raccogliere dati di profilatura in Azure per:
* Test delle prestazioni di un servizio cloud con un carico simulato o reale.
* Usare il metodo di strumentazione di raccolta dei dati di profilatura, come descritto più avanti in questo argomento.
* Test delle prestazioni del servizio nello stesso ambiente quando il servizio viene eseguito nell'ambiente di produzione.

In genere si simula un carico per testare i servizi cloud in normale o condizioni di sovraccarico.

## <a name="profiling-a-cloud-service-in-azure"></a>Profilatura di un servizio cloud in Azure
Quando si pubblica un servizio cloud da Visual Studio, è possibile analizzare il servizio e specificare le impostazioni di profilatura che forniscono le informazioni desiderate. Viene avviata una sessione di profilatura per ogni istanza di un ruolo. Per altre informazioni su come pubblicare un servizio da Visual Studio, vedere [pubblicazione in un servizio Cloud di Azure da Visual Studio](https://msdn.microsoft.com/library/azure/ee460772.aspx).

Per altre informazioni sulla profilatura delle prestazioni in Visual Studio, vedere [Guida per principianti alla profilatura delle prestazioni](https://msdn.microsoft.com/library/azure/ms182372.aspx) e [analisi delle prestazioni dell'applicazione tramite gli strumenti di profilatura](https://msdn.microsoft.com/library/azure/z9z62c29.aspx).

> [!NOTE]
> È possibile abilitare IntelliTrace o la profilatura quando si pubblica il servizio cloud. È possibile abilitare entrambi.
> 
> 

### <a name="profiler-collection-methods"></a>Metodi di raccolta Profiler
È possibile usare i metodi di raccolta diversi per la profilatura, in base alla soluzione dei problemi di prestazioni:

* **Campionamento CPU** -questo metodo raccoglie statistiche dell'applicazione che sono utili per l'analisi iniziale dei problemi relativi all'utilizzo della CPU. Campionamento CPU è il metodo consigliato per iniziare la maggior parte delle indagini sulle prestazioni. È presente un impatto minimo sull'applicazione da sottoporre a profilatura quando si raccolgono i dati di campionamento della CPU.
* **Strumentazione** -questo metodo raccoglie dati temporali dettagliati utili per l'analisi mirata e per l'analisi dei problemi relativi alle prestazioni di input/output. Il metodo di strumentazione registra ogni voce, uscita e chiamata di funzione delle funzioni in un modulo durante un'esecuzione della profilatura. Questo metodo è utile per raccogliere informazioni dettagliate sulle tempistiche per una sezione del codice e per comprendere l'impatto delle operazioni di input e output sulle prestazioni dell'applicazione. Questo metodo è disabilitato per un computer che esegue un sistema operativo a 32 bit. Questa opzione è disponibile solo quando si esegue il servizio cloud in Azure, non in locale nell'emulatore di calcolo.
* **Allocazione di memoria .NET** -questo metodo raccoglie dati sull'allocazione di memoria .NET Framework usando il metodo di profilatura del campionamento. I dati raccolti includono il numero e dimensioni degli oggetti allocati.
* **Concorrenza** -questo metodo raccoglie dati sui conflitti di risorse e dati di esecuzione di thread e processi utili per l'analisi delle applicazioni multithread e multiprocesso. Il metodo di concorrenza raccoglie i dati per ogni evento che blocca l'esecuzione del codice, ad esempio quando un thread attende che l'accesso bloccato a una risorsa di un'applicazione venga liberato. Questo metodo è utile per l'analisi delle applicazioni multithread.
* È anche possibile abilitare **profilatura interazione tra livelli**, che fornisce informazioni aggiuntive sui tempi di esecuzione di ADO.NET sincrone chiamate nelle funzioni di applicazioni multilivello che comunicano con uno o più database. È possibile raccogliere dati di interazione tra livelli con qualsiasi metodo di profilatura. Per altre informazioni sulla profilatura interazione tra livelli, vedere [visualizzazione interazioni tra livelli](https://msdn.microsoft.com/library/azure/dd557764.aspx).

## <a name="configuring-profiling-settings"></a>Configurazione delle impostazioni di profilatura
Nella figura seguente viene illustrato come configurare le impostazioni di profilatura dalla finestra di dialogo Pubblica applicazione Azure.

![Configurare le impostazioni di profilatura](./media/vs-azure-tools-performance-profiling-cloud-services/IC526984.png)

> [!NOTE]
> Per abilitare la **abilitare la profilatura** casella di controllo, è necessario che il profiler installato nel computer locale che si usa per pubblicare il servizio cloud. Per impostazione predefinita, il profiler viene installato quando si installa Visual Studio.
> 
> 

### <a name="to-configure-profiling-settings"></a>Per configurare le impostazioni di profilatura
1. In Esplora soluzioni aprire il menu di scelta rapida per il progetto Azure e quindi scegliere **pubblica**. Per informazioni dettagliate su come pubblicare un servizio cloud, vedere [pubblicazione di un servizio cloud con gli strumenti Azure](http://go.microsoft.com/fwlink/p?LinkId=623012).
2. Nel **pubblica applicazione Azure** della finestra di dialogo ha scelto il **impostazioni avanzate** scheda.
3. Per abilitare la profilatura, selezionare la **abilitare la profilatura** casella di controllo.
4. Per configurare le impostazioni di profilatura, scegliere il **impostazioni** collegamento ipertestuale. Viene visualizzata la finestra di dialogo Impostazioni di profilatura.
5. Dal **specificare il metodo di profilatura si vuole usare** pulsanti di opzione, scegliere il tipo di analisi necessario.
6. Per raccogliere i dati di profilatura di interazione tra livelli, selezionare la **Abilita profilatura interazione tra livelli** casella di controllo.
7. Per salvare le impostazioni, scegliere il **OK** pulsante.
   
    Quando si pubblica questa applicazione, queste impostazioni vengono usate per creare la sessione di profilatura per ogni ruolo.

## <a name="viewing-profiling-reports"></a>Visualizzazione di report per la profilatura
Viene creata una sessione di profilatura per ogni istanza di un ruolo nel servizio cloud. Per visualizzare i report di profilatura di ogni sessione da Visual Studio, è possibile visualizzare la finestra di Esplora Server e quindi scegliere il nodo di calcolo di Azure per selezionare un'istanza di un ruolo. È quindi possibile visualizzare i report di profilatura come illustrato nella figura seguente.

![Zobrazit Sestavu Profilace da Azure](./media/vs-azure-tools-performance-profiling-cloud-services/IC748914.png)

### <a name="to-view-profiling-reports"></a>Per visualizzare i rapporti di profilatura
1. Per visualizzare la finestra Esplora Server in Visual Studio, sulla barra dei menu scegliere Visualizza, Esplora Server.
2. Scegliere il nodo di calcolo di Azure e quindi scegliere il nodo di distribuzione di Azure per il servizio cloud selezionato per la profilatura durante la pubblicazione da Visual Studio.
3. Per visualizzare i rapporti di profilatura per un'istanza, scegliere il ruolo nel servizio, aprire il menu di scelta rapida per un'istanza specifica e quindi scegliere **Visualizza rapporto sulla profilatura**.
   
    Il report, un file con estensione vsp, viene ora scaricato da Azure e lo stato del download viene visualizzato nel Log attività di Azure. Al termine del download, il rapporto sulla profilatura viene visualizzato in una scheda nell'editor per Visual Studio denominata <Role name> *<Instance Number>* <identifier>con estensione vsp. I dati di riepilogo per il report viene visualizzato.
4. Per visualizzare viste diverse del report, nell'elenco Vista corrente, scegliere il tipo di visualizzazione che si desidera. Per altre informazioni, vedere [visualizzazioni dei rapporti degli strumenti di profilatura](https://msdn.microsoft.com/library/azure/bb385755.aspx).

## <a name="next-steps"></a>Passaggi successivi
[Debug di servizi Cloud](https://msdn.microsoft.com/library/azure/ee405479.aspx)

[Pubblicazione in un servizio Cloud di Azure da Visual Studio](https://msdn.microsoft.com/library/azure/ee460772.aspx)

