---
title: Profilatura delle prestazioni delle applicazioni SharePoint | Microsoft Docs
description: Profilare le prestazioni delle applicazioni SharePoint se sono in esecuzione lentamente o in modo non efficiente. Usare le funzionalità di profilatura di Visual Studio per trovare codice problematico.
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ecdacce58e17c616b22c9a6a8ba6fce9d5cf272c
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305098"
---
# <a name="profile-the-performance-of-sharepoint-applications"></a>Profilare le prestazioni delle applicazioni SharePoint

Se le applicazioni SharePoint sono in esecuzione lentamente o in modo inefficiente, è possibile usare le funzionalità di profilatura in Visual Studio per identificare il codice problematico e altri elementi. Utilizzando la funzionalità di test di carico, è possibile determinare il modo in cui un'applicazione SharePoint viene eseguita in condizioni di stress, ad esempio quando molti utenti accedono all'applicazione contemporaneamente. Eseguendo i test delle prestazioni Web, è possibile misurare le prestazioni dell'applicazione sul Web. Usando i test codificati dell'interfaccia utente, è possibile verificare che l'intera applicazione SharePoint, inclusa l'interfaccia utente, funzioni correttamente. Quando questi test vengono usati insieme, consentono di identificare i problemi di prestazioni prima di distribuire l'applicazione.

## <a name="profile-tools-overview"></a>Panoramica degli strumenti di profilo

La profilatura si riferisce al processo di osservazione e registrazione del comportamento delle prestazioni dell'applicazione durante l'esecuzione. Grazie alla profilatura dell'applicazione, è possibile individuare problemi quali colli di bottiglia, codice inefficiente e problemi di allocazione della memoria, in modo che le applicazioni vengano eseguite lentamente o usino una quantità eccessiva di memoria. Ad esempio, è possibile usare la profilatura per identificare gli hotspot nel codice, ovvero segmenti di codice spesso chiamati e che possono rallentare le prestazioni complessive dell'applicazione. Dopo aver identificato gli hotspot, è spesso possibile ottimizzarli o eliminarli.

È possibile utilizzare diversi strumenti di profilatura nel Integrated Development Environment (IDE) per identificare e individuare questi tipi di problemi di prestazioni. Questi strumenti funzionano allo stesso modo per i progetti SharePoint, come per altri tipi di progetti di Visual Studio. La creazione guidata sessione di prestazioni di Strumenti di profilatura consente di creare una sessione di prestazioni che usa i test specificati. Una sessione di prestazioni è un set di dati di configurazione usati per raccogliere informazioni sulle prestazioni da un'applicazione, insieme ai risultati di una o più esecuzioni della profilatura. Le sessioni di prestazioni vengono archiviate nella cartella del progetto e possono essere visualizzate in **Esplora prestazioni**. Per altre informazioni, vedere [Informazioni sui metodi di raccolta delle prestazioni](../profiling/understanding-performance-collection-methods.md).

Dopo aver creato ed eseguito un'analisi del profilo nell'applicazione, in un report vengono fornite informazioni dettagliate sulle prestazioni. Questo report può includere elementi quali un grafico dell'utilizzo della CPU nel tempo, uno stack di chiamate di funzione gerarchico o un albero delle chiamate. Il contenuto esatto del report può variare a seconda del tipo di test eseguito, ad esempio il campionamento o la strumentazione. Per ulteriori informazioni, vedere [Panoramica del Report strumenti di profilatura](../profiling/performance-report-overview.md).

## <a name="performance-session-process"></a>Processo della sessione di prestazioni

