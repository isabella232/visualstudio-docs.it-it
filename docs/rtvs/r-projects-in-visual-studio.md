---
title: Progetti R
description: Come creare una gestione di progetti di R in Visual Studio inclusi proprietà, comandi di progetto e modelli.
ms.date: 06/29/2017
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jmartens
ms.technology: vs-rtvs
ms.workload:
- data-science
ms.openlocfilehash: 4fd62b1641a9da10484d31e5f2eb212a09cbce12
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122060648"
---
# <a name="create-r-projects-in-visual-studio"></a>Creare progetti R in Visual Studio

Un progetto R (un file con estensione *rxproj*) identifica tutti i file di origine e di contenuto associati al progetto,  contiene le informazioni di compilazione relative a ogni file, gestisce le informazioni per l'integrazione con sistemi di controllo del codice sorgente e consente di organizzare l'applicazione in componenti logici. Le informazioni relative all'area di lavoro, ad esempio l'elenco dei pacchetti installati, vengono gestite, tuttavia, separatamente nell'area di lavoro stessa.

I progetti vengono sempre gestiti all'interno di una *soluzione* di Visual Studio, che può contenere un numero qualsiasi di progetti che possono fare riferimento l'uno all'altro. Vedere [Usare più tipi di progetto in Visual Studio](#use-multiple-project-types-in-visual-studio).

## <a name="creating-a-new-r-project"></a>Creazione di un nuovo progetto R

1. Aprire Visual Studio.
1. Scegliere **File > Nuovo > Progetto** (**CTRL**+**MAIUSC**+**N**)
1. Selezionare "R Project" in **Modelli** R, assegnare un nome e un percorso al progetto  >  e selezionare **OK:**

    ![Finestra di dialogo Nuovo progetto per R in Visual Studio (RTVS in VS2017)](media/getting-started-01-new-project.png)

Questo comando crea un progetto con un file *script.R* vuoto aperto nell'editor. Si noti anche che in **Esplora soluzioni** sono presenti altri due file per il progetto:

![Contenuto di un progetto R creato dal modello](media/projects-template-results.png)

Il file con estensione *Rhistory* registra tutti i comandi immessi dall'utente nella finestra [R interattivo](interactive-repl-for-r-in-visual-studio.md). È possibile aprire una finestra della cronologia dedicata con il **comando R Tools**  >  **Windows**  >  **Cronologia.** Tale finestra ha un pulsante della barra degli strumenti e voci di menu contestuale per cancellare il contenuto della cronologia.

Il file *rproject.rproj* consente di gestire alcune impostazioni di progetto specifiche di R non altrimenti gestite da Visual Studio:

| Proprietà | Predefinito | Descrizione |
| --- | --- | --- |
| Versione | 1.0 | La versione di R Tools per Visual Studio usata per creare il progetto. |
| RestoreWorkspace | Predefinito | Carica automaticamente le variabili precedenti dell'area di lavoro dal file `.RData` nella directory del progetto. |
| SaveWorkspace | Predefinito | Salva le variabili correnti dell'area di lavoro per il file `.RData` nella directory del progetto quando quest'ultimo viene chiuso. |
| AlwaysSaveHistory | Predefinito | Salva la cronologia corrente della finestra interattiva per il file `.RHistory` nella directory del progetto quando quest'ultimo viene chiuso. |
| EnableCodeIndexing | Sì | Determina se eseguire un'attività di indicizzazione in background per velocizzare le ricerche di codice. |
| UseSpacesForTab | Sì | Determina se inserire spazi (Sì) o un carattere di tabulazione (No) quando viene premuto **TAB** nell'editor. |
| NumSpacesForTab | 2 | Il numero di spazi da inserire se UseSpacesForTab è impostato su Sì. |
| Codifica | UTF-8 | La codifica predefinita per i file `.R`. |
| RnwWeave | Sweave | Pacchetto da usare per la composizione di un file Rnw. |
| LaTeX | pdfLaTeX | Libreria da usare durante la conversione di RMarkdown in PDF. |

