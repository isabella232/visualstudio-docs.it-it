---
title: Decompilare il codice .NET durante il debug | Microsoft Docs
description: Generare e incorporare codice sorgente da assembly .NET durante il debug in Visual Studio. Estrarre e visualizzare il codice sorgente incorporato.
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
ms.technology: vs-ide-debug
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.openlocfilehash: 024d202122452c21594ed04dbf9c96256e73ca6f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122112854"
---
# <a name="generate-source-code-from-net-assemblies-while-debugging"></a>Generare codice sorgente da assembly .NET durante il debug

Quando si esegue il debug di un'applicazione .NET, è possibile che si voglia visualizzare il codice sorgente che non si ha. Ad esempio, interruzione in caso di eccezione o uso dello stack di chiamate per passare a un percorso di origine.

> [!NOTE]
> * La generazione di codice sorgente (decompilazione) è disponibile solo per le applicazioni .NET ed è basata sul open source [ILSpy.](https://github.com/icsharpcode/ILSpy)
> * La decompilazione è disponibile solo in Visual Studio 2019 16.5 e versioni successive.
> * L'applicazione [dell'attributo SuppressIldasmAttribute](/dotnet/api/system.runtime.compilerservices.suppressildasmattribute) a un assembly o a un modulo impedisce Visual Studio tentativo di decompilazione.

## <a name="generate-source-code"></a>Generare codice sorgente

Quando si esegue il debug e non è disponibile  codice sorgente, Visual Studio mostra il documento Origine non trovata o, se non si dispone di simboli per l'assembly, il documento **Nessun** simbolo caricato. Entrambi i documenti hanno **un'opzione Decompile source code** che genera codice C# per la posizione corrente. Il codice C# generato può quindi essere usato come qualsiasi altro codice sorgente. È possibile visualizzare il codice, esaminare le variabili, impostare punti di interruzione e così via.

### <a name="no-symbols-loaded"></a>Nessun simbolo caricato

La figura seguente mostra il **messaggio Nessun simbolo caricato.**

![Screenshot di nessun documento caricato da simboli](media/decompilation-no-symbol-found.png)

### <a name="source-not-found"></a>Origine non trovata

La figura seguente mostra il **messaggio Origine non** trovata.

![Screenshot del documento di origine non trovato](media/decompilation-no-source-found.png)

## <a name="generate-and-embed-sources-for-an-assembly"></a>Generare e incorporare origini per un assembly

