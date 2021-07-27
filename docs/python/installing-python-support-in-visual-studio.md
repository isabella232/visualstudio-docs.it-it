---
title: Installare il supporto Python
description: Procedura relativa all'installazione di Python Tools for Visual Studio (PTVS) in Visual Studio 2017, 2015, 2013, 2012 e 2010, inclusi le opzioni e i percorsi di installazione.
ms.date: 03/13/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: d5a357cf2a2da1fee747d777d02aae146d97bd7b
ms.sourcegitcommit: 3c5b1a1d51b521356f42a6879c1f1745573dda65
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/23/2021
ms.locfileid: "114591917"
---
# <a name="how-to-install-python-support-in-visual-studio-on-windows"></a>Come installare il supporto di Python in Visual Studio in Windows

Per installare il supporto Python per Visual Studio (noto anche come Python Tools for Visual Studio o PTVS), seguire le istruzioni nella sezione corrispondente alla versione in uso di Visual Studio:

- [Visual Studio 2017 e Visual Studio 2019](#visual-studio-2017-and-2019)
- [Visual Studio 2015](#visual-studio-2015)
- [Visual Studio 2013 e versioni precedenti](#visual-studio-2013-and-earlier)

Per testare rapidamente il supporto di Python dopo aver seguito i passaggi di installazione, aprire la **finestra Interattiva** di Python premendo **ALT** + **I** e immettendo `2+2` . Se non viene visualizzato l'output `4`, eseguire nuovamente la procedura.

> [!Tip]
> Il carico di lavoro Python include l'utile estensione Cookiecutter, che offre un'interfaccia utente grafica per individuare modelli, inserire opzioni del modello e creare progetti e file. Per informazioni dettagliate, vedere [Usare l'estensione Cookiecutter](using-python-cookiecutter-templates.md).

> [!Note]
> Il supporto Python non è attualmente disponibile in Visual Studio per Mac, ma viene offerto su Mac e Linux tramite Visual Studio Code. Vedere le [domande e risposte](overview-of-python-tools-for-visual-studio.md#questions-and-answers).

<a name="visual-studio-2017-and-2019"></a>
## <a name="visual-studio-2019-and-visual-studio-2017"></a>Visual Studio 2019 e Visual Studio 2017

1. Scaricare ed eseguire il programma di installazione più recente di Visual Studio. Se Visual Studio è già installato, eseguire il programma di installazione di Visual Studio, selezionare l'opzione **Modifica** (vedere [Modificare Visual Studio](../install/modify-visual-studio.md)) e andare al passaggio 2.

    > [!div class="nextstepaction"]
    > [Installare Visual Studio 2019 Community](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Community&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted)

    >[!Tip]
    > L'edizione Community è per singoli sviluppatori, per la formazione in classe, la ricerca accademica e per lo sviluppo open source. Per altri usi, installare [Visual Studio 2019 Professional](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Professional&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted) oppure [Visual Studio 2019 Enterprise](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Enterprise&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted).

1. Il programma di installazione offre un elenco di carichi di lavoro, che sono gruppi di opzioni correlate per aree di sviluppo specifico. Per Python, selezionare il carico di lavoro **Sviluppo Python**.

    ![Carico di lavoro Sviluppo Python nel programma di installazione di Visual Studio](media/installation-python-workload.png)

    ::: moniker range="vs-2017"
    Facoltativo: se si usa l'analisi scientifica dei dati, valutare la possibilità di installare il carico di lavoro **Applicazioni analitiche e di analisi scientifica dei dati**. Questo carico di lavoro include il supporto per i linguaggi Python, R e F#. Per altre informazioni, vedere [Carico di lavoro relativo alle applicazioni analitiche e di analisi scientifica dei dati](data-science-and-analytical-applications-workload.md).

    > [!Note]
    > I carichi di lavoro di Python e di analisi scientifica dei dati sono disponibili solo con la versione di Visual Studio 2017 versione 15.2 e successive.

    ::: moniker-end

    ::: moniker range=">=vs-2019"
    Facoltativo: se si usa l'analisi scientifica dei dati, valutare la possibilità di installare il carico di lavoro **Applicazioni analitiche e di analisi scientifica dei dati**. Questo carico di lavoro include il supporto per i linguaggi Python e F#. Per altre informazioni, vedere [Carico di lavoro relativo alle applicazioni analitiche e di analisi scientifica dei dati](data-science-and-analytical-applications-workload.md).
    ::: moniker-end

1. Sul lato destro del programma di installazione è possibile scegliere le opzioni aggiuntive. Ignorare il passaggio per accettare le opzioni predefinite.

    ::: moniker range="vs-2017"
    ![Opzioni di sviluppo Python nel programma di installazione di Visual Studio](media/installation-python-options.png)
    ::: moniker-end

    ::: moniker range=">=vs-2019"
    ![Opzioni di sviluppo Python nel programma di installazione di Visual Studio 2019](media/installation-python-options-2019.png)
    ::: moniker-end

    ::: moniker range="<=vs-2017"
    | Opzione | Descrizione |
    | --- | --- |
    | Distribuzioni di Python | Scegliere qualsiasi combinazione delle opzioni disponibili, ad esempio le varianti a 32 e 64 bit delle distribuzioni di Python 2, Python 3, Miniconda, Anaconda2 e Anaconda3 che si intende usare. Ogni combinazione include interprete di distribuzione, runtime e librerie. Anaconda, in particolare, è una piattaforma aperta di data science che include una vasta gamma di pacchetti pre-installati. È possibile tornare al programma di Visual Studio in qualsiasi momento per aggiungere o rimuovere distribuzioni.  **Nota:** se è stata installata una distribuzione all'esterno del programma di Visual Studio, non è necessario selezionare l'opzione equivalente qui. Visual Studio rileva automaticamente le installazioni esistenti di Python. Vedere [Finestra Ambienti Python](managing-python-environments-in-visual-studio.md#the-python-environments-window). Inoltre, se è disponibile una versione di Python più recente rispetto a quella indicata nel programma di installazione, è possibile installare tale versione separatamente e Visual Studio la rileverà. |
    | **Supporto modello Cookiecutter** | Installa l'interfaccia utente di Cookiecutter per individuare modelli, inserire opzioni di modello e creare progetti e file. Vedere [Usare l'estensione Cookiecutter](using-python-cookiecutter-templates.md). |
    | **Supporto Web Python** | Installa gli strumenti per lo sviluppo Web, tra cui il supporto per HTML, CSS e JavaScript, oltre ai modelli per i progetti usando i framework Bottle, Flask e Django. Vedere [Modelli di progetti Web Python](python-web-application-project-templates.md). |
    | **Supporto Python IoT** | Supporta lo sviluppo di Windows IoT Core usando Python. |
    | **Strumenti di sviluppo nativo Python** | Installa il compilatore C++ e altri componenti necessari per sviluppare estensioni native per Python. Vedere [Creare un'estensione C++ per Python](working-with-c-cpp-python-in-visual-studio.md). Installare anche il carico di lavoro **Sviluppo di applicazioni desktop con C++** per il supporto completo di C++. |

    ::: moniker-end

    ::: moniker range=">=vs-2019"
    | Opzione | Descrizione |
    | --- | --- |
    | Distribuzioni di Python | Scegliere qualsiasi combinazione delle opzioni disponibili, ad esempio le varianti a 32 e 64 bit delle distribuzioni di Python 2, Python 3, Miniconda, Anaconda2 e Anaconda3 che si intende usare. Ogni combinazione include interprete di distribuzione, runtime e librerie. Anaconda, in particolare, è una piattaforma aperta di data science che include una vasta gamma di pacchetti pre-installati. È possibile tornare al programma di Visual Studio in qualsiasi momento per aggiungere o rimuovere distribuzioni.  **Nota:** se è stata installata una distribuzione all'esterno del programma di Visual Studio, non è necessario selezionare l'opzione equivalente qui. Visual Studio rileva automaticamente le installazioni esistenti di Python. Vedere [Finestra Ambienti Python](managing-python-environments-in-visual-studio.md#the-python-environments-window). Inoltre, se è disponibile una versione di Python più recente rispetto a quella indicata nel programma di installazione, è possibile installare tale versione separatamente e Visual Studio la rileverà. |
    | **Supporto modello Cookiecutter** | Installa l'interfaccia utente di Cookiecutter per individuare modelli, inserire opzioni di modello e creare progetti e file. Vedere [Usare l'estensione Cookiecutter](using-python-cookiecutter-templates.md). |
    | **Supporto Web Python** | Installa gli strumenti per lo sviluppo Web, tra cui il supporto per HTML, CSS e JavaScript, oltre ai modelli per i progetti usando i framework Bottle, Flask e Django. Vedere [Modelli di progetti Web Python](python-web-application-project-templates.md). |
    | **Strumenti di sviluppo nativo Python** | Installa il compilatore C++ e altri componenti necessari per sviluppare estensioni native per Python. Vedere [Creare un'estensione C++ per Python](working-with-c-cpp-python-in-visual-studio.md). Installare anche il carico di lavoro **Sviluppo di applicazioni desktop con C++** per il supporto completo di C++. |
    ::: moniker-end

1. Al termine dell'operazione, il programma di installazione specifica le opzioni per modificare, avviare, ripristinare o disinstallare Visual Studio. Il pulsante **Modifica** diventa **Aggiorna** quando sono disponibili aggiornamenti di Visual Studio per i componenti installati. **L'opzione** Modifica è quindi disponibile nel menu a discesa. È anche possibile avviare Visual Studio e il programma di installazione dal menu **Start** Windows selezionando "Visual Studio".

    ![Avvio, modifica, modifica o disinstallazione di Visual Studio dal programma di installazione](media/installation-vs-launch.png)

### <a name="troubleshooting"></a>Risoluzione dei problemi

Se si verificano problemi durante l'installazione o l'esecuzione di Python in Visual Studio, procedere come segue:

- Determinare se si verifica lo stesso errore usando l'interfaccia della riga di comando di Python, ovvero eseguendo *python.exe* al prompt dei comandi.
- Usare [**l'opzione**](../install/repair-visual-studio.md) Ripristina nel programma Visual Studio installazione.
- Ripristinare o reinstallare Python **tramite Impostazioni**  >  **app & funzionalità** in Windows.

**Errore di esempio**: Non è stato possibile avviare il processo interattivo: System.ComponentModel.Win32Exception (0x80004005): Errore sconosciuto (0xc0000135) in Microsoft.PythonTools.Repl.PythonInteractiveEvaluator.d__43.MoveNext().

## <a name="visual-studio-2015"></a>Visual Studio 2015

1. Per eseguire il programma di installazione di Visual Studio, scegliere **Pannello di controllo > Programmi e funzionalità**, selezionare **Microsoft Visual Studio 2015** e quindi **Cambia**.

1. Nel programma di installazione selezionare **Modifica**.

1. Selezionare **Linguaggi di**  >  **Python Tools for Visual Studio** e quindi **Avanti:**

    ![Opzione PTVS nel programma di installazione di Visual Studio 2015](media/installation-vs2015.png)

1. Una volta completata l'installazione di Visual Studio, [installare un interprete Python a scelta](installing-python-interpreters.md). Visual Studio 2015 supporta solo Python 3.5 e versioni precedenti. Nelle versioni successive viene generato un messaggio del tipo **Versione 3.6 di Python non supportata**. Se è già installato un interprete e Visual Studio non lo rileva automaticamente, vedere [Identificazione manuale di un ambiente esistente](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment).

## <a name="visual-studio-2013-and-earlier"></a>Visual Studio 2013 e versioni precedenti

1. Installare la versione appropriata di Python Tools for Visual Studio per la versione in uso di Visual Studio:

    - Visual Studio 2013: [PTVS 2.2.2 per Visual Studio 2013](https://github.com/Microsoft/PTVS/releases/v2.2.2). La **finestra**  >  **di dialogo Project** file in Visual Studio 2013 offre un collegamento per questo processo.
    - Visual Studio 2010 e 2012: [PTVS 2.1.1 per Visual Studio 2010 e 2012](https://github.com/Microsoft/PTVS/releases/v2.1.1)

1. [Installare un interprete Python a scelta](installing-python-interpreters.md). Se è già installato un interprete e Visual Studio non lo rileva automaticamente, vedere [Identificazione manuale di un ambiente esistente](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment).

## <a name="install-locations"></a>Percorsi di installazione

Per impostazione predefinita, il supporto Python viene installato per tutti gli utenti di un computer.

Per Visual Studio 2019 e Visual Studio 2017, il carico di lavoro Python è installato in *%ProgramFiles(x86)%\Microsoft Visual Studio\\<versione_VS>\\<edizione_VS>Common7\IDE\Extensions\Microsoft\Python* dove &lt;versione_VS&gt; è 2019 o 2017 ed &lt;edizione_VS&gt; è Community, Professional o Enterprise.

Per Visual Studio 2015 e versioni precedenti, i percorsi di installazione sono i seguenti:

- 32 bit:
  - Percorso: *%Programmi(x86)%\Microsoft Visual Studio \<VS_ver> \Common7\IDE\Extensions\Microsoft\Python Tools for Visual Studio \\<PTVS_ver>*
  - Posizione registro del percorso: **HKEY_LOCAL_MACHINE\Software\Microsoft\PythonTools\\<VS_ver>\InstallDir**
- 64 bit:
  - Percorso: *%Programmi%\Microsoft Visual Studio \<VS_ver> \Common7\IDE\Extensions\Microsoft\Python Tools for Visual Studio \\<PTVS_ver>*
  - Posizione registro del percorso: **HKEY_LOCAL_MACHINE\Software\Wow6432Node\Microsoft\PythonTools\\<VS_ver>\InstallDir**

dove:

- &lt;VS_ver&gt; corrisponde a:
  - 14.0 per Visual Studio 2015
  - 12.0 per Visual Studio 2013
  - 11.0 per Visual Studio 2012
  - 10.0 per Visual Studio 2010
- &lt;PTVS_ver è un numero di versione, ad esempio &gt; 2.2.2, 2.1.1, 2.0, 1.5, 1.1 o 1.0.

### <a name="user-specific-installations-15-and-earlier"></a>Installazioni specifiche dell'utente (versione 1.5 e versioni precedenti)

Con Python Tools for Visual Studio 1.5 e versioni precedenti è consentita l'installazione solo per l'utente corrente. In tal caso, il percorso di installazione è *%LocalAppData%\Microsoft\VisualStudio\\<VS_ver>\Extensions\Microsoft\Python Tools for Visual Studio\\<PTVS_ver>* dove i valori di &lt;VS_ver&gt; e &lt;PTVS_ver&gt; sono uguali a quelli descritti in precedenza.
