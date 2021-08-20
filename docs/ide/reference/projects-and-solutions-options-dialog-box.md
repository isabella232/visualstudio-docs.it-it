---
title: Pagina Progetti e soluzioni della finestra di dialogo Opzioni
description: Informazioni su come usare la pagina Generale nella sezione Progetti e soluzioni per definire il comportamento Visual Studio a progetti e soluzioni.
ms.custom: SEO-VS-2020
ms.date: 07/26/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Projects.General
helpviewer_keywords:
- Projects and Solutions Options dialog box
- Options dialog box, Projects and Solutions
ms.assetid: 2801f24e-a138-488a-ae3c-e1f99a678ac0
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 14a37e634dea3ae40e78f02c82937a5d03c73e3f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122151171"
---
# <a name="options-dialog-box-projects-and-solutions--general"></a>Finestra di dialogo Opzioni: Progetti e \> soluzioni Generali

Usare questa pagina per definire il comportamento di Visual Studio in relazione a progetti e soluzioni. Per accedere a queste opzioni, selezionare  >  **Opzioni strumenti,** espandere **Progetti e soluzioni** e quindi selezionare **Generale.**

Le opzioni seguenti sono disponibili nella pagina **Generale**.

## <a name="always-show-error-list-if-build-finishes-with-errors"></a>Mostra sempre Elenco errori se la compilazione termina con errori

Apre la finestra **Elenco errori** al completamento della compilazione, ma solo se la compilazione di un progetto non è riuscita. Vengono visualizzati gli errori che si sono verificati durante il processo di compilazione. Quando questa opzione è deselezionata, gli errori si verificano ugualmente, ma la finestra non verrà aperta una volta completata la compilazione. Questa opzione è attivata per impostazione predefinita.

## <a name="track-active-item-in-solution-explorer"></a>Tieni traccia degli elementi attivi in Esplora soluzioni

Se selezionata, **Esplora soluzioni** viene aperto automaticamente e l'elemento attivo viene selezionato. L'elemento selezionato cambia quando si lavora con diversi file in un progetto o soluzione oppure componenti diversi in una finestra di progettazione. Quando questa opzione è deselezionata, la selezione in **Esplora soluzioni** non viene modificata automaticamente. Questa opzione è attivata per impostazione predefinita.

## <a name="show-advanced-build-configurations"></a>Mostra configurazioni di generazione avanzate

Se selezionata, le opzioni di configurazione di compilazione vengono visualizzate nella finestra di dialogo **Pagine delle proprietà** del progetto e nella finestra di dialogo **Pagine delle proprietà** della soluzione. Se deselezionata, le opzioni di configurazione di compilazione non vengono visualizzate nelle finestre di dialogo **Pagine delle proprietà del progetto** e **Pagine delle proprietà della soluzione** per i progetti Visual Basic e C# che contengono una configurazione oppure le due configurazioni delle versioni di debug e di rilascio. Se un progetto ha una configurazione definita dall'utente, verranno visualizzate le opzioni di configurazione di compilazione.

Se è deselezionata, i comandi del menu **Compila**, ad esempio **Compila soluzione**, **Ricompila soluzione** e **Pulisci soluzione**, vengono eseguiti nella configurazione Rilascio e i comandi dal menu **Debug**, ad esempio **Avvia il debug** e **Avvia senza eseguire debug**, vengono eseguiti nella configurazione Debug.

## <a name="always-show-solution"></a>Mostra sempre soluzione

Se selezionata, la soluzione e tutti i comandi che agiscono sulle soluzioni vengono sempre visualizzati nell'IDE. Se deselezionata, tutti i progetti vengono creati come progetti autonomi e la soluzione non viene visualizzata in Esplora soluzioni o i comandi che agiscono sulle soluzioni non vengono visualizzati nell'IDE se la soluzione contiene un solo progetto.

::: moniker range="vs-2017"

## <a name="save-new-projects-when-created"></a>Salva nuovi progetti alla creazione

Se selezionata, è possibile specificare un percorso per il progetto nella finestra di dialogo **Nuovo progetto**. Se deselezionata, tutti i nuovi progetti vengono creati come progetti temporanei. Quando si lavora con i progetti temporanei, è possibile creare ed effettuare prove con un progetto senza dover specificare un percorso sul disco.

::: moniker-end

## <a name="warn-user-when-the-project-location-is-not-trusted"></a>Avvisa utente quando il percorso del progetto non è attendibile

