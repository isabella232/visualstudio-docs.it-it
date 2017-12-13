---
title: Installazione per Python in Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 09/22/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "11"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: 066612a132bf6a092771afd5fc4a876d4b3be425
ms.sourcegitcommit: b7d3b90d0be597c9d01879338dd2678c881087ce
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/01/2017
---
# <a name="installing-python-support-in-visual-studio-on-windows"></a>Installazione del supporto di Python in Visual Studio in Windows

Per installare il supporto Python per Visual Studio, seguire le istruzioni nella sezione corrispondente alla versione in uso di Visual Studio:

- [Visual Studio 2017](#visual-studio-2017)
- [Visual Studio 2015](#visual-studio-2015)
- [Visual Studio 2013 e versioni precedenti](#visual-studio-2013-and-earlier)

Per Visual Studio 2015 e versioni precedenti è anche necessario installare separatamente un interprete Python a scelta. Installare Python 3.5 e versioni precedenti; Python 3.6 non è supportato. Per informazioni dettagliate, vedere [Ambienti Python](python-environments.md). Nella stessa pagina sono contenute anche le istruzioni per l'aggiunta di un interprete Python esistente in Visual Studio 2017.

Per testare rapidamente il supporto Python dopo aver eseguito la procedura di installazione, aprire la finestra interattiva di Python premendo ALT+I e quindi immettere `2+2`. Se non viene visualizzato l'output `4`, eseguire nuovamente la procedura.

> [!Tip]
> Il carico di lavoro Python include l'utile estensione Cookiecutter, che offre un'interfaccia utente grafica per individuare modelli, inserire opzioni del modello e creare progetti e file. Per informazioni dettagliate, vedere [Uso dell'estensione Cookiecutter](cookiecutter.md).

> [!Note]
> Il supporto Python non è attualmente disponibile in Visual Studio per Mac, ma viene offerto su Mac e Linux tramite Visual Studio Code. Vedere [Domande e risposte](python-in-visual-studio.md#questions-and-answers).

## <a name="visual-studio-2017"></a>Visual Studio 2017

1. Scaricare ed eseguire il programma di installazione più recente di Visual Studio 2017:

    > [!div class="nextstepaction"]
    > <a target="frameTarget" href="https://www.visualstudio.com/thank-you-downloading-visual-studio/?sku=Community&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_install">Installare Visual Studio 2017 Community</a>

    >[!Tip]
    > L'edizione Community è per singoli sviluppatori, per la formazione in classe, la ricerca accademica e per lo sviluppo open source. Per altri usi, installare <a target="frameTarget" href="https://www.visualstudio.com/thank-you-downloading-visual-studio/?sku=Professional&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_install">Visual Studio 2017 Professional</a> oppure <a target="frameTarget" href="https://www.visualstudio.com/thank-you-downloading-visual-studio/?sku=Enterprise&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_install">Visual Studio 2017 Enterprise</a>.

1. Il programma di installazione offre un elenco di carichi di lavoro, che sono gruppi di opzioni correlate per aree di sviluppo specifico. Per Python, selezionare il carico di lavoro **Sviluppo Python**.

    ![Carico di lavoro Sviluppo Python nel programma di installazione di Visual Studio](media/installation-python-workload.png)

    Facoltativo: se si usa l'analisi scientifica dei dati, valutare la possibilità di installare il carico di lavoro **Applicazioni analitiche e di analisi scientifica dei dati**. Questo carico di lavoro include il supporto per Python, nonché per i linguaggi R e F#. Per altre informazioni, vedere [Carico di lavoro relativo alle applicazioni analitiche e di analisi scientifica dei dati](../rtvs/data-science-workload.md).

    > [!Note]
    > I carichi di lavoro di Python e di analisi scientifica dei dati sono disponibili solo con la versione di Visual Studio 2017 15.2 e versioni successive.

1. Sul lato destro del programma di installazione è possibile scegliere le opzioni aggiuntive. Ignorare il passaggio per accettare le opzioni predefinite.

    ![Opzioni di sviluppo Python nel programma di installazione di Visual Studio](media/installation-python-options.png)

    | Opzione | Descrizione | 
    | --- | --- |
    | Distribuzioni di Python | Scegliere qualsiasi combinazione delle varianti a 32 e 64 bit delle distribuzioni di Python 2, Python 3, Anaconda2 e Anaconda3 che si intende usare. Ogni combinazione include interprete di distribuzione, runtime e librerie. Anaconda, in particolare, è una piattaforma aperta di analisi scientifica dei dati che include una vasta gamma di pacchetti. È possibile tornare al programma di installazione di Visual Studio in qualsiasi momento per aggiungere o rimuovere le distribuzioni. |
    | Supporto modello Cookiecutter | Installa l'interfaccia utente di Cookiecutter per individuare modelli, inserire opzioni di modello e creare progetti e file. Vedere [Uso dell'estensione Cookicutter](cookiecutter.md). |
    | Supporto Web Python | Installa gli strumenti per lo sviluppo Web, tra cui il supporto per HTML, CSS e JavaScript, oltre ai modelli per i progetti usando i framework Bottle, Flask e Django. Vedere [Modelli di progetti Web Python](template-web.md). |
    | Supporto Python IoT | Supporta lo sviluppo di Windows IoT Core usando Python. |
    | Strumenti di sviluppo nativo Python | Installa il compilatore C++ e altri componenti necessari per sviluppare estensioni native per Python. Vedere [Creazione di un'estensione C++ per Python](cpp-and-python.md). |
    | Strumenti di base di Servizi cloud di Azure | Offre supporto aggiuntivo per sviluppare servizi cloud di Microsoft Azure in Python. Vedere [Progetti servizio cloud di Azure per Python](template-azure-cloud-service.md). |

1. Al termine dell'operazione, il programma di installazione specifica le opzioni per modificare, avviare, ripristinare o disinstallare Visual Studio. Il pulsante **Modifica** diventa **Aggiorna** quando sono disponibili aggiornamenti di Visual Studio per i componenti installati. L'opzione di modifica diventa disponibile nel menu a discesa. È anche possibile avviare Visual Studio e il programma di installazione dal menu Start di Windows eseguendo una ricerca su "Visual Studio".

    ![Avvio, modifica, modifica o disinstallazione di Visual Studio dal programma di installazione](media/installation-vs-launch.png)


> [!VIDEO https://mva.microsoft.com/en-US/training-courses-embed/python-tools-for-visual-studio-2017-18121/Video-Installing-Visual-Studio-Python-Support-go1id3LWE_1705918567]

## <a name="visual-studio-2015"></a>Visual Studio 2015

1. Per eseguire il programma di installazione di Visual Studio, scegliere **Pannello di controllo > Programmi e funzionalità**, selezionare **Microsoft Visual Studio 2015** e quindi **Cambia**.

1. Nel programma di installazione selezionare **Modifica**.

1. Selezionare **Linguaggi di programmazione > Python Tools for Visual Studio** e quindi **Avanti**:

    ![Opzione PTVS nel programma di installazione di Visual Studio 2015](media/installation-vs2015.png)    

1. Una volta completata l'installazione di Visual Studio, [installare un interprete Python a scelta](python-environments.md#selecting-and-installing-python-interpreters). Se è già installato un interprete, vedere [Creazione di un ambiente per un interprete esistente](python-environments.md#creating-an-environment-for-an-existing-interpreter).

## <a name="visual-studio-2013-and-earlier"></a>Visual Studio 2013 e versioni precedenti

1. Installare la versione appropriata di Python Tools for Visual Studio per la versione in uso di Visual Studio:

    - Visual Studio 2013: [PTVS 2.2 for Visual Studio 2013](https://github.com/Microsoft/PTVS/releases/v2.2). È possibile accedere rapidamente a questo processo dalla finestra di dialogo **File > Nuovo progetto** di Visual Studio 2013.
    - Visual Studio 2012: [PTVS 2.1 for Visual Studio 2012](https://pytools.codeplex.com/downloads/get/920478)
    - Visual Studio 2010: [PTVS 2.1 for Visual Studio 2010](https://pytools.codeplex.com/downloads/get/920479)

1. [Installare un interprete Python a scelta](python-environments.md#selecting-and-installing-python-interpreters). Se è già installato un interprete, vedere [Creazione di un ambiente per un interprete esistente](python-environments.md#creating-an-environment-for-an-existing-interpreter).

## <a name="install-locations"></a>Percorsi di installazione

Per impostazione predefinita, il supporto Python viene installato per tutti gli utenti di un computer.

Per Visual Studio 2017, il carico di lavoro Python è installato in `%ProgramFiles(x86)%\Microsoft Visual Studio\2017\<VS_edition>Common7\IDE\Extensions\Microsoft\Python`, dove &lt;VS_edition&gt; corrisponde a Community, Professional o Enterprise.

Per Visual Studio 2015 e versioni precedenti, i percorsi di installazione sono i seguenti:

- 32 bit:
  - Percorso: `%Program Files(x86)%\Microsoft Visual Studio <VS_ver>\Common7\IDE\Extensions\Microsoft\Python Tools for Visual Studio\<PTVS_ver>`
  - Chiave del Registro di sistema relativa al percorso: `HKEY_LOCAL_MACHINE\Software\Microsoft\PythonTools\<VS_ver>\InstallDir`
- 64 bit:
  - Percorso: `%Program Files%\Microsoft Visual Studio <VS_ver>\Common7\IDE\Extensions\Microsoft\Python Tools for Visual Studio\<PTVS_ver>`
  - Chiave del Registro di sistema relativa al percorso: `HKEY_LOCAL_MACHINE\Software\Wow6432Node\Microsoft\PythonTools\<VS_ver>\InstallDir`

dove:

- &lt;VS_ver&gt; corrisponde a:    
    - 14.0 per Visual Studio 2015
    - 12.0 per Visual Studio 2013
    - 11.0 per Visual Studio 2012
    - 10.0 per Visual Studio 2010
- &lt;PTVS_ver&gt; corrisponde a un numero di versione, ad esempio 2.2, 2.1, 2.0, 1.5, 1.1 o 1.0.

### <a name="user-specific-installations-15-and-earlier"></a>Installazioni specifiche dell'utente (versione 1.5 e versioni precedenti)

Con Python Tools for Visual Studio 1.5 e versioni precedenti è consentita l'installazione solo per l'utente corrente. In tal caso, il percorso di installazione è `%LocalAppData%\Microsoft\VisualStudio\<VS_ver>\Extensions\Microsoft\Python Tools for Visual Studio\<PTVS_ver>` dove i valori di &lt;VS_ver&gt; e &lt;PTVS_ver&gt; sono uguali a quelli descritti in precedenza.

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
