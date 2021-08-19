---
title: Informazioni sull'esercitazione Flask in Visual Studio, passaggio 1, concetti di base di Flask
titleSuffix: ''
description: Procedura dettagliata sui concetti di base relativi a Flask in un contesto di progetti Visual Studio, inclusi prerequisiti, GIT e ambienti virtuali.
ms.date: 01/07/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.technology: vs-python
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 528471301c1de6d44d5de6464fa24c81f13b8b36
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122054509"
---
# <a name="tutorial-get-started-with-the-flask-web-framework-in-visual-studio"></a>Esercitazione: Introduzione al framework Web Flask in Visual Studio

[Flask](https://palletsprojects.com/p/flask/) è un framework Python leggero per le applicazioni Web che offre le informazioni fondamentali per il routing dell'URL e il rendering della pagina.

Flask è definito un framework "micro" perché non mette direttamente a disposizione funzionalità come la convalida del modulo, l'astrazione di database, l'autenticazione e così via. Tali funzionalità sono invece contenute in speciali pacchetti Python denominati *estensioni* di Flask. Le estensioni si integrano perfettamente con Flask, come se facessero parte del framework. Ad esempio, lo stesso Flask non offre un motore del modello di pagina. La creazione dei modelli è possibile grazie alle estensioni, ad esempio Jinja e Jade, come illustrato in questa esercitazione.

::: moniker range="vs-2017"
In questa esercitazione verranno illustrate le procedure per:
- Creare un progetto Flask di base in un repository Git tramite il modello "Progetto Web Flask vuoto" (passaggio 1)
- Creare un'app Flask con un'unica pagina ed eseguire il rendering della pagina usando un modello (passaggio 2)
- Rendere disponibili file statici, aggiungere pagine e usare l'ereditarietà dei modelli (passaggio 3)
- Usare il modello Progetto Web Flask per creare un'app con più pagine e una progettazione reattiva (passaggio 4)
- Usare il modello Progetto Web Flask di sondaggi per creare un'app di sondaggi che usa un'ampia gamma di opzioni di archiviazione (Archiviazione di Azure, MongoDB o memoria).

Nel corso della procedura verrà creata un'unica soluzione di Visual Studio che contiene tre progetti separati. Il progetto viene creato usando diversi modelli di progetto Flask inclusi in Visual Studio. Mantenendo i progetti nella stessa soluzione, è possibile spostarsi facilmente tra i diversi file per confrontarli.
::: moniker-end

::: moniker range=">=vs-2019"

In questa esercitazione verranno illustrate le procedure per:
- Creare un progetto Flask di base in un repository Git tramite il modello "Progetto Web Flask vuoto" (passaggio 1)
- Creare un'app Flask con un'unica pagina ed eseguire il rendering della pagina usando un modello (passaggio 2)
- Rendere disponibili file statici, aggiungere pagine e usare l'ereditarietà dei modelli (passaggio 3)
- Usare il modello Progetto Web Flask per creare un'app con più pagine e una progettazione reattiva (passaggio 4)

Nel corso di questi passaggi viene creata una singola soluzione Visual Studio che contiene due progetti separati. Il progetto viene creato usando diversi modelli di progetto Flask inclusi in Visual Studio. Mantenendo i progetti nella stessa soluzione, è possibile spostarsi facilmente tra i diversi file per confrontarli.
::: moniker-end

> [!Note]
> Questa esercitazione si differenzia dalla guida [Flask Quickstart](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json) (Avvio rapido di Flask) per il fatto che offre un maggior numero di informazioni e spiega come usare i vari modelli di progetto Flask, ideali come punto di partenza per la creazione dei propri progetti. Ad esempio, i modelli di progetto installano automaticamente il pacchetto Flask durante la creazione di un progetto, evitando la necessità di installare il pacchetto manualmente come illustrato nell'Avvio rapido.

## <a name="prerequisites"></a>Prerequisiti

- Visual Studio 2017 o versioni successive in Windows con le opzioni seguenti:
  - Carico di lavoro **Sviluppo Python** (scheda **Carico di lavoro** nel programma di installazione). Per istruzioni, vedere [Installare il supporto Python in Visual Studio](installing-python-support-in-visual-studio.md).
  - **GIT per Windows** e **Estensione GitHub per Visual Studio** nella scheda **Singoli componenti** sotto a **Strumenti per il codice**.

I modelli di progetto Flask sono inclusi in tutte le versioni precedenti di Python Tools for Visual Studio, anche se alcuni dettagli possono differire rispetto a quanto presentato in questa esercitazione.

Lo sviluppo in Python non è attualmente supportato in Visual Studio per Mac. In Mac e Linux usare l'[estensione Python in Visual Studio Code](https://code.visualstudio.com/docs/python/python-tutorial).

## <a name="step-1-1-create-a-visual-studio-project-and-solution"></a>Passaggio 1-1: Creare un progetto e una soluzione di Visual Studio

1. In Visual Studio selezionare **File** Nuovo Project, cercare "Flask" e selezionare il modello Blank  >    >   **Flask Web Project (Project** Web Flask vuoto). Il modello è disponibile anche in **Python**  >  **Web** nell'elenco a sinistra.

    ![Finestra di dialogo Nuovo progetto in Visual Studio per il modello Progetto Web Flask vuoto](media/flask/step01-new-blank-project.png)

1. Nei campi nella parte inferiore della finestra di dialogo immettere le informazioni seguenti, come mostrato nella figura precedente, e quindi selezionare **OK**:

    - **Nome:** impostare il nome del progetto Visual Studio su **BasicProject.** Questo nome verrà usato anche per il progetto Flask.
    - **Percorso**: specificare un percorso in cui creare la soluzione e il progetto di Visual Studio.
    - **Nome della soluzione**: impostare su **LearningFlask**, un nome appropriato per la soluzione come contenitore per più progetti in questa esercitazione.
    - **Crea directory per soluzione**: lasciare impostato il valore predefinito.
    - **Crea nuovo repository Git**: selezionare questa opzione (deselezionata per impostazione predefinita), in modo che Visual Studio crei un repository Git locale durante la creazione della soluzione. Se questa opzione non è visualizzata, eseguire il programma di installazione di Visual Studio e aggiungere **GIT per Windows** ed **Estensione GitHub per Visual Studio** nella scheda **Singoli componenti** in **Strumenti per il codice**.

1. Dopo qualche istante, Visual Studio viene visualizzata una finestra di dialogo che indica Che il **progetto richiede pacchetti esterni** (illustrato di seguito). Questa finestra di dialogo viene visualizzata perché il modello include un file *requirements.txt* che fa riferimento al pacchetto Flask 1.x più recente. Selezionare **Mostra pacchetti necessari** per visualizzare le dipendenze esatte.

    ![Messaggio che indica che il progetto richiede pacchetti esterni](media/tutorials-common/step01-requirements-prompt-install-myself.png)

1. Selezionare l'opzione **Installazione manuale**. A breve si creerà l'ambiente virtuale per assicurarsi che venga escluso dal controllo del codice sorgente. L'ambiente può sempre essere creato da *requirements.txt*.

## <a name="step-1-2-examine-the-git-controls-and-publish-to-a-remote-repository"></a>Passaggio 1-2: Esaminare i controlli Git e pubblicare il progetto in un repository remoto

Poiché è stato selezionato **Crea nuovo repository Git** nella finestra di dialogo **Nuovo progetto**, il progetto è già stato sottoposto a commit nel controllo del codice sorgente subito dopo il completamento del processo di creazione. In questo passaggio si acquisirà familiarità con i controlli Git di Visual Studio e la finestra **Team Explorer**, in cui viene usato il controllo del codice sorgente.

1. Esaminare i controlli Git nella parte inferiore della finestra principale di Visual Studio. Da sinistra a destra, questi controlli mostrano i commit di cui è stato annullato il push, le modifiche non sottoposte a commit, il nome del repository e il ramo corrente:

    ![Controlli Git nella finestra di Visual Studio](media/flask/step01-git-controls.png)

    > [!Note]
    > Se non si seleziona **Crea nuovo repository Git** nella finestra di dialogo **Nuovo progetto**, i controlli Git mostrano solo il comando **Aggiungi al controllo del codice sorgente**, che crea un repository locale.
    >
    > ![Comando Aggiungi al controllo del codice sorgente visualizzato in Visual Studio se non è stato creato un repository](media/tutorials-common/step01-git-add-to-source-control.png)

1. Selezionare il pulsante Modifiche. Visual Studio visualizza la pagina **Modifiche** nella finestra di **Team Explorer**. Poiché del nuovo progetto creato è già stato automaticamente eseguito il commit nel controllo del codice sorgente, non viene visualizzata alcuna modifica in sospeso.

    ![Finestra di Team Explorer, pagina Modifiche](media/flask/step01-team-explorer-changes.png)

1. Sulla barra Visual Studio stato selezionare il pulsante commit di cui non è stato eseguito il  commit di cui è stato eseguito il commit (la freccia in su con **2**) per aprire la pagina Sincronizzazione in **Team Explorer**. Poiché è presente solo un repository locale, la pagina fornisce semplici opzioni per pubblicare il repository in diversi repository remoti.

    ![Finestra di Team Explorer che mostra le opzioni relative ai repository Git per il controllo del codice sorgente](media/flask/step01-team-explorer.png)

    È possibile scegliere qualsiasi servizio desiderato per i propri progetti. Questa esercitazione illustra l'uso di GitHub, in cui il codice di esempio completo per l'esercitazione è disponibile nel repository [Microsoft/python-sample-vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask).

1. Quando si seleziona uno qualsiasi dei controlli **Pubblica**, **Team Explorer** chiede altre informazioni. Ad esempio, per la pubblicazione dell'esempio per questa esercitazione, è stato necessario creare per primo il repository stesso, usando in questo caso l'opzione **Effettua push nel repository remoto** con l'URL del repository.

    ![Finestra di Team Explorer per il push in un repository remoto esistente](media/flask/step01-push-to-github.png)

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

Dopo aver configurato il controllo del codice sorgente per il progetto, è possibile creare l'ambiente virtuale con i pacchetti Flask necessari richiesti dal progetto. È quindi possibile usare **Team Explorer** per escludere la cartella dell'ambiente dal controllo del codice sorgente.

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo **Ambienti Python** e scegliere **Aggiungi ambiente virtuale**.

    ![Comando Aggiungi ambiente virtuale in Esplora soluzioni](media/flask/step01-add-virtual-environment-command.png)

1. Viene **visualizzata la finestra di dialogo** Aggiungi ambiente virtuale con un messaggio che indica Che è stato trovato requirements.txt **file.** Il messaggio indica che Visual Studio usa questo file per configurare l'ambiente virtuale.

    ![Finestra di dialogo Aggiungi ambiente virtuale con il messaggio sul file requirements.txt](media/tutorials-common/step01-add-virtual-environment-found-requirements.png)

1. Selezionare **Crea** per accettare i valori predefiniti. È possibile modificare il nome dell'ambiente virtuale, se si vuole, e questa operazione modifica solo il nome della sottocartella dell'ambiente, ma `env` è una convenzione standard.

1. Accettare i privilegi di amministratore se richiesto, quindi attendere alcuni minuti mentre Visual Studio scarica e installa i pacchetti. Questo per Flask e le relative dipendenze significa l'espansione di un migliaio di file in più di 100 sottocartelle. È possibile visualizzare lo stato di avanzamento nella finestra **Output** di Visual Studio. Durante l'attesa, leggere le sezioni delle domande seguenti. È anche possibile visualizzare una descrizione delle dipendenze di Flask nella pagina di [installazione di Flask](https://flask.palletsprojects.com/en/1.0.x/installation/#installation) (flask.pcocoo.org).

1. Nei controlli Git di Visual Studio nella barra di stato selezionare l'indicatore delle modifiche (indica **99&#42;**) che apre la pagina **Modifiche** in **Team Explorer**.

    La creazione dell'ambiente virtuale ha comportato centinaia di modifiche, ma non è necessario includerle nel controllo del codice sorgente, perché sarà sempre possibile, per l'utente o per chiunque altro cloni il progetto, ricreare l'ambiente da *requirements.txt*.

    Per escludere l'ambiente virtuale, fare clic con il pulsante destro del mouse sulla cartella **env** e selezionare **Ignora questi elementi locali**.

    ![Esclusione dell'ambiente virtuale dalle modifiche del controllo del codice sorgente](media/flask/step01-ignore-local-items.png)

1. Dopo l'esclusione dell'ambiente virtuale, le sole modifiche rimanenti riguardano il file di progetto e quello con estensione *gitignore*. Il file con estensione *gitignore* contiene una voce aggiunta per la cartella dell'ambiente virtuale. È possibile fare doppio clic sul file per visualizzare una differenza.

1. Immettere un messaggio per il commit, selezionare **Esegui commit di tutto** e quindi eseguire il push dei commit nel repository remoto, se lo si desidera.

### <a name="question-why-do-i-want-to-create-a-virtual-environment"></a>Domanda: Perché è utile creare un ambiente virtuale?

Risposta: Un ambiente virtuale è un ottimo strumento per isolare le dipendenze esatte dell'app. Questo isolamento evita i conflitti all'interno di un ambiente Python globale e semplifica i test e la collaborazione. Quando si sviluppa un'app, si finisce per introdurre nel tempo molti utili pacchetti Python. Inserendo questi pacchetti in un ambiente virtuale specifico del progetto, è possibile aggiornare facilmente il file *requirements.txt* del progetto che descrive l'ambiente e che è incluso nel controllo del codice sorgente. Quando il progetto viene copiato in altri computer, tra cui server di compilazione, server di distribuzione e altri computer di sviluppo, è facile ricreare l'ambiente usando solo *requirements.txt*, che è il motivo per cui non è necessario includere l'ambiente nel controllo del codice sorgente. Per altre informazioni, vedere [Usare ambienti virtuali](selecting-a-python-environment-for-a-project.md#use-virtual-environments).

### <a name="question-how-do-i-remove-a-virtual-environment-thats-already-committed-to-source-control"></a>Domanda: Come si rimuove un ambiente virtuale di cui è già stato eseguito il commit nel controllo del codice sorgente?

Risposta: Modificare prima di tutto il file con estensione *gitignore* per escludere la cartella: individuare la sezione alla fine del file con il commento `# Python Tools for Visual Studio (PTVS)` e aggiungere una nuova riga per la cartella dell'ambiente virtuale, ad esempio `/BasicProject/env`. Poiché Visual Studio non mostra il file in **Esplora soluzioni**, aprirlo direttamente usando il comando di menu **File** > **Apri** > **File**. È anche possibile aprire il file da **Team Explorer**: nella pagina **Impostazioni** selezionare **Impostazioni repository**, passare alla sezione **Ignora file e file attributi** e quindi selezionare il collegamento **Modifica** accanto a **.gitignore**.

In secondo luogo, aprire una finestra di comando, passare alla cartella, ad esempio *BasicProject* che contiene la cartella dell'ambiente virtuale, ad esempio *env*, ed eseguire `git rm -r env`. Eseguire quindi il commit delle modifiche dalla riga di comando (`git commit -m 'Remove venv'`) o dalla pagina **Modifiche** di **Team Explorer**.

## <a name="step-1-4-examine-the-boilerplate-code"></a>Passaggio 1-4: Esaminare il codice boilerplate

1. Completata la creazione del progetto, la soluzione e il progetto verranno visualizzati in **Esplora soluzioni**, dove il progetto contiene solo due file, *app.py* e *requirements.txt*:

    ![File del progetto Flask vuoto in Esplora soluzioni](media/flask/step01-blank-flask-project-in-solution-explorer.png)

1. Come indicato in precedenza, il file *requirements.txt* specifica la dipendenza del pacchetto Flask. La presenza di questo file è il motivo per cui creare un ambiente virtuale quando si crea il progetto per la prima volta.

1. Il singolo file *app.py* contiene tre parti. La prima è un'istruzione `import` per Flask, che crea un'istanza della classe `Flask`, che viene assegnata alla variabile `app`, quindi assegna una variabile `wsgi_app` (utile per la distribuzione in un host Web, ma al momento non usata):

    ```python
    from flask import Flask
    app = Flask(__name__)

    # Make the WSGI interface available at the top level so wfastcgi can get it.
    wsgi_app = app.wsgi_app
    ```

1. La seconda parte, alla fine del file, è una piccola porzione di codice facoltativo che avvia il server di sviluppo di Flask con valori specifici di host e porta ricavati dalle variabili di ambiente (l'impostazione predefinita è localhost:5555):

    ```python
    if __name__ == '__main__':
        import os
        HOST = os.environ.get('SERVER_HOST', 'localhost')
        try:
            PORT = int(os.environ.get('SERVER_PORT', '5555'))
        except ValueError:
            PORT = 5555
        app.run(HOST, PORT)
    ```

1. La terza è un piccolo frammento di codice che assegna una funzione a una route dell'URL, ovvero la funzione specifica la risorsa identificata dall'URL. Per definire le route usare l'elemento Decorator `@app.route` di Flask, il cui argomento è l'URL relativo della radice del sito. Come si può notare nel codice, in questo caso la funzione restituisce solo una stringa di testo, che è sufficiente per il rendering di un browser. Nei passaggi successivi viene eseguito il rendering di pagine più complete con HTML.

    ```python
    @app.route('/')
    def hello():
        """Renders a sample page."""
        return "Hello World!"
    ```

### <a name="question-what-is-the-purpose-of-the-__name__-argument-to-the-flask-class"></a>Domanda: Qual è lo scopo dell'argomento __name__ per la classe Flask?

Risposta: l'argomento è il nome del modulo o pacchetto dell'app e indica a Flask dove cercare modelli, file statici e altre risorse che appartengono all'app. Per le app contenute in un singolo modulo, `__name__` è sempre il valore appropriato. È anche importante per le estensioni che richiedono le informazioni di debug. Per altre informazioni e argomenti aggiuntivi, vedere la [documentazione relativa alla classe Flask](https://flask.palletsprojects.com/en/1.0.x/api/#flask.Flask) (flask.pocoo.org).

### <a name="question-can-a-function-have-more-than-one-route-decorator"></a>Domanda: Una funzione può avere più di un elemento Decorator di route?

Risposta: sì, è possibile usare qualsiasi numero di elementi Decorator se si usa la stessa funzione per più route. Ad esempio, per usare la funzione `hello` sia per "/" che per "/ hello", usare il codice seguente:

```python
@app.route('/')
@app.route('/hello')
def hello():
    """Renders a sample page."""
    return "Hello World!"
```

<a name="qa-url-variables"></a>

### <a name="question-how-does-flask-work-with-variable-url-routes-and-query-parameters"></a>Domanda: Come funziona Flask con route di URL e parametri di query variabili?

Risposta: In una route si contrassegna qualsiasi variabile con e Flask passa la variabile alla funzione usando un argomento `<variable_name>` denominato nel percorso URL. Ad esempio, una route nel formato genera `/hello/<name>` un argomento stringa denominato alla funzione `name` . I parametri di query sono disponibili tramite `request.args` la proprietà , in particolare tramite il metodo `request.args.get` . Per altre informazioni, vedere l'[oggetto Request](https://flask.palletsprojects.com/en/1.1.x/quickstart/#the-request-object) nella documentazione di Flask.

```python
# URL: /hello/<name>?message=Have%20a%20nice%20day
@app.route('/hello/<name>')
def hello(name):
    msg = request.args.get('message','')
    return "Hello " + name + "! "+ msg + "."
```

Per modificare il tipo, anteporre alla variabile `int`, `float`, `path` (che accetta le barre per delineare i nomi delle cartelle) e `uuid`. Per informazioni dettagliate, vedere le [regole delle variabili](https://flask.palletsprojects.com/en/1.0.x/quickstart/#variable-rules) nella documentazione di Flask.

### <a name="question-can-visual-studio-generate-a-requirementstxt-file-from-a-virtual-environment-after-i-install-other-packages"></a>Domanda: Visual Studio può generare un file requirements.txt da un ambiente virtuale dopo che si installano altri pacchetti?

Risposta: Sì. Espandere il nodo **Ambienti Python**, fare clic con il pulsante destro del mouse sull'ambiente virtuale e scegliere il comando **Genera requirements.txt**. È utile usare questo comando periodicamente man mano che si modifica l'ambiente e si esegue il commit delle modifiche apportate a *requirements.txt* nel controllo del codice sorgente, insieme a tutte le altre modifiche del codice che dipendono dall'ambiente. Se si configura l'integrazione continua in un server di compilazione, è necessario generare il file ed eseguire il commit delle modifiche ogni volta che si modifica l'ambiente.

## <a name="step-1-5-run-the-project"></a>Passaggio 1-5: Eseguire il progetto

1. In Visual Studio Debug Avvia debug (  >   **F5**) o usare il pulsante Server **Web** sulla barra degli strumenti (il browser visualizzato può variare):

    ![Pulsante di esecuzione del server Web della barra degli strumenti in Visual Studio](media/tutorials-common/run-web-server-toolbar-button.png)

1. Entrambi i comandi assegnano un numero di porta casuale alla variabile di ambiente PORT, quindi eseguono `python app.py`. Il codice avvia l'app usando quella porta all'interno del server di sviluppo di Flask. Se Visual Studio visualizza il messaggio **Impossibile avviare il debugger** perché manca il file di avvio, fare clic con il pulsante destro del mouse su **app.py** in **Esplora soluzioni** e selezionare **Imposta come file di avvio**.

1. All'avvio del server appare una finestra della console in cui è visualizzato il log del server. Visual Studio apre quindi automaticamente un browser per `http://localhost:<port>`, in cui viene visualizzato il messaggio sottoposto a rendering dalla funzione `hello`:

    ![Visualizzazione predefinita del progetto Flask](media/flask/step01-first-run-success.png)

1. Al termine, arrestare il server chiudendo la finestra della console o usando il comando **Debug** Arresta  >   debug in Visual Studio.

### <a name="question-whats-the-difference-between-using-the-debug-menu-commands-and-the-server-commands-on-the-projects-python-submenu"></a>Domanda: Qual è la differenza tra l'uso dei comandi del menu Debug e dei comandi del server nel sottomenu Python del progetto?

Risposta: Oltre ai comandi del menu **Debug** e ai pulsanti della barra degli strumenti, è possibile avviare il server anche usando i comandi **Python** > **Avvia server** o **Python** > **Avvia il server di debug** del menu di scelta rapida del progetto. Entrambi i comandi aprono una finestra della console in cui viene visualizzato l'URL locale (localhost:port) per il server in esecuzione. Tuttavia, è necessario aprire manualmente un browser con l'URL e l'esecuzione del server di debug non avvia automaticamente il debugger di Visual Studio. È possibile collegare un debugger al processo in esecuzione in un secondo momento, se necessario, usando il **comando Esegui debug** connessione  >  **a** processo.

## <a name="next-steps"></a>Passaggi successivi

A questo punto, il progetto Flask di base contiene il codice di avvio e il codice della pagina nello stesso file. È consigliabile separare questi due concetti e separare anche HTML e dati usando i modelli.

> [!div class="nextstepaction"]
> [Creare un'app Flask con visualizzazioni e modelli di pagina](learn-flask-visual-studio-step-02-create-app.md)

## <a name="go-deeper"></a>Approfondimento

- [Flask Quickstart](https://flask.palletsprojects.com/en/1.0.x/quickstart/) (Avvio rapido di Flask) (flask.pocoo.org)
- Codice sorgente per l'esercitazione su GitHub: [Microsoft/python-sample-vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask)