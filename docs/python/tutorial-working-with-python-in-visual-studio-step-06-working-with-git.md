---
title: Esercitazione sull'uso di Python in Visual Studio, passaggio 6, usare Git
titleSuffix: ''
description: Passaggio 6 di un'esercitazione di base per l'uso di Python in Visual Studio, dedicato alle funzionalità di Visual Studio correlate a Git.
ms.date: 01/28/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.technology: vs-python
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: e7e21f007d0248f84ecbfffb87e953b6d08f9a3a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122156474"
---
# <a name="step-6-work-with-git"></a>Passaggio 6: Utilizzo di Git

**Passaggio precedente: [ Installare i pacchetti e gestire l'ambiente Python](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md)**

Visual Studio offre l'integrazione diretta con repository Git locali e repository remoti di servizi quali GitHub e Azure Repos. L'integrazione include la clonazione di un repository, le modifiche di esecuzione del commit e la gestione dei rami.

Questo articolo offre una panoramica di base sulla creazione di un repository Git locale per un progetto esistente e consente di acquisire familiarità con alcune delle funzionalità di Visual Studio correlate a Git.

1. Con un progetto aperto in Visual Studio, ad esempio il progetto del [passaggio precedente](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md), fare clic col pulsante destro del mouse sulla soluzione e scegliere **Aggiungi soluzione al controllo del codice sorgente**. Visual Studio crea un repository Git locale che contiene il codice del progetto.

1. Quando Visual Studio rileva che il progetto viene gestito in un repository Git, lungo l'angolo inferiore destro della finestra di Visual Studio vengono visualizzati controlli relativi a Git. I controlli visualizzano le esecuzioni di commit in sospeso, le modifiche, il nome del repository e il ramo. Passare il mouse sui controlli per visualizzare le informazioni aggiuntive.

    ![Le informazioni aggiuntive vengono visualizzate quando si posiziona un controllo Git nella finestra di Visual Studio](media/working-with-git-01.png)

1. Quando si crea un nuovo repository o si seleziona uno dei controlli Git, Visual Studio apre la finestra **Team Explorer**. È possibile aprire la finestra in qualsiasi momento con **la** visualizzazione  >  **Team Explorer** comando di menu. La finestra include tre riquadri principali, tra cui l'uso dell'elenco a discesa nell Team Explorer **intestazione.** Il **riquadro Sincronizza,** che fornisce le operazioni di pubblicazione, viene visualizzato anche quando si seleziona il **controllo Push** (icona freccia su):

    ![Team Explorer in Visual Studio dopo la creazione di un repository locale](media/working-with-git-02.png)

1. Selezionare **Modifiche** (o il controllo Git con l'icona della matita) per esaminare le modifiche non sottoposte a commit ed eseguirne il commit nel momento desiderato.

    ![Team Explorer in Visual Studio per la visualizzazione di modifiche non sottoposte a commit](media/working-with-git-03.png)

    Fare doppio clic su un file nell'elenco **Modifiche** per aprire la visualizzazione delle differenze per il file:

    ![Visualizzazione delle differenze per le modifiche in un file](media/working-with-git-05.png)

1. Selezionare **Rami** (o il controllo Git con un nome di ramo) per esaminare i rami ed eseguire operazioni di unione e riassegnazione:

    ![Team Explorer in Visual Studio per la visualizzazione dei rami](media/working-with-git-04.png)

1. Selezionando il controllo Git con il nome del repository (**CosineWave** in un'immagine precedente), **Team Explorer** mostra un'interfaccia **Connessione** con cui è possibile passare rapidamente a un altro repository completamente.

1. Quando si usa un repository locale, le modifiche sottoposte a commit passano direttamente al repository. Se si è connessi a un repository remoto, selezionare l'intestazione  dell'elenco  a discesa in **Team Explorer,** scegliere Sincronizza per passare alla sezione Sincronizzazione e usare i comandi **Pull** e **Fetch** presentati qui.

## <a name="go-deeper"></a>Approfondimento

Per una breve procedura dettagliata sulla creazione di un progetto da un repository Git remoto, vedere Guida introduttiva: Clonare un repository di codice [Python in Visual Studio](quickstart-03-python-in-visual-studio-project-from-repository.md).

Per un'esercitazione molto più completa, comprendente la gestione dei conflitti di unione, la revisione di codice con richieste pull, la riassegnazione e il cherry-pick delle modifiche tra rami, vedere [Get started with Git and Azure Repos](/azure/devops/repos/git/gitquickstart) (Introduzione a Git e Azure Repos).

## <a name="tutorial-review"></a>Revisione dell'esercitazione

È stata completata questa esercitazione di Python in Visual Studio. In questa esercitazione si è appreso come:

- Creare progetti e visualizzare il contenuto di un progetto.
- Usare l'editor di codice ed eseguire un progetto.
- Usare la finestra **interattiva** per sviluppare il nuovo codice e copiare facilmente il codice nell'editor.
- Eseguire un programma nel debugger di Visual Studio.
- Installare pacchetti e gestire gli ambienti Python.
- Usare il codice in un repository Git.

Da qui è possibile esaminare i concetti e le procedure dettagliate, inclusi gli articoli seguenti:

- [Creare un'estensione C++ per Python](working-with-c-cpp-python-in-visual-studio.md)
- [Eseguire la pubblicazione nel servizio app di Azure](publishing-python-web-applications-to-azure-from-visual-studio.md)
- [Profilatura](profiling-python-code-in-visual-studio.md)
- [Testing unità](unit-testing-python-in-visual-studio.md)
