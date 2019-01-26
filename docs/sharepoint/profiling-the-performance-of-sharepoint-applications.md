---
title: Profilatura delle prestazioni delle applicazioni di SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Profiling.SilverlightWebPartOnly
- VS.SharePointTools.Profiling.DotNetTrustLevel
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, profiling
- performance testing [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, performance testing
- profiling [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8b59a3de88403300a46b7992a2dad72e3d6b59e0
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2019
ms.locfileid: "54864137"
---
# <a name="profile-the-performance-of-sharepoint-applications"></a>Profilare le prestazioni delle applicazioni di SharePoint

Se le applicazioni di SharePoint vengono eseguite lentamente o in modo inefficiente, è possibile usare le funzionalità di profilatura in Visual Studio per identificare i problemi con il codice e altri elementi. Usando funzionalità di test di carico, è possibile determinare come viene eseguita un'applicazione di SharePoint con utilizzo intensivo, ad esempio quando molti utenti accedono contemporaneamente all'applicazione. Tramite l'esecuzione di test delle prestazioni web, è possibile misurare come viene eseguita l'applicazione sul web. Con test codificati dell'interfaccia utente, è possibile verificare se l'intera applicazione SharePoint, inclusa l'interfaccia utente, funzioni correttamente. Quando si usano insieme questi test, si consenta di identificare i problemi di prestazioni prima di distribuire l'applicazione.

## <a name="profile-tools-overview"></a>Panoramica degli strumenti del profilo

Per profilatura si intende il processo di rilevare e registrare il comportamento delle prestazioni dell'applicazione mentre è in esecuzione. Profilando l'applicazione, è possibile identificare i problemi come i colli di bottiglia, codice inefficiente e problemi di allocazione della memoria, determinando le applicazioni a esecuzione lenta o utilizzano troppa memoria. Ad esempio, è possibile utilizzare profilatura per identificare le aree sensibili nel codice, ovvero i segmenti di codice chiamati di frequente e possono rallentare le prestazioni complessive dell'applicazione. Dopo aver identificato le aree sensibili, è spesso possibile ottimizzare o eliminarli.

È possibile usare diversi strumenti di profilatura nell'ambiente di sviluppo integrato (IDE) per identificare e individuare questi tipi di problemi di prestazioni. Questi strumenti funzionano allo stesso modo per i progetti SharePoint come avviene per altri tipi di progetti di Visual Studio. La procedura guidata di profilatura delle prestazioni degli strumenti illustra la creazione di una sessione di prestazioni che utilizza i test desiderati. Una sessione di prestazioni è un set di dati di configurazione che viene utilizzati per raccogliere informazioni sulle prestazioni da un'applicazione, con i risultati di una o più esecuzioni della profilatura. Sessioni di prestazioni vengono archiviate nella cartella del progetto ed è possibile visualizzarli nella **Esplora prestazioni**. Per altre informazioni, vedere [Informazioni sui metodi di raccolta delle prestazioni](../profiling/understanding-performance-collection-methods.md).

Dopo aver creato e si esegue un'analisi del profilo nell'applicazione, un rapporto fornisce dettagli sulle relative prestazioni. Questo report può includere elementi, ad esempio un grafico di utilizzo della CPU nel tempo, uno stack di chiamate di funzioni gerarchiche o un albero delle chiamate. Il contenuto esatto del report può variare, a seconda del tipo di test che si esegue, ad esempio il campionamento o strumentazione. Per altre informazioni, vedere [Report panoramica degli strumenti di profilatura](http://go.microsoft.com/fwlink/?LinkId=224689).

## <a name="performance-session-process"></a>Processo di sessione di prestazioni

Per profilare un'applicazione, iniziare con la procedura guidata di profilatura delle prestazioni degli strumenti per creare una sessione di prestazioni. Nella barra dei menu, scegliere **Analyze**, **Avvia Creazione guidata sessione di prestazioni**. Dopo avere completato la procedura guidata, immettere le informazioni necessarie per la sessione di prestazioni, ad esempio il metodo di profilo desiderato e l'applicazione che desideri profilare. Per altre informazioni, vedere [Procedura: Profilare un sito Web o applicazione Web tramite il Creazione guidata sessione di prestazioni](http://go.microsoft.com/fwlink/?LinkId=224692). In alternativa, è possibile usare le opzioni della riga di comando per configurare ed eseguire una sessione di prestazioni. Per altre informazioni, vedere [usando la profilatura degli strumenti da riga di comando](http://go.microsoft.com/fwlink/?LinkId=224703). Se si desidera configurare manualmente ogni aspetto di una sessione di prestazioni, vedere [come: Creare manualmente sessioni di prestazioni con gli strumenti di profilatura](http://go.microsoft.com/fwlink/?LinkId=224691). È anche possibile creare in una sessione di prestazioni da uno unit test, il **risultati Test** finestra, aprire il menu di scelta rapida per lo unit test e quindi scegliendo **Crea sessione prestazioni**.

Dopo aver impostato una sessione di prestazioni, la configurazione di sessione viene salvata, il server è configurato per fornire i dati di profilatura e l'esecuzione dell'applicazione. Quando si usa l'applicazione, i dati sulle prestazioni sono scritto in un file di log. Sessioni di prestazioni sono racchiusi **Esplora prestazioni** sotto il **destinazioni** cartella. Al termine di una sessione di prestazioni, il rapporto viene visualizzato nel **Reports** cartella **Esplora prestazioni**. Per visualizzare il rapporto, aprirlo in **Esplora prestazioni**. Per visualizzare o configurare le proprietà di una sessione di prestazioni, aprire il menu di scelta rapida **Esplora prestazioni**, quindi scegliere **proprietà**. Per altre informazioni sulle proprietà specifiche di una sessione di prestazioni, vedere [configurazione di sessioni di prestazioni per gli strumenti di profilatura](http://go.microsoft.com/fwlink/?LinkId=224694). Per informazioni su come interpretare i risultati di una sessione di prestazioni, vedere [analisi dei dati degli strumenti di profilatura](http://go.microsoft.com/fwlink/?LinkId=224704).

## <a name="stress-test"></a>Test di stress

È possibile analizzare le prestazioni di stress delle applicazioni creando test di carico e test delle prestazioni web in Visual Studio. Quando si crea un test di carico in Visual Studio, si specifica una combinazione di fattori, chiamato uno scenario, per testare l'applicazione con. Questi fattori includono modello di carico, modello di combinazione di test, combinazione di test, combinazione di reti e combinazione di web browser. Scenari di test di carico possono includere sia unit test e test delle prestazioni web.

Figura 1: Esempio dei risultati test di carico

![Visualizzazione di grafici di esecuzione test di carico](../sharepoint/media/load-webgraphs.png "visualizzazione grafici di test di carico in esecuzione")

Test delle prestazioni Web simulano come un utente finale può interagire con un'applicazione di SharePoint. È possibile creare test delle prestazioni web registrando le richieste HTTP in una sessione del browser o tramite il **registrazione Test prestazioni Web**. Le richieste web vengono visualizzati nei **Editor Test prestazioni Web** al termine della sessione del browser. È quindi possibile eseguire il debug i risultati nel **Visualizzatore risultati Test prestazioni Web**. È inoltre possibile compilare manualmente i test prestazioni web utilizzando il **Editor Test prestazioni Web**.

## <a name="test-user-interfaces"></a>Interfacce utente di test

I test codificati dell'interfaccia utente unità automaticamente l'applicazione SharePoint tramite l'interfaccia utente (UI). Questi test sono applicati i controlli dell'interfaccia utente, ad esempio i pulsanti e menu, verificare che funzionino correttamente. Questo tipo di test è particolarmente utile se la convalida o altra logica viene eseguita nell'interfaccia utente, ad esempio in una pagina web. È anche possibile usare test codificati dell'interfaccia utente per automatizzare i test manuali. Creazione di codificati dell'interfaccia utente per le applicazioni SharePoint nello stesso modo quando si creano i test per altri tipi di applicazioni. Per altre informazioni, vedere [Testing delle applicazioni di SharePoint 2010 con test codificati dell'interfaccia utente](../test/testing-sharepoint-2010-applications-with-coded-ui-tests.md).

## <a name="related-topics"></a>Argomenti correlati

|Titolo|Descrizione|
|-----------|-----------------|
|[Procedura dettagliata: Profilare un'applicazione SharePoint](../sharepoint/walkthrough-profiling-a-sharepoint-application.md)|Viene illustrato come eseguire un'analisi del profilo di campionamento su un'applicazione SharePoint.|
|[Eseguire il test delle prestazioni dell'applicazione prima del rilascio](/azure/devops/test/load-test/run-performance-tests-app-before-release?view=vsts)|Viene descritto come creare i test di carico, che consentono di test di stress delle applicazioni di SharePoint.|
|[Eseguire unit test del codice](../test/unit-test-your-code.md)|Viene descritto come individuare errori logici nel codice tramite unit test.|
|[Test delle applicazioni di SharePoint 2010 con test codificati dell'interfaccia utente](../test/testing-sharepoint-2010-applications-with-coded-ui-tests.md)|Descrive come testare l'interfaccia utente delle applicazioni SharePoint.|

## <a name="see-also"></a>Vedere anche

- [Build e debug delle soluzioni SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [Migliorare la qualità del codice](../test/improve-code-quality.md)