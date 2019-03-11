---
title: Progetti e soluzioni, Opzioni (finestra di dialogo)
ms.date: 07/14/2017
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Projects.General
- VS.ToolsOptionsPages.Projects.Locations
helpviewer_keywords:
- Projects and Solutions Options dialog box
- Options dialog box, Projects and Solutions
ms.assetid: 2801f24e-a138-488a-ae3c-e1f99a678ac0
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 51d4d81667bed3df6f970cd59c21286b7ef9a6a2
ms.sourcegitcommit: 87d7123c09812534b7b08743de4d11d6433eaa13
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/01/2019
ms.locfileid: "57223442"
---
# <a name="projects-and-solutions-page-options-dialog-box"></a>Pagina Progetti e soluzioni, finestra di dialogo Opzioni

Consente di impostare il comportamento di Visual Studio in relazione a progetti e soluzioni. Per accedere a queste opzioni selezionare **Strumenti** > **Opzioni**, espandere **Progetti e soluzioni** e selezionare **Generale**.

I percorsi predefiniti per le cartelle di progetti e modelli vengono impostati nella scheda **Percorsi** della stessa finestra di dialogo.

## <a name="general-page"></a>Pagina Generale

Le opzioni seguenti sono disponibili nella pagina **Generale**.

### <a name="always-show-error-list-if-build-finishes-with-errors"></a>Mostra sempre Elenco errori se la compilazione termina con errori

Apre la finestra **Elenco errori** al completamento della compilazione, ma solo se la compilazione di un progetto non è riuscita. Vengono visualizzati gli errori che si sono verificati durante il processo di compilazione. Quando questa opzione è deselezionata, gli errori si verificano ugualmente, ma la finestra non verrà aperta una volta completata la compilazione. Questa opzione è attivata per impostazione predefinita.

### <a name="track-active-item-in-solution-explorer"></a>Tieni traccia degli elementi attivi in Esplora soluzioni

Se selezionata, **Esplora soluzioni** viene aperto automaticamente e l'elemento attivo viene selezionato. L'elemento selezionato cambia quando si lavora con diversi file in un progetto o soluzione oppure componenti diversi in una finestra di progettazione. Quando questa opzione è deselezionata, la selezione in **Esplora soluzioni** non viene modificata automaticamente. Questa opzione è attivata per impostazione predefinita.

### <a name="show-advanced-build-configurations"></a>Mostra configurazioni di generazione avanzate

Se selezionata, le opzioni di configurazione di compilazione vengono visualizzate nella finestra di dialogo **Pagine delle proprietà** del progetto e nella finestra di dialogo **Pagine delle proprietà** della soluzione. Se deselezionata, le opzioni di configurazione di compilazione non vengono visualizzate nelle finestre di dialogo **Pagine delle proprietà del progetto** e **Pagine delle proprietà della soluzione** per i progetti Visual Basic e C# che contengono una configurazione oppure le due configurazioni delle versioni di debug e di rilascio. Se un progetto ha una configurazione definita dall'utente, verranno visualizzate le opzioni di configurazione di compilazione.

Se è deselezionata, i comandi del menu **Compila**, ad esempio **Compila soluzione**, **Ricompila soluzione** e **Pulisci soluzione**, vengono eseguiti nella configurazione Rilascio e i comandi dal menu **Debug**, ad esempio **Avvia il debug** e **Avvia senza eseguire debug**, vengono eseguiti nella configurazione Debug.

### <a name="always-show-solution"></a>Mostra sempre soluzione

Se selezionata, la soluzione e tutti i comandi che agiscono sulle soluzioni vengono sempre visualizzati nell'IDE. Se deselezionata, tutti i progetti vengono creati come progetti autonomi e la soluzione non viene visualizzata in Esplora soluzioni o i comandi che agiscono sulle soluzioni non vengono visualizzati nell'IDE se la soluzione contiene un solo progetto.

### <a name="save-new-projects-when-created"></a>Salva nuovi progetti alla creazione

