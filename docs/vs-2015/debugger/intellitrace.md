---
title: IntelliTrace | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.historicaldebug.overview
helpviewer_keywords:
- debugger, recording execution history
- debugging, recording execution history
- IntelliTrace [Visual Studio ALM]
- IntelliTrace, debugging applications
- debugger, (See also IntelliTrace [Visual Studio ALM])
- debugging, (See also IntelliTrace [Visual Studio ALM])
- IntelliTrace, collecting data from Test Manager
- IntelliTrace
- Test Manager, debugging with IntelliTrace
- IntelliTrace, debugging after a crash
ms.assetid: 486bfec2-39bd-4d78-892a-42352128ee52
caps.latest.revision: 142
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7bc1e36f6d5dea12a8c46e88a3e1f450cc30caa6
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2020
ms.locfileid: "75847214"
---
# <a name="intellitrace"></a>IntelliTrace
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [IntelliTrace](https://docs.microsoft.com/visualstudio/debugger/intellitrace) .  
  
È possibile ridurre il tempo richiesto per eseguire il debug dell'applicazione quando si usa IntelliTrace per registrare e tenere traccia della cronologia di esecuzione del codice. È possibile trovare facilmente i bug perché IntelliTrace consente di:  
  
- Registrare eventi specifici  
  
   Esaminare il codice correlato, i dati visualizzati nella finestra **Variabili locali** durante gli eventi del debugger e le informazioni di chiamata di funzione  
  
- Eseguire il debug di errori difficili da riprodurre o verificatisi in fase di distribuzione  
  
  È possibile utilizzare IntelliTrace in Visual Studio Enterprise edition (ma non le edizioni Professional o Community).  
  
## <a name="what-do-you-want-to-do"></a>Come procedere  
  
|||  
|-|-|  
|**Eseguire il debug dell'applicazione con IntelliTrace:**<br /><br /> -Mostra gli eventi precedenti.<br />-Visualizza le informazioni sulle chiamate con gli eventi precedenti.<br />-Salvare la sessione di IntelliTrace.<br />: Controllare i dati raccolti da IntelliTrace.|-   [Procedura dettagliata: uso di IntelliTrace](../debugger/walkthrough-using-intellitrace.md)<br />     [Funzionalità IntelliTrace](../debugger/intellitrace-features.md)<br />-   [configurare IntelliTrace](https://msdn.microsoft.com/7657ecab-e07e-4b1b-872d-f05d966be37e)<br />-   [Debug cronologico](../debugger/historical-debugging.md)|  
|**Raccogliere i dati IntelliTrace durante una sessione di test in Test Manager**|-   [Raccogliere un maggior numero di dati di diagnostica durante i test manuali](https://msdn.microsoft.com/library/bb5a2cc0-84f5-4dfe-9560-ca3d313aefd2)|  
|**Raccogliere dati IntelliTrace dalle applicazioni distribuite**|-   [Uso dell'agente di raccolta autonomo IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md)|  
|**Avviare il debug da un file di log IntelliTrace (file .iTrace).**|-   [Uso dei dati di IntelliTrace salvati](../debugger/using-saved-intellitrace-data.md)|  
  
## <a name="IntelliTraceSupport"></a> Di quali app è possibile eseguire il debug con IntelliTrace?  
  
|||  
|-|-|  
|**Supportato**|-Visual Basic e applicazioni C# visive che usano .NET Framework 2,0 o versioni successive.<br />     È possibile eseguire il debug della maggior parte delle applicazioni, comprese le app ASP.NET, Microsoft Azure, Windows Form, WCF, WPF, Windows Workflow, SharePoint 2010, SharePoint 2013 e a 64 bit.<br />     Per eseguire il debug di applicazioni SharePoint con IntelliTrace, vedere [procedura dettagliata: debug di un'applicazione SharePoint tramite IntelliTrace](https://msdn.microsoft.com/library/4bd80d2f-f680-4bf4-81c3-f14e8185f6a4).<br />     Per eseguire il debug di app Microsoft Azure con IntelliTrace, vedere [debug di un servizio cloud pubblicato con IntelliTrace e Visual Studio](../azure/vs-azure-tools-intellitrace-debug-published-cloud-services.md).|  
|**Supporto limitato**|- F# app su base sperimentale<br />-App di Windows Store supportate solo per gli eventi|  
|**Non supportato**|- C++, altri linguaggi e script<br />-App per servizi Windows, Silverlight, Xbox o [!INCLUDE[winmobile](../includes/winmobile-md.md)]|  
  
> [!NOTE]
> Se si desidera eseguire il debug di un processo già in esecuzione, non è possibile usare IntelliTrace. È necessario avviare IntelliTrace all'avvio del processo.  
  
## <a name="IntelliTraceVSTraditional"></a> Perché eseguire il debug con IntelliTrace?  
 Il debug tradizionale o *attivo* mostra solo lo stato corrente dell'applicazione con dati limitati sugli eventi passati. È necessario dedurre tali eventi dallo stato corrente dell'applicazione oppure ricrearli rieseguendo l'applicazione.  
  
 IntelliTrace consente di espandere questa esperienza di debug tradizionale registrando dati ed eventi specifici in un preciso momento. Ciò consente di verificare cosa sia accaduto nell'applicazione senza riavviarla, specialmente se si supera il punto in cui si è verificato il bug. IntelliTrace è attivato per impostazione predefinita durante il debug tradizionale e raccoglie i dati in modo automatico e invisibile. Ciò consente di passare facilmente dal debug tradizionale al debug IntelliTrace e viceversa per visualizzare le informazioni registrate. Vedere le [funzionalità IntelliTrace](../debugger/intellitrace-features.md) e [i dati raccolti da IntelliTrace.](#WhatData)  
  
 IntelliTrace consente anche di eseguire il debug di errori difficili da riprodurre o che si verificano in fase di distribuzione. È possibile raccogliere dati IntelliTrace e salvarli in un file di log IntelliTrace (file .iTrace), contenente dettagli su eccezioni, eventi di prestazioni, richieste Web, dati di test, thread, moduli e altre informazioni di sistema. È possibile aprire questo file in Visual Studio Enterprise, selezionare un elemento e avviare il debug con IntelliTrace. Ciò consente di passare a qualsiasi evento nel file e visualizzare dettagli specifici sull'applicazione in un dato momento.  
  
 È possibile salvare i dati IntelliTrace dalle seguenti origini:  
  
- Una sessione di IntelliTrace in Visual Studio 2015 Enterprise o versioni precedenti di Visual Studio Ultimate.  
  
- Una sessione di test in Microsoft Test Manager  
  
- App Web ASP.NET ospitate in IIS o applicazioni SharePoint 2010 e SharePoint 2013 in esecuzione nella distribuzione quando si usa Microsoft Monitoring Agent, in modalità autonoma o con System Center 2012. Vedere [uso dell'agente di raccolta autonomo IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md) e [monitoraggio con Microsoft Monitoring Agent](https://technet.microsoft.com/library/dn465153.aspx).  
  
  Di seguito sono riportati alcuni esempi sul modo in cui IntelliTrace semplifica le operazioni di debug:  
  
- L'applicazione ha danneggiato un file di dati, ma non si sa dove si è verificato l'evento.  
  
   Senza IntelliTrace, sarebbe necessario esaminare il codice per trovare tutti gli accessi possibili al file, inserire punti di interruzione in corrispondenza di tali accessi e quindi rieseguire l'applicazione per individuare dove si è verificato il problema. Con IntelliTrace è possibile vedere tutti gli eventi di accesso ai file raccolti e dettagli specifici sull'applicazione nel momento in cui si è verificato ciascun evento.  
  
- Si verifica un'eccezione.  
  
   Senza IntelliTrace si ottiene un messaggio su un'eccezione ma non si dispone di molte informazioni sugli eventi che ne hanno causato la comparsa. È possibile esaminare lo stack di chiamate per individuare la catena che ha generato l'eccezione, ma non è possibile visualizzare la sequenza di eventi che si sono verificati durante tali chiamate. Con IntelliTrace è possibile esaminare gli eventi che si sono verificati prima dell'eccezione.  
  
- L'applicazione si arresta in modo anomalo in un computer utilizzato per i test, ma viene eseguita correttamente in un computer di sviluppo.  
  
   È possibile raccogliere dati IntelliTrace da Microsoft Test Manager, salvare i dati in un file .iTrace e allegarlo a un elemento di lavoro Team Foundation Server per analizzarlo in un secondo momento. Vedere [raccogliere più dati di diagnostica nei test manuali](https://msdn.microsoft.com/library/bb5a2cc0-84f5-4dfe-9560-ca3d313aefd2) e [usare i dati di IntelliTrace salvati](../debugger/using-saved-intellitrace-data.md).  
  
- Un bug o un arresto anomalo si verifica in un'applicazione distribuita.  
  
   Per le app basate su Microsoft Azure, è possibile configurare la raccolta di dati IntelliTrace prima di pubblicare l'applicazione. Mentre l'applicazione è in esecuzione, IntelliTrace salva i dati in un file .iTrace. Vedere [Debug di un servizio cloud pubblicato con IntelliTrace e Visual Studio](../azure/vs-azure-tools-intellitrace-debug-published-cloud-services.md).  
  
   Per le app Web ASP.NET ospitate in IIS 7.0, 7.5 e 8.0 o le applicazioni SharePoint 2010 o SharePoint 2013, utilizzare Microsoft Monitoring Agent, in modalità autonoma o con System Center 2012, per salvare i dati IntelliTrace in un file .iTrace.  
  
   Si tratta di un'opzione utile per diagnosticare problemi con le app in fase di distribuzione. Vedere [uso dell'agente di raccolta autonomo IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md).  
  
## <a name="WhatData"></a> Quali dati raccoglie IntelliTrace?  
 **Raccolta delle informazioni sugli eventi**  
  
 Per impostazione predefinita, IntelliTrace registra solo gli eventi di IntelliTrace: eventi del debugger, eccezioni, eventi .NET Framework e altri eventi di sistema utili per il debug. È possibile scegliere i tipi di eventi IntelliTrace che si desidera raccogliere, tranne gli eventi del debugger e le eccezioni, che vengono sempre raccolti. Vedere [Configure IntelliTrace](https://msdn.microsoft.com/7657ecab-e07e-4b1b-872d-f05d966be37e).  
  
- **Eventi del debugger**  
  
   IntelliTrace registra sempre gli eventi che si verificano nel debugger di Visual Studio. Ad esempio, l'avvio dell'applicazione è un evento del debugger. Altri eventi del debugger sono eventi di arresto, ossia quelli che interrompono l'esecuzione dell'applicazione, ad esempio il rilevamento di un punto di interruzione, il rilevamento di un punto di analisi o l'esecuzione di un comando di **esecuzione**.  
  
   Ai fini delle prestazioni, IntelliTrace non registra ogni possibile valore per un evento del debugger. Vengono invece registrati questi valori:  
  
  - Valori nella finestra **Variabili locali**. Per visualizzarli, mantenere aperta la finestra **Variabili locali**.  
  
  - Valori nella finestra **Auto** solo se la finestra **Auto** è aperta  
  
  - Valori nei suggerimenti dati mostrati quando si sposta il puntatore del mouse su una variabile nella finestra di origine per visualizzarne il valore. Tramite IntelliTrace non vengono raccolti i valori nei suggerimenti dati bloccati.  
  
- **Eccezioni**  
  
   Tramite IntelliTrace vengono registrati il tipo di eccezione e il messaggio per questi tipi di eccezione:  
  
  - Eccezioni gestite in cui l'eccezione viene generata e rilevata  
  
  - Eccezioni non gestite  
  
- **Eventi .NET Framework**  
  
   Per impostazione predefinita, tramite IntelliTrace vengono registrati gli eventi .NET Framework più comuni. Ad esempio:  
  
  - Per un evento di accesso ai file, tramite IntelliTrace viene raccolto il nome del file.  
  
  - Per un evento di verifica della casella di controllo, raccoglie lo stato e il testo della casella di controllo.  
  
- **Eventi delle applicazioni SharePoint 2010 e SharePoint 2013**  
  
   È possibile registrare eventi di profili utente e un subset di eventi del sistema di registrazione unificato per le applicazioni SharePoint 2010 e 2013 in esecuzione all'esterno di Visual Studio. È possibile salvare questi eventi in un file .iTrace. Richiede Visual Studio Enterprise 2015, una versione precedente di Visual Studio Ultimate o [Microsoft Monitoring Agent](https://go.microsoft.com/fwlink/?LinkID=309771) in esecuzione in modalità **Trace** .  
  
   Quando si apre il file .iTrace, immettere un ID di correlazione SharePoint per trovare la richiesta Web corrispondente, visualizzare gli eventi registrati e avviare il debug da un evento specifico. Se il file contiene eccezioni non gestite, è possibile scegliere un ID di correlazione per avviare il debug di un'eccezione.  
  
   Vedere:  
  
  - [Uso dell'agente di raccolta autonomo IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md)  
  
  - [Uso dei dati di IntelliTrace salvati](../debugger/using-saved-intellitrace-data.md)  
  
  - [Procedura dettagliata: debug di un'applicazione di SharePoint tramite IntelliTrace](https://msdn.microsoft.com/library/4bd80d2f-f680-4bf4-81c3-f14e8185f6a4)  
  
  **Raccolta delle informazioni sulle chiamate di funzione**  
  
  È possibile configurare IntelliTrace per la raccolta delle informazioni sulle chiamate per le funzioni. Tali informazioni consentono di visualizzare la cronologia dello stack di chiamate e scorrere in avanti e indietro le chiamate nel codice. Per ogni chiamata di funzione, IntelliTrace registra i seguenti dati:  
  
- Nome funzione  
  
- Valori dei tipi di dati primitivi passati come parametri nei punti di ingresso di una funzione e restituiti nei punti di uscita  
  
- Valori delle proprietà automatiche quando vengono letti o modificati  
  
- Puntatori agli oggetti figlio di primo livello, ma non ai relativi valori, se non quelli che indicano se lo stato è null oppure no  
  
> [!NOTE]
> IntelliTrace raccoglie solo i primi 256 oggetti in matrici e i primi 256 caratteri per le stringhe.  
  
 Vedere [Configure IntelliTrace](https://msdn.microsoft.com/7657ecab-e07e-4b1b-872d-f05d966be37e).  
  
 **Raccolta delle informazioni sui moduli**  
  
 Per controllare la quantità di informazioni sulle chiamate raccolte da IntelliTrace, specificare solo i moduli di interesse. In questo modo è possibile migliorare le prestazioni dell'applicazione durante la raccolta. Vedere [Configure IntelliTrace](https://msdn.microsoft.com/7657ecab-e07e-4b1b-872d-f05d966be37e).  
  
## <a name="AffectPerformance"></a> IntelliTrace rallenterà l'applicazione?  
 Per impostazione predefinita, vengono raccolti dati solo per eventi di IntelliTrace selezionati. Ciò può rallentare o meno l'applicazione, a seconda della struttura e dell'organizzazione del codice. Ad esempio, se IntelliTrace registra spesso un evento, questo potrebbe rallentare l'applicazione. Potrebbe essere opportuno anche considerare il refactoring dell'applicazione.  
  
 La raccolta di informazioni sulle chiamate potrebbe rallentare significativamente l'applicazione. Potrebbe inoltre aumentare la dimensione di ogni file di log IntelliTrace (file .iTrace) salvato nel disco. Per ridurre al minimo questi effetti, raccogliere le informazioni sulle chiamate solo per i moduli desiderati.  Per modificare la dimensione massima dei file .iTrace, passare a **Strumenti**, **Opzioni**, **IntelliTrace**, **Avanzate**. Vedere [Configure IntelliTrace](https://msdn.microsoft.com/7657ecab-e07e-4b1b-872d-f05d966be37e).  
  
## <a name="in-this-section"></a>In questa sezione  
 [Funzionalità IntelliTrace](../debugger/intellitrace-features.md)  
  
 [Configurare IntelliTrace](https://msdn.microsoft.com/7657ecab-e07e-4b1b-872d-f05d966be37e)  
  
 [Inclusione dei dati di traccia di diagnostica con bug difficili da riprodurre](https://msdn.microsoft.com/library/944ae9af-5a55-4c58-b520-0108c03b3564)  
  
 [Diagnosticare i problemi dopo la distribuzione](../debugger/diagnose-problems-after-deployment.md)  
  
 [Uso dei dati di IntelliTrace salvati](../debugger/using-saved-intellitrace-data.md)  
  
### <a name="blogs"></a>Blog  
 [Visual Studio ALM + Team Foundation Server](https://blogs.msdn.com/b/visualstudioalm)  
  
### <a name="forums"></a>Forums  
 [Diagnostica di Visual Studio](https://social.msdn.microsoft.com/Forums/vsdebug)
