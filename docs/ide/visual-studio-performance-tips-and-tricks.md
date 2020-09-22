---
title: Suggerimenti per migliorare le prestazioni
ms.date: 08/13/2020
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a5531a85bcdff90db816e942d196e0bab3b66139
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810324"
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

1. Selezionare **strumenti**  >  **Opzioni** per aprire la finestra di dialogo **Opzioni** .

1. Nella pagina **progetti e soluzioni**  >  **generale** deselezionare **Riapri documenti al caricamento della soluzione**.

Se si disabilita il ripristino automatico dei file, è possibile accedere velocemente ai file da aprire usando il comando [Vai a](../ide/go-to.md):

- Per le funzionalità generali di **Vai a**, selezionare **Modifica** > **Vai a** > **Vai a tutti** oppure premere ** CTRL**+**T**.

- Passare all'ultimo percorso di modifica in una soluzione usando **modifica**  >  **Vai a**  >  **Vai a percorso Ultima modifica**o premendo **CTRL** + **MAIUSC**indietro + **Backspace**.

- Usare **Go To Recent File** (Vai a file recenti) per visualizzare un elenco di file visitati di recente in una soluzione. Selezionare **modifica**  >  **Vai a**  >  **Vai a file recente**oppure premere **CTRL** + **1**, **CTRL** + **R**.

## <a name="configure-debugging-options"></a>Configurare le opzioni di debug

Se in genere si verificano problemi di memoria insufficiente durante le sessioni di debug, è possibile ottimizzare le prestazioni apportando una o più modifiche alla configurazione.

- **Abilita Just My Code**

    L'ottimizzazione più semplice consiste nell'abilitazione della funzionalità **Just My Code** che carica solo i simboli per il proprio progetto. L'abilitazione di questa funzionalità può offrire un notevole risparmio di memoria per il debug delle applicazioni gestite (.NET). Questa opzione è già abilitata per impostazione predefinita in alcuni tipi di progetto.

    Per abilitare **Just My Code**, scegliere **Strumenti** > **Opzioni** > **Debug** > **Generale**, quindi selezionare **Abilita Just My Code**.

- **Specificare i simboli da caricare**

    Per il debug nativo, il caricamento dei file di simboli (con estensione *pdb*) è dispendioso in termini di risorse di memoria. È possibile configurare le impostazioni dei simboli del debugger per risparmiare memoria. In genere, si configura la soluzione per caricare solo i moduli del proprio progetto.

    Per specificare il caricamento dei simboli, scegliere **strumenti**  >  **Opzioni**  >  **debug**  >  **simboli**.

    Impostare le opzioni su **Solo moduli specificati** anziché su **Tutti i moduli** e quindi specificare quali moduli si intende caricare. Durante il debug, è anche possibile fare doppio clic su moduli specifici nella finestra **Moduli** per includere in modo esplicito un modulo nel caricamento dei simboli Per aprire la finestra durante il debug, scegliere **debug**  >  . **Windows**  >  **Moduli**.)

    Per altre informazioni, vedere [Understand symbol files](?view=vs-2019) (Informazioni sui file dei simboli).

- **Disabilitare gli strumenti di diagnostica**

    È consigliabile disabilitare la profilatura della CPU dopo l'uso. Questa funzionalità può utilizzare grandi quantità di risorse. Dopo aver abilitato la profilatura della CPU, questo stato viene mantenuto per le sessioni di debug successive, perciò è preferibile disattivarla al termine. È possibile risparmiare risorse disabilitando gli strumenti di diagnostica durante il debug se la funzionalità offerte non sono necessarie.

    Per disabilitare gli **strumenti di diagnostica**, avviare una sessione di debug, scegliere **Strumenti** > **Opzioni** > **Abilita strumenti di diagnostica** e deselezionare l'opzione.

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

    Per disabilitare **CodeLens**, scegliere **Strumenti** > **Opzioni** > ** Editor di testo** > **Tutti i linguaggi** > **CodeLens** e deselezionare la funzionalità.

    > [!NOTE]
    > CodeLens è disponibile nelle edizioni Professional ed Enterprise di Visual Studio.

### <a name="other-tools-and-extensions"></a>Altri strumenti ed estensioni

- **Disabilitare le estensioni**

    Le estensioni sono componenti software aggiuntivi aggiunti di Visual Studio che offrono nuove funzionalità o estendono le funzionalità esistenti. Le estensioni possono spesso dare origine a problemi di memoria. Se si verificano problemi di memoria, provare a disabilitare estensioni una alla volta per verificarne l'impatto su scenario o flusso di lavoro.

   ::: moniker range="vs-2017"

    Per disabilitare le estensioni, andare a **Strumenti** > **Estensioni e aggiornamenti** e disabilitare l'estensione specifica.

   ::: moniker-end

   ::: moniker range=">=vs-2019"

    Per disabilitare le estensioni, andare a **Estensioni** > **Gestisci estensioni** e disabilitare l'estensione specifica.

   ::: moniker-end