Oltre a generare codice sorgente per un percorso specifico, è possibile generare tutto il codice sorgente per un determinato assembly .NET. A tale scopo, passare alla finestra **Moduli** e dal menu di scelta rapida di un assembly .NET e quindi selezionare il **comando Decompile source code (Decompila codice sorgente).** Visual Studio genera un file di simboli per l'assembly e quindi incorpora l'origine nel file di simboli. In un passaggio successivo è possibile estrarre [il](#extract-and-view-the-embedded-source-code) codice sorgente incorporato.

![Screenshot del menu di scelta rapida dell'assembly nella finestra dei moduli con il comando decompile source.](media/decompilation-decompile-source-code.png)

## <a name="extract-and-view-the-embedded-source-code"></a>Estrarre e visualizzare il codice sorgente incorporato

È possibile estrarre i file di origine incorporati in un file di simboli usando il comando **Estrai** codice sorgente nel menu di scelta rapida della **finestra** Moduli.

![Screenshot del menu di scelta rapida dell'assembly nella finestra dei moduli con il comando estrai origini.](media/decompilation-extract-source-code.png)

I file di origine estratti vengono aggiunti alla soluzione [come file esterni.](../ide/reference/miscellaneous-files.md) La funzionalità file esterni è disattivata per impostazione predefinita in Visual Studio. È possibile abilitare questa funzionalità dalla **casella** di controllo Strumenti Opzioni Ambiente Documenti Mostra file  >    >    >    >  **esterni Esplora soluzioni.** Senza abilitare questa funzionalità, non sarà possibile aprire il codice sorgente estratto.

![Screenshot della pagina delle opzioni degli strumenti con l'opzione file esterni abilitata.](media/decompilation-tools-options-misc-files.png)

I file di origine estratti vengono visualizzati nei file esterni in **Esplora soluzioni**.

![Screenshot di Esplora soluzioni con file esterni.](media/decompilation-solution-explorer.png)

## <a name="known-limitations"></a>Limitazioni note

### <a name="requires-break-mode"></a>Richiede la modalità di interruzione

La generazione di codice sorgente tramite decompilazione è possibile solo quando il debugger è in modalità di interruzione e l'applicazione è sospesa. Ad esempio, Visual Studio attiva la modalità di interruzione quando raggiunge un punto di interruzione o un'eccezione. È possibile attivare facilmente il Visual Studio alla successiva esecuzione del  codice usando il comando Interrompi tutto ( ![ icona Interrompi tutto ](media/decompilation-break-all.png) ).

### <a name="decompilation-limitations"></a>Limitazioni della decompilazione

La generazione di codice sorgente dal formato intermedio (IL) usato negli assembly .NET presenta alcune limitazioni intrinseche. Di conseguenza, il codice sorgente generato non è simile al codice sorgente originale. La maggior parte delle differenze si verifica in posizioni in cui le informazioni nel codice sorgente originale non sono necessarie in fase di esecuzione. Ad esempio, informazioni come spazi vuoti, commenti e nomi delle variabili locali non sono necessarie in fase di esecuzione. È consigliabile usare l'origine generata per comprendere come viene eseguito il programma e non come sostituzione del codice sorgente originale.

### <a name="debug-optimized-or-release-assemblies"></a>Eseguire il debug di assembly ottimizzati o di versione

Quando si esegue il debug di codice decompilato da un assembly compilato usando le ottimizzazioni del compilatore, è possibile che si insodrranno i problemi seguenti:
- I punti di interruzione non possono sempre essere associati alla posizione di origine corrispondente.
- L'esecuzione di istruzioni non sempre può essere un'istruzione alla posizione corretta.
- Le variabili locali potrebbero non avere nomi accurati.
- Alcune variabili potrebbero non essere disponibili per la valutazione.

Altri dettagli sono disponibili nella pagina GitHub: [Integrazione di ICSharpCode.Decompiler in VS Debugger.](https://github.com/icsharpcode/ILSpy/issues/1901)

### <a name="decompilation-reliability"></a>Affidabilità della decompilazione

Una percentuale relativamente piccola di tentativi di decompilazione può causare un errore. Ciò è dovuto a un errore di riferimento Null del punto di sequenza in ILSpy.  L'errore è stato attenuato intercettando questi problemi e fallendo normalmente il tentativo di decompilazione.

Altri dettagli sono disponibili nella pagina GitHub: [Integrazione di ICSharpCode.Decompiler in VS Debugger.](https://github.com/icsharpcode/ILSpy/issues/1901)

### <a name="limitations-with-async-code"></a>Limitazioni con il codice asincrono

I risultati della decompilazione dei moduli con modelli di codice asincrono/await possono essere incompleti o non riuscire completamente. L'implementazione ILSpy di async/await e yield state-machines è implementata solo parzialmente. 

Altri dettagli sono disponibili nel problema GitHub: Stato del [generatore PDB](https://github.com/icsharpcode/ILSpy/issues/1422).

### <a name="just-my-code"></a>Just My Code

Le [Just My Code (JMC)](./just-my-code.md) consentono Visual Studio di eseguire le istruzioni su sistema, framework, libreria e altre chiamate non utente. Durante una sessione di debug, la **finestra Moduli** mostra i moduli di codice trattati dal debugger come My Code (codice utente).

La decompilazione di moduli ottimizzati o di versione produce codice non utente. Se il debugger si interrompe nel codice non utente decompilato, ad esempio, viene visualizzata la **finestra Nessuna** origine. Per disabilitare Just My Code, passare a Opzioni strumenti (o Opzioni di  >     >  debug) > **Debug** generale e quindi deselezionare Abilita Just My Code  >  . 

### <a name="extracted-sources"></a>Origini estratte

Il codice sorgente estratto da un assembly presenta le limitazioni seguenti:
- Il nome e il percorso dei file generati non sono configurabili.
- I file sono temporanei e verranno eliminati da Visual Studio.
- I file vengono inseriti in una singola cartella e non viene usata alcuna gerarchia di cartelle delle origini originali.
- Il nome file per ogni file contiene un hash di checksum del file.

### <a name="generated-code-is-c-only"></a>Il codice generato è solo C#
La decompilazione genera solo file di codice sorgente in C#. Non è possibile generare file in altre lingue.