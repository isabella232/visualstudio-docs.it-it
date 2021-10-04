---
title: IntelliTrace | Microsoft Docs
description: Usare IntelliTrace per registrare e tracciare la cronologia di esecuzione del codice in Visual Studio. Registrare eventi specifici, esaminare il codice correlato ed eseguire il debug degli errori.
ms.custom: SEO-VS-2020
ms.date: 09/19/2018
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
- IntelliTrace
- IntelliTrace, debugging after a crash
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 539e1e89f31851897adab932d75c0dca170155f9
ms.sourcegitcommit: 541871db9065c4fb1b21c24f980c563991b183c7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2021
ms.locfileid: "129431094"
---
# <a name="intellitrace-for-visual-studio-enterprise-c-visual-basic-c"></a>IntelliTrace per Visual Studio Enterprise (C#, Visual Basic, C++)

È possibile ridurre il tempo richiesto per eseguire il debug dell'applicazione quando si usa IntelliTrace per registrare e tenere traccia della cronologia di esecuzione del codice. È possibile trovare facilmente i bug perché IntelliTrace consente di:

- Registrare eventi specifici

- Esaminare il codice correlato, i dati visualizzati nella finestra **Variabili locali** durante gli eventi del debugger e le informazioni di chiamata di funzione

- Eseguire il debug di errori difficili da riprodurre o verificatisi in fase di distribuzione

È possibile utilizzare IntelliTrace in Visual Studio Enterprise edition (ma non le edizioni Professional o Community).

## <a name="what-do-you-want-to-do"></a>Per saperne di più

