---
title: Decompilare il codice .NET durante il debug | Microsoft Docs
description: Generare e incorporare il codice sorgente dagli assembly .NET durante il debug in Visual Studio. Estrarre e visualizzare il codice sorgente incorporato.
ms.custom: SEO-VS-2020
ms.date: 2/2/2020
ms.topic: how-to
dev_langs:
- CSharp
helpviewer_keywords:
- decompilation, debugger, exception
- debugging [Visual Studio], decompilation, source not found
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.openlocfilehash: 84ba27607a594862905ef77b7979e89009eb098e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99872157"
---
# <a name="generate-source-code-from-net-assemblies-while-debugging"></a>Genera codice sorgente da assembly .NET durante il debug

Quando si esegue il debug di un'applicazione .NET, è possibile che si desideri visualizzare il codice sorgente che non è presente. Ad esempio, è possibile suddividere in un'eccezione o usare lo stack di chiamate per passare a un percorso di origine.

> [!NOTE]
> * La generazione del codice sorgente (decompilazione) è disponibile solo per le applicazioni .NET ed è basata sul progetto open source [ILSpy](https://github.com/icsharpcode/ILSpy) .
> * La decompilazione è disponibile solo in Visual Studio 2019 16,5 e versioni successive.
> * L'applicazione dell'attributo [SuppressIldasmAttribute](/dotnet/api/system.runtime.compilerservices.suppressildasmattribute) a un assembly o un modulo impedisce a Visual Studio di provare a eseguire la decompilazione.

## <a name="generate-source-code"></a>Genera codice sorgente

Quando si esegue il debug e non è disponibile codice sorgente, Visual Studio Mostra il documento di **origine non trovato** o, se non sono presenti simboli per l'assembly, il documento **Nessun simbolo** è stato caricato. In entrambi i documenti è presente un'opzione di **codice sorgente decompilata** che genera codice C# per il percorso corrente. Il codice C# generato può quindi essere usato in modo analogo a qualsiasi altro codice sorgente. È possibile visualizzare il codice, controllare le variabili, impostare i punti di interruzione e così via.

### <a name="no-symbols-loaded"></a>Nessun simbolo caricato

Nella figura seguente viene mostrato il messaggio **Nessun simbolo caricato** .

![Screenshot del documento nessun simbolo caricato](media/decompilation-no-symbol-found.png)

### <a name="source-not-found"></a>Origine non trovata

Nella figura seguente viene illustrato il messaggio di **origine non trovato** .

![Screenshot del documento di origine non trovato](media/decompilation-no-source-found.png)

## <a name="generate-and-embed-sources-for-an-assembly"></a>Generare e incorporare origini per un assembly

Oltre a generare codice sorgente per un percorso specifico, è possibile generare tutto il codice sorgente per un determinato assembly .NET. A tale scopo, passare alla finestra **moduli** e dal menu di scelta rapida di un assembly .NET, quindi selezionare il comando **Decompila codice sorgente** . Visual Studio genera un file di simboli per l'assembly, quindi incorpora l'origine nel file di simboli. In un passaggio successivo è possibile [estrarre](#extract-and-view-the-embedded-source-code) il codice sorgente incorporato.

![Screenshot del menu di scelta rapida dell'assembly nella finestra moduli con comando Decompila origine.](media/decompilation-decompile-source-code.png)

## <a name="extract-and-view-the-embedded-source-code"></a>Estrarre e visualizzare il codice sorgente incorporato

È possibile estrarre i file di origine incorporati in un file di simboli usando il comando **Estrai codice sorgente** nel menu di scelta rapida della finestra **moduli** .

![Screenshot del menu di scelta rapida dell'assembly nella finestra moduli con il comando Estrai origini.](media/decompilation-extract-source-code.png)

I file di origine estratti vengono aggiunti alla soluzione come [file esterni](../ide/reference/miscellaneous-files.md). La funzionalità file esterni è disattivata per impostazione predefinita in Visual Studio. È possibile abilitare questa funzionalità dalla casella di controllo **strumenti**  >  **Opzioni**  >  **ambiente**  >  **documenti**  >  **Mostra file esterni in Esplora soluzioni casella di** controllo. Senza abilitare questa funzionalità, non sarà possibile aprire il codice sorgente estratto.

![Screenshot della pagina delle opzioni degli strumenti con l'opzione file esterni abilitata.](media/decompilation-tools-options-misc-files.png)

I file di origine estratti vengono visualizzati nei file esterni in **Esplora soluzioni**.

![Screenshot di Esplora soluzioni con file esterni.](media/decompilation-solution-explorer.png)

## <a name="known-limitations"></a>Limitazioni note

### <a name="requires-break-mode"></a>Richiede la modalità di interruzioni

La generazione di codice sorgente tramite la decompilazione è possibile solo quando il debugger è in modalità di interruzione e l'applicazione viene sospesa. Ad esempio, in Visual Studio viene attivata la modalità di interruzione quando viene raggiunto un punto di interruzione o un'eccezione. È possibile attivare facilmente Visual Studio per interrompere la prossima esecuzione del codice usando il comando **Interrompi tutto** ( ![ icona Interrompi tutto ](media/decompilation-break-all.png) ).

### <a name="decompilation-limitations"></a>Limitazioni della decompilazione

La generazione di codice sorgente dal formato intermedio (IL) utilizzato negli assembly .NET presenta alcune limitazioni intrinseche. Di conseguenza, il codice sorgente generato non ha un aspetto simile al codice sorgente originale. La maggior parte delle differenze si trova in posizioni in cui le informazioni nel codice sorgente originale non sono necessarie in fase di esecuzione. Ad esempio, le informazioni quali spazi vuoti, commenti e nomi di variabili locali non sono necessarie in fase di esecuzione. Si consiglia di utilizzare l'origine generata per comprendere il modo in cui il programma è in esecuzione e non come sostituzione del codice sorgente originale.

### <a name="debug-optimized-or-release-assemblies"></a>Debug di assembly ottimizzati o versione

Quando si esegue il debug di codice decompilato da un assembly compilato con ottimizzazioni del compilatore, è possibile che si verifichino i problemi seguenti:
- I punti di interruzione potrebbero non essere sempre associati al percorso di origine corrispondente.
- L'esecuzione di istruzioni potrebbe non sempre passare alla posizione corretta.
- Le variabili locali non possono avere nomi accurati.
- Alcune variabili potrebbero non essere disponibili per la valutazione.

Per altri dettagli, vedere il problema relativo a GitHub: [integrazione di icsharpcode. Decompiler nel debugger di Visual](https://github.com/icsharpcode/ILSpy/issues/1901)Studio.

### <a name="decompilation-reliability"></a>Affidabilità della decompilazione

Una percentuale relativamente ridotta dei tentativi di decompilazione può causare un errore. Ciò è dovuto a un errore di riferimento null del punto di sequenza in ILSpy.  L'errore è stato mitigato intercettando questi problemi e il tentativo di decompilazione non riesce correttamente.

Per altri dettagli, vedere il problema relativo a GitHub: [integrazione di icsharpcode. Decompiler nel debugger di Visual](https://github.com/icsharpcode/ILSpy/issues/1901)Studio.

### <a name="limitations-with-async-code"></a>Limitazioni con codice asincrono

I risultati della decompilazione dei moduli con i modelli di codice async/await potrebbero essere incompleti o non riuscire completamente. L'implementazione ILSpy di async/await e yield state-machines è implementata solo parzialmente. 

Per altri dettagli, vedere il problema [relativo al generatore PDB](https://github.com/icsharpcode/ILSpy/issues/1422)di GitHub.

### <a name="just-my-code"></a>Just My Code

Le impostazioni di [Just My Code (JMC)](./just-my-code.md) consentono a Visual Studio di eseguire un'istruzione/routine di sistema, Framework, libreria e altre chiamate non utente. Durante una sessione di debug, nella finestra **moduli** vengono visualizzati i moduli di codice che il debugger sta trattando come codice utente (codice utente).

La decompilazione di moduli ottimizzati o versione produce codice non utente. Se il debugger si interrompe nel codice non utente decompilato, ad esempio, non viene visualizzata **alcuna** finestra di origine. Per disabilitare Just My Code, passare a **strumenti**  >  **Opzioni** (o   >  **Opzioni** di debug) > **debug**  >  **generale**, quindi deselezionare **Abilita Just My Code**.

### <a name="extracted-sources"></a>Origini estratte

Il codice sorgente Estratto da un assembly presenta le limitazioni seguenti:
- Il nome e il percorso dei file generati non sono configurabili.
- I file sono temporanei e verranno eliminati da Visual Studio.
- I file si trovano in una singola cartella e in qualsiasi gerarchia di cartelle utilizzata dalle origini originali.
- Il nome file di ogni file contiene un hash di checksum del file.

### <a name="generated-code-is-c-only"></a>Il codice generato è solo C#
La decompilazione genera solo file di codice sorgente in C#. Non è possibile generare file in altre lingue.