### <a name="converting-a-folder-of-files-to-an-r-project"></a>Conversione di una cartella di file in un progetto R

Se si vuole gestire all'interno di un progetto una cartella di file *.R* esistente, seguire questa procedura:

1. Creare un nuovo progetto in Visual Studio come descritto nella sezione precedente.
1. Copiare i file nella cartella del progetto.
1. Nella finestra Visual Studio Esplora soluzioni fare clic con il pulsante destro del mouse sul progetto, scegliere Aggiungi elemento esistente e selezionare i  >  file da aggiungere. Quando si seleziona **OK**, questi compaiono nell'albero del progetto.
1. Per organizzare il codice in sottocartelle, fare clic con il pulsante destro del mouse sul progetto, selezionare prima Aggiungi nuova cartella, quindi copiare i file in tale cartella e aggiungere gli  >   elementi esistenti nel passaggio 3.

## <a name="project-properties"></a>Proprietà progetto

Per aprire le pagine delle proprietà del progetto, fare clic con il pulsante destro del mouse su **Esplora soluzioni** e selezionare **Proprietà** oppure scegliere la voce di menu **Progetto > (nome progetto)**. La finestra visualizzata riporta le proprietà del progetto:

| Scheda | Proprietà | Descrizione |
| --- | --- | --- |
| Esegui | File di avvio | Nome del file che viene eseguito con il comando **Source startup file** (File di avvio di origine), **F5**, **Debug** > **Avvia debug** oppure **Debug** > **Avvia senza eseguire debug**. Facendo clic con il pulsante destro del mouse sul file nel progetto e selezionando **Imposta come script R di avvio**, il file viene impostato anche come file di avvio. |
| | Ripristina R interattivo durante l'esecuzione | Cancella tutte le variabili dall'area di lavoro della finestra interattiva quando si esegue il progetto. Questa operazione garantisce che non ci sia contenuto residuo dell'area di lavoro dall'esecuzione precedente. |
| | Percorso progetto remoto | Percorso di un'area di lavoro remota. |
| | Trasferisci file durante l'esecuzione | Indica se i file di progetto, soggetti al filtro in **File da trasferire**, devono essere copiati in un'area di lavoro remota a ogni esecuzione. |
| | File da trasferire | Nomi di file e caratteri jolly che indicano i file specifici da copiare un'area di lavoro remota se l'opzione **Trasferisci file durante l'esecuzione** è selezionata. |
| Impostazioni | (File Settings.R) | Le impostazioni dei progetti R vengono ereditate dai file *Settings.R* o **.Settings.R* che si trovano all'interno del progetto. Se non esistono file di impostazioni, è possibile aggiungere variabili, salvare la pagina. Un file *Settings.R* predefinito verrà automaticamente creato. È anche possibile aggiungere il file di impostazioni al progetto tramite il **comando di** menu File  >  **Aggiungi nuovo** elemento. <br/> Le impostazioni vengono memorizzate come codice R e il file può essere originato prima di eseguire altri moduli, pre-popolando in questo modo l'ambiente con le impostazioni predefinite. |

## <a name="r-specific-project-commands"></a>Comandi di progetto specifici di R

I progetti di Visual Studio supportano diversi comandi generali sia tramite il menu di scelta rapida che tramite il menu **Progetto**. Per i dettagli su queste funzionalità generali, vedere [Soluzioni e progetti in Visual Studio](../ide/solutions-and-projects-in-visual-studio.md). Si ricorda però che per i progetti R, R Tools per Visual Studio (RTVS) aggiunge diversi comandi specifici al menu di scelta rapida nonché file e cartelle all'interno del progetto.

