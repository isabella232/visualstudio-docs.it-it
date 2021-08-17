---
title: Selezionare un ambiente Python per un progetto
description: È possibile selezionare un particolare ambiente Python, inclusi Anaconda e ambienti virtuali, da applicare a un progetto specifico.
ms.date: 03/18/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.technology: vs-python
ms.custom: seodec18, SEO-VS-2020
ms.workload:
- python
- data-science
ms.openlocfilehash: 1305aec9581cb4ae933980e022f88c878738df7d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122027253"
---
# <a name="how-to-select-a-python-environment-for-a-project"></a>Come selezionare un ambiente Python per un progetto

Tutto il codice in un progetto Python viene eseguito nel contesto di un ambiente specifico, ad esempio un ambiente Python globale, un ambiente Anaconda, un ambiente virtuale o un ambiente Conda. Visual Studio usa tale ambiente anche per il debug, i completamenti per importazioni e membri, il controllo della sintassi e altre attività che richiedono servizi del linguaggio specifici per la versione Python e un set di pacchetti installati.

Tutti i nuovi progetti Python in Visual Studio sono configurati inizialmente per l'uso dell'ambiente globale predefinito, visualizzato nel nodo **Ambienti Python** in **Esplora soluzioni**:

![Ambiente di Python globale predefinito visualizzato in Esplora soluzioni](media/environments/environments-project.png)

::: moniker range="vs-2017"
Per modificare l'ambiente per un progetto, fare clic con il pulsante destro del mouse sul nodo **Ambienti Python** e selezionare **Aggiungi/Rimuovi ambienti Python**. Nell'elenco visualizzato, che include gli ambienti globali, virtuali e Conda, selezionare tutti quelli che devono apparire sotto il nodo **Ambienti Python**:

![Finestra Aggiungi/Rimuovi ambienti Python](media/environments/environments-add-remove.png)

Dopo aver selezionato **OK**, tutti gli ambienti selezionati vengono visualizzati nel nodo **Ambienti Python**. L'ambiente attualmente attivato è visualizzato in grassetto:

![Più ambienti Python visualizzati in Esplora soluzioni](media/environments/environments-project-multiple.png)

Per attivare rapidamente un altro ambiente, fare clic con il pulsante destro del mouse sull'ambiente e selezionare **Attiva ambiente**. La scelta viene salvata con il progetto e tale ambiente viene attivato ogni volta che si apre il progetto in futuro. Se si deselezionano tutte le opzioni nella finestra di dialogo **Aggiungi/Rimuovi ambienti Python**, Visual Studio attiva l'ambiente globale predefinito.

Il menu di scelta rapida del nodo **Ambienti Python** contiene anche altri comandi:

