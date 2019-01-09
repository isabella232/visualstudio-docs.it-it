---
title: Selezionare un interprete e un ambiente Python per un progetto
description: È possibile selezionare un particolare ambiente Python, inclusi Anaconda e ambienti virtuali, da applicare a un progetto specifico.
ms.date: 11/08/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 25492d3f6d152369bdabaad5eafc05f5e8822132
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53879358"
---
# <a name="how-to-select-a-python-environment-for-a-project"></a>Come selezionare un ambiente Python per un progetto

Tutto il codice in un progetto Python viene eseguito nel contesto di un ambiente specifico, ad esempio un ambiente Python globale, un ambiente Anaconda, un ambiente virtuale o un ambiente Conda. Visual Studio usa tale ambiente anche per il debug, i completamenti per importazioni e membri, il controllo della sintassi e altre attività che richiedono servizi del linguaggio specifici per la versione Python e un set di pacchetti installati.

Tutti i nuovi progetti Python in Visual Studio sono configurati inizialmente per l'uso dell'ambiente globale predefinito, visualizzato nel nodo **Ambienti Python** in **Esplora soluzioni**:

![Ambiente di Python globale predefinito visualizzato in Esplora soluzioni](media/environments-project.png)

Per modificare l'ambiente per un progetto, fare clic con il pulsante destro del mouse sul nodo **Ambienti Python** e selezionare **Aggiungi/Rimuovi ambienti Python**. Nell'elenco visualizzato, che include gli ambienti globali, virtuali e Conda, selezionare tutti quelli che devono apparire sotto il nodo **Ambienti Python**:

![Finestra Aggiungi/Rimuovi ambienti Python](media/environments-add-remove.png)

Dopo aver selezionato **OK**, tutti gli ambienti selezionati vengono visualizzati nel nodo **Ambienti Python**. L'ambiente attualmente attivato è visualizzato in grassetto:

![Più ambienti Python visualizzati in Esplora soluzioni](media/environments-project-multiple.png)

Per attivare rapidamente un altro ambiente, fare clic con il pulsante destro del mouse sull'ambiente e selezionare **Attiva ambiente**. La scelta viene salvata con il progetto e tale ambiente viene attivato ogni volta che si apre il progetto in futuro. Se si deselezionano tutte le opzioni nella finestra di dialogo **Aggiungi/Rimuovi ambienti Python**, Visual Studio attiva l'ambiente globale predefinito.

Il menu di scelta rapida del nodo **Ambienti Python** contiene anche altri comandi:

