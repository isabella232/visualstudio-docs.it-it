---
title: Profilatura delle prestazioni delle SharePoint applicazioni | Microsoft Docs
description: Profilare le prestazioni delle SharePoint applicazioni se vengono eseguite lentamente o in modo inefficiente. Usare Visual Studio di profilatura per trovare codice problematico.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 0d230bc3f5f99f03661ec8322fa6e478b39c4048
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126710137"
---
# <a name="profile-the-performance-of-sharepoint-applications"></a>Profilare le prestazioni delle SharePoint applicazioni

Se le SharePoint le prestazioni delle applicazioni sono lente o inefficienti, è possibile usare le funzionalità di profilatura in Visual Studio identificare il codice problematico e altri elementi. Usando la funzionalità di test di carico, è possibile determinare le prestazioni di un'applicazione SharePoint sotto stress, ad esempio quando molti utenti accedono contemporaneamente all'applicazione. Eseguendo test delle prestazioni Web, è possibile misurare le prestazioni dell'applicazione sul Web. Usando test codificati dell'interfaccia utente, è possibile verificare se l'intera SharePoint, inclusa l'interfaccia utente, funzioni correttamente. Quando si usano questi test insieme, possono essere utili per identificare i problemi di prestazioni prima di distribuire l'applicazione.

## <a name="profile-tools-overview"></a>Panoramica degli strumenti di profilatura

La profilatura si riferisce al processo di osservazione e registrazione del comportamento delle prestazioni dell'applicazione durante l'esecuzione. Profilando l'applicazione, è possibile individuare problemi quali colli di bottiglia, codice inefficiente e problemi di allocazione della memoria, che causano un'esecuzione lenta delle applicazioni o l'uso di una quantità di memoria insufficiente. Ad esempio, è possibile usare la profilatura per identificare le aree sensibili nel codice, ovvero segmenti di codice chiamati di frequente e che possono rallentare le prestazioni complessive dell'applicazione. Dopo aver identificato gli hotspot, è spesso possibile ottimizzarli o eliminarli.

È possibile usare diversi strumenti di profilatura nell'ambiente di sviluppo integrato (IDE) per identificare e individuare questi tipi di problemi di prestazioni. Questi strumenti funzionano allo stesso modo per i SharePoint come per altri tipi di Visual Studio progetti. La Strumenti di profilatura guidata prestazioni consente di creare una sessione di prestazioni che usa i test specificati. Una sessione di prestazioni è un set di dati di configurazione usati per raccogliere informazioni sulle prestazioni da un'applicazione, insieme ai risultati di una o più esecuzioni di profilatura. Le sessioni di prestazioni vengono archiviate nella cartella del progetto ed è possibile visualizzarle in **Esplora prestazioni**. Per altre informazioni, vedere [Informazioni sui metodi di raccolta delle prestazioni](../profiling/understanding-performance-collection-methods.md).

Dopo aver creato ed eseguito un'analisi del profilo nell'applicazione, un report fornisce informazioni dettagliate sulle relative prestazioni. Questo report può includere elementi come un grafico dell'utilizzo della CPU nel tempo, uno stack di chiamate di funzione gerarchico o un albero delle chiamate. Il contenuto esatto del report può variare a seconda del tipo di test eseguito, ad esempio campionamento o strumentazione. Per altre informazioni, vedere Panoramica [Strumenti di profilatura report](../profiling/performance-report-overview.md).

## <a name="performance-session-process"></a>Processo della sessione di prestazioni

