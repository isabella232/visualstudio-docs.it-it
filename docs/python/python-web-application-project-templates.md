---
title: Modelli di applicazione Web per Python
description: Visual Studio offre modelli per applicazioni Web Python usando i framework Bottle, Flask e Django. Sono supportate le configurazioni di debug e la pubblicazione in Servizio app di Azure.
ms.date: 01/28/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 6553017034dc46cfd1c035564a83dde89d77d057
ms.sourcegitcommit: 4908561809ad397c99cf204f52d5e779512e502c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/17/2021
ms.locfileid: "112254849"
---
# <a name="python-web-application-project-templates"></a>Modelli di progetto applicazione Web di Python

Python in Visual Studio supporta lo sviluppo di progetti Web nei framework Bottle, Flask e Django, usando modelli di progetto e un'utilità di avvio del debug che può essere configurata in modo da gestire diversi framework. Questi modelli includono un file *requirements.txt* per dichiarare le dipendenze necessarie. Quando si crea un progetto da uno di questi modelli, Visual Studio richiede di installare i pacchetti. Vedere [Installare i requisiti di progetto](#install-project-requirements) più avanti in questo articolo.

È anche possibile usare il modello **di progetto Web** generico per altri framework, ad esempio Pyramid. In questo caso, con il modello non vengono installati framework. In alternativa, installare i pacchetti necessari nell'ambiente in uso per il progetto (vedere [Finestra Ambienti Python- Scheda Pacchetti](python-environments-window-tab-reference.md#packages-tab)).

Per informazioni sulla distribuzione di un'app Web Python in Azure, vedere [Eseguire la pubblicazione nel servizio app di Azure](publishing-python-web-applications-to-azure-from-visual-studio.md).

## <a name="use-a-project-template"></a>Usare un modello di progetto

Per creare un progetto da un modello, usare **File**  >  **Nuovo**  >  **progetto**. Per visualizzare i modelli per i progetti **Web,** selezionare Web Python  >   sul lato sinistro della finestra di dialogo. Quindi, selezionare un modello a scelta, specificare il nome del progetto e della soluzione, impostare le opzioni per una directory soluzione e un repository Git e selezionare **OK**.

![Finestra di dialogo Nuovo progetto per app Web](media/projects-new-project-dialog-web.png)

::: moniker range="<=vs-2017"

Il modello **progetto Web** generico, citato in precedenza, fornisce solo un progetto Visual Studio vuoto senza codice e senza presupposti se non un progetto Python. Per informazioni dettagliate sul modello **Servizio Cloud Azure**, vedere [Progetti servizio cloud di Azure per Python](python-azure-cloud-service-project-template.md).

::: moniker-end

::: moniker range=">=vs-2019"

Il modello **progetto Web** generico, citato in precedenza, fornisce solo un progetto Visual Studio vuoto senza codice e senza presupposti se non un progetto Python.

::: moniker-end