Se selezionata, è possibile specificare un percorso per il progetto nella finestra di dialogo **Nuovo progetto**. Se deselezionata, tutti i nuovi progetti vengono creati come progetti temporanei. Quando si lavora con i progetti temporanei, è possibile creare ed effettuare prove con un progetto senza dover specificare un percorso sul disco.

### <a name="warn-user-when-the-project-location-is-not-trusted"></a>Avvisa utente quando il percorso del progetto non è attendibile

Se si prova a creare un nuovo progetto o ad aprire un progetto esistente in una posizione non completamente attendibile (ad esempio, in un percorso UNC o un percorso HTTP), verrà visualizzato un messaggio. Usare questa opzione per specificare se il messaggio viene visualizzato ogni volta che si prova a creare o ad aprire un progetto in una posizione non completamente attendibile.

### <a name="show-output-window-when-build-starts"></a>Mostra finestra di output a inizio generazione

Consente di visualizzare automaticamente la [finestra Output](../../ide/reference/output-window.md) nell'IDE all'inizio delle compilazioni della soluzione.

### <a name="prompt-for-symbolic-renaming-when-renaming-files"></a>Richiedi ridenominazione simbolica quando vengono rinominati i file

Se selezionata, Visual Studio visualizza una finestra di messaggio in cui chiede se rinominare o meno anche tutti i riferimenti all'elemento di codice contenuti nel progetto.

### <a name="prompt-before-moving-files-to-a-new-location"></a>Chiedi conferma prima di spostare i file in un'altra posizione

Se selezionata, Visual Studio visualizza una finestra di messaggio di conferma prima che i percorsi dei file vengano modificati dalle azioni in **Esplora soluzioni**.

### <a name="reopen-documents-on-solution-load"></a>Riapri documenti al caricamento della soluzione

**Introdotta in Visual Studio 2017 versione 15.8**

Se selezionata, i documenti lasciati aperti alla chiusura precedente della soluzione vengono aperti automaticamente quando viene aperta la soluzione.

La riapertura di determinati tipi di file o finestre di progettazione può ritardare il caricamento della soluzione. Deselezionare questa opzione per [migliorare le prestazioni di caricamento della soluzione](../../ide/visual-studio-performance-tips-and-tricks.md#disable-automatic-file-restore) se non si vuole ripristinare il contesto precedente della soluzione.

## <a name="locations-page"></a>Pagina Percorsi

Le opzioni seguenti sono disponibili nella pagina **Percorsi**.

### <a name="projects-location"></a>Percorso progetti

Specifica il percorso predefinito in cui Visual Studio crea nuove cartelle di progetti e soluzioni. Anche diverse finestre di dialogo usano il percorso impostato in questa opzione come punto di partenza della cartella. Ad esempio, la finestra di dialogo **Apri progetto** usa questo percorso per il collegamento **Progetti**.

### <a name="user-project-templates-location"></a>Percorso dei modelli di progetto utente

Specifica il percorso predefinito usato dalla finestra di dialogo **Nuovo progetto** per creare l'elenco **Modelli personali**. Per altre informazioni, vedere [Procedura: Individuare e organizzare modelli](../../ide/how-to-locate-and-organize-project-and-item-templates.md).

### <a name="user-item-templates-location"></a>Percorso dei modelli di elemento utente

Specifica il percorso predefinito usato dalla finestra di dialogo **Aggiungi nuovo elemento** per creare l'elenco **Modelli personali**. Per altre informazioni, vedere [Procedura: Individuare e organizzare modelli](../../ide/how-to-locate-and-organize-project-and-item-templates.md).

## <a name="see-also"></a>Vedere anche

- [Finestra di dialogo Opzioni, Progetti e soluzioni, Compila ed esegui](../../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md)
- [Finestra di dialogo Opzioni, Progetti e soluzioni, Progetti Web](../../ide/reference/options-dialog-box-projects-and-solutions-web-projects.md)
