---
title: Decompilazione di codice .NET durante il debug . Documenti Microsoft
ms.date: 2/2/2020
ms.topic: conceptual
dev_langs:
- CSharp
helpviewer_keywords:
- decompilation, debugger, exception
- debugging [Visual Studio], decompilation, source not found
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.openlocfilehash: d63c05120842d52dd54359e128d0cc5f2a195817
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "79508745"
---
# <a name="generate-source-code-from-net-assemblies-while-debugging"></a>Generare codice sorgente da assembly .NET durante il debugGenerate source code from .NET assemblies while debugging

Quando si esegue il debug di un'applicazione .NET, è possibile che si desidera visualizzare il codice sorgente che non si dispone. Ad esempio, l'interruzione su un'eccezione o utilizzando lo stack di chiamate per passare a un percorso di origine.

> [!NOTE]
> * La generazione di codice sorgente (decompilazione) è disponibile solo per le applicazioni .NET ed è basata sul progetto [ILSpy](https://github.com/icsharpcode/ILSpy) open source.
> * La decompilazione è disponibile solo in Visual Studio 2019 16.5 e versioni successive.
> * L'applicazione dell'attributo [SuppressIldasmAttribute](https://docs.microsoft.com/dotnet/api/system.runtime.compilerservices.suppressildasmattribute) a un assembly o a un modulo impedisce a Visual Studio di tentare la decompilazione.

## <a name="generate-source-code"></a>Genera codice sorgente

Quando si esegue il debug e non è disponibile alcun codice sorgente, Visual Studio mostra il documento **Source Not Found** o, se non si dispone di simboli per l'assembly, il documento Nessun simbolo **caricato.** Entrambi i documenti dispongono di un'opzione **Decompila codice sorgente** che genera il codice C ' per la posizione corrente. Il codice generato in c'è quindi può essere utilizzato come qualsiasi altro codice sorgente. È possibile visualizzare il codice, esaminare le variabili, impostare punti di interruzione e così via.

### <a name="no-symbols-loaded"></a>Nessun simbolo caricato

Nella figura seguente viene illustrato il messaggio Nessun simbolo **caricato.**

![Schermata di nessun documento caricato con simbolo](media/decompilation-no-symbol-found.png)

### <a name="source-not-found"></a>Origine non trovata

Nella figura seguente viene illustrato il messaggio **Origine non trovata.**

![Screenshot del documento di origine non trovato](media/decompilation-no-source-found.png)

## <a name="generate-and-embed-sources-for-an-assembly"></a>Generare e incorporare origini per un assembly

Oltre a generare codice sorgente per un percorso specifico, è possibile generare tutto il codice sorgente per un determinato assembly .NET. A tale scopo, passare alla finestra **moduli** e dal menu di scelta rapida di un assembly .NET, quindi selezionare il comando **Decompila codice sorgente.** Visual Studio genera un file di simboli per l'assembly e quindi incorpora l'origine nel file di simboli. In un passaggio successivo, è possibile [estrarre](#extract-and-view-the-embedded-source-code) il codice sorgente incorporato.

![Screenshot del menu di contesto dell'assembly nella finestra dei moduli con il comando Decompila origine.](media/decompilation-decompile-source-code.png)

## <a name="extract-and-view-the-embedded-source-code"></a>Estrarre e visualizzare il codice sorgente incorporato

È possibile estrarre i file di origine incorporati in un file di simboli utilizzando il comando **Estrai codice sorgente** nel menu di scelta rapida della finestra **Moduli.**

![Screenshot del menu contestuale dell'assieme nella finestra dei moduli con il comando Estrai origini.](media/decompilation-extract-source-code.png)

I file di origine estratti vengono aggiunti alla soluzione come [file vari](../ide/reference/miscellaneous-files.md). La funzionalità dei file vari è disattivata per impostazione predefinita in Visual Studio.The miscellaneous files feature is off by default in Visual Studio. È possibile attivare **Tools** > questa funzionalità dalla casella di controllo Strumenti**Opzioni** > **documenti ambiente** > **Documents** > **Mostra file esterni in Esplora soluzioni.** Senza abilitare questa funzionalità, non sarà possibile aprire il codice sorgente estratto.

![Screenshot della pagina delle opzioni degli strumenti con l'opzione File vari abilitata.](media/decompilation-tools-options-misc-files.png)

I file di origine estratti vengono visualizzati nei file vari in **Esplora soluzioni**.

![Screenshot di Esplora soluzioni con file vari.](media/decompilation-solution-explorer.png)

## <a name="known-limitations"></a>Limitazioni note

### <a name="requires-break-mode"></a>Richiede la modalità di interruzione

La generazione di codice sorgente mediante la decompilazione è possibile solo quando il debugger è in modalità di interruzione e l'applicazione viene sospesa. Ad esempio, Visual Studio passa alla modalità di interruzione quando raggiunge un punto di interruzione o un'eccezione. È possibile attivare facilmente Visual Studio per interrompere la prossima![esecuzione del](media/decompilation-break-all.png)codice utilizzando il comando **Interrompi tutto** ( Interrompi tutto icona ).

### <a name="decompilation-limitations"></a>Limitazioni della decompilazione

La generazione di codice sorgente dal formato intermedio (IL) utilizzato negli assembly .NET presenta alcune limitazioni intrinseche. Di conseguenza, il codice sorgente generato non ha l'aspetto del codice sorgente originale. La maggior parte delle differenze si trovano in posizioni in cui le informazioni nel codice sorgente originale non sono necessarie in fase di esecuzione. Ad esempio, informazioni quali spazi vuoti, commenti e nomi delle variabili locali non sono necessarie in fase di esecuzione. Si consiglia di utilizzare l'origine generata per comprendere come il programma è in esecuzione e non in sostituzione del codice sorgente originale.

### <a name="debug-optimized-or-release-assemblies"></a>Debug di assembly ottimizzati o di rilascioDebug optimized or release assemblies

Quando si esegue il debug di codice che è stato decompilato da un assembly compilato utilizzando le ottimizzazioni del compilatore, è possibile riscontrare i seguenti problemi:
- I punti di interruzione potrebbero non essere sempre associati al percorso di approvvigionamento corrispondente.
- L'esecuzione potrebbe non essere sempre nella posizione corretta.
- Le variabili locali potrebbero non avere nomi precisi.
- Alcune variabili potrebbero non essere disponibili per la valutazione.

Ulteriori dettagli sono disponibili nel problema GitHub: [Integrazione ICSharpCode.Decompiler in VS Debugger](https://github.com/icsharpcode/ILSpy/issues/1901).

### <a name="decompilation-reliability"></a>Affidabilità della decompilazione

Una percentuale relativamente piccola di tentativi di decompilazione può causare errori. Ciò è dovuto a un errore di riferimento null del punto di sequenza in ILSpy.This is due to a sequence point null-reference error in ILSpy.  Abbiamo attenuato l'errore analizzando questi problemi e eseguendo normalmente il tentativo di decompilazione.

Ulteriori dettagli sono disponibili nel problema GitHub: [Integrazione ICSharpCode.Decompiler in VS Debugger](https://github.com/icsharpcode/ILSpy/issues/1901).

### <a name="limitations-with-async-code"></a>Limitazioni con codice asincronoLimitations with async code

I risultati dei moduli di decompilazione con modelli di codice async/await potrebbero essere incompleti o non riuscire del tutto. L'implementazione ILSpy di async/await e yield state-machines è implementata solo parzialmente. 

Ulteriori dettagli sono disponibili nel problema GitHub: [PDB Generator Status](https://github.com/icsharpcode/ILSpy/issues/1422).

### <a name="just-my-code"></a>Just My Code

Le impostazioni [JMC (Just My Code)](https://docs.microsoft.com/visualstudio/debugger/just-my-code) consentono a Visual Studio di eseguire un'istruzione alla volta nel sistema, nel framework, nella libreria e in altre chiamate non utente. Durante una sessione di debug, la finestra **Moduli** mostra quali moduli di codice il debugger considera come My Code (codice utente).

La decompilazione di moduli ottimizzati o di rilascio produce codice non utente. Se il debugger si interrompe nel codice non utente decompilato, ad esempio, viene visualizzata la finestra **Nessuna origine.** Per disattivare Just My **Code,** passare a**Opzioni** degli **strumenti** > (o**Opzioni**di **debug** > ) > **Debug** > **generale**, quindi deselezionare Abilita Just My Code .

### <a name="extracted-sources"></a>Fonti estratte

Il codice sorgente estratto da un assembly presenta le limitazioni seguenti:Source code extracted from an assembly has the following limitations:
- Il nome e il percorso dei file generati non sono configurabili.
- I file sono temporanei e verranno eliminati da Visual Studio.
- I file vengono inseriti in una singola cartella e qualsiasi gerarchia di cartelle che le origini originali avevano non viene utilizzata.
- Il nome del file per ogni file contiene un hash di checksum del file.

### <a name="generated-code-is-c-only"></a>Il codice generato è solo in C
La decompilazione genera solo i file di codice sorgente in C . Non è possibile generare file in qualsiasi altra lingua.
