---
title: Debug del codice gestito | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging managed code
- debugging ASP.NET Web applications, managed code
- managed code, debugging
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 14dc53413f646718b85ec9ea43d968dc9f64a96f
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56719316"
---
# <a name="debugging-managed-code"></a>Debug del codice gestito

In questa sezione vengono descritti alcuni problemi di debug comuni e vengono illustrate varie tecniche per le applicazioni gestite, ovvero scritte in linguaggi compatibili con Common Language Runtime, ad esempio Visual Basic, C# e C++. Le tecniche descritte sono di livello avanzato. [Presentazione del debugger](../debugger/debugger-feature-tour.md).

## <a name="in-this-section"></a>In questa sezione

[Messaggi diagnostici nella finestra di Output](../debugger/diagnostic-messages-in-the-output-window.md) descrive le <xref:System.Diagnostics.Debug> e <xref:System.Diagnostics.Trace> classi, con cui è possibile scrivere messaggi in fase di esecuzione per il **Output** finestra. Queste classi includono metodi di output che supportano l'output di informazioni senza interruzione dell'esecuzione e l'output di informazioni con interruzione dell'esecuzione se non viene rispettata una condizione specificata.

[Asserzioni nel codice gestito](../debugger/assertions-in-managed-code.md) vengono descritte le asserzioni nel codice gestito, che verificano le condizioni specificate come argomenti a `Assert` metodi. In questo argomento vengono anche forniti il codice di esempio, le informazioni sull'utilizzo dei metodi <xref:System.Diagnostics.Debug> e <xref:System.Diagnostics.Trace>, le considerazioni sulle versioni di debug e di rilascio del codice, gli effetti secondari, gli argomenti assert, la personalizzazione del comportamento assert e i file di configurazione.

[Istruzioni Stop in Visual Basic](../debugger/stop-statements-in-visual-basic.md) descrive il `Stop` istruzione, che offre un'alternativa all'impostazione di un punto di interruzione. Sono inoltre disponibili esempi di codice e un confronto tra le istruzioni `Stop` ed `End` e tra le istruzioni `Stop` e `Assert`.

[Procedura dettagliata: Debug di un Form Windows](../debugger/walkthrough-debugging-a-windows-form.md) offre istruzioni dettagliate per la creazione di un modulo di Windows e il debug di tale modulo. Un Windows Form, un componente standard di un'applicazione Windows gestita, è una delle applicazioni gestite più comuni. In questa procedura dettagliata vengono utilizzati Visual C# e Visual Basic, ma le tecniche per la creazione di un Windows Form con C++ sono simili.

[Debug del metodo OnStart](../debugger/how-to-debug-the-onstart-method.md) vengono forniti esempi di codice per consentire il debug di `OnStart` metodo di un servizio Windows gestito. Per eseguire il debug del metodo `OnStart` di un servizio Windows, è necessario aggiungere alcune righe di codice per simulare il servizio.

[Debug in modalità mista](../debugger/debugging-mixed-mode-applications.md) esamina il debug di applicazioni in modalità mista. ovvero qualsiasi applicazione nella quale vengono combinati codice nativo e codice gestito.

[Errore: Eseguire il debug perché nel sistema è attivato un debugger del kernel](../debugger/error-debugging-isn-t-possible-because-a-kernel-debugger-is-enabled-on-the-system.md) descrive un messaggio di errore che si verifica se si prova a eseguire il debug di codice gestito in un [!INCLUDE[win7](../debugger/includes/win7_md.md)], [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)], [!INCLUDE[winxp](../code-quality/includes/winxp_md.md)], [!INCLUDE[Win2kFamily](../code-quality/includes/win2kfamily_md.md)], o un sistema di Windows NT che è stato avviato in modalità di debug.

[Debug e ottimizzazione JIT](../debugger/jit-optimization-and-debugging.md) descrive gli effetti dell'ottimizzazione JIT sul debug.

[Debug di LINQ e DLINQ](../debugger/debugging-linq.md) vengono illustrate le tecniche per il debug di query LINQ.

[Procedura dettagliata: Debug di un'applicazione parallela](../debugger/walkthrough-debugging-a-parallel-application.md) descrive come usare il **attività in parallelo** e **stack in parallelo** finestre degli strumenti di debug di un'applicazione parallela.

## <a name="related-sections"></a>Sezioni correlate

[IntelliTrace](../debugger/intellitrace.md) individuare i bug più veloci e semplici registrando la cronologia di esecuzione dell'app con IntelliTrace. Eseguire all'indietro e in avanti gli eventi registrati e le chiamate per esaminare lo stato dell'app in determinati momenti. Eseguire il debug del codice senza impostare molti punti di interruzione o riavviare l'app con frequenza. Richiede Visual Studio Enterprise.

[Tracciare e instrumentare applicazioni](/dotnet/framework/debug-trace-profile/tracing-and-instrumenting-applications) descrive la traccia, un modo per monitorare l'esecuzione dell'applicazione mentre è in esecuzione e la strumentazione, che prevede l'inserimento di istruzioni di traccia in posizioni strategiche nel codice. In questo argomento vengono anche forniti collegamenti a un'introduzione all'instrumentazione e alla traccia, opzioni di traccia, listener di traccia, traccia del codice in un'applicazione, aggiunta di istruzioni di traccia al codice dell'applicazione e compilazione in modo condizionale con <xref:System.Diagnostics.Debug> e <xref:System.Diagnostics.Trace>.

[/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute) descrive un'opzione del linker che aggiunge <xref:System.Diagnostics.DebuggableAttribute> al codice scritto con C++. Questo attributo è necessario per l'utilizzo di funzionalità di debug, quali la connessione con C++.

[Debug di applicazioni di servizio di Windows](/dotnet/framework/windows-services/how-to-debug-windows-service-applications) vengono fornite considerazioni per il debug di applicazioni di servizio di Windows, inclusa l'impostazione di, connessione al processo, debug del codice del servizio `OnStart` (metodo) e il codice principale metodo, i punti di interruzione di impostazione e utilizzando Gestione controllo servizi per avviare, arrestare, sospendere e riprendere il servizio.

[Debug e profilatura](/dotnet/framework/debug-trace-profile/index) vengono illustrati i requisiti di configurazione e debug di applicazioni .NET Framework.

[Debug di Script e applicazioni Web](/visualstudio/debugger/how-to-enable-debugging-for-aspnet-applications) descrive le tecniche che possono verificarsi durante il debug di script e applicazioni Web e i problemi di debug comuni.

[Novità relative al Debugger di Visual Studio 2015](../debugger/what-s-new-for-the-debugger-in-visual-studio.md) descrizione della nuova funzionalità di debug integrate in questa versione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

[Home Page del debug](../debugger/debugger-feature-tour.md) vengono forniti collegamenti a sezioni più ampie della documentazione sul debug. Le informazioni fornite comprendono: novità del debugger, impostazioni e preparazione, punti di interruzione, gestione delle eccezioni, modifica e continuazione, debug di codice gestito, debug di progetti Visual C++, debug di COM e ActiveX, debug di DLL, debug di SQL e riferimenti per l'interfaccia utente.

## <a name="see-also"></a>Vedere anche

[Procedura dettagliata: Debug personalizzati Windows Form controlli in fase di progettazione](/dotnet/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time)
[sicurezza del Debugger](../debugger/debugger-security.md)
[debug in Visual Studio](../debugger/index.md) 
 [ Iniziare a esaminare il debugger](../debugger/debugger-feature-tour.md)