Se si prova a creare un nuovo progetto o ad aprire un progetto esistente in una posizione non completamente attendibile (ad esempio, in un percorso UNC o un percorso HTTP), verrà visualizzato un messaggio. Usare questa opzione per specificare se il messaggio viene visualizzato ogni volta che si prova a creare o ad aprire un progetto in una posizione non completamente attendibile.

## <a name="show-output-window-when-build-starts"></a>Mostra finestra di output a inizio generazione

Consente di visualizzare automaticamente la [finestra Output](../../ide/reference/output-window.md) nell'IDE all'inizio delle compilazioni della soluzione.

## <a name="prompt-for-symbolic-renaming-when-renaming-files"></a>Richiedi ridenominazione simbolica quando vengono rinominati i file

Se selezionata, Visual Studio visualizza una finestra di messaggio in cui chiede se rinominare o meno anche tutti i riferimenti all'elemento di codice contenuti nel progetto.

## <a name="prompt-before-moving-files-to-a-new-location"></a>Chiedi conferma prima di spostare i file in un'altra posizione

Se selezionata, Visual Studio visualizza una finestra di messaggio di conferma prima che i percorsi dei file vengano modificati dalle azioni in **Esplora soluzioni**.

## <a name="reopen-documents-on-solution-load"></a>Riapri documenti al caricamento della soluzione

Se selezionata, i documenti lasciati aperti alla chiusura precedente della soluzione vengono aperti automaticamente quando viene aperta la soluzione.

La riapertura di determinati tipi di file o finestre di progettazione può ritardare il caricamento della soluzione. Deselezionare questa opzione per [migliorare le prestazioni di caricamento della soluzione](../../ide/visual-studio-performance-tips-and-tricks.md#disable-automatic-file-restore) se non si vuole ripristinare il contesto precedente della soluzione.

::: moniker range=">=vs-2019"

## <a name="restore-solution-explorer-project-hierarchy-state-on-solution-load"></a>Ripristinare lo stato della gerarchia del progetto in Esplora soluzioni durante il caricamento della soluzione

Quando questa opzione è selezionata, viene ripristinato lo stato di espansione o compressione dei nodi in Esplora soluzioni esistente al momento dell'ultima apertura della soluzione. Deselezionare questa opzione per ridurre il tempo di caricamento della soluzione per le soluzioni di grandi dimensioni.

> [!TIP]
> Se si disabilita questa opzione, un modo semplice per passare al documento attivo in Esplora soluzioni consiste nel selezionare **Sincronizza con documento attivo** sulla barra degli strumenti di **Esplora soluzioni**.
>
> ![Sincronizza con documento attivo in Esplora soluzioni](media/sync-active-document.png)

## <a name="open-sdk-style-project-files-with-double-click-or-the-enter-key"></a>Aprire i file di progetto in stile SDK con doppio clic o il tasto INVIO

Quando questa opzione è selezionata e si fa doppio clic su un nodo di progetto in stile SDK in Esplora soluzioni o lo si seleziona e quindi si preme **INVIO**, il file di progetto (ad esempio, un file \*.csproj) si apre come XML nell'editor. Quando questa opzione è deselezionata, quando si fa doppio clic su un nodo di progetto in stile SDK in Esplora soluzioni oppure lo si seleziona e si preme **INVIO** viene solo espanso o compresso il nodo.

Se questa opzione non è selezionata e si vuole modificare un file di progetto in stile SDK, fare clic con il pulsante destro del mouse sul nodo del progetto in Esplora soluzioni e scegliere **Modifica file di progetto**. Per gli altri tipi di progetto, è necessario prima di tutto scaricare il progetto prima di modificarlo in Visual Studio.

> [!TIP]
> Un *progetto in stile SDK*, o [SDK progetto](../../msbuild/how-to-use-project-sdk.md), presenta un formato di file di progetto più nuovo e semplice, introdotto con MSBuild 15.0. Un progetto in stile SDK contiene un attributo `Sdk` per l'elemento `Project`, ad esempio `<Project Sdk="Microsoft.NET.Sdk">`. Visual Studio crea un progetto in stile SDK quando si crea un nuovo progetto .NET Core da uno dei modelli di Visual Studio, ad esempio.

::: moniker-end

## <a name="see-also"></a>Vedi anche

- [Finestra di dialogo Opzioni: Percorsi di progetti e \> soluzioni](projects-solutions-locations-options.md)
- [Finestra di dialogo Opzioni, Progetti e soluzioni, Compila ed esegui](../../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md)
- [Opzioni (finestra di dialogo), Progetti e soluzioni, Progetti Web](../../ide/reference/options-dialog-box-projects-and-solutions-web-projects.md)