|Scenario|Titolo|
|-|-|
|**Eseguire il debug dell'applicazione con IntelliTrace:**<br /><br /> - Mostrare gli eventi passati.<br />- Mostrare le informazioni sulle chiamate con gli eventi passati.<br />- Salvare la sessione di IntelliTrace.<br />- Controllare i dati raccolti da IntelliTrace.|- [Esaminare gli stati delle app precedenti usando IntelliTrace](../debugger/view-historical-application-state.md)<br />- [Procedura dettagliata: uso di IntelliTrace](../debugger/walkthrough-using-intellitrace.md)<br />- [Funzionalità di IntelliTrace](../debugger/intellitrace-features.md)<br />- [Debug cronologico](../debugger/historical-debugging.md)|
|**Raccogliere dati IntelliTrace dalle applicazioni distribuite**|- [Uso dell'agente di raccolta autonomo IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md)|
|**Avviare il debug da un file di log IntelliTrace (file .iTrace).**|- [Uso dei dati IntelliTrace salvati](../debugger/using-saved-intellitrace-data.md)|

## <a name="what-apps-can-i-debug-with-intellitrace"></a><a name="IntelliTraceSupport"></a> Di quali app è possibile eseguire il debug con IntelliTrace?

| Livello di supporto| Tipi di applicazioni |
|---------------------| - |
| **Supporto completo** | - Applicazioni Visual Basic e Visual C# che usano .NET Framework 2.0 o versioni successive.<br/>È possibile eseguire il debug della maggior parte delle applicazioni, comprese le app ASP.NET, Microsoft Azure, Windows Form, WCF, WPF, Windows Workflow, SharePoint 2010, SharePoint 2013 e a 64 bit.<br/>Per eseguire il debug SharePoint applicazioni con IntelliTrace, vedere Procedura dettagliata: debug di [un SharePoint appalto tramite IntelliTrace.](../sharepoint/walkthrough-debugging-a-sharepoint-application-by-using-intellitrace.md)<br/> Per eseguire il debug Microsoft Azure app con IntelliTrace, vedere Debug di un servizio cloud pubblicato [con IntelliTrace e Visual Studio](../azure/vs-azure-tools-intellitrace-debug-published-cloud-services.md). |
| **Supporto limitato** | - Le app C++ Windows supportano la visualizzazione di snapshot con la funzionalità per tornare indietro di IntelliTrace. Sono supportati solo gli eventi di debugger ed eccezione.<br />- App .NET Core e ASP.NET Core supportate solo per determinati eventi (eventi controller MVC, ADO.NET e HTTPClient) nel debug locale. L'agente di raccolta autonomo non è supportato per .NET Core o ASP.NET Core app.<br />- App F# su base sperimentale<br />- App UWP supportate solo per gli eventi |
| **Non supportato** | - Altri linguaggi e script<br />- Windows, Silverlight, Xbox o Windows per dispositivi mobili |

> [!NOTE]
> Se si vuole eseguire il debug di un processo già in esecuzione, è possibile raccogliere solo eventi IntelliTrace (nessuna informazione di chiamata). È possibile connettersi a un processo a 32 bit o a 64 bit solo nel computer locale. Gli eventi che si verificano prima della connessione al processo non vengono raccolti.

## <a name="why-debug-with-intellitrace"></a><a name="IntelliTraceVSTraditional"></a> Perché eseguire il debug con IntelliTrace?

Il debug tradizionale o *attivo* mostra solo lo stato corrente dell'applicazione con dati limitati sugli eventi passati. È necessario dedurre tali eventi dallo stato corrente dell'applicazione oppure ricrearli rieseguendo l'applicazione.

IntelliTrace consente di espandere questa esperienza di debug tradizionale registrando dati ed eventi specifici in un preciso momento. Ciò consente di verificare cosa sia accaduto nell'applicazione senza riavviarla, specialmente se si supera il punto in cui si è verificato il bug. IntelliTrace è attivato per impostazione predefinita durante il debug tradizionale e raccoglie i dati in modo automatico e invisibile. Ciò consente di passare facilmente dal debug tradizionale al debug IntelliTrace e viceversa per visualizzare le informazioni registrate. Vedere [Funzionalità di IntelliTrace](../debugger/intellitrace-features.md) [e Quali dati raccoglie IntelliTrace?](#WhatData)

IntelliTrace consente anche di eseguire il debug di errori difficili da riprodurre o che si verificano in fase di distribuzione. È possibile raccogliere dati IntelliTrace e salvarli in un file di log IntelliTrace (file .iTrace), contenente dettagli su eccezioni, eventi di prestazioni, richieste Web, dati di test, thread, moduli e altre informazioni di sistema. È possibile aprire questo file in Visual Studio Enterprise, selezionare un elemento e avviare il debug con IntelliTrace. Ciò consente di passare a qualsiasi evento nel file e visualizzare dettagli specifici sull'applicazione in un dato momento.

È possibile salvare i dati IntelliTrace dalle seguenti origini:

- Una sessione di IntelliTrace in Visual Studio 2015 Enterprise o versioni successive o versioni precedenti di Visual Studio Ultimate.

- App Web ASP.NET ospitate in IIS o applicazioni SharePoint 2010 e SharePoint 2013 in esecuzione nella distribuzione quando si usa Microsoft Monitoring Agent, in modalità autonoma o con System Center 2012. Vedere [Usare l'agente di raccolta autonomo IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md) e [Monitoraggio con Microsoft Monitoring Agent](/previous-versions/system-center/system-center-2012-R2/dn465153(v=sc.12)).

Di seguito sono riportati alcuni esempi sul modo in cui IntelliTrace semplifica le operazioni di debug:

- L'applicazione ha danneggiato un file di dati, ma non si sa dove si è verificato l'evento.

  Senza IntelliTrace, sarebbe necessario esaminare il codice per trovare tutti gli accessi possibili al file, inserire punti di interruzione in corrispondenza di tali accessi e quindi rieseguire l'applicazione per individuare dove si è verificato il problema. Con IntelliTrace è possibile vedere tutti gli eventi di accesso ai file raccolti e dettagli specifici sull'applicazione nel momento in cui si è verificato ciascun evento.

- Si verifica un'eccezione.

  Senza IntelliTrace si ottiene un messaggio su un'eccezione ma non si dispone di molte informazioni sugli eventi che ne hanno causato la comparsa. È possibile esaminare lo stack di chiamate per individuare la catena che ha generato l'eccezione, ma non è possibile visualizzare la sequenza di eventi che si sono verificati durante tali chiamate. Con IntelliTrace è possibile esaminare gli eventi che si sono verificati prima dell'eccezione.

- Un bug o un arresto anomalo si verifica in un'applicazione distribuita.

  Per le app basate su Microsoft Azure, è possibile configurare la raccolta di dati IntelliTrace prima di pubblicare l'applicazione. Mentre l'applicazione è in esecuzione, IntelliTrace salva i dati in un file .iTrace. Vedere [Eseguire il debug di un servizio cloud pubblicato con IntelliTrace e Visual Studio](../azure/vs-azure-tools-intellitrace-debug-published-cloud-services.md).

  Per le app Web ASP.NET ospitate in IIS 7.0, 7.5 e 8.0 o le applicazioni SharePoint 2010 o SharePoint 2013, utilizzare Microsoft Monitoring Agent, in modalità autonoma o con System Center 2012, per salvare i dati IntelliTrace in un file .iTrace.

  Si tratta di un'opzione utile per diagnosticare problemi con le app in fase di distribuzione. Vedere [Usare l'agente di raccolta autonomo IntelliTrace.](../debugger/using-the-intellitrace-stand-alone-collector.md)

## <a name="what-data-does-intellitrace-collect"></a><a name="WhatData"></a> Quali dati raccoglie IntelliTrace?

**Raccogliere informazioni sull'evento**

Per impostazione predefinita, IntelliTrace registra solo gli eventi di IntelliTrace: eventi del debugger, eccezioni, eventi .NET Framework e altri eventi di sistema utili per il debug. È possibile scegliere i tipi di eventi IntelliTrace che si desidera raccogliere, tranne gli eventi del debugger e le eccezioni, che vengono sempre raccolti. Vedere [Funzionalità di IntelliTrace.](../debugger/intellitrace-features.md)

- **Eventi del debugger**

  IntelliTrace registra sempre gli eventi che si verificano nel debugger di Visual Studio. Ad esempio, l'avvio dell'applicazione è un evento del debugger. Altri eventi del debugger sono eventi di arresto, ossia quelli che interrompono l'esecuzione dell'applicazione, ad esempio il rilevamento di un punto di interruzione, il rilevamento di un punto di analisi o l'esecuzione di un comando di **esecuzione**.

  Per impostazione predefinita, per migliorare le prestazioni, IntelliTrace non registra tutti i valori possibili per un evento del debugger. Vengono invece registrati questi valori:

  - Valori nella finestra **Variabili locali**. Per visualizzarli, mantenere aperta la finestra **Variabili locali**.

  - Valori nella finestra **Auto** solo se la finestra **Auto** è aperta

  - Valori nei suggerimenti dati mostrati quando si sposta il puntatore del mouse su una variabile nella finestra di origine per visualizzarne il valore. Tramite IntelliTrace non vengono raccolti i valori nei suggerimenti dati bloccati.

    Quando è abilitata la modalità Eventi e snapshot di IntelliTrace, IntelliTrace esegue uno snapshot del processo dell'applicazione in corrispondenza di ogni evento **Punto** di interruzione **e Passaggio del** debugger. Verranno registrati i valori nelle **finestre Variabili** locali , **Auto** ed **Espressioni** di controllo , indipendentemente dal fatto che le finestre siano aperte o meno. Verranno raccolti anche i valori nei suggerimenti dati aggiunti.

- **Eccezioni**

  Tramite IntelliTrace vengono registrati il tipo di eccezione e il messaggio per questi tipi di eccezione:

  - Eccezioni gestite in cui l'eccezione viene generata e rilevata

  - Eccezioni non gestite

- **Eventi .NET Framework**

  Per impostazione predefinita, tramite IntelliTrace vengono registrati gli eventi .NET Framework più comuni. Ad esempio, per un evento, IntelliTrace raccoglie lo stato e il <xref:System.Windows.Forms.CheckBox.CheckedChanged?displayProperty=nameWithType> testo della casella di controllo.

- **Eventi delle applicazioni SharePoint 2010 e SharePoint 2013**

  È possibile registrare eventi di profili utente e un subset di eventi del sistema di registrazione unificato per le applicazioni SharePoint 2010 e 2013 in esecuzione all'esterno di Visual Studio. È possibile salvare questi eventi in un file .iTrace. Richiede Visual Studio Enterprise 2015 o versioni successive, una versione precedente [](https://visualstudio.microsoft.com/vs/older-downloads/#visual-studio-2015-and-other-products) di Visual Studio Ultimate o Microsoft Monitoring Agent in esecuzione in **modalità di** traccia.

  Quando si apre il file .iTrace, immettere un ID di correlazione SharePoint per trovare la richiesta Web corrispondente, visualizzare gli eventi registrati e avviare il debug da un evento specifico. Se il file contiene eccezioni non gestite, è possibile scegliere un ID di correlazione per avviare il debug di un'eccezione.

  Vedere:

  - [Usare l'agente di raccolta autonomo IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md)

  - [Usare i dati di IntelliTrace salvati](../debugger/using-saved-intellitrace-data.md)

  - [Procedura dettagliata: debug di un'applicazione SharePoint tramite IntelliTrace](../sharepoint/walkthrough-debugging-a-sharepoint-application-by-using-intellitrace.md)

**Acquisire snapshot**

È possibile configurare IntelliTrace per acquisire snapshot a ogni punto di interruzione e a ogni evento del passaggio del debugger. IntelliTrace registra lo stato completo dell'applicazione in ogni snapshot, che consente di visualizzare variabili complesse e di valutare le espressioni.

> [!NOTE]
> [L'agente di raccolta autonomo IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md) non supporta l'acquisizione di snapshot.

Vedere [Esaminare gli stati dell'app precedenti usando IntelliTrace.](../debugger/view-historical-application-state.md)

**Raccogliere informazioni sulle chiamate di funzione**

È possibile configurare IntelliTrace per la raccolta delle informazioni sulle chiamate per le funzioni. Tali informazioni consentono di visualizzare la cronologia dello stack di chiamate e scorrere in avanti e indietro le chiamate nel codice. Per ogni chiamata di funzione, IntelliTrace registra i seguenti dati:

- Nome della funzione
- Valori dei tipi di dati primitivi passati come parametri nei punti di ingresso di una funzione e restituiti nei punti di uscita
- Valori delle proprietà automatiche quando vengono letti o modificati
- Puntatori agli oggetti figlio di primo livello, ma non ai relativi valori, se non quelli che indicano se lo stato è null oppure no

> [!NOTE]
> IntelliTrace raccoglie solo i primi 256 oggetti in matrici e i primi 256 caratteri per le stringhe.

Vedere [Esaminare l'app con il debug cronologico.](../debugger/historical-debugging-inspect-app.md)

**Raccogliere informazioni sul modulo**

Per controllare la quantità di informazioni sulle chiamate raccolte da IntelliTrace, specificare solo i moduli di interesse. In questo modo è possibile migliorare le prestazioni dell'applicazione durante la raccolta. Vedere la sezione [Controllare la quantità di informazioni raccolte da IntelliTrace](../debugger/intellitrace-features.md#ControlCallData) nelle funzionalità di IntelliTrace.

## <a name="will-intellitrace-slow-down-my-application"></a><a name="AffectPerformance"></a> IntelliTrace rallenterà l'applicazione?

Per impostazione predefinita, vengono raccolti dati solo per eventi di IntelliTrace selezionati. Ciò può rallentare o meno l'applicazione, a seconda della struttura e dell'organizzazione del codice. Ad esempio, se IntelliTrace registra spesso un evento, questo potrebbe rallentare l'applicazione. Potrebbe essere opportuno anche considerare il refactoring dell'applicazione.

La raccolta di informazioni sulle chiamate potrebbe rallentare significativamente l'applicazione. Potrebbero inoltre aumentare le dimensioni di ogni file di log IntelliTrace (file con estensione iTrace) salvato nel disco. Per ridurre al minimo questi effetti, raccogliere le informazioni sulle chiamate solo per i moduli desiderati.  Per modificare la dimensione massima dei file .iTrace, passare a **Strumenti**, **Opzioni**, **IntelliTrace**, **Avanzate**.

### <a name="blogs"></a>Blog

[Microsoft DevOps](https://devblogs.microsoft.com/devops/)

### <a name="forums"></a>Forum

[Diagnostica di Visual Studio](https://social.msdn.microsoft.com/Forums/en-US/home)