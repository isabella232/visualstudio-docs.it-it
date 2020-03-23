---
title: Informazioni di riferimento sulla finestra Ambienti Python
description: Dettagli su ognuna delle schede visualizzate nella finestra Ambienti Python in Visual Studio.
ms.date: 03/18/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 578f73aabfb8b5a4c8336c8611f634b8947c8885
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "79302770"
---
# <a name="python-environments-window-tabs-reference"></a>Informazioni di riferimento sulle schede della finestra Ambienti Python

Per aprire la finestra **Ambienti Python**:

- Selezionare il comando di menu **Visualizza** > **altri** > ambienti Windows**Python.**
- Fare clic con il pulsante destro del mouse sul nodo **Ambienti Python** per un progetto in **Esplora soluzioni** e selezionare **Visualizza tutti gli ambienti Python**.

Se si espande la finestra **Ambienti Python** abbastanza ampia, queste opzioni vengono visualizzate come schede, che potrebbe essere più comodo da usare. Per maggiore chiarezza, le schede in questo articolo sono visualizzate nella modalità espansa.

::: moniker range="vs-2017"
![Visualizzazione espansa della finestra Ambienti Python](media/environments/environments-expanded-view.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Visualizzazione espansa della finestra Ambienti Python](media/environments/environments-expanded-view-2019.png)
::: moniker-end

## <a name="overview-tab"></a>Scheda Panoramica

Include informazioni di base e comandi per l'ambiente:

::: moniker range="vs-2017"
![Scheda Panoramica di Ambienti Python](media/environments/environments-overview-tab.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Scheda Panoramica di Ambienti Python](media/environments/environments-overview-tab-2019.png)
::: moniker-end

