---
title: Suggerimenti per migliorare le prestazioni
description: Informazioni su come ottimizzare Visual Studio funzionalità che potrebbero non essere in uso per migliorare le prestazioni.
ms.custom: SEO-VS-2020
ms.date: 03/02/2021
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 61c57e489df355e399bc970549f0725a9c495f72
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122116656"
---
# <a name="visual-studio-performance-tips-and-tricks"></a>Suggerimenti sulle prestazioni di Visual Studio

I suggerimenti per le prestazioni di Visual Studio si riferiscono a situazioni di memoria insufficiente che possono verificarsi in casi eccezionali. In queste situazioni, è possibile ottimizzare determinate funzionalità di Visual Studio che potrebbero non essere in uso. I suggerimenti seguenti non sono intesi come indicazioni generali.

> [!NOTE]
> In caso di difficoltà di uso del prodotto a causa di problemi di memoria, segnalarlo tramite lo [strumento di feedback](../ide/how-to-report-a-problem-with-visual-studio.md).

## <a name="use-a-64-bit-os"></a>Usare un sistema operativo a 64 bit

Se si aggiorna il sistema da una versione di Windows a 32 bit a una versione a 64 bit, espandere la quantità di memoria virtuale disponibile per Visual Studio da 2 a 4 GB. Ciò consente a Visual Studio di gestire carichi di lavoro di dimensioni notevolmente maggiori anche tramite il processo a 32 bit.

Per altre informazioni, vedere i [limiti di memoria](/windows/desktop/Memory/memory-limits-for-windows-releases) e la pagina[Use /LARGEADDRESSAWARE on 64-bit Window](https://blogs.msdn.microsoft.com/oldnewthing/20050601-24/?p=35483/) ( Uso di /LARGEADDRESSAWARE in Windows a 64 bit).

## <a name="disable-automatic-file-restore"></a>Disabilitare il ripristino automatico dei file

Visual Studio riaprire automaticamente i documenti lasciati aperti nella sessione precedente. Questa azione può prolungare il tempo necessario per caricare una soluzione di oltre il 30%, a seconda del tipo di progetto e dei documenti lasciati aperti. L'apertura di alcune finestre di progettazione, come Windows Forms e XAML, e di alcuni file JavaScript e TypeScript potrebbe risultare lenta.

Tramite una barra gialla, Visual Studio indica se il ripristino automatico dei documenti sta rallentando considerevolmente il caricamento di una soluzione. È possibile disabilitare la riapertura automatica dei file seguendo questa procedura:

1. Selezionare **Opzioni**  >  **strumenti** per aprire la **finestra di dialogo** Opzioni.

1. Nella pagina **Progetti e soluzioni**  >  **Generali** deselezionare Riapri **documenti al caricamento della soluzione**.

Se si disabilita il ripristino automatico dei file, è possibile accedere velocemente ai file da aprire usando il comando [Vai a](../ide/go-to.md):

- Per le funzionalità generali di **Vai a**, selezionare **Modifica** > **Vai a** > **Vai a tutti** oppure premere **CTRL**+**T**.

- Passare all'ultima posizione di modifica in una **soluzione** usando Modifica Vai all'ultima modifica oppure premendo  >    >   **CTRL** +  + **MAIUSC+BACKSPACE**.

- Usare **Go To Recent File** (Vai a file recenti) per visualizzare un elenco di file visitati di recente in una soluzione. Selezionare **Modifica**  >  **Vai a** file  >  **recente** oppure premere **CTRL** + **1**, **CTRL** + **R**.

## <a name="configure-debugging-options"></a>Configurare le opzioni di debug

Se in genere si verificano problemi di memoria insufficiente durante le sessioni di debug, è possibile ottimizzare le prestazioni apportando una o più modifiche alla configurazione.

- **Abilitare Just My Code**

    L'ottimizzazione più semplice consiste nell'abilitazione della funzionalità **Just My Code** che carica solo i simboli per il proprio progetto. L'abilitazione di questa funzionalità può offrire un notevole risparmio di memoria per il debug delle applicazioni gestite (.NET). Questa opzione è già abilitata per impostazione predefinita in alcuni tipi di progetto.

    Per abilitare **Just My Code**, scegliere **Strumenti** > **Opzioni** > **Debug** > **Generale**, quindi selezionare **Abilita Just My Code**.

- **Specificare i simboli da caricare**

    Per il debug nativo, il caricamento dei file di simboli (con estensione *pdb*) è dispendioso in termini di risorse di memoria. È possibile configurare le impostazioni dei simboli del debugger per risparmiare memoria. In genere, si configura la soluzione per caricare solo i moduli del proprio progetto.

    Per specificare il caricamento dei simboli, scegliere **Strumenti**  >  **Opzioni**  >  **Simboli di**  >  **debug**.

    Impostare le opzioni su **Solo moduli specificati** anziché su **Tutti i moduli** e quindi specificare quali moduli si intende caricare. Durante il debug, è anche possibile fare doppio clic su moduli specifici nella finestra **Moduli** per includere in modo esplicito un modulo nel caricamento dei simboli Per aprire la finestra durante il debug, scegliere **Debug**  >  **Windows**  >  **Moduli**.)

    Per altre informazioni, vedere [Understand symbol files](?view=vs-2019&preserve-view=true) (Informazioni sui file dei simboli).

