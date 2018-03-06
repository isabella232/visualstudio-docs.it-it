---
title: Selezione di un ambiente per un progetto | Microsoft Docs
description: "In Esplora soluzioni di Visual Studio è possibile assegnare un interprete (ambiente) Python specifico da usare sempre per un determinato progetto, ignorando l'ambiente predefinito. È anche possibile creare e gestire ambienti virtuali."
ms.custom: 
ms.date: 02/20/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: 6f422cc60638b7eed4a5b42516e7496c4a6f6209
ms.sourcegitcommit: c0a2385a16cc4f47d2e1ff23d35c4da40f5605e0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/23/2018
---
# <a name="selecting-a-python-interpreter-and-environment-for-use-in-a-project"></a>Selezione di un interprete e un ambiente Python da usare in un progetto

Tutto il codice in un progetto Python viene eseguito nel contesto di un ambiente specifico. Visual Studio usa anche tale ambiente per il debug, i completamenti per importazioni e membri, il controllo della sintassi e altre attività che richiedono un ambiente.

Tutti i nuovi progetti Python in Visual Studio sono configurati inizialmente per l'uso dell'ambiente globale predefinito, visualizzato nel nodo **Ambienti Python** in Esplora soluzioni:

![Ambiente di Python globale predefinito visualizzato in Esplora soluzioni](media/environments-project.png)

È possibile rendere disponibili altri ambienti per il progetto, inclusi gli ambienti virtuali. È possibile attivare un solo ambiente in qualsiasi momento.

## <a name="using-global-environments"></a>Uso degli ambienti globali

