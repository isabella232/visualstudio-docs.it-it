---
title: Gestire gli ambienti e gli interpreti Python
description: Usare la finestra Ambienti Python per gestire ambienti globali, virtuali e Conda, installare pacchetti e interpreti Python e assegnare gli ambienti ai progetti di Visual Studio.
ms.date: 08/06/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.technology: vs-python
ms.workload:
- python
- data-science
ms.openlocfilehash: 90bd3bd30f4a30277fd36fa639760922377f5c99
ms.sourcegitcommit: 541871db9065c4fb1b21c24f980c563991b183c7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2021
ms.locfileid: "129430612"
---
# <a name="how-to-create-and-manage-python-environments-in-visual-studio"></a>Come creare e gestire gli ambienti Python in Visual Studio

Un **ambiente Python** è un contesto in cui si esegue codice Python e include ambienti globali, virtuali e conda. Un ambiente è costituito da un interprete, una libreria (in genere quella standard Python) e un set di pacchetti installati. Questi componenti nel loro insieme determinano la sintassi e i costrutti di linguaggio validi, le funzionalità accessibili del sistema operativo e i pacchetti che è possibile usare.

In Visual Studio in Windows la finestra **Ambienti Python**, descritta in questo articolo, consente di gestire gli ambienti e di selezionarne uno come predefinito per i nuovi progetti. Altri aspetti degli ambienti sono disponibili negli articoli seguenti:

- Per ogni progetto è possibile [selezionare un ambiente specifico](selecting-a-python-environment-for-a-project.md) anziché usare quello predefinito.

- Per informazioni dettagliate sulla creazione e l'uso di ambienti virtuali per i progetti Python, vedere [Usare gli ambienti virtuali](selecting-a-python-environment-for-a-project.md#use-virtual-environments).