Tutti gli altri modelli sono basati su framework Web Bottle, Flask o Django e rientrano in tre categorie generali come descritto nelle sezioni seguenti. Le app create con uno di questi modelli contengono codice sufficiente per eseguire l'app in locale ed eseguirne il debug. Ognuno di essi fornisce anche l'[oggetto app WSGI](https://www.python.org/dev/peps/pep-3333/) (python.org) necessario per l'uso con i server Web di produzione.

### <a name="blank-group"></a>Gruppo vuoto

Tutti **i modelli progetto \<framework> Web** vuoto creano un progetto con codice boilerplate più o meno minimo e le dipendenze necessarie dichiarate in un file *requirements.txt* file.

| Modello | Descrizione |
| --- | --- |
| **Progetto Web Bottle vuoto** | Genera un'app minima in *app.py* con una home page per `/` e una pagina `/hello/<name>` che restituisce `<name>` usando un modello di pagina inline molto breve. |
| **Progetto Web Django vuoto** | Genera un progetto Django con la struttura fondamentale del sito Django ma nessuna app Django. Per altre informazioni, vedere i [modelli Django](python-django-web-application-project-template.md) e il [passaggio 1 dell'esercitazione su Django](learn-django-in-visual-studio-step-01-project-and-solution.md). |
| **Progetto Web Flask vuoto** | Genera un'app minima con un'unica pagina "Hello World!" per `/`. Questa app è simile al risultato che si ottiene seguendo i passaggi dettagliati nella [Guida introduttiva: Creare per la prima volta un'app Web Python con Visual Studio](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json). Vedere anche [Informazioni su Flask, passaggio 1](learn-flask-visual-studio-step-01-project-solution.md).

### <a name="web-group"></a>Gruppo Web

Tutti **\<Framework> i modelli di** progetto Web creano un'app Web iniziale con una progettazione identica indipendentemente dal framework scelto. L'app prevede le pagine Home, Informazioni e Contatti, una barra di navigazione e una struttura reattiva basata su bootstrap. Ogni app è configurata in modo appropriato per i file statici (CSS, JavaScript e i tipi di carattere) e usa un meccanismo per il modello di pagina appropriato per il framework.

| Modello | Descrizione |
| --- | --- |
| **Progetto Web Bottle** | Genera un'app i cui file statici sono contenuti nella cartella *static* e gestiti tramite codice in *app.py*. Il routing per le singole pagine è specificato in *routes.py* e la cartella *views* contiene i modelli di pagina.|
| **Progetto Web Django** | Genera un progetto Django e un'app Django con tre pagine, il supporto dell'autenticazione e un database SQLite (ma nessun modello dati). Per altre informazioni, vedere i [modelli Django](python-django-web-application-project-template.md) e il [passaggio 4 dell'esercitazione su Django](learn-django-in-visual-studio-step-04-full-django-project-template.md). |
| **Progetto Web Flask** | Genera un'app i cui file statici sono contenuti nella cartella *static*. Il codice in *views.py* gestisce il routing e i modelli di pagina usano il motore Jinja contenuto nella cartella *templates*. Il file *runserver.py* fornisce il codice di avvio. Vedere [Informazioni su Flask, passaggio 4](learn-flask-visual-studio-step-04-full-flask-project-template.md). |
| **Progetto Web Flask/Jade** | Genera la stessa app del modello **progetto Web Flask,** ma usando l'estensione Jade per il motore di modello Jinja. |

::: moniker range="vs-2017"
### <a name="polls-group"></a>Gruppo di sondaggi

I **modelli progetto Web \<framework> di** sondaggi creano un'app Web iniziale tramite la quale gli utenti possono votare domande di sondaggio diverse. Ogni app si basa sulla struttura dei modelli progetto **Web** per usare un database per gestire i sondaggi e le risposte dell'utente. Le app includono modelli di dati appropriati e una speciale pagina dell'app (/seed) che carica i sondaggi da un file *samples.json*.

| Modello | Descrizione |
| --- | --- |
| **Progetto Web Bottle di sondaggi** | Genera un'app che può essere eseguita su un database in memoria, MongoDB o un archivio tabelle di Azure, che viene configurato tramite la variabile di ambiente `REPOSITORY_NAME`. I modelli di dati e il codice dell'archivio dati sono contenuti nella cartella *models* e il file *settings.py* contiene codice per determinare l'archivio dati usato. |
| **Progetto Web Django di sondaggi** | Genera un progetto Django e un'app Django con tre pagine e un database SQLite. Include le personalizzazioni per l'interfaccia amministrativa Django che consentono a un amministratore autenticato di creare e gestire i sondaggi. Per altre informazioni, vedere i [modelli Django](python-django-web-application-project-template.md) e il [passaggio 6 dell'esercitazione su Django](learn-django-in-visual-studio-step-06-polls-django-web-project-template.md). |
| **Progetto Web Flask di sondaggi** | Genera un'app che può essere eseguita su un database in memoria, MongoDB o un archivio tabelle di Azure, che viene configurato tramite la variabile di ambiente `REPOSITORY_NAME`. I modelli di dati e il codice dell'archivio dati sono contenuti nella cartella *models* e il file *settings.py* contiene codice per determinare l'archivio dati usato. L'app utilizza il motore Jinja per i modelli di pagina. Vedere [Informazioni su Flask, passaggio 5](learn-flask-visual-studio-step-05-polls-flask-web-project-template.md). |
| **Progetto Web Flask/Jade di sondaggi** | Genera la stessa app del modello **Progetto Web Flask** di sondaggi, ma usando l'estensione Jade per il motore di modello Jinja. |
::: moniker-end

## <a name="install-project-requirements"></a>Installare i requisiti di progetto

Quando si crea un progetto da un modello specifico del framework, viene visualizzata una finestra di dialogo che consente di installare i pacchetti necessari con pip. Per i progetti Web è inoltre consigliabile usare un [ambiente virtuale](selecting-a-python-environment-for-a-project.md#use-virtual-environments), in modo che durante la pubblicazione del sito Web vengano incluse le dipendenze corrette:

![Finestra di dialogo in cui è possibile installare i pacchetti necessari per un modello di progetto](media/template-web-requirements-txt-wizard.png)

Se si usa il controllo del codice sorgente, è pratica comune omettere la cartella dell'ambiente virtuale poiché l'ambiente può essere ricreato usando solo *requirements.txt*. Il modo migliore per escludere la cartella consiste innanzitutto nel selezionare **Installazione manuale** nel messaggio visualizzato sopra, quindi disabilitare il commit automatico prima di creare l'ambiente virtuale. Per informazioni dettagliate, vedere [Esercitazione su Django, passaggi 1-2 e 1-3](learn-django-in-visual-studio-step-01-project-and-solution.md#step-1-2-examine-the-git-controls-and-publish-to-a-remote-repository) e [Esercitazione su Flask, passaggi 1-2 e 1-3](learn-flask-visual-studio-step-01-project-solution.md#step-1-2-examine-the-git-controls-and-publish-to-a-remote-repository).

Durante la distribuzione nel servizio app di Microsoft Azure, selezionare una versione di Python come [estensione sito](./managing-python-on-azure-app-service.md?view=vs-2019&preserve-view=true) e installare manualmente i pacchetti. Inoltre, poiché il servizio app di Azure **non** installa automaticamente i pacchetti da un file *requirements.txt* quando viene distribuito da Visual Studio, attenersi ai dettagli di configurazione indicati in [aka.ms/PythonOnAppService](managing-python-on-azure-app-service.md).

::: moniker range="<=vs-2017"

I servizi cloud di Microsoft Azure invece *supportano* il file *requirements.txt*. Vedere [Progetti servizio cloud di Azure per Python](python-azure-cloud-service-project-template.md) per informazioni più dettagliate.

::: moniker-end

## <a name="debugging"></a>Debug

Quando si avvia un progetto Web per il debug, Visual Studio avvia un server Web locale su una porta casuale e apre il browser predefinito usando l'indirizzo e la porta specificati. Per specificare opzioni aggiuntive, fare clic con il pulsante destro del mouse sul progetto, scegliere **Proprietà** e selezionare la **scheda Utilità di avvio** Web:

![Proprietà dell'utilità di Web per il modello Web generico](media/template-web-launcher-properties.png)

Nel gruppo **Debug** specificare le proprietà seguenti:

- **Percorsi di ricerca**, **Argomenti dello script**, **Argomenti dell'interprete** e **Percorso dell'interprete**: queste opzioni sono uguali a quelle per il [debug normale](debugging-python-in-visual-studio.md).
- **URL di avvio**: specifica l'URL che viene aperto nel browser. Il valore predefinito è `localhost`.
- **Numero di porta**: porta da usare se non ne viene specificata nessuna nell'URL (Visual Studio ne seleziona una automaticamente per impostazione predefinita). Questa impostazione consente di eseguire l'override del valore predefinito della variabile di ambiente `SERVER_PORT`, usata dai modelli per configurare la porta su cui è in ascolto il server di debug locale.

Le proprietà nei gruppi **Comando esegui server** e **Comando debug server** (quest'ultimo illustrato nell'immagine) determinano la modalità di avvio del server Web. Con molti framework è richiesto l'uso di uno script esterno al progetto corrente, di conseguenza è possibile configurare qui lo script e passare il nome del modulo di avvio come parametro.

- **Comando**: può essere uno script Python (file *\*.py*), un nome di modulo (come in `python.exe -m module_name`) o una singola riga di codice (come in `python.exe -c "code"`). Il valore nell'elenco a discesa indica il tipo da usare.
- **Argomenti**: questi argomenti vengono passati nella riga di comando dopo il comando.
- **Ambiente:** elenco di coppie separate da nuova riga \<NAME> = \<VALUE> che specificano le variabili di ambiente. Queste variabili vengono impostate dopo tutte le proprietà che possono comportare la modifica dell'ambiente, ad esempio il numero di porta e i percorsi di ricerca, di conseguenza possono sovrascrivere tali valori.

Per specificare qualsiasi proprietà di progetto o variabile di ambiente, è possibile usare la sintassi MSBuild, ad esempio: `$(StartupFile) --port $(SERVER_PORT)`.
`$(StartupFile)` è il percorso relativo del file di avvio, mentre `{StartupModule}` è il nome importabile del file di avvio. `$(SERVER_HOST)`e sono variabili di ambiente normali impostate dalle proprietà URL di avvio e Numero di porta, automaticamente `$(SERVER_PORT)` o dalla **proprietà** Ambiente .  

> [!Note]
> I valori in **Comando esegui server** vengono usati con il comando **Debug** > **Avvia server** oppure quando si preme **CTRL**+**F5**. I valori nel gruppo **Comando debug server** vengono usati con il comando **Debug** > **Avvia il server di debug** oppure quando si preme **F5**.

### <a name="sample-bottle-configuration"></a>Esempio di configurazione di Bottle

Il **modello progetto Web Bottle** include codice boilerplate che esegue la configurazione necessaria. Un'app Bottle importata potrebbe però non includere questo codice. In questo caso, le impostazioni seguenti consentono di avviare l'app usando il modulo `bottle` installato:

- Gruppo **Comando esegui server**:
  - **Comando**: `bottle` (modulo)
  - **Argomenti**: `--bind=%SERVER_HOST%:%SERVER_PORT% {StartupModule}:app`

- Gruppo **Comando debug server**:
  - **Comando**: `bottle` (modulo)
  - **Argomenti**`--debug --bind=%SERVER_HOST%:%SERVER_PORT% {StartupModule}:app`

L'opzione `--reload` è sconsigliata quando si usa Visual Studio per il debug.

### <a name="sample-pyramid-configuration"></a>Esempio di configurazione di Pyramid

Per la creazione di app Pyramid è attualmente preferibile usare lo strumento da riga di comando `pcreate`. L'app creata può quindi essere importata usando il modello [**Da codice Python esistente**](managing-python-projects-in-visual-studio.md#create-a-project-from-existing-files). Successivamente, selezionare la personalizzazione **Progetto Web generico** per configurare le opzioni. In queste impostazioni si presuppone che Pyramid sia installato in un ambiente virtuale nel percorso `..\env`.

- Gruppo **Debug**:
  - **Porta server**: 6543 (o qualunque altra sia configurata nei file con estensione *ini*)

- Gruppo **Comando esegui server**:
  - Comando: `..\env\scripts\pserve-script.py` (script)
  - Argomenti: `Production.ini`

- Gruppo **Comando debug server**:
  - Comando: `..\env\scripts\pserve-script.py` (script)
  - Argomenti: `Development.ini`

> [!Tip]
> È probabilmente necessario configurare la proprietà **Directory di lavoro** del progetto perché le app Pyramid si trovano in genere una cartella sotto la radice del progetto.

### <a name="other-configurations"></a>Altre configurazioni

Se si vogliono condividere impostazioni personalizzate per un altro framework oppure richiederne altre, aprire una [segnalazione in GitHub](https://github.com/Microsoft/PTVS/issues).

::: moniker range="<=vs-2017"

## <a name="convert-a-project-to-azure-cloud-service"></a>Convertire un progetto in un servizio cloud di Azure

Il **comando Converti in Microsoft Azure progetto di servizio cloud** (immagine seguente) aggiunge un progetto di servizio cloud alla soluzione. Questo progetto include le impostazioni di distribuzione e la configurazione per i servizi e le macchine virtuali da usare. Usare il comando **Pubblica** nel progetto cloud per eseguire la distribuzione nei servizi cloud. Con il comando **Pubblica** nel progetto Python la distribuzione viene ancora eseguita nei siti Web. Per altre informazioni, vedere [Progetti servizio cloud di Azure](python-azure-cloud-service-project-template.md).

![Comando Converti in progetto servizio cloud di Microsoft Azure](media/template-web-convert-menu.png)

::: moniker-end

## <a name="see-also"></a>Vedi anche

- [Informazioni di riferimento sui modelli di elemento Python](python-item-templates.md)
- [Eseguire la pubblicazione nel servizio app di Azure](publishing-python-web-applications-to-azure-from-visual-studio.md)