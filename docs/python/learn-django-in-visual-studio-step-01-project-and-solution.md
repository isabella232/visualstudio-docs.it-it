---
title: Informazioni sull'esercitazione Django in Visual Studio, passaggio 1, concetti di base relativi a Django
titleSuffix: ''
description: Procedura dettagliata dei concetti di base relativi a Django nel contesto dei progetti di Visual Studio, che presenta il supporto offerto da Visual Studio per lo sviluppo di soluzioni Django.
ms.date: 11/19/2018
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.technology: vs-python
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: bd3bb5bd5b9ac4864c9eb38f290d34d7cdd7fc1f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122156617"
---
# <a name="tutorial-get-started-with-the-django-web-framework-in-visual-studio"></a>Esercitazione: Introduzione al framework Web Django in Visual Studio

[Django](https://www.djangoproject.com/) è un framework Python di alto livello progettato per lo sviluppo rapido, sicuro e scalabile di applicazioni Web. Questa esercitazione esplora il framework Django nel contesto dei modelli di progetto forniti da Visual Studio per semplificare la creazione di app Web basate su Django.

In questa esercitazione verranno illustrate le procedure per:

::: moniker range="vs-2017"
- Creare un progetto Django di base in un repository Git tramite il modello "Progetto Web Django vuoto" (passaggio 1)
- Creare un'app Django con un'unica pagina ed eseguire il rendering della pagina tramite un modello (passaggio 2)
- Rendere disponibili file statici, aggiungere pagine e usare l'ereditarietà dei modelli (passaggio 3)
- Usare il modello di progetto Web Django per creare un'app con più pagine e una progettazione reattiva (passaggio 4)
- Autenticare gli utenti (passaggio 5)
- Usare il modello di progetto Web Django per le votazioni per creare un'app che usa modelli, migrazioni di database e personalizzazioni per l'interfaccia amministrativa (passaggio 6)
::: moniker-end

::: moniker range=">=vs-2019"
- Creare un progetto Django di base in un repository Git tramite il modello "Progetto Web Django vuoto" (passaggio 1)
- Creare un'app Django con un'unica pagina ed eseguire il rendering della pagina tramite un modello (passaggio 2)
- Rendere disponibili file statici, aggiungere pagine e usare l'ereditarietà dei modelli (passaggio 3)
- Usare il modello di progetto Web Django per creare un'app con più pagine e una progettazione reattiva (passaggio 4)
- Autenticare gli utenti (passaggio 5)
::: moniker-end

## <a name="prerequisites"></a>Prerequisiti

- Visual Studio 2017 o versioni successive in Windows con le opzioni seguenti:
  - Carico di lavoro **Sviluppo Python** (scheda **Carico di lavoro** nel programma di installazione). Per istruzioni, vedere [Installare il supporto Python in Visual Studio](installing-python-support-in-visual-studio.md).
  - **GIT per Windows** e **Estensione GitHub per Visual Studio** nella scheda **Singoli componenti** sotto a **Strumenti per il codice**.

I modelli di progetto Django sono inclusi anche in tutte le versioni precedenti di Python Tools for Visual Studio, anche se alcuni dettagli possono differire rispetto a quanto presentato in questa esercitazione, in particolare con le versioni precedenti del framework Django.

Lo sviluppo in Python non è attualmente supportato in Visual Studio per Mac. In Mac e Linux usare l'[estensione Python in Visual Studio Code](https://code.visualstudio.com/docs/python/python-tutorial).

### <a name="visual-studio-projects-and-django-projects"></a>"Progetti di Visual Studio" e "progetti Django"

Nella terminologia associata a Django, un "progetto Django" è costituito da diversi file di configurazione a livello di sito insieme a una o più "app" distribuite in un host Web per creare un'applicazione web completa. Un progetto Django può contenere più app e la stessa app può essere inclusa in più progetti Django.

Un progetto di Visual Studio, d'altro canto, può contenere il progetto Django insieme a più app. Per motivi di semplicità, ogni volta che in questa esercitazione si usa semplicemente il termine "progetto", ci si riferisce al progetto di Visual Studio. Quando si intende fare riferimento alla parte legata al "progetto Django" dell'applicazione Web, si usa espressamente il termine "progetto Django".

Durante questa esercitazione si creerà un'unica soluzione di Visual Studio contenente tre progetti Django separati, ognuno dei quali include una singola app Django. Mantenendo i progetti nella stessa soluzione, è possibile spostarsi facilmente tra i diversi file per confrontarli.

## <a name="step-1-1-create-a-visual-studio-project-and-solution"></a>Passaggio 1-1: Creare un progetto e una soluzione di Visual Studio

Quando si usa Django dalla riga di comando, generalmente si avvia un progetto eseguendo il comando `django-admin startproject <project_name>`. In Visual Studio l'uso del modello Progetto Web Django vuoto fornisce la stessa struttura che in un progetto e una soluzione di Visual Studio.

1. In Visual Studio selezionare **File** nuovo  >    >  **Project,** cercare "Django" e selezionare il modello di Project **Web Django** vuoto. Il modello si trova anche in **Python**  >  **Web** nell'elenco a sinistra.

    ![Finestra di dialogo Nuovo progetto in Visual Studio per il modello Progetto Web Django vuoto](media/django/step01-new-blank-project.png)

1. Nei campi nella parte inferiore della finestra di dialogo immettere le informazioni seguenti, come mostrato nella figura precedente, e quindi selezionare **OK**:

    - **Nome**: impostare il nome del progetto Visual Studio su **BasicProject.** Questo nome verrà usato anche per il progetto Django.
    - **Percorso**: specificare un percorso in cui creare la soluzione e il progetto di Visual Studio.
    - **Soluzione:** lasciare questo controllo impostato su Crea **nuova soluzione** predefinito.
    - **Nome soluzione:** impostare su **LearningDjango,** appropriato per la soluzione come contenitore per più progetti in questa esercitazione.
    - **Crea directory per soluzione**: lasciare impostato il valore predefinito.
    - **Crea nuovo repository Git**: selezionare questa opzione (deselezionata per impostazione predefinita), in modo che Visual Studio crei un repository Git locale durante la creazione della soluzione. Se questa opzione non è visualizzata, eseguire il programma di installazione di Visual Studio e aggiungere **GIT per Windows** ed **Estensione GitHub per Visual Studio** nella scheda **Singoli componenti** in **Strumenti per il codice**.

1. Dopo un po', Visual Studio viene visualizzata una finestra di dialogo che indica che questo **progetto richiede pacchetti esterni** (illustrato di seguito). Questa finestra di dialogo viene visualizzata perché il modello include un file *requirements.txt* che fa riferimento al pacchetto Django 1.x più recente. Selezionare **Mostra pacchetti necessari** per visualizzare le dipendenze esatte.

    ![Messaggio che indica che il progetto richiede pacchetti esterni](media/django/step01-requirements-prompt-install-myself.png)

1. Selezionare l'opzione **Installazione manuale**. A breve si creerà l'ambiente virtuale per assicurarsi che venga escluso dal controllo del codice sorgente. L'ambiente può sempre essere creato da *requirements.txt*.

## <a name="step-1-2-examine-the-git-controls-and-publish-to-a-remote-repository"></a>Passaggio 1-2: Esaminare i controlli Git e pubblicare il progetto in un repository remoto

Poiché è stato selezionato **Crea nuovo repository Git** nella finestra di dialogo **Nuovo progetto**, il progetto è già stato sottoposto a commit nel controllo del codice sorgente subito dopo il completamento del processo di creazione. In questo passaggio si acquisirà familiarità con i controlli Git di Visual Studio e la finestra **Team Explorer**, in cui viene usato il controllo del codice sorgente.

1. Esaminare i controlli Git nella parte inferiore della finestra principale di Visual Studio. Da sinistra a destra, questi controlli mostrano i commit di cui è stato annullato il push, le modifiche non sottoposte a commit, il nome del repository e il ramo corrente:

    ![Controlli Git nella finestra di Visual Studio](media/django/step01-git-controls.png)

    > [!Note]
    > Se non si seleziona **Crea nuovo repository Git** nella finestra di dialogo **Nuovo progetto**, i controlli Git mostrano solo il comando **Aggiungi al controllo del codice sorgente**, che crea un repository locale.
    >
    > ![Comando Aggiungi al controllo del codice sorgente visualizzato in Visual Studio se non è stato creato un repository](media/django/step01-git-add-to-source-control.png)

1. Selezionare il pulsante Modifiche. Visual Studio visualizza la pagina **Modifiche** nella finestra di **Team Explorer**. Poiché del nuovo progetto creato è già stato automaticamente eseguito il commit nel controllo del codice sorgente, non viene visualizzata alcuna modifica in sospeso.

    ![Finestra di Team Explorer, pagina Modifiche](media/django/step01-team-explorer-changes.png)

1. Nella barra Visual Studio stato selezionare il pulsante commit non associati (freccia su **con 2)** per aprire la pagina Sincronizzazione in  **Team Explorer**. Poiché è presente solo un repository locale, la pagina fornisce semplici opzioni per pubblicare il repository in diversi repository remoti.

    ![Finestra di Team Explorer che mostra le opzioni relative ai repository Git per il controllo del codice sorgente](media/django/step01-team-explorer.png)

    È possibile scegliere qualsiasi servizio desiderato per i propri progetti. Questa esercitazione mostra l'uso di GitHub, in cui il codice di esempio completo per l'esercitazione è disponibile nel repository [Microsoft/python-sample-vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django).

1. Quando si seleziona uno qualsiasi dei controlli **Pubblica**, **Team Explorer** chiede altre informazioni. Ad esempio, per la pubblicazione dell'esempio per questa esercitazione, è stato necessario creare per primo il repository stesso, usando in questo caso l'opzione **Effettua push nel repository remoto** con l'URL del repository.

    ![Finestra di Team Explorer per il push in un repository remoto esistente](media/django/step01-push-to-github.png)

    Se non è disponibile un repository esistente, le opzioni **Pubblica in GitHub** e **Esegui push ad Azure DevOps** consentono di crearne uno direttamente da Visual Studio.

1. Durante lo svolgimento di questa esercitazione, abituarsi a usare periodicamente i controlli in Visual Studio per il commit e il push delle modifiche. Questa esercitazione ricorda di eseguire queste operazioni nei momenti appropriati.

> [!Tip]
> Per spostarsi rapidamente **all'interno Team Explorer**, selezionare  l'intestazione (che legge Modifiche o **Push** nelle immagini precedenti) per visualizzare un menu a comparsa delle pagine disponibili.

### <a name="question-what-are-some-advantages-of-using-source-control-from-the-beginning-of-a-project"></a>Domanda: Quali sono alcuni dei vantaggi dell'uso del controllo del codice sorgente sin dall'inizio di un progetto?

Risposta: Prima di tutto, l'uso del controllo del codice sorgente sin dall'inizio, in particolare con un repository remoto, garantisce un backup regolare del progetto in un'altra posizione. A differenza della situazione in cui si mantiene un progetto solo in un file system locale, il controllo del codice sorgente fornisce anche una cronologia delle modifiche completa e la possibilità di ripristinare un singolo file o l'intero progetto in base a uno stato precedente in tutta semplicità. La cronologia delle modifiche permette di determinare la causa delle regressioni (errori di test). Inoltre, il controllo del codice sorgente è essenziale se più persone lavorano su un progetto, perché gestisce le sovrascritture ed esegue la risoluzione dei conflitti. Infine, il controllo del codice sorgente, che è sostanzialmente una forma di automazione, offre tutti gli strumenti necessari per l'automazione delle compilazioni, dei test e della gestione del rilascio. Si tratta davvero del primo passaggio quando si usa DevOps per un progetto e poiché le limitazioni preliminari sono minime, non vi è alcun motivo per non usare il controllo del codice sorgente sin dall'inizio.

Per altre informazioni sul controllo del codice sorgente come strumento di automazione, vedere [ Source of Truth: il ruolo dei repository in DevOps](/archive/msdn-magazine/2016/september/mobile-devops-the-source-of-truth-the-role-of-repositories-in-devops), un articolo in MSDN Magazine scritto per le app per dispositivi mobili, ma valido anche per le app Web.

### <a name="question-can-i-prevent-visual-studio-from-auto-committing-a-new-project"></a>Domanda: È possibile impedire a Visual Studio di eseguire il commit automatico di un nuovo progetto?

Risposta: Sì. Per disabilitare il commit automatico, passare alla pagina **Impostazioni** in **Team Explorer**, selezionare **Git** > **Impostazioni globali**, deselezionare l'opzione **Esegui il commit delle modifiche dopo il merge per impostazione predefinita** e quindi selezionare **Aggiorna**.

## <a name="step-1-3-create-the-virtual-environment-and-exclude-it-from-source-control"></a>Passaggio 1-3: Creare l'ambiente virtuale ed escluderlo dal controllo del codice sorgente

Dopo aver configurato il controllo del codice sorgente per il progetto, è possibile creare l'ambiente virtuale contenente i pacchetti Django necessari per il progetto. È quindi possibile usare **Team Explorer** per escludere la cartella dell'ambiente dal controllo del codice sorgente.

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo **Ambienti Python** e scegliere **Aggiungi ambiente virtuale**.

    ![Comando Aggiungi ambiente virtuale in Esplora soluzioni](media/django/step01-add-virtual-environment-command.png)

1. Viene **visualizzata una finestra di dialogo** Aggiungi ambiente virtuale con un messaggio che indica che è stato trovato un file requirements.txt **virtuale.** Il messaggio indica che Visual Studio usa questo file per configurare l'ambiente virtuale.

    ![Finestra di dialogo Aggiungi ambiente virtuale con il messaggio sul file requirements.txt](media/django/step01-add-virtual-environment-found-requirements.png)

1. Selezionare **Crea** per accettare i valori predefiniti. È possibile modificare il nome dell'ambiente virtuale, se si vuole, e questa operazione modifica solo il nome della sottocartella dell'ambiente, ma `env` è una convenzione standard.

1. Accettare i privilegi di amministratore se richiesto, quindi attendere alcuni minuti mentre Visual Studio scarica e installa i pacchetti. Questo per Django significa l'espansione di diverse migliaia di file in circa altrettante sottocartelle. È possibile visualizzare lo stato di avanzamento nella finestra **Output** di Visual Studio. Durante l'attesa, leggere le sezioni delle domande seguenti.

1. Nei controlli Git di Visual Studio nella barra di stato selezionare l'indicatore delle modifiche (indica **99&#42;**) che apre la pagina **Modifiche** in **Team Explorer**.

    La creazione dell'ambiente virtuale ha comportato migliaia di modifiche, ma non è necessario includerle nel controllo del codice sorgente, perché sarà sempre possibile, per l'utente o per chiunque altro cloni il progetto, ricreare l'ambiente da *requirements.txt*.

    Per escludere l'ambiente virtuale, fare clic con il pulsante destro del mouse sulla cartella **env** e selezionare **Ignora questi elementi locali**.

    ![Esclusione dell'ambiente virtuale dalle modifiche del controllo del codice sorgente](media/django/step01-ignore-local-items.png)

1. Dopo l'esclusione dell'ambiente virtuale, le sole modifiche rimanenti riguardano il file di progetto e quello con estensione *gitignore*. Il file con estensione *gitignore* contiene una voce aggiunta per la cartella dell'ambiente virtuale. È possibile fare doppio clic sul file per visualizzare una differenza.

1. Immettere un messaggio per il commit, selezionare **Esegui commit di tutto** e quindi eseguire il push dei commit nel repository remoto, se lo si desidera.

### <a name="question-why-do-i-want-to-create-a-virtual-environment"></a>Domanda: Perché è utile creare un ambiente virtuale?

Risposta: Un ambiente virtuale è un ottimo strumento per isolare le dipendenze esatte dell'app. Questo isolamento evita i conflitti all'interno di un ambiente Python globale e semplifica i test e la collaborazione. Quando si sviluppa un'app, si finisce per introdurre nel tempo molti utili pacchetti Python. Inserendo questi pacchetti in un ambiente virtuale specifico del progetto, è possibile aggiornare facilmente il file *requirements.txt* del progetto che descrive l'ambiente e che è incluso nel controllo del codice sorgente. Quando il progetto viene copiato in altri computer, tra cui server di compilazione, server di distribuzione e altri computer di sviluppo, è facile ricreare l'ambiente usando solo *requirements.txt*, che è il motivo per cui non è necessario includere l'ambiente nel controllo del codice sorgente. Per altre informazioni, vedere [Usare ambienti virtuali](selecting-a-python-environment-for-a-project.md#use-virtual-environments).

### <a name="question-how-do-i-remove-a-virtual-environment-thats-already-committed-to-source-control"></a>Domanda: Come si rimuove un ambiente virtuale di cui è già stato eseguito il commit nel controllo del codice sorgente?

Risposta: Modificare prima di tutto il file con estensione *gitignore* per escludere la cartella: individuare la sezione alla fine del file con il commento `# Python Tools for Visual Studio (PTVS)` e aggiungere una nuova riga per la cartella dell'ambiente virtuale, ad esempio `/BasicProject/env`. Poiché Visual Studio non mostra il file in **Esplora soluzioni**, aprirlo direttamente usando il comando di menu **File** > **Apri** > **File**. È anche possibile aprire il file da **Team Explorer**: nella pagina **Impostazioni** selezionare **Impostazioni repository**, passare alla sezione **Ignora file e file attributi** e quindi selezionare il collegamento **Modifica** accanto a **.gitignore**.

In secondo luogo, aprire una finestra di comando, passare alla cartella, ad esempio *BasicProject* che contiene la cartella dell'ambiente virtuale, ad esempio *env*, ed eseguire `git rm -r env`. Eseguire quindi il commit delle modifiche dalla riga di comando (`git commit -m 'Remove venv'`) o dalla pagina **Modifiche** di **Team Explorer**.

## <a name="step-1-4-examine-the-boilerplate-code"></a>Passaggio 1-4: Esaminare il codice boilerplate

Al termine della creazione del progetto, esaminare il codice boilerplate del progetto Django, che è lo stesso generato dal comando `django-admin startproject <project_name>` dell'interfaccia della riga di comando.

1. Nella radice del progetto si trova *manage.py*, l'utilità di amministrazione della riga di comando Django che Visual Studio imposta automaticamente come file di avvio del progetto. Eseguire l'utilità nella riga di comando usando `python manage.py <command> [options]`. Per attività Django comuni, Visual Studio offre pratici comandi di menu. Fare clic con il pulsante destro del mouse sul progetto in **Esplora soluzioni** e scegliere **Python** per visualizzare l'elenco. Alcuni di questi comandi verranno presentati nel corso di questa esercitazione.

    ![Comandi Django in un menu di scelta rapida del progetto Python](media/django/step01-django-commands-menu.png)

2. Nel progetto è presente una cartella con lo stesso nome del progetto. La cartella contiene i file di progetto Django di base:

   - *__init.py*: file vuoto che indica a Python che questa cartella è un pacchetto Python.
   - *wsgi.py*: punto di ingresso per server Web compatibili con WSGI per gestire il progetto. In genere, questo file viene lasciato così com'è, in quanto fornisce gli hook per i server Web di produzione.
   - *settings.py*: contiene le impostazioni per il progetto Django, che vengono modificate durante lo sviluppo di un'app Web.
   - *urls.py*: contiene una tabella di contenuti per il progetto Django, che verrà anch'essa modificata durante lo sviluppo.

     ![File del progetto Django in Esplora soluzioni](media/django/step01-django-project-in-solution-explorer.png)

3. Come indicato sopra, il modello di Visual Studio aggiunge anche un file *requirements.txt* al progetto specificando la dipendenza dei pacchetti Django. La presenza di questo file è il motivo per cui creare un ambiente virtuale quando si crea il progetto per la prima volta.

### <a name="question-can-visual-studio-generate-a-requirementstxt-file-from-a-virtual-environment-after-i-install-other-packages"></a>Domanda: Visual Studio può generare un file requirements.txt da un ambiente virtuale dopo che si installano altri pacchetti?

Risposta: Sì. Espandere il nodo **Ambienti Python**, fare clic con il pulsante destro del mouse sull'ambiente virtuale e scegliere il comando **Genera requirements.txt**. È utile usare questo comando periodicamente man mano che si modifica l'ambiente e si esegue il commit delle modifiche apportate a *requirements.txt* nel controllo del codice sorgente, insieme a tutte le altre modifiche del codice che dipendono dall'ambiente. Se si configura l'integrazione continua in un server di compilazione, è necessario generare il file ed eseguire il commit delle modifiche ogni volta che si modifica l'ambiente.

## <a name="step-1-5-run-the-empty-django-project"></a>Passaggio 1-5: Eseguire il progetto Django vuoto

1. In Visual Studio Debug Avvia debug (  >   **F5**) o usare il pulsante Server **Web** sulla barra degli strumenti (il browser visualizzato può variare):

    ![Pulsante di esecuzione del server Web della barra degli strumenti in Visual Studio](media/django/run-web-server-toolbar-button.png)

1. Eseguire il server significa eseguire il comando `manage.py runserver <port>`, che avvia il server di sviluppo integrato di Django. Se Visual Studio visualizza il messaggio **Impossibile avviare il debugger** perché manca il file di avvio, fare clic con il pulsante destro del mouse su **manage.py** in **Esplora soluzioni** e selezionare **Imposta come file di avvio**.

1. Quando si avvia il server, viene visualizzata una finestra della console che mostra il log del server. Visual Studio apre automaticamente un browser all'indirizzo `http://localhost:<port>`. Poiché il progetto Django non include alcuna app, tuttavia, Django mostra solo una pagina predefinita per indicare che quello che è stato fatto fino a questo punto funziona:

    ![Visualizzazione predefinita del progetto Django](media/django/step01-first-run-success.png)

1. Al termine, arrestare il server chiudendo la finestra della console o usando il comando **Debug** Arresta  >   debug in Visual Studio.

### <a name="question-is-django-a-web-server-as-well-as-a-framework"></a>Domanda: Django è un server Web e anche un framework?

Risposta: Sì e no. Django ha un server Web integrato, usato per scopi di sviluppo. Il server Web viene usato quando si esegue l'app Web in locale, ad esempio quando si esegue il debug in Visual Studio. Quando si esegue la distribuzione in un host Web, tuttavia, Django usa invece il server Web dell'host. Il modulo *wsgi.py* nel progetto Django si occupa dell'hook nei server di produzione.

### <a name="question-whats-the-difference-between-using-the-debug-menu-commands-and-the-server-commands-on-the-projects-python-submenu"></a>Domanda: Qual è la differenza tra l'uso dei comandi del menu Debug e dei comandi del server nel sottomenu Python del progetto?

Risposta: Oltre ai comandi del menu **Debug** e ai pulsanti della barra degli strumenti, è possibile avviare il server anche usando i comandi **Python** > **Avvia server** o **Python** > **Avvia il server di debug** del menu di scelta rapida del progetto. Entrambi i comandi aprono una finestra della console in cui viene visualizzato l'URL locale (localhost:port) per il server in esecuzione. Tuttavia, è necessario aprire manualmente un browser con l'URL e l'esecuzione del server di debug non avvia automaticamente il debugger di Visual Studio. È possibile collegare un debugger al processo in esecuzione in un secondo momento, se necessario, usando il **comando Esegui debug** connessione  >  **a** processo.

## <a name="next-steps"></a>Passaggi successivi

A questo punto, il progetto Django di base non contiene alcuna app. L'app verrà creata nel prossimo passaggio. Poiché in genere si usano più spesso le app Django che non il progetto Django, al momento non è necessario avere un'eccessiva familiarità con i file boilerplate.

> [!div class="nextstepaction"]
> [Creare un'app Django con visualizzazioni e modelli di pagina](learn-django-in-visual-studio-step-02-create-an-app.md)

## <a name="go-deeper"></a>Approfondimento

- Codice del progetto Django: [Writing your first Django app, part 1](https://docs.djangoproject.com/en/2.0/intro/tutorial01/) (Scrittura della prima app Django, parte 1) (docs.djangoproject.com)
- Utilità di amministrazione: [django-admin and manage.py](https://docs.djangoproject.com/en/2.0/ref/django-admin/) (docs.djangoproject.com)
- Codice sorgente per l'esercitazione su GitHub: [Microsoft/python-sample-vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django)