---
title: Debug di codice gestito | Microsoft Docs
description: Vedere i problemi e le tecniche di debug comuni in Visual Studio per le applicazioni gestite o le app scritte in linguaggi che hanno come destinazione Common Language Runtime.
ms.custom: SEO-VS-2020
ms.date: 09/23/2019
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- dotnet
ms.openlocfilehash: 0b4ff397996ac57d85ac52a338bdce6049e392dc725227c2021e384c81093931
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121240403"
---
# <a name="debug-managed-code-c-visual-basic-f-ccli"></a>Eseguire il debug di codice gestito (C#, Visual Basic, F#, C++/CLI)

Questa sezione illustra i problemi di debug comuni e le tecniche per le applicazioni gestite o le applicazioni scritte in linguaggi che hanno come destinazione Common Language Runtime, ad esempio Visual Basic, C# e C++/CLI. Le tecniche descritte sono di livello avanzato. [Esaminare prima di tutto il debugger](../debugger/debugger-feature-tour.md).

## <a name="in-this-section"></a>Contenuto della sezione

[Messaggi di diagnostica nel Finestra di output](../debugger/diagnostic-messages-in-the-output-window.md)\
Vengono descritte le classi <xref:System.Diagnostics.Debug> e <xref:System.Diagnostics.Trace>, con le quali è possibile scrivere messaggi di runtime nella finestra di **Output**. Queste classi includono metodi di output che supportano l'output di informazioni senza interruzione dell'esecuzione e l'output di informazioni con interruzione dell'esecuzione se non viene rispettata una condizione specificata.

[Asserzioni nel codice gestito](../debugger/assertions-in-managed-code.md)\
Vengono descritte le asserzioni nel codice gestito, che verificano le condizioni specificate come argomenti per i metodi `Assert`. In questo argomento vengono anche forniti il codice di esempio, le informazioni sull'utilizzo dei metodi <xref:System.Diagnostics.Debug> e <xref:System.Diagnostics.Trace>, le considerazioni sulle versioni di debug e di rilascio del codice, gli effetti secondari, gli argomenti assert, la personalizzazione del comportamento assert e i file di configurazione.

[Istruzioni Stop in Visual Basic](../debugger/stop-statements-in-visual-basic.md)\
Viene descritta l'istruzione `Stop`, che fornisce un'alternativa all'impostazione di un punto di interruzione. Sono inoltre disponibili esempi di codice e un confronto tra le istruzioni `Stop` ed `End` e tra le istruzioni `Stop` e `Assert`.

[Procedura dettagliata: debug di un form Windows dati](../debugger/walkthrough-debugging-a-windows-form.md)\
Vengono date istruzioni dettagliate per la creazione di un Windows Form e per il debug di tale form. Un Windows Form, un componente standard di un'applicazione Windows gestita, è una delle applicazioni gestite più comuni. In questa procedura dettagliata vengono utilizzati Visual C# e Visual Basic, ma le tecniche per la creazione di un Windows Form con C++ sono simili.

[Debug del metodo OnStart](../debugger/how-to-debug-the-onstart-method.md)\
Vengono forniti codici di esempio per consentire il debug del metodo `OnStart` di un servizio Windows gestito. Per eseguire il debug del metodo `OnStart` di un servizio Windows, è necessario aggiungere alcune righe di codice per simulare il servizio.

[Debug in modalità mista](../debugger/debugging-mixed-mode-applications.md)\
Viene descritto il debug di applicazioni in modalità mista, ovvero qualsiasi applicazione nella quale vengono combinati codice nativo e codice gestito.

[Errore: Il debug non è possibile perché nel sistema è abilitato un debugger del kernel](../debugger/error-debugging-isn-t-possible-because-a-kernel-debugger-is-enabled-on-the-system.md)\
Viene descritto un messaggio di errore visualizzato se si tenta di eseguire il debug del codice gestito in un sistema [!INCLUDE[win7](../debugger/includes/win7_md.md)], [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)], [!INCLUDE[winxp](../code-quality/includes/winxp_md.md)], [!INCLUDE[Win2kFamily](../code-quality/includes/win2kfamily_md.md)] o Windows NT avviato in modalità debug.

[Ottimizzazione e debug JIT](../debugger/jit-optimization-and-debugging.md)\
Vengono descritti gli effetti dell'ottimizzazione JIT sul debug.

[Debug di LINQ e DLINQ](../debugger/debugging-linq.md)\
Vengono illustrate le tecniche per il debug di query LINQ.

[Procedura dettagliata: debug di un'applicazione parallela](../debugger/walkthrough-debugging-a-parallel-application.md)\
Viene descritto come usare le finestre degli strumenti **Attività in parallelo** e **Stack in parallelo** per eseguire il debug di un'applicazione parallela.

## <a name="related-sections"></a>Sezioni correlate

[Intellitrace](../debugger/intellitrace.md)\
Individuare i bug in modo più rapido e semplice registrando la cronologia di esecuzione dell'app con IntelliTrace. Eseguire all'indietro e in avanti gli eventi registrati e le chiamate per esaminare lo stato dell'app in determinati momenti. Eseguire il debug del codice senza impostare molti punti di interruzione o riavviare l'app con frequenza. Richiede Visual Studio Enterprise.

[Traccia e strumentazione di applicazioni](/dotnet/framework/debug-trace-profile/tracing-and-instrumenting-applications)\
Vengono descritte la traccia, che consente di monitorare l'esecuzione dell'applicazione, e la strumentazione, che prevede l'inserimento di istruzioni di traccia in corrispondenza di posizioni strategiche nel codice. In questo argomento vengono anche forniti collegamenti a un'introduzione all'instrumentazione e alla traccia, opzioni di traccia, listener di traccia, traccia del codice in un'applicazione, aggiunta di istruzioni di traccia al codice dell'applicazione e compilazione in modo condizionale con <xref:System.Diagnostics.Debug> e <xref:System.Diagnostics.Trace>.

[/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute)\
Viene descritta un'opzione del linker che aggiunge <xref:System.Diagnostics.DebuggableAttribute> al codice scritto con C++. Questo attributo è necessario per l'utilizzo di funzionalità di debug, quali la connessione con C++.

[Debug Windows applicazioni di servizio](/dotnet/framework/windows-services/how-to-debug-windows-service-applications)\
Vengono fornite considerazioni per il debug di applicazioni di servizio Windows, quali: impostazione, connessione al processo, debug del codice nel metodo `OnStart` del servizio e il codice nel metodo Main, impostazione di punti di interruzione e utilizzo di Services Control Manager per avviare, interrompere, arrestare e continuare il servizio.

[Debug e profilatura](/dotnet/framework/debug-trace-profile/index)\
Vengono illustrati il debug di applicazioni .NET e i requisiti di configurazione.

[Debug di script e applicazioni Web](how-to-enable-debugging-for-aspnet-applications.md)\
Vengono presentati le tecniche di debug e i problemi più comuni riscontrabili durante il debug di script e applicazioni Web.

## <a name="see-also"></a>Vedi anche

- [Procedura dettagliata: Eseguire il debug di Windows form personalizzati in fase di progettazione](/dotnet/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time)
- [Sicurezza del debugger](../debugger/debugger-security.md)
- [Debug in Visual Studio](../debugger/index.yml)
- [Presentazione del debugger](../debugger/debugger-feature-tour.md)