- Per installare i pacchetti in un ambiente, vedere le [informazioni di riferimento sulla scheda Pacchetti](python-environments-window-tab-reference.md#packages-tab).

- Per installare un altro interprete Python, vedere [Installare interpreti Python](installing-python-interpreters.md). In generale, se si scarica e si esegue un programma di installazione per una distribuzione principale di Python Visual Studio rileva la nuova installazione e l'ambiente viene visualizzato nella finestra **Ambienti Python** e può essere selezionato per i progetti.

Se non si ha familiarità con Python in Visual Studio, vedere gli articoli seguenti per le informazioni di base necessarie:

- [usare Python in Visual Studio](overview-of-python-tools-for-visual-studio.md)
- [Installare il supporto per Python in Visual Studio](installing-python-support-in-visual-studio.md)

::: moniker range="vs-2017"
> [!Note]
> Non è possibile gestire gli ambienti per il codice Python aperto solo come cartella usando il **comando Apri**  >    >  **cartella.** In alternativa, [creare un progetto Python da codice esistente](quickstart-01-python-in-visual-studio-project-from-existing-code.md) per sfruttare le funzionalità dell'ambiente di Visual Studio.
::: moniker-end

::: moniker range=">=vs-2019"
> [!Note]
> È possibile gestire gli ambienti per il codice Python aperto come cartella usando il **comando Apri**  >    >  **cartella** file. La barra degli strumenti di Python consente di spostarsi tra tutti gli ambienti rilevati e anche di aggiungere un nuovo ambiente. Le informazioni sull'ambiente sono archiviate nel file PythonSettings.json nella cartella Workspace.vs.
::: moniker-end

## <a name="the-python-environments-window"></a>Finestra Ambienti Python

Gli ambienti rilevati da Visual Studio vengono visualizzati nella finestra **Ambienti Python**. Per aprire la finestra, usare uno dei metodi seguenti:

- Selezionare il **comando di** menu  >  **Visualizza Windows** ambienti  >  **Python.**
- Fare clic con il pulsante destro del mouse sul nodo **Ambienti Python** per un progetto in **Esplora soluzioni** e scegliere **Visualizza tutti gli ambienti Python**:

    ::: moniker range="vs-2017"
    ![Comando Visualizza tutti gli ambienti Python in Esplora soluzioni](media/environments/environments-view-all.png)
    ::: moniker-end
    ::: moniker range=">=vs-2019"
    ![Comando Visualizza tutti gli ambienti Python in Esplora soluzioni](media/environments/environments-view-all-2019.png)
    ::: moniker-end

In entrambi i casi, la finestra **Ambienti Python** viene visualizzata accanto a **Esplora soluzioni**:

::: moniker range="vs-2017"
![Finestra Ambienti Python](media/environments/environments-default-view.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Finestra Ambienti Python](media/environments/environments-default-view-2019.png)
::: moniker-end

Visual Studio cerca gli ambienti globali installati usando il Registro di sistema (in base a [PEP 514](https://www.python.org/dev/peps/pep-0514/)), oltre agli ambienti virtuali e agli ambienti Conda (vedere [Tipi di ambienti](#types-of-environments)). Se l'elenco non include un ambiente previsto, vedere [Identificare manualmente un ambiente esistente](#manually-identify-an-existing-environment).

Quando si seleziona un ambiente nell'elenco, Visual Studio visualizza varie proprietà e comandi per tale ambiente nella **scheda** Panoramica. Ad esempio, è possibile vedere nell'immagine precedente che la posizione dell'interprete è *C:\Python36-32*. Ognuno dei quattro comandi nella parte inferiore della scheda **Panoramica** apre un prompt dei comandi con l'interprete in esecuzione. Per altre informazioni, vedere [Informazioni di riferimento sulle schede della finestra Ambienti Python - Panoramica](python-environments-window-tab-reference.md#overview-tab).

Usare l'elenco a discesa disponibile sotto l'elenco degli ambienti per spostarsi tra le diverse schede, ad esempio **Pacchetti** e **IntelliSense**. Queste schede sono descritte anche in [Informazioni di riferimento sulle schede della finestra Ambienti Python](python-environments-window-tab-reference.md).

La selezione di un ambiente non cambia la relazione dell'ambiente con eventuali progetti. L'ambiente predefinito, visualizzato in grassetto nell'elenco, è quello che Visual Studio usa per i nuovi progetti. Per usare un altro ambiente con i nuovi progetti, usare il comando **Imposta come ambiente predefinito per i nuovi progetti**. Nel contesto di un progetto è sempre possibile selezionare un ambiente specifico. Per altre informazioni, vedere [Selezionare un ambiente per un progetto](selecting-a-python-environment-for-a-project.md).

A destra di ogni ambiente elencato è presente un controllo che apre una **finestra interattiva** per tale ambiente. (In Visual Studio 2017 15.5 e versioni precedenti potrebbe essere visualizzato un altro controllo che aggiorna il database di IntelliSense per tale ambiente. Vedere [Informazioni di riferimento sulle schede della finestra Ambienti](python-environments-window-tab-reference.md) per informazioni dettagliate sul database.)

::: moniker range="vs-2017"
> [!Tip]
> Se si espande a sufficienza la finestra **Ambienti Python**, si otterrà una visualizzazione più completa degli ambienti che può risultare più comoda.
>
> ![Visualizzazione espansa della finestra Ambienti Python](media/environments/environments-expanded-view.png)
::: moniker-end

::: moniker range=">=vs-2019"
> [!Tip]
> Se si espande a sufficienza la finestra **Ambienti Python**, si otterrà una visualizzazione più completa degli ambienti che può risultare più comoda.
>
> ![Visualizzazione espansa della finestra Ambienti Python](media/environments/environments-expanded-view-2019.png)
::: moniker-end

> [!Note]
> Anche se Visual Studio rispetta l'opzione dei pacchetti dei siti di sistema, non consente di modificarla da Visual Studio.

### <a name="what-if-no-environments-appear"></a>Se non viene visualizzato alcun ambiente

Se non viene visualizzato alcun ambiente, significa che Visual Studio non è riuscito a rilevare installazioni di Python nelle posizioni standard. È possibile, ad esempio, avere installato Visual Studio 2017 o versioni successive con tutte le opzioni per l'interprete deselezionate nelle opzioni del programma di installazione per il carico di lavoro di Python. Analogamente, è possibile che sia installato Visual Studio 2015 o versione precedente, ma che non sia stato installato manualmente un interprete. Vedere [Installare interpreti Python](installing-python-interpreters.md).

Se si è certi di disporre di un interprete Python nel computer in uso, ma Visual Studio (qualsiasi versione) non lo rileva, usare il comando **+ Personalizzato** per specificarne il percorso manualmente. Vedere la sezione successiva, [Identificare manualmente un ambiente esistente](#manually-identify-an-existing-environment).

::: moniker range="<=vs-2017"

> [!Tip]
> Visual Studio rileva gli aggiornamenti a un interprete esistente, ad esempio l'aggiornamento di Python 2.7.11 a 2.7.14 usando i programmi di installazione da python.org. Durante il processo di installazione, l'ambiente precedente scompare dall'elenco **Ambienti Python** prima che l'aggiornamento venga visualizzato al suo posto.
>
> Tuttavia, se si sposta manualmente un interprete e il relativo ambiente tramite il file system, Visual Studio non conosce il nuovo percorso. Per altre informazioni, vedere [Spostare un interprete](installing-python-interpreters.md#move-an-interpreter).
::: moniker-end

### <a name="types-of-environments"></a>Tipi di ambienti

Visual Studio funziona con ambienti con globali, virtuali e ambienti Conda.

#### <a name="global-environments"></a>Ambienti globali

Ogni installazione di Python (ad esempio Python 2.7, Python 3.6, Python 3.7, Anaconda 4.4.0 e così via, vedere [Installare interpreti Python](installing-python-interpreters.md)) mantiene il proprio *ambiente globale*. Ogni ambiente è costituito dall'interprete Python specifico e dalla relativa libreria standard, da un set di pacchetti preinstallati e dai pacchetti aggiuntivi che si decide di installare durante l'attivazione dell'ambiente. L'installazione di un pacchetto in un ambiente globale lo rende disponibile per tutti i progetti che usano tale ambiente. Se l'ambiente si trova in un'area protetta del file system, ad esempio in *C:\Programmi*, l'installazione dei pacchetti richiede i privilegi di amministratore.

Gli ambienti globali sono disponibili per tutti i progetti nel computer. In Visual Studio si seleziona un ambiente globale come predefinito e tale ambiente viene usato per tutti i progetti a meno che non se ne scelga in modo specifico un altro per un progetto. Per altre informazioni, vedere [Selezionare un ambiente per un progetto](selecting-a-python-environment-for-a-project.md).

#### <a name="virtual-environments"></a>Ambienti virtuali

Anche se lavorare in un ambiente globale è un modo semplice per iniziare, nel corso del tempo l'ambiente verrà occupato da molti pacchetti installati per progetti diversi. Questo tipo di disordine complica il test completo di un'applicazione rispetto a un set specifico di pacchetti con versioni note, che è esattamente il tipo di ambiente da configurare in un server Web o di compilazione. Possono anche verificarsi conflitti quando due progetti richiedono pacchetti non compatibili o versioni diverse dello stesso pacchetto.

Per questo motivo, spesso gli sviluppatori creano un *ambiente virtuale* per un progetto. Un ambiente virtuale è una sottocartella di un progetto che contiene una copia di un interprete specifico. Quando si attiva l'ambiente virtuale, tutti i pacchetti che si installano vengono installati solo in quella sottocartella dell'ambiente. Quando si esegue un programma Python all'interno dell'ambiente, si sa che viene eseguito solo con quei pacchetti specifici.

Visual Studio offre supporto diretto per la creazione di un ambiente virtuale per un progetto. Se ad esempio si apre un progetto che contiene un file *requirements.txt* o si crea un progetto da un modello che include quel file, Visual Studio chiede di creare automaticamente un ambiente virtuale e di installare le dipendenze necessarie.

È possibile creare un nuovo ambiente virtuale in qualsiasi momento all'interno di un progetto aperto. In **Esplora soluzioni** espandere il nodo del progetto, fare clic con il pulsante destro del mouse sul nodo **Ambienti Python** e scegliere "Aggiungi ambiente virtuale". Per altre informazioni, vedere [Creare un ambiente virtuale](./selecting-a-python-environment-for-a-project.md?view=vs-2019&preserve-view=true#create-a-virtual-environment-1).

Visual Studio include anche un comando che consente di generare un file *requirements.txt* dall'ambiente virtuale, facilitando la riproduzione dell'ambiente in altri computer. Per altre informazioni, vedere [Usare ambienti virtuali](selecting-a-python-environment-for-a-project.md#use-virtual-environments).

#### <a name="conda-environments"></a>Ambienti Conda

Un ambiente Conda è un ambiente creato usando lo strumento `conda` o con la gestione Conda integrata in Visual Studio 2017 15.7 e versioni successive. Richiede Anaconda o Miniconda, disponibili tramite il programma di installazione di Visual Studio. Vedere [Installazione](installing-python-support-in-visual-studio.md#visual-studio-2019-and-visual-studio-2017).

::: moniker range="vs-2017"

1. Selezionare **+ Crea ambiente Conda** nella finestra **Ambienti Python**. Verrà aperta una scheda **Crea nuovo ambiente Conda**:

    ![Scheda per la creazione di un nuovo ambiente Conda](media/environments/environments-conda-1.png)

1. Immettere un nome per l'ambiente nel campo **Nome**, selezionare un interprete Python di base nel campo **Python** e selezionare **Crea**.

1. Nella finestra **Output** viene visualizzato lo stato di avanzamento per il nuovo ambiente, con alcune istruzioni dell'interfaccia della linea di comando al termine della creazione:

    ![Creazione completata correttamente di un ambiente Conda](media/environments/environments-conda-2.png)

1. All'interno di Visual Studio è possibile attivare un ambiente Conda per un progetto come per qualsiasi altro ambiente come descritto in [Selezionare un ambiente per un progetto](selecting-a-python-environment-for-a-project.md).

1. Per installare i pacchetti nell'ambiente, usare la [scheda Pacchetti](python-environments-window-tab-reference.md#packages-tab).
::: moniker-end

::: moniker range=">=vs-2019"

1. Selezionare **Aggiungi ambiente...** nella finestra **Ambienti Python** (o dalla barra degli strumenti Python), che apre la finestra di **dialogo** Aggiungi ambiente. Nella finestra di dialogo selezionare la scheda **Ambiente Conda**:

    ![Scheda Ambiente Conda nella finestra di dialogo Aggiungi ambiente](media/environments/environments-conda-1-2019.png)

1. Configurare i campi seguenti:

    | Campo | Descrizione |
    | --- | --- |
    | Project | Progetto in cui creare l'ambiente (in presenza di più progetti nella stessa soluzione di Visual Studio). |
    | Nome | Nome per l'ambiente Conda. |
    | Aggiungi pacchetti da | Scegliere **File di ambiente** se è disponibile un file *environment.yml* che descrive le dipendenze oppure scegliere **Uno o più nomi di pacchetto Anaconda** ed elencare almeno un pacchetto Python o una versione di Python nel campo sottostante. L'elenco dei pacchetti indica a Conda di creare un ambiente Python. Per installare la versione più recente di Python, usare `python`. Per installare una versione specifica, usare `python=,major>.<minor>` come in `python=3.7`. È anche possibile usare il pulsante Pacchetto per selezionare le versioni e i pacchetti comuni di Python da una serie di menu. |
    | Imposta come ambiente corrente | Dopo aver creato l'ambiente, attiva il nuovo ambiente nel progetto selezionato. |
    | Imposta come ambiente predefinito per i nuovi progetti | Imposta e attiva automaticamente l'ambiente Conda in tutti i nuovi progetti creati in Visual Studio. Questa opzione equivale a selezionare **Imposta come ambiente predefinito per i nuovi progetti** nella finestra **Ambienti Python**. |
    | Visualizza nella finestra Ambienti Python | Specifica se visualizzare la finestra **Ambienti Python** dopo la creazione dell'ambiente. |

    > [!Important]
    > Quando si crea un ambiente Conda, assicurarsi di specificare almeno una versione di Python o un pacchetto di Python usando `environments.yml` o l'elenco dei pacchetti, che assicura che l'ambiente contenga un runtime di Python. In caso contrario, Visual Studio ignora l'ambiente, ovvero l'ambiente non viene visualizzato nella finestra **Ambienti Python**, non viene impostato come ambiente corrente per un progetto e non è disponibile come ambiente globale.
    >
    > Se si crea un ambiente Conda senza una versione di Python, usare il comando `conda info` per visualizzare i percorsi delle cartelle dell'ambiente Conda e quindi rimuovere manualmente la sottocartella per l'ambiente da quel percorso.

1. Selezionare **Crea** e osservare lo stato di avanzamento nella finestra **Output**. Una volta completata la creazione, l'output include alcune istruzioni della riga di comando:

    ![Creazione completata correttamente di un ambiente Conda](media/environments/environments-conda-2-2019.png)

1. All'interno di Visual Studio è possibile attivare un ambiente Conda per un progetto come per qualsiasi altro ambiente come descritto in [Selezionare un ambiente per un progetto](selecting-a-python-environment-for-a-project.md).

1. Per installare pacchetti aggiuntivi nell'ambiente, usare la [scheda Pacchetti](python-environments-window-tab-reference.md#packages-tab).
::: moniker-end

> [!Note]
> Per ottenere risultati ottimali con gli ambienti Conda, usare Conda 4.4.8 o versione successiva (le versioni Conda sono diverse rispetto alle versioni Anaconda). È possibile installare le versioni adatte di Miniconda (Visual Studio 2019) e Anaconda (Visual Studio 2017) tramite il programma di installazione di Visual Studio.

Per visualizzare la versione Conda, in cui sono archiviati gli ambienti Conda, e altre informazioni, eseguire `conda info` a un prompt dei comandi Anaconda (ovvero, un prompt dei comandi nel percorso in cui è presente Anaconda):

```cli
conda info
```

Le cartelle di ambiente Conda vengono visualizzate come segue:

```output
       envs directories : C:\Users\user\.conda\envs
                          c:\anaconda3\envs
                          C:\Users\user\AppData\Local\conda\conda\envs
```

Poiché gli ambienti Conda non sono archiviati con un progetto, agiscono in modo analogo agli ambienti globali. Ad esempio, l'installazione di un nuovo pacchetto in un ambiente Conda lo rende disponibile per tutti i progetti che usano tale ambiente.

Per Visual Studio 2017 15.6 e versioni precedenti, è possibile usare ambienti Conda puntando a essi manualmente come descritto in [Identificare manualmente un ambiente esistente](#manually-identify-an-existing-environment).

Visual Studio 2017 15.7 e versioni successive rileva automaticamente gli ambienti Conda e li visualizza nella finestra **Ambienti Python** come descritto nella sezione successiva.

## <a name="manually-identify-an-existing-environment"></a>Identificare manualmente un ambiente esistente

Usare questa procedura per identificare un ambiente installato in un percorso non standard, inclusi gli ambienti Conda in Visual Studio 2017 versione 15.6 e precedenti:

::: moniker range="vs-2017"

1. Selezionare **+ Personalizzato** nella finestra **Ambienti Python**. Verrà aperta la scheda **Configura**:

    ![Visualizzazione predefinita per un nuovo ambiente personalizzato](media/environments/environments-custom-1.png)

1. Immettere un nome per l'ambiente nel campo **Descrizione**.

1. Immettere o selezionare (tramite **...**) il percorso dell'interprete nel campo **Percorso di prefisso**.

1. Se Visual Studio rileva un interprete Python nel percorso specificato, ad esempio il percorso illustrato di seguito per un ambiente Conda, viene abilitato il comando **Rilevamento automatico**. Selezionando **Rilevamento automatico** vengono compilati i restanti campi. È anche possibile compilare manualmente questi campi.

    ![Abilitazione del comando Rilevamento automatico](media/environments/environments-custom-2.png)

    ![Completamento dei campi di ambiente dopo l'uso di Rilevamento automatico](media/environments/environments-custom-3.png)

1. Quando i campi contengono i valori desiderati, selezionare **Applica** per salvare la configurazione. È ora possibile usare l'ambiente come qualsiasi altro all'interno di Visual Studio.

1. Se è necessario rimuovere un ambiente identificato manualmente, selezionare il **comando** Rimuovi nella **scheda** Configura. Gli ambienti rilevati automaticamente non forniscono questa opzione. Per altre informazioni, vedere [Scheda Configura](python-environments-window-tab-reference.md#configure-tab).

::: moniker-end

::: moniker range=">=vs-2019"

1. Selezionare **Aggiungi ambiente...** nella finestra **Ambienti Python** (o dalla barra degli strumenti Python) per aprire la finestra di **dialogo** Aggiungi ambiente. Nella finestra di dialogo selezionare la scheda **Ambiente esistente**:

    ![Scheda Ambiente esistente nella finestra di dialogo Aggiungi ambiente](media/environments/environments-custom-1-2019.png)

1. Selezionare l'elenco a discesa **Ambiente** e quindi selezionare **Personalizzato**:

    ![Opzione di ambiente personalizzato nella finestra di dialogo Aggiungi ambiente](media/environments/environments-custom-2-2019.png)

1. Negli appositi campi nella finestra di dialogo, immettere o selezionare (tramite **...**) il percorso dell'interprete in **Percorso di prefisso**. Viene così compilata la maggior parte degli altri campi. Dopo aver esaminato questi valori e aver apportato le eventuali modifiche necessarie, selezionare **Aggiungi**.

    ![Campi per specificare i dettagli per un'opzione di ambiente personalizzato nella finestra di dialogo Aggiungi ambiente](media/environments/environments-custom-3-2019.png)

1. I dettagli dell'ambiente possono essere controllati e modificati in qualsiasi momento nella finestra **Ambienti Python**. In tale finestra selezionare l'ambiente e quindi selezionare la **scheda** Configura. Dopo aver apportato le modifiche, selezionare **il comando** Applica. È anche possibile rimuovere l'ambiente tramite il comando **Rimuovi** (non disponibile per gli ambienti rilevati automaticamente). Per altre informazioni, vedere [Scheda Configura](python-environments-window-tab-reference.md#configure-tab).
::: moniker-end

## <a name="fix-or-delete-invalid-environments"></a>Correggere o eliminare gli ambienti non validi

Se Visual Studio le voci del Registro di sistema per un ambiente, ma il percorso dell'interprete non è valido, la finestra **Ambienti Python** mostra il nome con un carattere barrato:

::: moniker range="vs-2017"
![Finestra Ambienti Python con ambiente non valido visualizzato](media/environments/environments-invalid-entry.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Finestra Ambienti Python con ambiente non valido visualizzato](media/environments/environments-invalid-entry-2019.png)
::: moniker-end

Per correggere un ambiente che si vuole mantenere, provare prima a usare il processo di **riparazione** del programma di installazione. Ad esempio, i programmi di installazione per la versione Python 3.x standard includono tale opzione.

Per correggere un ambiente che non dispone di un'opzione di riparazione o per rimuovere un ambiente non valido, usare la procedura seguente per modificare direttamente il Registro di sistema. Visual Studio aggiorna automaticamente la **finestra Ambienti Python** quando si apportano modifiche al Registro di sistema.

1. Eseguire *regedit.exe*.
1. Passare a **HKEY_LOCAL_MACHINE\SOFTWARE\Python** o **HKEY_CURRENT_USER\SOFTWARE\Python**. Per IronPython, cercare invece **IronPython**.
1. Espandere il nodo che corrisponde alla distribuzione, ad esempio **Python Core** per CPython o **ContinuumAnalytics** per Anaconda. Per IronPython, espandere il nodo del numero di versione.
1. Controllare i valori nel nodo **InstallPath**:

    ![Voci del Registro di sistema per una tipica installazione CPython](media/environments/environments-registry-entries.png)

    - Se l'ambiente è ancora presente nel computer, modificare il valore di **ExecutablePath** nella posizione corretta. Correggere anche i valori **(Predefinito)** e **WindowedExecutablePath** in base alle esigenze.
    - Se l'ambiente non è più presente nel computer e si vuole rimuoverlo dalla finestra **Ambienti Python**, eliminare il nodo padre di **InstallPath**, ad esempio **3.6** nell'immagine precedente.
    - Le impostazioni non valide **HKEY_CURRENT_USER\SOFTWARE\Python** sostituire le impostazioni in **HKEY_LOCAL_MACHINE\SOFTWARE\Python**

## <a name="see-also"></a>Vedi anche

- [Installare interpreti Python](installing-python-interpreters.md)
- [Selezionare un interprete per un progetto](selecting-a-python-environment-for-a-project.md)
- [Usare requirements.txt per le dipendenze](managing-required-packages-with-requirements-txt.md)
- [Percorsi di ricerca](search-paths.md)
- [Informazioni di riferimento sulla finestra Ambienti Python](python-environments-window-tab-reference.md)