Per profilare un'applicazione, iniziare usando la creazione guidata Strumenti di profilatura prestazioni per creare una sessione di prestazioni. Sulla barra dei menu scegliere **Analizza**, **Avvia Creazione guidata prestazioni**. Al termine della procedura guidata, immettere le informazioni necessarie per la sessione di prestazioni, ad esempio il metodo di profilo desiderato e l'applicazione da profilare. Per altre informazioni, vedere [Procedura: Profilare un sito Web o un'applicazione Web usando la Creazione guidata prestazioni](../profiling/how-to-collect-performance-data-for-a-web-site.md). In alternativa, è possibile usare le opzioni della riga di comando per configurare ed eseguire una sessione di prestazioni. Per altre informazioni, vedere [Using the Strumenti di profilatura From the Command-Line](../profiling/using-the-profiling-tools-from-the-command-line.md). Per configurare manualmente ogni aspetto di una sessione di prestazioni, vedere [Procedura: Creare manualmente sessioni](../profiling/how-to-manually-create-performance-sessions.md)di prestazioni con il Strumenti di profilatura . È anche possibile creare una sessione di prestazioni da un unit test da, nella finestra **Risultati test,** aprendo il menu di scelta rapida per il unit test e quindi scegliendo Crea sessione di **prestazioni**.

Dopo aver configurato una sessione di prestazioni, la configurazione della sessione viene salvata, il server viene configurato per fornire i dati di profilatura e l'applicazione viene eseguita. Quando si usa l'applicazione, i dati sulle prestazioni vengono scritti in un file di log. Le sessioni di prestazioni sono **elencate Esplora prestazioni** nella **cartella** Destinazioni. Al termine di una sessione di prestazioni, il report viene visualizzato nella **cartella Report** in **Esplora prestazioni**. Per visualizzare il report, aprirlo in **Esplora prestazioni**. Per visualizzare o configurare le proprietà di una sessione di prestazioni, aprire il menu di scelta rapida **in** Esplora prestazioni e quindi scegliere **Proprietà**. Per altre informazioni sulle proprietà specifiche di una sessione di prestazioni, vedere [Configuring Performance Sessions for Strumenti di profilatura](../profiling/configuring-performance-sessions.md). Per informazioni su come interpretare i risultati di una sessione di prestazioni, vedere Analisi dei [Strumenti di profilatura dati](../profiling/analyzing-performance-tools-data.md).

## <a name="stress-test"></a>Prova di sforzp

È possibile analizzare le prestazioni di stress delle applicazioni creando test di carico e test delle prestazioni Web in Visual Studio. Quando si crea un test di carico in Visual Studio, si specifica una combinazione di fattori, denominata scenario, su cui testare l'applicazione. Questi fattori includono il modello di carico, il modello di combinazione di test, la combinazione di test, la combinazione di reti e la combinazione di Web browser. Gli scenari di test di carico possono includere sia unit test che test delle prestazioni Web.

Figura 1: Esempio di risultati dei test di carico

![Esecuzione della visualizzazione grafici del test di carico](../sharepoint/media/load-webgraphs.png "Esecuzione della visualizzazione grafici del test di carico")

I test delle prestazioni Web simulano il modo in cui un utente finale potrebbe interagire con un'SharePoint applicazione. È possibile creare test delle prestazioni Web registrando le richieste HTTP in una sessione del browser o usando **Web Performance Test Recorder**. Le richieste Web vengono visualizzate nel **Editor test prestazioni Web** al termine della sessione del browser. È quindi possibile eseguire il debug dei risultati in **Web Performance Risultati test Viewer**. È anche possibile compilare manualmente test delle prestazioni Web usando **l'Editor test prestazioni Web**.

## <a name="test-user-interfaces"></a>Testare le interfacce utente

I test codificati dell'interfaccia utente guidano automaticamente SharePoint'applicazione tramite la relativa interfaccia utente. Questi test riguardano i controlli dell'interfaccia utente, ad esempio pulsanti e menu, per verificare che funzionino correttamente. Questo tipo di test è particolarmente utile se nell'interfaccia utente viene eseguita una convalida o un'altra logica, ad esempio in una pagina Web. È anche possibile usare test codificati dell'interfaccia utente per automatizzare i test manuali. È possibile creare test codificati dell'interfaccia utente per SharePoint applicazioni nello stesso modo in cui si creano test per altri tipi di applicazioni. Per altre informazioni, vedere [Testing SharePoint 2010 Applications with Coded UI Tests (Test delle applicazioni 2010 con test codificati dell'interfaccia utente).](/previous-versions/visualstudio/visual-studio-2015/test/testing-sharepoint-2010-applications-with-coded-ui-tests?preserve-view=true&view=vs-2015)

## <a name="related-topics"></a>Argomenti correlati

|Titolo|Descrizione|
|-----------|-----------------|
|[Procedura dettagliata: Profilare un'SharePoint applicazione](../sharepoint/walkthrough-profiling-a-sharepoint-application.md)|Illustra come eseguire un'analisi del profilo di campionamento in un'SharePoint di campionamento.|
|[Eseguire il test delle prestazioni dell'applicazione prima del rilascio](/azure/devops/test/load-test/run-performance-tests-app-before-release?view=vsts&preserve-view=true)|Viene descritto come creare test di carico che consentono di stressare i test SharePoint applicazioni.|
|[Unit test del codice](../test/unit-test-your-code.md)|Viene descritto come trovare errori logici nel codice tramite unit test.|
|[Test delle applicazioni di SharePoint 2010 con test codificati dell'interfaccia utente](/previous-versions/visualstudio/visual-studio-2015/test/testing-sharepoint-2010-applications-with-coded-ui-tests?preserve-view=true&view=vs-2015)|Viene descritto come testare l'interfaccia utente delle SharePoint applicazioni.|

## <a name="see-also"></a>Vedi anche

- [Build e debug delle soluzioni SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [Migliorare la qualità del codice](../test/improve-code-quality.md)