| Comando | Description |
| --- | --- |
| **Aggiungi ambiente virtuale** | Avvia il processo di creazione di un nuovo ambiente virtuale nel progetto. Vedere [Creare un ambiente virtuale](#create-a-virtual-environment). |
| **Aggiungi ambiente virtuale esistente** | Richiede la selezione di una cartella contenente un ambiente virtuale e aggiunge l'ambiente all'elenco sotto **Ambienti Python** senza attivarlo. Vedere [Attivare un ambiente virtuale esistente](#activate-an-existing-virtual-environment). |
| **Crea ambiente Conda** | Consente di passare alla *finestra* **Ambienti Python**in cui si può immettere un nome per l'ambiente e specificare il relativo interprete di base. Vedere [Ambienti Conda](managing-python-environments-in-visual-studio.md#conda-environments). |

## <a name="use-virtual-environments"></a>Usare gli ambienti virtuali

Un ambiente virtuale è una combinazione univoca di un interprete Python specifico e un set specifico di librerie, diversa da altri ambienti globali e Conda. Un ambiente virtuale è specifico di un progetto e viene gestito in una cartella del progetto. Tale cartella contiene le librerie installate dell'ambiente oltre a un file *pyvenv.cfg* che specifica il percorso per l'*interprete di base* dell'ambiente in un'altra posizione nel file system. Ovvero, un ambiente virtuale non contiene una copia dell'interprete, solo un collegamento ad esso. 

Un vantaggio offerto dall'uso di un ambiente virtuale è che nel corso dello sviluppo del progetto l'ambiente virtuale riflette sempre le dipendenze esatte del progetto. Un ambiente globale condiviso contiene invece qualsiasi numero di librerie, indipendentemente dal fatto che vengano usate o meno nel progetto. È quindi possibile creare facilmente un file *requirements.txt* dall'ambiente virtuale e successivamente usarlo per reinstallare tali dipendenze in un altro computer di sviluppo o di produzione. Per altre informazioni, vedere [Gestire i pacchetti necessari con requirements.txt](managing-required-packages-with-requirements-txt.md).

Quando si apre in Visual Studio un progetto che contiene un file *requirements.txt*, Visual Studio offre automaticamente la possibilità di ricreare l'ambiente virtuale. Nei computer in cui non è installato Visual Studio, è possibile usare `pip install -r requirements.txt` per ripristinare i pacchetti.

Poiché un ambiente virtuale contiene un percorso hardcoded all'interprete di base ed è possibile ricreare l'ambiente usando *requirements.txt*, in genere si omette l'intera cartella dell'ambiente virtuale dal controllo del codice sorgente.

Le sezioni seguenti illustrano come attivare in un progetto un ambiente virtuale già esistente e come creare un nuovo ambiente virtuale.

In Visual Studio un ambiente virtuale può essere attivato per un progetto come qualsiasi altro ambiente usando il nodo **Ambienti Python** in **Esplora soluzioni**.

Dopo essere stato aggiunto al progetto, l'ambiente virtuale viene visualizzato nella finestra **Ambienti Python**. È quindi possibile attivarlo come qualsiasi altro ambiente, nonché gestire i pacchetti correlati.

### <a name="create-a-virtual-environment"></a>Creare un ambiente virtuale

È possibile creare un nuovo ambiente virtuale direttamente da Visual Studio, come indicato di seguito:

1. Fare clic con il pulsante destro del mouse su **Ambienti Python** in **Esplora soluzioni** e scegliere **Aggiungi ambiente virtuale** per visualizzare la finestra di dialogo seguente:

    ![Creazione di un ambiente virtuale](media/environments-add-virtual-1.png)

1. Nel campo **Percorso dell'ambiente virtuale** specificare un percorso per l'ambiente virtuale. Se si specifica solo un nome, l'ambiente virtuale viene creato all'interno del progetto corrente in una sottocartella con lo stesso nome.

1. Selezionare un ambiente come interprete di base e selezionare **Crea**. Visual Studio visualizza un indicatore di stato mentre configura l'ambiente e scarica tutti i pacchetti necessari. A questo punto l'ambiente virtuale viene visualizzato nella finestra **Ambienti Python** per il progetto che lo contiene.

1. L'ambiente virtuale non viene attivato per impostazione predefinita. Per attivarlo per il progetto, fare clic con il pulsante destro del mouse su di esso e scegliere **Attiva ambiente**.

> [!Note]
> Se il percorso identifica un ambiente virtuale esistente, Visual Studio rileva l'interprete di base automaticamente, usando il file *orig-prefix.txt* nella directory *lib* dell'ambiente, e modifica il pulsante **Crea** in **Aggiungi**.
>
> Se quando si aggiunge un ambiente virtuale esiste un file *requirements.txt*, nella finestra di dialogo **Aggiungi ambiente virtuale** viene visualizzata un'opzione per installare automaticamente i pacchetti, in modo da ricreare facilmente un ambiente in un altro computer:
>
> ![Creazione di un ambiente virtuale con requirements.txt](media/environments-requirements-txt.png)
>
> In entrambi i casi il risultato è lo stesso di quello ottenuto con il comando **Aggiungi ambiente virtuale esistente**.

### <a name="activate-an-existing-virtual-environment"></a>Attivare un ambiente virtuale esistente

Se è già stato creato un ambiente virtuale in un'altra posizione, è possibile attivarlo per un progetto come indicato di seguito:

1. Fare clic con il pulsante destro del mouse su **Ambienti Python** in **Esplora soluzioni** e scegliere **Aggiungi ambiente virtuale esistente**.

1. Nella finestra di dialogo **Sfoglia** visualizzata individuare e selezionare la cartella che contiene l'ambiente virtuale, quindi selezionare **OK**. Se Visual Studio rileva un file *requirements.txt* in tale ambiente, richiede se installare tali pacchetti.

1. Dopo alcuni istanti, l'ambiente virtuale viene visualizzato nel nodo **Ambienti Python** in **Esplora soluzioni**. L'ambiente virtuale non è attivato per impostazione predefinita, quindi fare clic con pulsante destro del mouse su di esso e scegliere **Attiva ambiente**.

### <a name="remove-a-virtual-environment"></a>Rimuovere un ambiente virtuale

1. In **Esplora soluzioni**, fare clic con il pulsante destro del mouse sull'ambiente virtuale e scegliere **Rimuove**.

1. Visual Studio chiede se rimuovere o eliminare l'ambiente virtuale. Se si seleziona **Rimuovi**, l'ambiente non sarà più disponibile per il progetto, ma rimane nel file system. Se si seleziona **Elimina**, l'ambiente viene rimosso sia dal progetto che dal file system. Non ci sono effetti per l'interprete di base.

## <a name="view-installed-packages"></a>Visualizzare i pacchetti installati

In Esplora soluzioni espandere il nodo di qualsiasi ambiente specifico per visualizzare rapidamente i pacchetti installati in tale ambiente, ovvero i pacchetti che possono essere importati e usati nel codice quando l'ambiente è attivo:

![Pacchetti Python per un ambiente in Esplora soluzioni](media/environments-installed-packages.png)

Per installare nuovi pacchetti, fare clic con il pulsante destro del mouse sull'ambiente e scegliere **Installa pacchetto Python** per passare alla scheda **Pacchetti** nella finestra **Ambienti Python**. Immettere un termine di ricerca (in genere il nome del pacchetto). Visual Studio visualizza i pacchetti corrispondenti.

In Visual Studio, i pacchetti e le dipendenze vengono scaricati dall'[indice dei pacchetti Python (PyPI)](https://pypi.org), in cui è anche possibile cercare i pacchetti disponibili. Le informazioni sull'installazione sono visualizzate nella barra di stato e nella finestra di output di Visual Studio. Per disinstallare un pacchetto, fare clic con il pulsante del destro sul pacchetto e scegliere **Rimuovi**.

Tenere presente che è possibile che le voci visualizzate non siano sempre accurate e che l'installazione e la disinstallazione non siano disponibili o affidabili. Visual Studio usa la funzionalità di gestione dei pacchetti pip, se disponibile, scaricandola e installandola quando necessario. Visual Studio può anche usare la funzionalità di gestione pacchetti easy_install. Vengono visualizzati anche i pacchetti installati con `pip` o `easy_install` dalla riga di comando.

Si noti inoltre che Visual Studio non supporta attualmente l'uso di `conda` per installare i pacchetti in un ambiente Conda. Usare invece `conda` dalla riga di comando.

> [!Tip]
> Può capitare spesso che pip non riesca a installare un pacchetto quando questo include il codice sorgente per i componenti nativi in file con estensione *\*pyd*. Se non è installata la versione richiesta di Visual Studio, pip non può compilare questi componenti. Il messaggio di errore visualizzato in questa situazione è **Errore: vcvarsall.bat non è stato trovato**. `easy_install` è spesso in grado di scaricare file binari precompilati ed è possibile scaricare un compilatore appropriato per le versioni precedenti di Python da [https://aka.ms/VCPython27](https://aka.ms/VCPython27). Per altre informazioni, vedere [How to deal with the pain of "unable to find vcvarsallbat"](https://blogs.msdn.microsoft.com/pythonengineering/2016/04/11/unable-to-find-vcvarsall-bat/) (Come gestire l'errore "vcvarsallbat non trovato") nel blog del team degli strumenti Python.

## <a name="see-also"></a>Vedere anche

- [Gestire ambienti Python in Visual Studio](managing-python-environments-in-visual-studio.md)
- [Usare requirements.txt per le dipendenze](managing-required-packages-with-requirements-txt.md)
- [Percorsi di ricerca](search-paths.md)
- [Informazioni di riferimento sulla finestra Ambienti Python](python-environments-window-tab-reference.md)