| Comando | Descrizione |
| --- | --- |
| Imposta directory di lavoro qui | Imposta la directory di lavoro della finestra interattiva R sulla cartella del progetto, che può essere usata anche in qualsiasi sottocartella all'interno di un progetto. |
| Apri cartella superiore | Apre Esplora risorse in corrispondenza del percorso del file selezionato. |
| Aggiungi script R | Crea e apre un nuovo file *.R* con nome predefinito. È anche possibile usare il **comando Aggiungi**  >  **nuovo elemento** per creare *. File R* e diversi altri tipi di file. Vedere [Modelli di elemento specifici di R](#r-specific-item-templates). |
| Aggiungi R Markdown | Crea e apre un nuovo documento *.rmd* con nome predefinito. È anche possibile usare il **comando Aggiungi** nuovo elemento per creare file con estensione  >   *rmd* e diversi altri tipi di file. Vedere [Modelli di elemento specifici di R](#r-specific-item-templates).  |
| Pubblica stored procedure | Avvia il processo di pubblicazione di eventuali stored procedure presenti all'interno di script R. Vedere [Usare stored procedure di SQL Server](integrating-sql-server-with-r.md#work-with-sql-server-stored-procedures). |

## <a name="r-specific-item-templates"></a>Modelli di elemento specifici di R

RTVS include diversi modelli per tipi di file specifici. Per accedere ai modelli, fare clic con il pulsante destro del mouse su un progetto R e scegliere Aggiungi nuovo elemento selezionando Project Aggiungi nuovo elemento oppure usando File nuovo file e selezionando la  >     >     >    >   **scheda R.** Il modo migliore per esplorare un modello è creare un nuovo progetto e inserire file di ogni tipo.

> [!Note]
> I **comandi** Aggiungi nuovo elemento visualizzano anche i tipi di file generali non elencati nella tabella. Con File nuovo file tali tipi sono invece  >   contenuti nella   >    >   **scheda** Generale.

| Tipo di file | Descrizione |
| --- | --- |
| Script R | Un file di testo che contiene gli stessi comandi che è possibile immettere nella riga di comando R. |
| R Markdown | File contenente un documento [R Markdown](rmarkdown-with-r-in-visual-studio.md). |
| Impostazioni R | File che contiene le impostazioni applicazione R. |
| Documentazione di R | File di documentazione di R generico che contiene solo i campi nome, alias e titolo. |
| Documentazione di R (funzione) | File di documentazione di R contenente molti campi con commenti di descrizione di una funzione. |
| Documentazione di R (set di dati) | File di documentazione di R contenente molti campi con commenti di descrizione di un set di dati. |
| Query SQL | Un file *con estensione sql* vuoto. Vedere [Usare SQL Server ed R](integrating-sql-server-with-r.md). |
| Stored procedure con R | File R con una query SQL figlio e un file modello di stored procedure figlio. Vedere [Usare SQL Server ed R](integrating-sql-server-with-r.md). |

## <a name="use-multiple-project-types-in-visual-studio"></a>Usare più tipi di progetto in Visual Studio

Le soluzioni di Visual Studio rappresentano un modo pratico per raccogliere e gestire progetti correlati in un'unica posizione logica, consentendo un'organizzazione efficiente del codice e semplificando la collaborazione all'interno del team.

Nell'esempio seguente la soluzione contiene un progetto R con un modello compilato tramite R e Azure Machine Learning, un progetto Python/scikit-learn, un progetto C++ contenente moduli per un processo di calcolo intensivo, un progetto SQL per la gestione dei dati e un progetto Python/Bottle per il sito Web in cui viene pubblicato il risultato:

![Esplora soluzioni di Visual Studio con più progetti correlati in una soluzione](media/projects-polyglot.png)

Il progetto evidenziato in grassetto è il progetto di "avvio" per la soluzione. Per cambiarlo, fare clic con il pulsante destro del mouse su un altro progetto e selezionare **Imposta come progetto di avvio**.

> [!Note]
> Al momento, a differenza di quanto avviene con Python (vedere [Creare un'estensione C++ per Python](../python/working-with-c-cpp-python-in-visual-studio.md)) non esiste alcuna integrazione esplicita tra R e i linguaggi C#/C++.  Sono tuttavia disponibili librerie che consentono di creare punti di comunicazione tra R e i linguaggi C# e C++.

Per altre informazioni sulla gestione di progetti e soluzioni in generale, vedere [Soluzioni e progetti in Visual Studio](../ide/solutions-and-projects-in-visual-studio.md).
