---
title: Informazioni di riferimento sulla finestra Ambienti Python
description: Dettagli su ognuna delle schede visualizzate nella finestra Ambienti Python in Visual Studio.
ms.date: 09/04/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 45a14fb5667d7eb28d4d298731886db662985d17
ms.sourcegitcommit: 9ea4b62163ad6be556e088da1e2a355f31366f39
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2018
ms.locfileid: "43996077"
---
# <a name="python-environments-window-tabs-reference"></a>Informazioni di riferimento sulle schede della finestra Ambienti Python

Per aprire la finestra **Ambienti Python**:

- Selezionare il comando di menu **Visualizza** > **Altre finestre** > **Ambienti Python**.
- Fare clic con il pulsante destro del mouse sul nodo **Ambienti Python** per un progetto in **Esplora soluzioni** e scegliere **Visualizza tutti gli ambienti Python**.

Se si allarga a sufficienza la finestra **Ambienti Python**, queste opzioni vengono visualizzate come schede, un layout che può risultare più comodo. Per maggiore chiarezza, le schede in questo articolo sono visualizzate nella modalità espansa.

![Visualizzazione espansa della finestra Ambienti Python](media/environments-expanded-view.png)

## <a name="overview-tab"></a>Scheda Panoramica

Include informazioni di base e comandi per l'ambiente:

![Scheda Panoramica di Ambienti Python](media/environments-overview-tab.png)