- **Disabilitare gli strumenti di diagnostica**

    È consigliabile disabilitare la profilatura della CPU dopo l'uso. Questa funzionalità può utilizzare grandi quantità di risorse. Dopo aver abilitato la profilatura della CPU, questo stato viene mantenuto per le sessioni di debug successive, perciò è preferibile disattivarla al termine. È possibile risparmiare risorse disabilitando gli strumenti di diagnostica durante il debug se la funzionalità offerte non sono necessarie.

    Per disabilitare la **Strumenti di diagnostica**, avviare una sessione di debug, selezionare Opzioni strumenti Debug generale e quindi deselezionare l'opzione Abilita Strumenti di diagnostica  >    >    >   **durante il** debug.

    Per altre informazioni, vedere [Strumenti di profilatura](../profiling/profiling-feature-tour.md).

## <a name="disable-tools-and-extensions"></a>Disabilitare strumenti ed estensioni

Per migliorare le prestazioni, è possibile disabilitare alcuni strumenti o estensioni.

> [!TIP]
> È in genere possibile isolare i problemi di prestazioni disattivando le estensioni una alla volta e ricontrollando le prestazioni.

### <a name="managed-language-service-roslyn"></a>Servizio di linguaggio gestito (Roslyn)

Per informazioni sulle prestazioni di .NET Compiler Platform ("Roslyn"), vedere [Considerazioni sulle prestazioni di soluzioni di grandi dimensioni](https://github.com/dotnet/roslyn/blob/master/docs/wiki/Performance-considerations-for-large-solutions.md).

- **Disabilitare l'analisi della soluzione completa**

    Visual Studio esegue l'analisi dell'intera soluzione per fornire un'esperienza completa di verifica degli errori prima di richiamare una compilazione. Questa funzionalità è utile per identificare gli errori il più presto possibile. In caso di soluzioni di grandi dimensioni, questa funzionalità può tuttavia richiedere un maggiore utilizzo delle risorse di memoria. In caso di memoria insufficiente o di problemi analoghi, è possibile disabilitare questa funzionalità per liberare risorse. Per impostazione predefinita, questa opzione è abilitata per Visual Basic ed è disabilitata per C#.

    Per disabilitare l'**analisi della soluzione completa**, scegliere **Strumenti** > **Opzioni** > **Editor di testo**, quindi selezionare **Visual Basic** o **C#**. Scegliere **Avanzate** e deselezionare **Abilita analisi della soluzione completa**.

- **Disabilitare CodeLens**

    Visual Studio esegue un'attività **Trova tutti i riferimenti** su ogni metodo quando viene visualizzato. CodeLens offre funzionalità come la visualizzazione inline del numero di riferimenti. Il lavoro viene eseguito in un processo separato, ad esempio *ServiceHub.RoslynCodeAnalysisService32*. In soluzioni di grandi dimensioni o in sistemi con risorse limitate, questa funzionalità può influenzare notevolmente le prestazioni. Se si riscontra un elevato utilizzo della CPU in questo processo o se si verificano problemi di memoria, ad esempio durante il caricamento di una soluzione di grandi dimensioni in un computer da 4 GB, è possibile disabilitare la funzionalità CodeLens per liberare le risorse.

    Per disabilitare **CodeLens**, scegliere **Strumenti** > **Opzioni** > **Editor di testo** > **Tutti i linguaggi** > **CodeLens** e deselezionare la funzionalità.

    > [!NOTE]
    > CodeLens è disponibile nelle edizioni Professional ed Enterprise di Visual Studio.

### <a name="other-tools-and-extensions"></a>Altri strumenti ed estensioni

- **Disabilitare le estensioni**

    Le estensioni sono componenti software aggiuntivi aggiunti di Visual Studio che offrono nuove funzionalità o estendono le funzionalità esistenti. Le estensioni possono spesso dare origine a problemi di memoria. Se si verificano problemi di memoria, provare a disabilitare estensioni una alla volta per verificarne l'impatto su scenario o flusso di lavoro.

   ::: moniker range="vs-2017"

    Per disabilitare le estensioni, passare **a Estensioni** e aggiornamenti degli strumenti e > disabilitare una determinata estensione.

   ::: moniker-end

   ::: moniker range=">=vs-2019"

    Per disabilitare le estensioni, passare **a Estensioni** > **Gestione estensioni** e disabilitare una determinata estensione.

   ::: moniker-end

- **Disabilitare la modalità mappa**

    [**La modalità mappa**](how-to-track-your-code-by-customizing-the-scrollbar.md#display-modes) visualizza le righe di codice, in miniatura, sulla barra di scorrimento. La modalità mappa è abilitata per impostazione predefinita.

    Per disabilitare la modalità mappa, passare a Strumenti Opzioni Editor di testo Tutte le barre di scorrimento lingue e nella sezione Comportamento deselezionare l'opzione Usa modalità mappa per barra  >    >    >    >   **di scorrimento** verticale. 

- **Disabilitare il ritorno a capo automatico**

    [**Il ritorno a**](./reference/how-to-manage-word-wrap-in-the-editor.md) capo automatico visualizza la parte di una lunga riga di codice che si estende oltre la larghezza corrente della finestra dell'editor di codice. Il ritorno a capo automatico è on per impostazione predefinita.

    Per disabilitare il ritorno a capo automatico per un progetto su cui si sta lavorando, passare a **Modifica**  >  **ritorno a capo** automatico  >  **avanzato.** È possibile attivare o disattivare questa impostazione usando gli stessi comandi di menu.

    Per disabilitare il ritorno a capo automatico per tutti i progetti, passare a Opzioni strumenti Editor di testo generale Tutti i linguaggi Generale e nella sezione Impostazioni deselezionare l'opzione  >    >    >    >    >  Ritorno **a capo** automatico. 

- **Disabilitare la finestra di progettazione XAML**

    La finestra di progettazione XAML è abilitata per impostazione predefinita, ma usa risorse solo se si apre un file con estensione *xaml*. Se si utilizzano file XAML ma non si intende usare la funzionalità della finestra di progettazione, disabilitare questa funzionalità per liberare memoria.

    Per disabilitare finestra di progettazione XAML, passare **a** Strumenti  >  **Opzioni**  >  **finestra di progettazione XAML**  >  **Abilita finestra di progettazione XAML** e deselezionare l'opzione.

- **Rimuovere i carichi di lavoro**

    È possibile utilizzare il programma di installazione di Visual Studio per rimuovere i carichi di lavoro che non vengono più utilizzati. Questa azione può ridurre le esigenze di memoria di avvio ed esecuzione escludendo i pacchetti e gli assembly non più necessari.

- **Aggiungere file non tracciati al file con estensione gitignore locale**

    Visual Studio il comando Git con file non tracciati per offrire un'esperienza facile quando `git status` si aggiungono nuovi file a un repository. Quando è presente un numero elevato di file non tracciati, `git status` può utilizzare memoria aggiuntiva. Per ignorare questi file e migliorare le prestazioni di , è possibile aggiungere questi file o cartelle `git status` al file gitignore locale. Per accedere al file, passare a **Git**  >  **Impostazioni**  >  **Git Repository Impostazioni**. Nella sezione **File Git** fare  clic su Aggiungi per creare un  file con estensione gitignore oppure fare clic su Modifica se ne è già presente uno.

## <a name="force-a-garbage-collection"></a>Imporre una Garbage Collection

CLR usa una sistema di gestione della memoria di Garbage Collection. In questo sistema, talvolta viene utilizzata memoria da oggetti non più necessari. Questo stato è temporaneo, il Garbage Collector libera questa memoria in base alla propria euristica di prestazioni e uso delle risorse. È possibile imporre a CLR la raccolta della memoria inutilizzata usando un tasto di scelta rapida in Visual Studio. Se in presenza di una quantità elevata di garbage in attesa di raccolta si forza una Garbage Collection, si noterà una riduzione nel consumo di memoria da parte del processo *devenv.exe* in **Gestione attività**. È raramente è necessario utilizzare questo metodo. Tuttavia, dopo il completamento di un'operazione dispendiosa (ad esempio una compilazione completa, una sessione di debug o un evento di apertura della soluzione), può consentire di determinare la quantità di memoria effettivamente usata dal processo. Poiché Visual Studio è misto (gestito e nativo), è talvolta possibile che allocatore nativo e Garbage Collector si contengono le risorse di memoria. In condizioni di utilizzo elevato della memoria, può essere utile per imporre l'esecuzione del Garbage Collector.

Per forzare un'operazione di Garbage Collection, usare il tasto di scelta rapida: **CTRL** + **ALT** + **MAIUSC** + **F12**, **CTRL** + **ALT** + **MAIUSC** + **F12** (premere due volte).

Se l'imposizione della Garbage Collection risulta particolarmente efficiente nel proprio scenario, compilare un report tramite lo strumento per il feedback di Visual Studio poiché questo comportamento è in genere sintomo di un bug.

Per una descrizione dettagliata del Garbage Collector di CLR, vedere [Nozioni fondamentali sulla Garbage Collection](/dotnet/standard/garbage-collection/fundamentals).

## <a name="see-also"></a>Vedi anche

- [Ottimizzare le prestazioni di Visual Studio](../ide/optimize-visual-studio-performance.md)
- [Load solutions faster (Visual Studio blog)](https://devblogs.microsoft.com/visualstudio/load-solutions-faster-with-visual-studio-2017-version-15-6/) (blog di Visual Studio Caricare più rapidamente soluzioni)