| Comando | Descrizione |
| --- | --- |
| **Aggiungi ambiente virtuale** | Avvia il processo di creazione di un nuovo ambiente virtuale nel progetto. Vedere [Creare un ambiente virtuale](#create-a-virtual-environment). |
| **Aggiungi ambiente virtuale esistente** | Richiede la selezione di una cartella contenente un ambiente virtuale e aggiunge l'ambiente all'elenco sotto **Ambienti Python** senza attivarlo. Vedere [Attivare un ambiente virtuale esistente](#activate-an-existing-virtual-environment). |
| **Crea ambiente Conda** | Passa alla finestra **Ambienti Python** *in* cui si immette un nome per l'ambiente e si specifica l'interprete di base. Vedere [Ambienti Conda](managing-python-environments-in-visual-studio.md#conda-environments). |
::: moniker-end

::: moniker range=">=vs-2019"
Per modificare l'ambiente per un progetto, fare clic con il pulsante destro del mouse sul **nodo Ambienti Python** e scegliere Aggiungi **ambiente**. È anche possibile selezionare **Aggiungi ambiente dall'elenco** a discesa ambiente nella barra degli strumenti di Python.

Nella finestra di dialogo **Aggiungi ambiente** selezionare la scheda **Ambiente esistente** e quindi selezionare un nuovo ambiente nell'elenco a discesa **Ambiente**:

![Selezione di un ambiente per il progetto nella finestra di dialogo Aggiungi ambienti](media/environments/environments-project-2019.png)

Se è già stato aggiunto un ambiente diverso da quello predefinito globale a un progetto, potrebbe essere necessario attivare il nuovo ambiente aggiunto. Fare clic con il pulsante destro del mouse su tale ambiente nel nodo **Ambienti Python** e scegliere **Attiva ambiente**. Per rimuovere un ambiente dal progetto, selezionare **Rimuovi**.

![Attivazione e rimozione di un ambiente del progetto](media/environments/environments-project-add-remove-2019.png)
::: moniker-end

## <a name="use-virtual-environments"></a>Usare gli ambienti virtuali

Un ambiente virtuale è una combinazione univoca di un interprete Python specifico e un set specifico di librerie, diversa da altri ambienti globali e Conda. Un ambiente virtuale è specifico di un progetto e viene gestito in una cartella del progetto. Tale cartella contiene le librerie installate dell'ambiente oltre a un file *pyvenv.cfg* che specifica il percorso per l'*interprete di base* dell'ambiente in un'altra posizione nel file system. Ovvero, un ambiente virtuale non contiene una copia dell'interprete, solo un collegamento ad esso.

Un vantaggio offerto dall'uso di un ambiente virtuale è che nel corso dello sviluppo del progetto l'ambiente virtuale riflette sempre le dipendenze esatte del progetto. Un ambiente globale condiviso, d'altra parte, contiene un numero qualsiasi di librerie indipendentemente dal fatto che siano usate o meno nel progetto. È quindi possibile creare facilmente un file *requirements.txt* dall'ambiente virtuale, che viene quindi usato per reinstallare tali dipendenze in un altro computer di sviluppo o di produzione. Per altre informazioni, vedere [Gestire i pacchetti necessari con requirements.txt](managing-required-packages-with-requirements-txt.md).

Quando si apre in Visual Studio un progetto che contiene un file *requirements.txt*, Visual Studio offre automaticamente la possibilità di ricreare l'ambiente virtuale. Nei computer in cui non è installato Visual Studio, è possibile usare `pip install -r requirements.txt` per ripristinare i pacchetti.

Poiché un ambiente virtuale contiene un percorso hardcoded all'interprete di base ed è possibile ricreare l'ambiente usando *requirements.txt*, in genere si omette l'intera cartella dell'ambiente virtuale dal controllo del codice sorgente.

Le sezioni seguenti illustrano come attivare in un progetto un ambiente virtuale già esistente e come creare un nuovo ambiente virtuale.

In Visual Studio un ambiente virtuale può essere attivato per un progetto come qualsiasi altro ambiente usando il nodo **Ambienti Python** in **Esplora soluzioni**.

Dopo essere stato aggiunto al progetto, l'ambiente virtuale viene visualizzato nella finestra **Ambienti Python**. È quindi possibile attivarlo come qualsiasi altro ambiente, nonché gestire i pacchetti correlati.

::: moniker range="vs-2017"
### <a name="create-a-virtual-environment"></a>Creare un ambiente virtuale

È possibile creare un nuovo ambiente virtuale direttamente in Visual Studio, come indicato di seguito:

1. Fare clic con il pulsante destro del mouse su **Ambienti Python** in **Esplora soluzioni** e scegliere **Aggiungi ambiente virtuale** per visualizzare la finestra di dialogo seguente:

    ![Creazione di un ambiente virtuale](media/environments/environments-add-virtual-1.png)

1. Nel campo **Percorso dell'ambiente virtuale** specificare un percorso per l'ambiente virtuale. Se si specifica solo un nome, l'ambiente virtuale viene creato all'interno del progetto corrente in una sottocartella con lo stesso nome.

1. Selezionare un ambiente come interprete di base e selezionare **Crea**. Visual Studio visualizza un indicatore di stato mentre configura l'ambiente e scarica tutti i pacchetti necessari. Al termine, l'ambiente virtuale viene visualizzato nella finestra **Ambienti Python** per il progetto che lo contiene.

1. L'ambiente virtuale non viene attivato per impostazione predefinita. Per attivare l'ambiente virtuale per il progetto, fare clic con il pulsante destro del mouse su di esso e **scegliere Attiva ambiente**.

> [!Note]
> Se il percorso identifica un ambiente virtuale esistente, Visual Studio rileva l'interprete di base automaticamente, usando il file *orig-prefix.txt* nella directory *lib* dell'ambiente, e modifica il pulsante **Crea** in **Aggiungi**.
>
> Se quando si aggiunge un ambiente virtuale esiste un file *requirements.txt*, nella finestra di dialogo **Aggiungi ambiente virtuale** viene visualizzata un'opzione per installare automaticamente i pacchetti, in modo da ricreare facilmente un ambiente in un altro computer:
>
> ![Creazione di un ambiente virtuale con requirements.txt](media/environments/environments-requirements-txt.png)
>
> In entrambi i casi il risultato è lo stesso di quello ottenuto con il comando **Aggiungi ambiente virtuale esistente**.

### <a name="activate-an-existing-virtual-environment"></a>Attivare un ambiente virtuale esistente

Se è già stato creato un ambiente virtuale in un'altra posizione, è possibile attivarlo per un progetto come indicato di seguito:

1. Fare clic con il pulsante destro del mouse su **Ambienti Python** in **Esplora soluzioni** e scegliere **Aggiungi ambiente virtuale esistente**.

1. Nella finestra di dialogo **Sfoglia** visualizzata individuare e selezionare la cartella che contiene l'ambiente virtuale, quindi selezionare **OK**. Se Visual Studio rileva un file *requirements.txt* in tale ambiente, richiede se installare tali pacchetti.

1. Dopo alcuni istanti, l'ambiente virtuale viene visualizzato nel nodo **Ambienti Python** in **Esplora soluzioni**. L'ambiente virtuale non è attivato per impostazione predefinita, quindi fare clic con pulsante destro del mouse su di esso e scegliere **Attiva ambiente**.
::: moniker-end

::: moniker range=">=vs-2019"
### <a name="create-a-virtual-environment"></a>Creare un ambiente virtuale

È possibile creare un nuovo ambiente virtuale direttamente in Visual Studio, come indicato di seguito:

1. Fare clic con il pulsante destro del mouse sul nodo **Ambienti Python** in **Esplora soluzioni** e scegliere **Aggiungi ambiente** oppure selezionare **Aggiungi ambiente** nell'elenco a discesa degli ambienti sulla barra degli strumenti Python. Nella finestra di dialogo **Aggiungi ambiente** visualizzata selezionare la scheda **Ambiente virtuale**:

    ![Scheda Ambiente virtuale della finestra di dialogo Aggiungi ambiente](media/environments/environments-add-virtual-1-2019.png)

1. Specificare un nome per l'ambiente virtuale, selezionare un interprete di base e verificare il percorso. In **Installa pacchetti dal file** specificare il percorso di un file *requirements.txt* se lo si desidera.

1. Esaminare le altre opzioni nella finestra di dialogo:

    | Opzione | Descrizione |
    | --- | --- |
    | Imposta come ambiente corrente | Dopo aver creato l'ambiente, attiva il nuovo ambiente nel progetto selezionato. |
    | Imposta come ambiente predefinito per i nuovi progetti | Imposta e attiva automaticamente l'ambiente virtuale in tutti i nuovi progetti creati in Visual Studio. Quando si usa questa opzione, l'ambiente virtuale deve essere inserito in una posizione esterna a un progetto specifico.  |
    | Visualizza nella finestra Ambienti Python | Specifica se aprire la finestra **Ambienti Python** dopo la creazione dell'ambiente. |
    | Rendi questo ambiente disponibile a livello globale | Specifica se l'ambiente virtuale funge anche da ambiente globale. Quando si usa questa opzione, l'ambiente virtuale deve essere inserito in una posizione esterna a un progetto specifico. |

1. Selezionare **Crea** per finalizzare l'ambiente virtuale. Visual Studio visualizza un indicatore di stato mentre configura l'ambiente e scarica tutti i pacchetti necessari. Dopo il completamento, l'ambiente virtuale viene attivato e visualizzato nel nodo **Ambienti Python** in **Esplora soluzioni** e nella finestra **Ambienti Python** per il progetto che lo contiene.

### <a name="activate-an-existing-virtual-environment"></a>Attivare un ambiente virtuale esistente

Se è già stato creato un ambiente virtuale in un'altra posizione, è possibile attivarlo per un progetto come indicato di seguito:

1. Fare clic con il pulsante destro del mouse su **Ambienti Python** in **Esplora soluzioni** e scegliere **Aggiungi ambiente**.

1. Nella finestra di dialogo **Sfoglia** visualizzata individuare e selezionare la cartella che contiene l'ambiente virtuale, quindi selezionare **OK**. Se Visual Studio rileva un file *requirements.txt* in tale ambiente, richiede se installare tali pacchetti.

1. Dopo alcuni istanti, l'ambiente virtuale viene visualizzato nel nodo **Ambienti Python** in **Esplora soluzioni**. L'ambiente virtuale non è attivato per impostazione predefinita, quindi fare clic con pulsante destro del mouse su di esso e scegliere **Attiva ambiente**.
::: moniker-end

### <a name="remove-a-virtual-environment"></a>Rimuovere un ambiente virtuale

1. In **Esplora soluzioni**, fare clic con il pulsante destro del mouse sull'ambiente virtuale e scegliere **Rimuove**.

1. Visual Studio chiede se rimuovere o eliminare l'ambiente virtuale. Se si seleziona **Rimuovi**, l'ambiente non sarà più disponibile per il progetto, ma rimane nel file system. Se si seleziona **Elimina**, l'ambiente viene rimosso sia dal progetto che dal file system. Non ci sono effetti per l'interprete di base.

## <a name="view-installed-packages"></a>Visualizzare i pacchetti installati

In Esplora soluzioni espandere il nodo di qualsiasi ambiente specifico per visualizzare rapidamente i pacchetti installati in tale ambiente, ovvero i pacchetti che possono essere importati e usati nel codice quando l'ambiente è attivo:

![Pacchetti Python per un ambiente in Esplora soluzioni](media/environments/environments-installed-packages.png)

::: moniker range="vs-2017"
Per installare nuovi pacchetti, fare clic con il pulsante destro del mouse sull'ambiente e scegliere **Installa pacchetto Python** per passare alla scheda **Pacchetti** appropriata nella finestra **Ambienti Python**. Immettere un termine di ricerca (in genere il nome del pacchetto). Visual Studio visualizza i pacchetti corrispondenti.
::: moniker-end
::: moniker range=">=vs-2019"
Per installare nuovi pacchetti, fare clic con il pulsante destro del mouse sull'ambiente e scegliere **Gestisci pacchetti Python** (o usare il pulsante Pacchetto sulla barra degli strumenti Python) per passare alla scheda **Pacchetti** appropriata nella finestra **Ambienti Python**. Nella scheda **Pacchetti** immettere un termine di ricerca (in genere il nome del pacchetto). Visual Studio visualizza i pacchetti corrispondenti.
::: moniker-end

In Visual Studio, i pacchetti e le dipendenze per la maggior parte degli ambienti vengono scaricati dall'[indice dei pacchetti Python (PyPI)](https://pypi.org), in cui è anche possibile cercare i pacchetti disponibili. Le informazioni sull'installazione sono visualizzate nella barra di stato e nella finestra di output di Visual Studio. Per disinstallare un pacchetto, fare clic con il pulsante del destro sul pacchetto e scegliere **Rimuovi**.

La gestione pacchetti Conda usa in genere `https://repo.continuum.io/pkgs/` come canale predefinito, ma sono disponibili altri canali. Per altre informazioni, vedere [Manage Channels](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-channels.html) (Gestire i canali) nel sito docs.conda.io.

Tenere presente che è possibile che le voci visualizzate non siano sempre accurate e che l'installazione e la disinstallazione non siano disponibili o affidabili. Visual Studio usa la funzionalità di gestione dei pacchetti pip, se disponibile, scaricandola e installandola quando necessario. Visual Studio può anche usare la funzionalità di gestione pacchetti easy_install. Vengono visualizzati anche i pacchetti installati con `pip` o `easy_install` dalla riga di comando.

Si noti inoltre che Visual Studio non supporta attualmente l'uso di `conda` per installare i pacchetti in un ambiente Conda. Usare invece `conda` dalla riga di comando.

> [!Tip]
> Una situazione comune in cui pip non riesce a installare un pacchetto è quando il pacchetto include il codice sorgente per i componenti nativi nei *\* file con estensione pyd.* Se non è installata la versione richiesta di Visual Studio, pip non può compilare questi componenti. Il messaggio di errore visualizzato in questa situazione è **errore: Impossibile trovare vcvarsall.bat**. `easy_install` è spesso in grado di scaricare file binari precompilati ed è possibile scaricare un compilatore adatto per le versioni precedenti di Python da [https://www.microsoft.com/download/details.aspx?id=44266](https://www.microsoft.com/download/details.aspx?id=44266) . Per altre informazioni, vedere [How to deal with the pain of "unable to find vcvarsallbat"](https://devblogs.microsoft.com/python/unable-to-find-vcvarsall-bat/) (Come gestire l'errore "vcvarsallbat non trovato") nel blog del team degli strumenti Python.

## <a name="see-also"></a>Vedi anche

- [Gestire ambienti Python in Visual Studio](managing-python-environments-in-visual-studio.md)
- [Usare requirements.txt per le dipendenze](managing-required-packages-with-requirements-txt.md)
- [Percorsi di ricerca](search-paths.md)
- [Informazioni di riferimento sulla finestra Ambienti Python](python-environments-window-tab-reference.md)