| Comando | Descrizione |
| --- | --- |
| **Make this environment the default for new projects (Imposta questo ambiente come predefinito per i nuovi progetti)** | Imposta l'ambiente attivo, facendo sì che Visual Studio (2017 versione 15.5 e precedenti) non risponda per un breve periodo finché non viene caricato il database di IntelliSense. Gli ambienti che contengono molti pacchetti potrebbero non rispondere per un periodo più lungo. |
| **Visit the distributor's website (Visita il sito Web del server di distribuzione)** | Apre un browser all'URL offerto dalla distribuzione di Python. Python 3.x, ad esempio, passa a python.org. |
| **Apri finestra interattiva** | Apre la [finestra (REPL) interattiva](python-interactive-repl-in-visual-studio.md) per questo ambiente all'interno di Visual Studio, applicando qualunque [script di avvio (vedere sotto)](#startup-scripts). |
| **Esplora gli script interattivi** | Vedere [Script di avvio](#startup-scripts). |
| **Usa la modalità interattiva IPython** | Se impostato, apre la finestra **Interattiva** con IPython per impostazione predefinita. Vengono abilitati i tracciati inline e la sintassi IPython estesa, come `name?` per visualizzare la Guida e `!command` per i comandi della shell. Questa opzione è consigliata quando si usa una distribuzione Anaconda, perché richiede pacchetti aggiuntivi. Per altre informazioni, vedere [Usare IPython nella finestra interattiva](interactive-repl-ipython.md). |
| **Apri in PowerShell** | Avvia l'interprete in una finestra di comando di PowerShell. |
| (Collegamenti alla cartella e ai programmi) | Consentono di accedere rapidamente alla cartella di installazione dell'ambiente, all'interprete *python.exe* e all'interprete *pythonw.exe*. Il primo apre Esplora risorse, gli ultimi due aprono una finestra della console. |

### <a name="startup-scripts"></a>Script di avvio

Quando si usano le finestre interattive nel proprio flusso di lavoro quotidiano, è probabile sviluppare funzioni helper da usare regolarmente. Ad esempio, è possibile creare una funzione che apre un dataframe in Excel, quindi salvare tale codice come script di avvio in modo che sia sempre disponibile nella finestra **Interattiva**.

Gli script di avvio contengono codice che la finestra **Interattiva** carica ed esegue automaticamente, incluse le importazioni, le definizioni di funzione e letteralmente qualunque altra cosa. Tali script sono referenziati in due modi:

1. Quando si installa un ambiente, Visual Studio crea una cartella *Documents\Visual Studio 2017\Python Scripts\\\<environment>* dove &lt;environment&gt; corrisponde al nome dell'ambiente. È possibile passare alla cartella specifica dell'ambiente con il comando **Esplora gli script interattivi**. Quando si avvia la finestra **Interattiva** per tale ambiente, vengono caricati ed eseguiti tutti i file con estensione *py* disponibili qui in ordine alfabetico.

1. Il controllo **Script** nella scheda **Strumenti** > **Opzioni** > **Strumenti Python** > **Finestre interattive** (vedere [Opzioni delle finestre interattive](python-support-options-and-settings-in-visual-studio.md#interactive-windows-options)) è destinato a specificare una cartella aggiuntiva per gli script di avvio che vengono caricati ed eseguiti in tutti gli ambienti. Tuttavia, questa funzionalità non è attualmente operativa.

## <a name="configure-tab"></a>Scheda Configura

Se disponibile, contiene i dettagli descritti nella tabella seguente. Se questa scheda non è presente, Visual Studio gestisce automaticamente tutti i dettagli.

![Scheda Configura di Ambienti Python](media/environments-configure-tab.png)

| Campo | Descrizione |
| --- | --- |
| **Descrizione** | Nome da assegnare all'ambiente. |
| **Percorso di prefisso** | Percorso della cartella di base dell'interprete. Se si compila questo valore e si fa clic su **Rilevamento automatico**, Visual Studio prova a compilare automaticamente gli altri campi. |
| **Percorso dell'interprete** | Percorso del file eseguibile dell'interprete, costituito in genere dal percorso di prefisso seguito da **python.exe** |
| **Interprete con finestra** | Percorso del file eseguibile non di console, spesso costituito dal percorso di prefisso seguito da **pythonw.exe**. |
| **Percorso della libreria**<br/>(se disponibile) | Radice della libreria standard. Questo valore può essere ignorato se Visual Studio è in grado di richiedere un percorso più accurato all'interprete. |
| **Versione del linguaggio** | Selezionata dal menu a discesa. |
| **Architettura** | In genere rilevata e inserita automaticamente; in caso contrario, il valore da specificare è **32 bit** o **64 bit**. |
| **Variabile di ambiente del percorso** | Variabile di ambiente usata dall'interprete per trovare i percorsi di ricerca. All'avvio di Python, Visual Studio modifica il valore della variabile in modo che contenga i percorsi di ricerca del progetto. In genere questa proprietà deve essere impostata su **PYTHONPATH**, ma alcuni interpreti usano un valore diverso. |

## <a name="packages-tab"></a>Scheda Pacchetti

*Denominata anche "pip" nelle versioni precedenti.*

Consente di gestire i pacchetti installati nell'ambiente con Pip, nonché di cercare e installare quelli nuovi (incluse eventuali dipendenze). In Visual Studio 2017 15.7 e versioni successive, viene visualizzata la scheda **Pacchetti (Conda)** che invece usa lo strumento di gestione dei pacchetti Conda. Se l'opzione non appare, impostare l'opzione **Strumenti** > **Opzioni** > **Python** > **Sperimentale** > **Usa strumento di gestione pacchetti Conda quando disponibile (anziché Pip)** e riavviare Visual Studio.

I pacchetti già installati vengono visualizzati con controlli per aggiornare (freccia rivolta verso l'alto) e disinstallare (X in un cerchio) il pacchetto:

![Scheda Pacchetti della finestra Ambienti Python](media/environments-pip-tab-controls.png)

Quando di immette un termine di ricerca viene filtrato l'elenco dei pacchetti installati e quello dei pacchetti che possono essere installati da PyPI.

![Scheda Pacchetti nella finestra Ambienti Python con la ricerca di "num"](media/environments-pip-tab.png)

Come illustrato nella figura precedente, i risultati della ricerca mostrano un numero di pacchetti corrispondenti al termine di ricerca. La prima voce dell'elenco, tuttavia, è un comando per l'esecuzione diretta di **pip install \<name>**. La scheda **Pacchetti (Conda)** visualizza invece **conda install \<name>**:

![Scheda Pacchetti (Conda) con un comando di installazione di Conda](media/environments-conda-tab-install.png)

In entrambi i casi, è possibile personalizzare l'installazione aggiungendo gli argomenti nella casella di ricerca dopo il nome del pacchetto. Quando si includono gli argomenti, i risultati della ricerca mostrano **pip install** o **conda install** seguito dal contenuto della casella di ricerca:

![Uso degli argomenti nei comandi di installazione pip e conda](media/environments-pip-tab-arguments.png)

L'installazione di un pacchetto crea sottocartelle all'interno della cartella *Lib* dell'ambiente nel file system. Se ad esempio Python 3.6 è installato in *c:\Python36*, i pacchetti vengono installati in *c:\Python36\Lib*. Se Anaconda3 è installato in *c:\Programmi\Anaconda3*, i pacchetti vengono installati in *c:\Programmi\Anaconda3\Lib*.

### <a name="grant-administrator-privileges-for-package-install"></a>Concedere i privilegi di amministratore per l'installazione dei pacchetti

Durante l'installazione di pacchetti in un ambiente che si trova in un'area protetta del file system, ad esempio *c:\Programmi\Anaconda3\Lib*, Visual Studio deve eseguire `pip install` con privilegi elevati per consentire la creazione di sottocartelle di pacchetto. Quando è necessaria l'elevazione, Visual Studio visualizza il prompt dei comandi, **Potrebbero essere necessari i privilegi di amministratore per installare, aggiornare o rimuovere i pacchetti per questo ambiente**:

![Richiesta di elevazione dei privilegi per l'installazione del pacchetto](media/environments-pip-elevate.png)

**Eleva ora** concede privilegi di amministratore per pip per un'unica operazione, subordinatamente anche a qualunque richiesta di permessi del sistema operativo. Se si seleziona **Continua senza privilegi di amministratore** viene tentata l'installazione del pacchetto, ma pip ha esito negativo quando cerca di creare delle cartelle con un output come **errore: impossibile creare 'C:\Programmi\Anaconda3\Lib\site-packages\png.py': Autorizzazione negata**.

Selezionando **Eleva sempre quando si installano o rimuovono pacchetti** si impedisce la visualizzazione della finestra di dialogo per l'ambiente in questione. Per visualizzare nuovamente la finestra di dialogo, passare a **Strumenti** > **Opzioni** > **Strumenti Python** > **Generale** e selezionare il pulsante **Ripristina tutte le finestre di dialogo nascoste in modo permanente**.

Nella stessa scheda **Opzioni** è anche possibile selezionare **Esegui sempre pip come amministratore** per eliminare la finestra di dialogo per tutti gli ambienti. Vedere [Opzioni - Scheda Generale](python-support-options-and-settings-in-visual-studio.md#general-options).

### <a name="security-restrictions-with-older-versions-of-python"></a>Restrizioni di sicurezza con le versioni precedenti di Python

Quando si usa Python 2.6, 3.1 e 3.2, Visual Studio visualizza il messaggio di avviso che comunica che **l'installazione da Internet potrebbe non funzionare nella versione di Python a causa di nuove restrizioni di sicurezza**:

![Messaggio sulle restrizioni di installazione pip con una versione precedente di Python](media/environments-old-version-restriction.png)

L'avviso viene visualizzato poiché nelle versioni precedenti di Python `pip install` non include il supporto di Transport Security Layer (TLS) 1.2 necessario per il download dei pacchetti dall'origine dei pacchetti pypi.org. Le build di Python personalizzate possono supportare TLS 1.2 e consentire il funzionamento di `pip install`.

È possibile scaricare la versione appropriata di *get-pip.py* per un pacchetto da [bootstrap.pypa.io](https://bootstrap.pypa.io/), scaricare manualmente un pacchetto da [pypi.org](https://pypi.org/) e quindi installarlo dalla copia locale.

È consigliabile, tuttavia, eseguire semplicemente l'aggiornamento a Python 2.7 o 3.3+. In tal caso, l'avviso non viene visualizzato.

## <a name="intellisense-tab"></a>Scheda IntelliSense

Mostra lo stato corrente del database di completamento IntelliSense:

![Scheda IntelliSense di Ambienti Python](media/environments-intellisense-tab.png)

- In **Visual Studio 2017 versione 15.5** e versioni precedenti, i completamenti IntelliSense dipendono da un database che è stato compilato per tale libreria. La creazione del database viene eseguita in background quando viene installata una libreria, ma potrebbe richiedere tempo e non essere completa quando si avvia la scrittura del codice.
- **Visual Studio 2017 versione 15.6** e versioni successive usano un metodo più rapido per rendere disponibili i completamenti che non dipendono dal database per impostazione predefinita. Per questo motivo la scheda ha l'etichetta **IntelliSense [database disabilitato]**. È possibile abilitare il database deselezionando l'opzione **Strumenti** > **Opzioni** > **Python** > **Sperimentale** > **Usa nuovo stile IntelliSense per gli ambienti**.

Quando Visual Studio rileva un nuovo ambiente (o ne viene aggiunto uno), avvia automaticamente la compilazione del database analizzando i file di origine della libreria. Questo processo può avvenire ovunque e richiedere da un minuto a oltre un'ora a seconda dei componenti installati. Anaconda include ad esempio molte librerie, di conseguenza la compilazione del database può richiedere molto tempo. Al termine dell'operazione, si ottengono informazioni IntelliSense dettagliate e non è necessario aggiornare di nuovo il database (con il pulsante **Aggiorna database**) fino a quando non si installano altre librerie.

Le librerie i cui dati non sono stati compilati vengono contrassegnate con un punto esclamativo (**!**). È presente un punto esclamativo (**!**) anche accanto al database di un ambiente non completo nell'elenco degli ambienti principale.

## <a name="see-also"></a>Vedere anche

- [Gestire ambienti Python in Visual Studio](managing-python-environments-in-visual-studio.md)
- [Selezionare un interprete per un progetto](selecting-a-python-environment-for-a-project.md)
- [Usare requirements.txt per le dipendenze](managing-required-packages-with-requirements-txt.md)
- [Percorsi di ricerca](search-paths.md)
