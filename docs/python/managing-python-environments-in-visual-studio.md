---
title: Gestire gli ambienti e gli interpreti Python
description: Usare la finestra Ambienti Python per gestire ambienti globali, virtuali e Conda, installare pacchetti e interpreti Python e assegnare gli ambienti ai progetti di Visual Studio.
ms.date: 07/23/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: bb2a93ae9c05bef49551e3dd3fa6d68d998e09ec
ms.sourcegitcommit: 56ae5032d99d948aae0548ae318ca2bae97ea962
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/07/2018
ms.locfileid: "39586579"
---
# <a name="how-to-create-and-manage-python-environments-in-visual-studio"></a>Come creare e gestire gli ambienti Python in Visual Studio

Un *ambiente* Python è un contesto in cui eseguire il codice Python e include gli ambienti globale, virtuale e Conda. Un ambiente è costituito da un interprete, una libreria (in genere quella standard Python) e un set di pacchetti installati. Questi componenti nel loro insieme determinano la sintassi e i costrutti di linguaggio validi, le funzionalità accessibili del sistema operativo e i pacchetti che è possibile usare.

In Visual Studio in Windows, la finestra [**Ambienti Python**](#the-python-environments-window), descritta in questo articolo, è la posizione in cui si gestiscono questi ambienti e se ne seleziona uno come predefinito per i nuovi progetti. Per ogni progetto, è anche possibile [selezionare un ambiente specifico](selecting-a-python-environment-for-a-project.md) anziché usare quello predefinito.

>[!NOTE]
>Se non si ha familiarità con Python in Visual Studio, vedere gli articoli seguenti per raccogliere le informazioni di base necessarie:
>
>- [Usare Python in Visual Studio](overview-of-python-tools-for-visual-studio.md)
>- [Come installare il supporto di Python in Visual Studio](installing-python-support-in-visual-studio.md)

Si noti anche che non è possibile gestire gli ambienti per il codice Python aperto solo come cartella tramite il comando **File** > **Apri** > **Cartella**. In alternativa, [creare un progetto Python da codice esistente](quickstart-01-python-in-visual-studio-project-from-existing-code.md) per sfruttare le funzionalità dell'ambiente di Visual Studio.

Per installare i pacchetti in un ambiente, vedere le [informazioni di riferimento sulla scheda Pacchetti](python-environments-window-tab-reference.md#packages-tab).

## <a name="types-of-environments"></a>Tipi di ambienti

### <a name="global-environments"></a>Ambienti globali

Ogni installazione di Python (ad esempio Python 2.7, Python 3.6, Anaconda 4.4.0 e così via, vedere [Installare interpreti Python](installing-python-interpreters.md)) mantiene il proprio ambiente globale. Ogni ambiente è costituito dall'interprete Python specifico e dalla relativa libreria standard, oltre a un set di pacchetti preinstallati. L'installazione di un pacchetto in un ambiente globale lo rende disponibile per tutti i progetti che usano tale ambiente. Se l'ambiente si trova in un'area protetta del file system, ad esempio in *c:\program files*, per l'installazione dei pacchetti sono richiesti privilegi di amministratore.

Gli ambienti globali sono disponibili per tutti i progetti nel computer. In Visual Studio si seleziona un ambiente globale come predefinito e tale ambiente viene usato per tutti i progetti a meno che non se ne scelga in modo specifico un altro per un progetto. Per altre informazioni, vedere [Selezionare un ambiente per un progetto](selecting-a-python-environment-for-a-project.md).

### <a name="virtual-environments"></a>Ambienti virtuali

Dal momento che i pacchetti installati in un ambiente globale sono disponibili per tutti i progetti che usano tale ambiente, possono verificarsi conflitti quando due progetti richiedono pacchetti non compatibili o versioni diverse dello stesso pacchetto. Gli ambienti virtuali consentono di evitare questi conflitti usando l'interprete e la libreria standard da un ambiente globale, ma mantenendo gli archivi dei pacchetti in cartelle isolate.

In Visual Studio è possibile creare un ambiente virtuale per un progetto specifico, che viene archiviato in una sottocartella del progetto. Visual Studio offre un comando che consente di generare un file *c:\program files* dall'ambiente virtuale, rendendo più semplice ricreare l'ambiente in altri computer. Per altre informazioni, vedere [Uso di ambienti virtuali](selecting-a-python-environment-for-a-project.md#use-virtual-environments).

### <a name="conda-environments"></a>Ambienti Conda

Un ambiente Conda è un ambiente creato usando lo strumento `conda` o con la gestione Conda integrata in Visual Studio 2017 15.7 e versioni successive. (Richiede Anaconda o Miniconda; Anaconda è disponibile tramite il programma di installazione di Visual Studio, vedere [Installazione - Visual Studio 2017](installing-python-support-in-visual-studio.md#visual-studio-2017).)

> [!Note]
> Per ottenere risultati ottimali con gli ambienti Conda, usare Conda 4.4.8 o versione successiva (le versioni Conda sono diverse rispetto alle versioni Anaconda). Installare Anaconda 5.1 dal programma di installazione di Visual Studio 2017.

Per visualizzare la versione Conda, in cui sono archiviati gli ambienti Conda, e altre informazioni, eseguire `conda info` a un prompt dei comandi Anaconda (ovvero, un prompt dei comandi nel percorso in cui è presente Anaconda):

```cli
conda info
```

Le cartelle di ambiente Conda vengono visualizzate come segue:

```output
       envs directories : c:\anaconda3\envs
                          C:\Users\user\AppData\Local\conda\conda\envs
                          C:\Users\user\.conda\envs
```

Poiché gli ambienti Conda non sono archiviati con un progetto, agiscono in modo analogo agli ambienti globali. Ad esempio, l'installazione di un nuovo pacchetto in un ambiente Conda lo rende disponibile per tutti i progetti che usano tale ambiente.

Per Visual Studio 2017 15.6 e versioni precedenti, è possibile usare ambienti Conda puntando a essi manualmente come descritto in [Identificare manualmente un ambiente esistente](#manually-identify-an-existing-environment).

Visual Studio 2017 15.7 e versioni successive rileva automaticamente gli ambienti Conda e li visualizza nella finestra **Ambienti Python** come descritto nella sezione successiva.

## <a name="the-python-environments-window"></a>Finestra Ambienti Python

Gli ambienti rilevati da Visual Studio vengono visualizzati nella finestra **Ambienti Python**. Per aprire la finestra, usare uno dei metodi seguenti:

- Selezionare il comando di menu **Visualizza** > **Altre finestre** > **Ambienti Python**.
- Fare clic con il pulsante destro del mouse sul nodo **Ambienti Python** per un progetto in **Esplora soluzioni** e scegliere **Visualizza tutti gli ambienti Python**:

    ![Comando Visualizza tutti gli ambienti Python in Esplora soluzioni](media/environments-view-all.png)

In entrambi i casi, la finestra **Ambienti Python** viene visualizzata come una scheda di pari livello in **Esplora soluzioni**:

![Finestra Ambienti Python](media/environments-default-view.png)

Visual Studio segue [PEP 514](https://www.python.org/dev/peps/pep-0514/) per identificare gli ambienti installati usando il Registro di sistema. Se l'elenco non include un ambiente previsto, vedere [Identificare manualmente un ambiente esistente](#manually-identify-an-existing-environment).

La selezione di un ambiente nell'elenco determina la visualizzazione di vari comandi e proprietà per l'ambiente nella scheda **Panoramica**. Nell'immagine precedente si può ad esempio vedere che il percorso dell'interprete è *C:\Python36-32*. Usare l'elenco a discesa disponibile sotto l'elenco degli ambienti per spostarsi tra le diverse schede, ad esempio **Pacchetti** e **IntelliSense**. Queste schede sono descritte in [Informazioni di riferimento sulle schede della finestra Ambienti Python](python-environments-window-tab-reference.md).

La selezione di un ambiente non ne determina l'attivazione in alcun modo. L'ambiente predefinito, visualizzato in grassetto nell'elenco, è l'ambiente attualmente attivato che Visual Studio usa per i nuovi progetti. Per attivare un ambiente diverso, usare il comando **Imposta come ambiente predefinito per i nuovi progetti**. Nel contesto di un progetto è sempre possibile attivare un ambiente diverso. Per altre informazioni, vedere [Selezionare un ambiente per un progetto](selecting-a-python-environment-for-a-project.md).

A destra di ogni ambiente elencato è disponibile un controllo che consente di aprire una finestra **interattiva** per tale ambiente. (In Visual Studio 2017 15.5 e versioni precedenti potrebbe essere visualizzato un altro controllo che aggiorna il database di IntelliSense per tale ambiente. Vedere [Informazioni di riferimento sulle schede della finestra Ambienti](python-environments-window-tab-reference.md#intellisense-tab) per informazioni dettagliate sul database.)

> [!Tip]
> Se si espande a sufficienza la finestra **Ambienti Python**, si otterrà una visualizzazione più completa degli ambienti che può risultare più comoda.
>
> ![Visualizzazione espansa della finestra Ambienti Python](media/environments-expanded-view.png)

> [!Note]
> Anche se Visual Studio rispetta l'opzione dei pacchetti dei siti di sistema, non consente di modificarla da Visual Studio.

|   |   |
|---|---|
| ![icona della telecamera](../install/media/video-icon.png "Guardare un video") | [Guardare un video (Microsoft Virtual Academy)](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=qrDmN4LWE_8305918567) sugli ambienti Python in Visual Studio (2m 35s).|

### <a name="what-if-no-environments-appear"></a>Se non viene visualizzato alcun ambiente

Se non viene visualizzato alcun ambiente, significa che Visual Studio non è riuscito a rilevare installazioni di Python nelle posizioni standard. È possibile, ad esempio, avere installato Visual Studio 2017 con tutte le opzioni per l'interprete deselezionate nelle opzioni del programma di installazione per il carico di lavoro di Python. Analogamente, è possibile che sia installato Visual Studio 2015 o versione precedente, ma che non sia stato installato manualmente un interprete. Vedere [Installare interpreti Python](installing-python-interpreters.md).

Se si è certi di disporre di un interprete Python nel computer in uso, ma Visual Studio (qualsiasi versione) non lo rileva, usare il comando **+ Personalizzato** per specificarne il percorso manualmente. Vedere la sezione successiva, [Identificare manualmente un ambiente esistente](#manually-identify-an-existing-environment).

> [!Tip]
> Visual Studio rileva gli aggiornamenti per un interprete esistente, ad esempio l'aggiornamento di Python 2.7.11 a 2.7.14 tramite i programmi di installazione da python.org. Durante il processo di installazione, l'ambiente precedente scompare dall'elenco **Ambienti Python** prima che venga visualizzato l'aggiornamento nella posizione prevista.
>
> Tuttavia, se si sposta manualmente un interprete e il relativo ambiente tramite il file system, Visual Studio non conosce il nuovo percorso. Per altre informazioni, vedere [Spostare un interprete](installing-python-interpreters.md#move-an-interpreter).

## <a name="fix-or-delete-invalid-environments"></a>Correggere o eliminare gli ambienti non validi

Se per un ambiente Visual Studio rileva voci del Registro di sistema, ma il percorso all'interprete non è valido, nella finestra **Ambienti Python** il nome viene visualizzato barrato:

![Finestra Ambienti Python con ambiente non valido visualizzato](media/environments-invalid-entry.png)

Per correggere un ambiente che si vuole mantenere, provare prima a usare il processo di **riparazione** del programma di installazione. Ad esempio, i programmi di installazione per la versione Python 3.x standard includono tale opzione.

Per correggere un ambiente che non dispone di un'opzione di riparazione o per rimuovere un ambiente non valido, usare la procedura seguente per modificare direttamente il Registro di sistema. Visual Studio aggiorna automaticamente la finestra **Ambienti Python** dopo aver apportato le modifiche al Registro di sistema.

1. Eseguire *regedit.exe*.
1. Passare a **HKEY_LOCAL_MACHINE\SOFTWARE\Python** per gli interpreti 32 bit o a **HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Python** per gli interpreti a 64 bit. Per IronPython, cercare invece **IronPython**.
1. Espandere il nodo che corrisponde alla distribuzione, ad esempio **PythonCore** per CPython o **ContinuumAnalytics** per Anaconda. Per IronPython, espandere il nodo del numero di versione.
1. Controllare i valori nel nodo **InstallPath**:

    ![Voci del Registro di sistema per una tipica installazione CPython](media/environments-registry-entries.png)

    - Se l'ambiente è ancora presente nel computer, modificare il valore di **ExecutablePath** nella posizione corretta. Correggere anche i valori **(Predefinito)** e **WindowedExecutablePath** in base alle esigenze.
    - Se l'ambiente non è più presente nel computer e si vuole rimuoverlo dalla finestra **Ambienti Python**, eliminare il nodo padre di **InstallPath**, ad esempio **3.6** nell'immagine precedente.

## <a name="manually-identify-an-existing-environment"></a>Identificare manualmente un ambiente esistente

Usare questa procedura per identificare un ambiente installato in un percorso non standard, inclusi gli ambienti Conda in Visual Studio 2017 versione 15.6 e precedenti:

1. Selezionare **+ Personalizzato** nella finestra **Ambienti Python**. Verrà aperta la scheda **Configura**:

    ![Visualizzazione predefinita per un nuovo ambiente personalizzato](media/environments-custom-1.png)

1. Immettere un nome per l'ambiente nel campo **Descrizione**.

1. Immettere o selezionare (tramite **...**) il percorso dell'interprete nel campo **Percorso di prefisso**.

1. Se Visual Studio rileva un interprete Python nel percorso specificato, ad esempio il percorso illustrato di seguito per un ambiente Conda, viene abilitato il comando **Rilevamento automatico**. Selezionando **Rilevamento automatico** vengono compilati i restanti campi. È anche possibile compilare manualmente questi campi.

    ![Abilitazione del comando Rilevamento automatico](media/environments-custom-2.png)

    ![Completamento dei campi di ambiente dopo l'uso di Rilevamento automatico](media/environments-custom-3.png)

1. Quando i campi contengono i valori desiderati, selezionare **Applica** per salvare la configurazione. È ora possibile usare l'ambiente come qualsiasi altro all'interno di Visual Studio.

1. Se è necessario rimuovere un ambiente identificato manualmente, selezionare il comando **Rimuovi** nella scheda **Configura**. Gli ambienti rilevati automaticamente non offrono questa opzione. Per altre informazioni, vedere [Scheda Configura](python-environments-window-tab-reference.md#configure-tab).

## <a name="create-a-conda-environment"></a>Creare un ambiente Conda

*Visual Studio 2017 15.7 e versioni successive.*

1. Selezionare **+ Crea ambiente Conda** nella finestra **Ambienti Python**. Verrà aperta una scheda **Crea nuovo ambiente Conda**:

    ![Scheda per la creazione di un nuovo ambiente Conda](media/environments-conda-1.png)

1. Immettere un nome per l'ambiente nel campo **Nome**, selezionare un interprete Python di base nel campo **Python** e selezionare **Crea**.

1. Nella finestra **Output** viene visualizzato lo stato di avanzamento per il nuovo ambiente, con alcune istruzioni dell'interfaccia della linea di comando al termine della creazione:

    ![Creazione completata correttamente di un ambiente Conda](media/environments-conda-2.png)

1. All'interno di Visual Studio è possibile attivare un ambiente Conda per un progetto come per qualsiasi altro ambiente come descritto in [Selezionare un ambiente per un progetto](selecting-a-python-environment-for-a-project.md).

1. Per installare i pacchetti nell'ambiente, usare la [scheda Pacchetti](python-environments-window-tab-reference.md#packages-tab).

## <a name="see-also"></a>Vedere anche

- [Installare interpreti Python](installing-python-interpreters.md)
- [Selezionare un interprete per un progetto](selecting-a-python-environment-for-a-project.md)
- [Usare requirements.txt per le dipendenze](managing-required-packages-with-requirements-txt.md)
- [Percorsi di ricerca](search-paths.md)
- [Informazioni di riferimento sulla finestra Ambienti Python](python-environments-window-tab-reference.md)