Per profilare un'applicazione, iniziare utilizzando la creazione guidata sessione di prestazioni Strumenti di profilatura per creare una sessione di prestazioni. Sulla barra dei menu scegliere **analizza**, **Avvia Creazione guidata sessione di prestazioni**. Quando si completa la procedura guidata, immettere le informazioni necessarie per la sessione di prestazioni, ad esempio il metodo del profilo desiderato e l'applicazione che si desidera profilare. Per ulteriori informazioni, vedere [procedura: profilare un sito Web o un'applicazione Web utilizzando la creazione guidata sessione di prestazioni](../profiling/how-to-collect-performance-data-for-a-web-site.md). In alternativa, è possibile usare le opzioni della riga di comando per configurare ed eseguire una sessione di prestazioni. Per ulteriori informazioni, vedere [utilizzo del strumenti di profilatura dalla riga di comando](../profiling/using-the-profiling-tools-from-the-command-line.md). Se si desidera configurare manualmente ogni aspetto di una sessione di prestazioni, vedere [procedura: creare manualmente sessioni di prestazioni con il strumenti di profilatura](../profiling/how-to-manually-create-performance-sessions.md). È anche possibile creare una sessione di prestazioni da un unit test, nella finestra **risultati test** aprire il menu di scelta rapida per il unit test e quindi scegliere **Crea sessione di prestazioni**.

Dopo aver impostato una sessione di prestazioni, la configurazione di sessione viene salvata, il server è configurato per fornire i dati di profilatura e l'applicazione viene eseguita. Quando si usa l'applicazione, i dati sulle prestazioni vengono scritti in un file di log. Le sessioni di prestazioni sono elencate in **Esplora prestazioni** nella cartella **destinazioni** . Al termine di una sessione di prestazioni, il report viene visualizzato nella cartella **report** in **Esplora prestazioni**. Per visualizzare il report, aprirlo in **Esplora prestazioni**. Per visualizzare o configurare le proprietà di una sessione di prestazioni, aprire il menu di scelta rapida in **Esplora prestazioni**, quindi scegliere **Proprietà**. Per ulteriori informazioni sulle proprietà specifiche di una sessione di prestazioni, vedere [Configuring performance Sessions for strumenti di profilatura](../profiling/configuring-performance-sessions.md). Per informazioni su come interpretare i risultati di una sessione di prestazioni, vedere [analisi dei dati strumenti di profilatura](../profiling/analyzing-performance-tools-data.md).

## <a name="stress-test"></a>Test di stress

È possibile analizzare le prestazioni di stress delle applicazioni creando test di carico e test delle prestazioni Web in Visual Studio. Quando si crea un test di carico in Visual Studio, si specifica una combinazione di fattori, detti scenario, per il test dell'applicazione. Questi fattori includono il modello di carico, il modello di combinazione di test, la combinazione di test, la combinazione di reti e la combinazione di Web browser. Gli scenari di test di carico possono includere sia unit test che test delle prestazioni Web.

Figura 1: esempio di risultati del test di carico

![Esecuzione della visualizzazione grafici del test di carico](../sharepoint/media/load-webgraphs.png "Esecuzione della visualizzazione grafici del test di carico")

I test delle prestazioni Web simulano il modo in cui un utente finale può interagire con un'applicazione SharePoint. È possibile creare test delle prestazioni Web registrando le richieste HTTP in una sessione del browser o utilizzando la **registrazione del test delle prestazioni Web**. Le richieste Web vengono visualizzate nel **Editor test prestazioni Web** al termine della sessione del browser. È quindi possibile eseguire il debug dei risultati nel **visualizzatore risultati test prestazioni Web**. È anche possibile compilare manualmente i test delle prestazioni Web usando il **Editor test prestazioni Web**.

## <a name="test-user-interfaces"></a>Interfacce utente di test

I test codificati dell'interfaccia utente indirizzano automaticamente l'applicazione SharePoint tramite la relativa interfaccia utente. Questi test coprono i controlli dell'interfaccia utente, ad esempio pulsanti e menu, per verificare che funzionino correttamente. Questo tipo di test è particolarmente utile se nell'interfaccia utente viene eseguita la convalida o un'altra logica, ad esempio in una pagina Web. È anche possibile usare i test codificati dell'interfaccia utente per automatizzare i test manuali. Si creano test codificati dell'interfaccia utente per le applicazioni SharePoint nello stesso modo in cui si creano test per altri tipi di applicazioni. Per altre informazioni, vedere [test di applicazioni SharePoint 2010 con test codificati dell'interfaccia utente](/previous-versions/visualstudio/visual-studio-2015/test/testing-sharepoint-2010-applications-with-coded-ui-tests?preserve-view=true&view=vs-2015).

## <a name="related-topics"></a>Argomenti correlati

|Titolo|Descrizione|
|-----------|-----------------|
|[Procedura dettagliata: profilare un'applicazione SharePoint](../sharepoint/walkthrough-profiling-a-sharepoint-application.md)|Viene illustrato come eseguire un'analisi del profilo di campionamento in un'applicazione SharePoint.|
|[Eseguire il test delle prestazioni dell'applicazione prima del rilascio](/azure/devops/test/load-test/run-performance-tests-app-before-release?view=vsts&preserve-view=true)|Viene descritto come creare test di carico che consentono di sottoporre a test le applicazioni SharePoint.|
|[Eseguire unit test del codice](../test/unit-test-your-code.md)|Viene descritto come trovare errori di logica nel codice tramite unit test.|
|[Test delle applicazioni di SharePoint 2010 con test codificati dell'interfaccia utente](/previous-versions/visualstudio/visual-studio-2015/test/testing-sharepoint-2010-applications-with-coded-ui-tests?preserve-view=true&view=vs-2015)|Viene descritto come testare l'interfaccia utente delle applicazioni SharePoint.|

## <a name="see-also"></a>Vedere anche

- [Build e debug delle soluzioni SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [Migliorare la qualità del codice](../test/improve-code-quality.md)