Per rendere disponibili ambienti globali specifici per il progetto (inclusi gli ambienti Conda [identificati manualmente](managing-python-environments-in-visual-studio.md#manually-identifying-an-existing-environment)), fare clic con il pulsante destro del mouse sul nodo **Ambienti Python** e scegliere **Aggiungi/Rimuovi ambienti Python**. Nell'elenco visualizzato selezionare gli ambienti desiderati:

![Finestra Aggiungi/Rimuovi ambienti Python](media/environments-add-remove.png)

Dopo aver selezionato **OK**, tutti gli ambienti selezionati vengono visualizzati nel nodo **Ambienti Python**. L'ambiente attualmente attivato è visualizzato in grassetto:

![Più ambienti Python visualizzati in Esplora soluzioni](media/environments-project-multiple.png)

Per attivare un ambiente diverso, fare clic con il pulsante destro del mouse sull'ambiente e scegliere **Attiva ambiente**. La scelta viene salvata con il progetto e tale ambiente viene attivato ogni volta che si apre il progetto in futuro.

Se si deselezionano tutte le opzioni nella finestra di dialogo **Aggiungi/Rimuovi ambienti Python**, Visual Studio attiva l'ambiente globale predefinito.

## <a name="using-virtual-environments"></a>Uso di ambienti virtuali

Un ambiente virtuale è una combinazione univoca di un interprete Python specifico e un set specifico di librerie, diversa da altri ambienti globali e Conda. In genere si usa un ambiente virtuale quando si hanno esigenze specifiche in un progetto e non si vogliono modificare altri ambienti per soddisfare tali esigenze.

Dopo essere stato aggiunto al progetto, l'ambiente virtuale viene visualizzato nella finestra **Ambienti Python** ed è possibile attivarlo come qualsiasi altro ambiente, nonché gestirne i pacchetti.

Uno degli svantaggi degli ambienti virtuali è che contengono percorsi di file hardcoded e di conseguenza non possono essere facilmente condivisi o trasportati in altri computer di sviluppo. Fortunatamente, è possibile usare il file `requirements.txt` per consentire ai destinatari del progetto di ripristinare facilmente l'ambiente. Per altre informazioni, vedere [Gestione dei pacchetti necessari con requirements.txt](managing-required-packages-with-requirements-txt.md).

### <a name="activating-an-existing-virtual-environment"></a>Attivazione di un ambiente virtuale esistente

Se è già stato creato un ambiente virtuale in un'altra posizione, è possibile attivarlo per un progetto come indicato di seguito:

1. Fare clic con il pulsante destro del mouse su **Ambienti Python** in Esplora soluzioni e scegliere **Aggiungi ambiente virtuale esistente**.

1. Nella finestra di dialogo **Sfoglia** visualizzata individuare e selezionare la cartella che contiene l'ambiente virtuale, quindi selezionare **OK**. Se Visual Studio rileva un file `requirements.txt` in tale ambiente, richiede se installare tali pacchetti.

1. Dopo alcuni istanti, l'ambiente virtuale viene visualizzato nel nodo **Ambienti Python** in Esplora soluzioni. L'ambiente virtuale non è attivato per impostazione predefinita, quindi fare clic con pulsante destro del mouse su di esso e scegliere **Attiva ambiente**.

### <a name="creating-a-virtual-environment"></a>Creazione di un ambiente virtuale

È possibile creare un nuovo ambiente virtuale direttamente da Visual Studio, come indicato di seguito:

1. Fare clic con il pulsante destro del mouse su **Ambienti Python** in Esplora soluzioni e scegliere **Aggiungi ambiente virtuale** per visualizzare la finestra di dialogo seguente:

    ![Creazione di un ambiente virtuale](media/environments-add-virtual-1.png)

1. Nel campo **Percorso dell'ambiente virtuale** specificare un percorso per l'ambiente virtuale. Se si specifica solo un nome, l'ambiente virtuale viene creato all'interno del progetto corrente in una sottocartella con lo stesso nome.

1. Selezionare un ambiente come interprete di base e selezionare **Crea**. Visual Studio visualizza un indicatore di stato mentre configura l'ambiente e scarica tutti i pacchetti necessari. A questo punto l'ambiente virtuale viene visualizzato nella finestra **Ambienti Python** per il progetto che lo contiene.

1. L'ambiente virtuale non viene attivato per impostazione predefinita. Per attivarlo per il progetto, fare clic con il pulsante destro del mouse su di esso e scegliere **Attiva ambiente**.

> [!Note]
> Se il percorso identifica un ambiente virtuale esistente, Visual Studio rileva l'interprete di base automaticamente (mediante il file `orig-prefix.txt` nella directory `lib` dell'ambiente) e modifica il pulsante Crea in **Aggiungi**.
>
> Se, quando si aggiunge un ambiente virtuale, esiste un file `requirements.txt`, nella finestra di dialogo **Aggiungi ambiente virtuale** viene visualizzata un'opzione per installare automaticamente i pacchetti, in modo da ricreare facilmente un ambiente in un altro computer:
>
> ![Creazione di un ambiente virtuale con requirements.txt](media/environments-requirements-txt.png)
>
> In entrambi i casi, il risultato è lo stesso di quello ottenuto con il comando **Aggiungi ambiente virtuale esistente**.

### <a name="remove-a-virtual-environment"></a>Rimuovere un ambiente virtuale

1. In Esplora soluzioni fare clic con il pulsante destro del mouse sull'ambiente virtuale e scegliere **Rimuovi**.

1. Visual Studio chiede se rimuovere o eliminare l'ambiente virtuale. Se si seleziona **Rimuovi**, l'ambiente non sarà più disponibile per il progetto, ma rimane nel file system. Se si seleziona **Elimina**, l'ambiente viene rimosso sia dal progetto che dal file system. Non ci sono effetti per l'interprete di base.

## <a name="viewing-installed-packages"></a>Visualizzazione dei pacchetti installati

In Esplora soluzioni espandere il nodo di qualsiasi ambiente specifico per visualizzare rapidamente i pacchetti installati in tale ambiente, ovvero i pacchetti che possono essere importati e usati nel codice quando l'ambiente è attivo:

![Pacchetti Python per un ambiente in Esplora soluzioni](media/environments-installed-packages.png)

Per installare nuovi pacchetti, fare clic con il pulsante destro del mouse sull'ambiente e scegliere **Installa pacchetto Python** per passare alla scheda **Pacchetti** nella finestra **Ambienti Python**. Immettere un termine di ricerca (in genere il nome del pacchetto). Visual Studio visualizza i pacchetti corrispondenti.

In Visual Studio, i pacchetti e le dipendenze vengono scaricati dall'[indice dei pacchetti Python (PyPI)](https://pypi.python.org/pypi), in cui è anche possibile cercare i pacchetti disponibili. Le informazioni sull'installazione sono visualizzate nella barra di stato e nella finestra di output di Visual Studio. Per disinstallare un pacchetto, fare clic con il pulsante del destro sul pacchetto e scegliere **Rimuovi**.

Tenere presente che è possibile che le voci visualizzate non siano sempre accurate e che l'installazione e la disinstallazione non siano disponibili o affidabili. Visual Studio usa la funzionalità di gestione dei pacchetti pip, se disponibile, scaricandola e installandola quando necessario. Visual Studio può anche usare la funzionalità di gestione pacchetti easy_install. Vengono visualizzati anche i pacchetti installati con `pip` o `easy_install` dalla riga di comando.

Si noti inoltre che Visual Studio non supporta attualmente l'uso di `conda` per installare i pacchetti in un ambiente Conda. Usare invece `conda` dalla riga di comando.

> [!Tip]
> Può capitare spesso che pip non riesca a installare un pacchetto quando questo include il codice sorgente per i componenti nativi in file `*.pyd`. Se non è installata la versione richiesta di Visual Studio, pip non può compilare questi componenti. Il messaggio di errore visualizzato in questa situazione è `error: Unable to find vcvarsall.bat`. `easy_install` è spesso in grado di scaricare file binari precompilati ed è possibile scaricare un compilatore appropriato per le versioni precedenti di Python all'indirizzo [http://aka.ms/VCPython27](http://aka.ms/VCPython27). Per altre informazioni, vedere [How to deal with the pain of "unable to find vcvarsallbat"](https://blogs.msdn.microsoft.com/pythonengineering/2016/04/11/unable-to-find-vcvarsall-bat/) (Come gestire l'errore "vcvarsallbat non trovato") nel blog del team degli strumenti Python.

## <a name="see-also"></a>Vedere anche

- [Gestione di ambienti Python in Visual Studio](managing-python-environments-in-visual-studio.md)
- [Uso di requirements.txt per le dipendenze](managing-required-packages-with-requirements-txt.md)
- [Percorsi di ricerca](search-paths.md)
- [Informazioni di riferimento sulla finestra Ambienti Python](python-environments-window-tab-reference.md)