| Comando | Descrizione |
| --- | --- |
| **Make this environment the default for new projects (Imposta questo ambiente come predefinito per i nuovi progetti)** | Imposta l'ambiente attivo, facendo sì che Visual Studio (2017 versione 15.5 e precedenti) non risponda per un breve periodo finché non viene caricato il database di IntelliSense. Gli ambienti che contengono molti pacchetti potrebbero non rispondere per un periodo più lungo. |
| **Visita il sito Web del server di distribuzione** | Apre un browser all'URL offerto dalla distribuzione di Python. Python 3.x, ad esempio, passa a python.org. |
| **Apri finestra interattiva** | Apre la [finestra (REPL) interattiva](python-interactive-repl-in-visual-studio.md) per questo ambiente all'interno di Visual Studio, applicando qualunque [script di avvio (vedere sotto)](#startup-scripts). |
| **Esplora gli script interattivi** | Vedere [Script di avvio](#startup-scripts). |
| **Usa la modalità interattiva IPython** | Quando è impostato, apre la finestra **interattiva** con IPython per impostazione predefinita. Vengono abilitati i tracciati inline e la sintassi IPython estesa, come `name?` per visualizzare la Guida e `!command` per i comandi della shell. Questa opzione è consigliata quando si usa una distribuzione Anaconda, perché richiede pacchetti aggiuntivi. Per altre informazioni, vedere [Usare IPython nella finestra interattiva](interactive-repl-ipython.md). |
| **Apri in PowerShell** | Avvia l'interprete in una finestra di comando di PowerShell. |
| (Collegamenti alla cartella e ai programmi) | Fornire un rapido accesso alla cartella di installazione dell'ambiente, all'interprete *python.exe* e all'interprete *pythonw.exe.* Il primo apre Esplora risorse, gli ultimi due aprono una finestra della console. |

### <a name="startup-scripts"></a>Script di avvio

Quando si usano le finestre interattive nel proprio flusso di lavoro quotidiano, è probabile sviluppare funzioni helper da usare regolarmente. Ad esempio, è possibile creare una funzione che apre un frame di dati in Excel e quindi salvare il codice come script di avvio in modo che sia sempre disponibile nella finestra **interattiva.**

Gli script di avvio contengono codice che la finestra **interattiva** carica ed esegue automaticamente, incluse le importazioni, le definizioni di funzione e letteralmente qualsiasi altra cosa. Tali script sono referenziati in due modi:

1. Quando si installa un ambiente, Visual Studio crea una cartella *Documenti, versione di Visual Studio \<>,Python Scripts\\\<>* in cui &lt;&gt; &lt;la versione&gt; è la versione di Visual Studio (ad esempio 2017 o 2019) e l'ambiente corrisponde al nome dell'ambiente. È possibile passare alla cartella specifica dell'ambiente con il comando **Esplora gli script interattivi**. Quando si avvia la finestra **Interattiva** per tale ambiente, vengono caricati ed eseguiti tutti i file con estensione *py* disponibili qui in ordine alfabetico.

1. Il controllo **Script** nella scheda **Strumenti** > **Opzioni** > **Python** > **Finestre interattive** (vedere [Opzioni delle finestre interattive](python-support-options-and-settings-in-visual-studio.md#interactive-windows-options)) è destinato a specificare una cartella aggiuntiva per gli script di avvio che vengono caricati ed eseguiti in tutti gli ambienti. Tuttavia, questa funzionalità non è attualmente operativa.

## <a name="configure-tab"></a>Scheda Configura

Se disponibile, la scheda **Configura** contiene i dettagli descritti nella tabella seguente. Se questa scheda non è presente, Visual Studio gestisce automaticamente tutti i dettagli.

::: moniker range="vs-2017"
![Scheda Configura di Ambienti Python](media/environments/environments-configure-tab.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Scheda Configura di Ambienti Python](media/environments/environments-configure-tab-2019.png)
::: moniker-end

| Campo | Descrizione |
| --- | --- |
| **Descrizione** | Nome da assegnare all'ambiente. |
| **Percorso di prefisso** | Percorso della cartella di base dell'interprete. Se si compila questo valore e si fa clic su **Rilevamento automatico**, Visual Studio prova a compilare automaticamente gli altri campi. |
| **Percorso dell'interprete** | Percorso del file eseguibile dell'interprete, costituito in genere dal percorso di prefisso seguito da **python.exe** |
| **Interprete con finestra** | Percorso del file eseguibile non di console, spesso costituito dal percorso di prefisso seguito da **pythonw.exe**. |
| **Percorso della libreria**<br/>(se disponibile) | Radice della libreria standard. Questo valore può essere ignorato se Visual Studio è in grado di richiedere un percorso più accurato all'interprete. |
| **Versione linguistica** | Selezionata dal menu a discesa. |
| **Architettura** | Normalmente rilevato e compilato automaticamente, altrimenti specifica **32-bit** o **64-bit**. |
| **Variabile di ambiente del percorso** | Variabile di ambiente usata dall'interprete per trovare i percorsi di ricerca. All'avvio di Python, Visual Studio modifica il valore della variabile in modo che contenga i percorsi di ricerca del progetto. In genere questa proprietà deve essere impostata su **PYTHONPATH**, ma alcuni interpreti usano un valore diverso. |

## <a name="packages-tab"></a>Scheda Pacchetti

*Denominata anche "pip" nelle versioni precedenti.*

Gestisce i pacchetti installati nell'ambiente tramite pip (scheda **Pacchetti (PyPI)**) o conda (scheda **Pacchetti (Conda)**, per gli ambienti Conda in Visual Studio 2017 versione 15.7 e successive). In questa scheda è anche possibile cercare e installare nuovi pacchetti, incluse le relative dipendenze.

I pacchetti già installati vengono visualizzati con controlli per aggiornare (freccia rivolta verso l'alto) e disinstallare (X in un cerchio) il pacchetto:

![Scheda Pacchetti della finestra Ambienti Python](media/environments/environments-pip-tab-controls.png)

Quando di immette un termine di ricerca viene filtrato l'elenco dei pacchetti installati e quello dei pacchetti che possono essere installati da PyPI.

::: moniker range="vs-2017"
![Scheda Pacchetti nella finestra Ambienti Python con la ricerca di "num"](media/environments/environments-pip-tab.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Scheda Pacchetti nella finestra Ambienti Python con la ricerca di "num"](media/environments/environments-pip-tab-2019.png)
::: moniker-end

Come illustrato nella figura precedente, i risultati della ricerca mostrano un numero di pacchetti corrispondenti al termine di ricerca. La prima voce dell'elenco, tuttavia, è un comando per l'esecuzione diretta di **pip install \<name>**. La scheda **Pacchetti (Conda)** visualizza invece **conda install \<name>**:

::: moniker range="vs-2017"
![Scheda Pacchetti (Conda) con un comando di installazione di Conda](media/environments/environments-conda-tab-install.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Scheda Pacchetti (Conda) con un comando di installazione di Conda](media/environments/environments-conda-tab-install-2019.png)
::: moniker-end

In entrambi i casi, è possibile personalizzare l'installazione aggiungendo gli argomenti nella casella di ricerca dopo il nome del pacchetto. Quando si includono gli argomenti, i risultati della ricerca mostrano **pip install** o **conda install** seguito dal contenuto della casella di ricerca:

::: moniker range="vs-2017"
![Uso degli argomenti nei comandi di installazione pip e conda](media/environments/environments-pip-tab-arguments.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Uso degli argomenti nei comandi di installazione pip e conda](media/environments/environments-pip-tab-arguments-2019.png)
::: moniker-end

L'installazione di un pacchetto crea sottocartelle all'interno della cartella *Lib* dell'ambiente nel file system. Se ad esempio Python 3.6 è installato in *c:\Python36*, i pacchetti vengono installati in *c:\Python36\Lib*. Se Anaconda3 è installato in *c:\Programmi\Anaconda3*, i pacchetti vengono installati in *c:\Programmi\Anaconda3\Lib*. Per gli ambienti Conda, i pacchetti vengono installati in tale cartella dell'ambiente.

### <a name="grant-administrator-privileges-for-package-install"></a>Concedere i privilegi di amministratore per l'installazione dei pacchetti

Durante l'installazione di pacchetti in un ambiente che si trova in un'area protetta del file system, ad esempio *c:\Programmi\Anaconda3\Lib*, Visual Studio deve eseguire `pip install` con privilegi elevati per consentire la creazione di sottocartelle di pacchetto. Quando è necessaria l'elevazione dei privilegi, Visual Studio visualizza il prompt, **potrebbe essere necessario disporre dei privilegi di amministratore per installare, aggiornare o rimuovere i pacchetti per questo ambiente:**

![Richiesta di elevazione dei privilegi per l'installazione del pacchetto](media/environments/environments-pip-elevate.png)

**Eleva ora** concede privilegi di amministratore per pip per un'unica operazione, subordinatamente anche a qualunque richiesta di permessi del sistema operativo. Se si seleziona Continua senza privilegi di **amministratore,** il pip non riesce quando si tenta di creare cartelle con output come **l'errore: impossibile creare 'C:'Programmi'Anaconda3'Lib'pacchetti-sito'png.py': Autorizzazione negata.**

Selezionando **Eleva sempre quando si installano o rimuovono pacchetti** si impedisce la visualizzazione della finestra di dialogo per l'ambiente in questione. Per visualizzare nuovamente la finestra **Tools** > di dialogo, vai a**Strumenti Opzioni** > **Python** > **Generale** e seleziona il pulsante Reimposta tutte le finestre di **dialogo nascoste in modo permanente**.

Nella stessa scheda **Opzioni,** è anche possibile selezionare **Esegui sempre pip come amministratore** per sopprimere la finestra di dialogo per tutti gli ambienti. Vedere [Opzioni - Scheda Generale](python-support-options-and-settings-in-visual-studio.md#general-options).

### <a name="security-restrictions-with-older-versions-of-python"></a>Restrizioni di sicurezza con le versioni precedenti di Python

Quando si usa Python 2.6, 3.1 e 3.2, Visual Studio visualizza il messaggio di avviso che comunica che **l'installazione da Internet potrebbe non funzionare nella versione di Python a causa di nuove restrizioni di sicurezza**:

![Messaggio sulle restrizioni di installazione pip con una versione precedente di Python](media/environments/environments-old-version-restriction.png)

Il motivo dell'avviso è che con `pip install` queste versioni precedenti di Python, non contiene il supporto per il Transport Security Layer (TLS) 1.2, necessario per il download di pacchetti dall'origine del pacchetto, pypi.org. Le build Python personalizzate possono supportare `pip install` TLS 1.2 nel qual caso potrebbe funzionare.

È possibile scaricare la versione appropriata di *get-pip.py* per un pacchetto da [bootstrap.pypa.io](https://bootstrap.pypa.io/), scaricare manualmente un pacchetto da [pypi.org](https://pypi.org/) e quindi installarlo dalla copia locale.

È consigliabile, tuttavia, eseguire semplicemente l'aggiornamento a Python 2.7 o 3.3+. In tal caso, l'avviso non viene visualizzato.

::: moniker range="vs-2017"
## <a name="intellisense-tab"></a>Scheda IntelliSense

Mostra lo stato corrente del database di completamento IntelliSense:

![Scheda IntelliSense di Ambienti Python](media/environments/environments-intellisense-tab.png)

- In Visual Studio 2017 versione 15.5 e versioni precedenti, i completamenti IntelliSense dipendono da un database che è stato compilato per tale libreria. La creazione del database viene eseguita in background quando viene installata una libreria, ma potrebbe richiedere tempo e non essere completa quando si avvia la scrittura del codice.
- Visual Studio 2017 versione 15.6 e versioni successive usano un metodo più rapido per rendere disponibili i completamenti che non dipendono dal database per impostazione predefinita. Per questo motivo la scheda ha l'etichetta **IntelliSense [database disabilitato]**. È possibile abilitare il database deselezionando l'opzione **Opzioni strumenti** > **Python** > **Python** > **Experimental** > Usa nuovo stile**IntelliSense per gli ambienti**.

Quando Visual Studio rileva un nuovo ambiente (o ne viene aggiunto uno), avvia automaticamente la compilazione del database analizzando i file di origine della libreria. Questo processo può avvenire ovunque e richiedere da un minuto a oltre un'ora a seconda dei componenti installati. (Anaconda, ad esempio, viene fornito con molte librerie e richiede del tempo per compilare il database.) Al termine, si ottiene IntelliSense dettagliato e non è necessario aggiornare nuovamente il database (con il pulsante **Aggiorna DB)** fino a quando non si installano altre librerie.

Le librerie i cui dati non sono stati compilati vengono contrassegnate con un punto esclamativo (**!**). È presente un punto esclamativo (**!**) anche accanto al database di un ambiente non completo nell'elenco degli ambienti principale.

::: moniker-end

## <a name="see-also"></a>Vedere anche

- [Gestire ambienti Python in Visual Studio](managing-python-environments-in-visual-studio.md)
- [Selezionare un interprete per un progetto](selecting-a-python-environment-for-a-project.md)
- [Usare requirements.txt per le dipendenze](managing-required-packages-with-requirements-txt.md)
- [Percorsi di ricerca](search-paths.md)