- **Disabilitare la modalità mappa**

    [**Modalità mappa**](how-to-track-your-code-by-customizing-the-scrollbar.md#display-modes) Visualizza le righe di codice, in miniatura, sulla barra di scorrimento. La modalità mappa è abilitata per impostazione predefinita.

    Per disabilitare la modalità mappa, passare a **strumenti**  >  **Opzioni**  >  **editor di testo**  >  **tutti i linguaggi**  >  **barre di scorrimento**e nella sezione **comportamento** deselezionare l'opzione **Usa modalità mappa per barra di scorrimento verticale** .

- **Disabilitare il ritorno a capo automatico**

    A [**capo automatico**](./reference/how-to-manage-word-wrap-in-the-editor.md) viene visualizzata la parte di una lunga riga di codice che si estende oltre la larghezza corrente della finestra dell'editor di codice. Il ritorno a capo automatico è on per impostazione predefinita.

    Per disabilitare il ritorno a capo automatico per un progetto su cui si sta lavorando, vedere **modificare**  >  **Advanced**  >  **Word Wrap**. È possibile abilitare o disabilitare questa impostazione usando gli stessi comandi di menu.

    Per disabilitare il ritorno a capo automatico per tutti i progetti, passare a **strumenti**  >  **Opzioni**  >  **generale**  >  **editor di testo**  >  **tutti i linguaggi**  >  **generale**e nella sezione **Impostazioni** deselezionare l'opzione a **capo automatico** .

- **Disabilitare la finestra di progettazione XAML**

    La finestra di progettazione XAML è abilitata per impostazione predefinita, ma usa risorse solo se si apre un file con estensione *xaml*. Se si utilizzano file XAML ma non si intende usare la funzionalità della finestra di progettazione, disabilitare questa funzionalità per liberare memoria.

    Per disabilitare finestra di progettazione XAML, passare a **strumenti**  >  **Opzioni**  >  **finestra di progettazione XAML**  >  **Abilita finestra di progettazione XAML**e deselezionare l'opzione.

- **Rimuovere i carichi di lavoro**

    È possibile utilizzare il programma di installazione di Visual Studio per rimuovere i carichi di lavoro che non vengono più utilizzati. Questa azione può ridurre le esigenze di memoria di avvio ed esecuzione escludendo i pacchetti e gli assembly non più necessari.

## <a name="force-a-garbage-collection"></a>Imporre una Garbage Collection

CLR usa una sistema di gestione della memoria di Garbage Collection. In questo sistema, talvolta viene utilizzata memoria da oggetti non più necessari. Questo stato è temporaneo, il Garbage Collector libera questa memoria in base alla propria euristica di prestazioni e uso delle risorse. È possibile imporre a CLR la raccolta della memoria inutilizzata usando un tasto di scelta rapida in Visual Studio. Se in presenza di una quantità elevata di garbage in attesa di raccolta si forza una Garbage Collection, si noterà una riduzione nel consumo di memoria da parte del processo *devenv.exe *in **Gestione attività**. È raramente è necessario utilizzare questo metodo. Tuttavia, dopo il completamento di un'operazione dispendiosa (ad esempio una compilazione completa, una sessione di debug o un evento di apertura della soluzione), può consentire di determinare la quantità di memoria effettivamente usata dal processo. Poiché Visual Studio è misto (gestito e nativo), è talvolta possibile che allocatore nativo e Garbage Collector si contengono le risorse di memoria. In condizioni di utilizzo elevato della memoria, può essere utile per imporre l'esecuzione del Garbage Collector.

Per forzare un Garbage Collection, usare il tasto di scelta rapida: **CTRL** + **ALT** + **MAIUSC** + **F12**, **CTRL** + **ALT** + **MAIUSC** + **F12** (premere due volte).

Se l'imposizione della Garbage Collection risulta particolarmente efficiente nel proprio scenario, compilare un report tramite lo strumento per il feedback di Visual Studio poiché questo comportamento è in genere sintomo di un bug.

Per una descrizione dettagliata del Garbage Collector di CLR, vedere [Nozioni fondamentali sulla Garbage Collection](/dotnet/standard/garbage-collection/fundamentals).

## <a name="see-also"></a>Vedere anche

- [Ottimizzare le prestazioni di Visual Studio](../ide/optimize-visual-studio-performance.md)
- [Load solutions faster (Visual Studio blog)](https://devblogs.microsoft.com/visualstudio/load-solutions-faster-with-visual-studio-2017-version-15-6/) (blog di Visual Studio Caricare più rapidamente soluzioni)