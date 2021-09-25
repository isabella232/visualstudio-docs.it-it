---
title: "Guida introduttiva: Creare un'app Web Python con Visual Studio"
titleSuffix: ''
description: In questa guida introduttiva vengono usati Visual Studio e il framework Flask per compilare un'app Web semplice in Python.
ms.date: 09/14/2021
ms.technology: vs-python
ms.topic: quickstart
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom:
- vs-acquisition
- SEO-VS-2020
ms.workload:
- python
- data-science
ms.openlocfilehash: 817a7fed100c9095468c3c481417a3f53104c3ee
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2021
ms.locfileid: "128429441"
---
# <a name="quickstart-create-your-first-python-web-app-using-visual-studio"></a>Guida introduttiva: Creare per la prima volta un'app Web Python con Visual Studio

In questa introduzione di 5-10 minuti a Visual Studio come ambiente di sviluppo integrato di Python viene creata una semplice applicazione Web Python basata sul framework Flask. Il progetto viene creato tramite passaggi discreti che consentono di apprendere le funzionalità di base di Visual Studio.

::: moniker range="vs-2017"

Se non è ancora stato installato Visual Studio, passare alla pagina [Visual Studio download](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) per installarlo gratuitamente. Verificare di selezionare il carico di lavoro **Sviluppo Python** nel programma di installazione.

::: moniker-end

::: moniker range="vs-2019"

Se non è ancora stato installato Visual Studio, passare alla pagina [Visual Studio download](https://visualstudio.microsoft.com/downloads) per installarlo gratuitamente. Verificare di selezionare il carico di lavoro **Sviluppo Python** nel programma di installazione.

::: moniker-end

::: moniker range=">=vs-2022"

Se non è ancora stato installato Visual Studio, passare alla pagina [Visual Studio download](https://visualstudio.microsoft.com/downloads) per installarlo gratuitamente. Nell'Programma di installazione di Visual Studio selezionare il carico di **lavoro Sviluppo Python** e nei dettagli dell'installazione selezionare Supporto Web **Python.**

![Screenshot dell'Programma di installazione di Visual Studio con il carico di lavoro Sviluppo Python e il supporto Web Python selezionati.](media/vs-2022/python-web.png)

::: moniker-end

## <a name="create-the-project"></a>Creare il progetto

La procedura seguente crea un progetto vuoto che funge da contenitore per l'applicazione:

::: moniker range="vs-2017"
1. Aprire Visual Studio 2017.

2. Nella barra dei menu scegliere **File > Nuovo > Progetto**.

3. Nella finestra di dialogo **Nuovo progetto** immettere "Python Web Project" nel campo di ricerca in alto a destra, scegliere **Progetto Web** nell'elenco al centro, assegnare al progetto un nome, ad esempio "HelloPython" e quindi scegliere **OK**.

    ![Finestra di dialogo Nuovo progetto con visualizzati i progetti Web Python](media/quickstart-python-00-web-project.png)

    Se i modelli di progetto Python non sono visualizzati,  eseguire il Programma di installazione di Visual Studio , selezionare **Altro** modifica, selezionare il carico di lavoro Sviluppo >  **Python** e quindi **scegliere Modifica.**

    ![Carico di lavoro Sviluppo Python nel programma di installazione di Visual Studio](../python/media/installation-python-workload.png)

4. Il nuovo progetto viene aperto in **Esplora soluzioni** nel riquadro a destra. In questa fase il progetto è vuoto perché non contiene altri file.

    ![Esplora soluzioni con il progetto vuoto appena creato](media/quickstart-python-01-empty-project.png)
::: moniker-end

::: moniker range="vs-2019"
1. Aprire Visual Studio 2019.
2. Nella schermata iniziale selezionare **Crea un nuovo progetto**.
3. Nella finestra di dialogo **Crea un nuovo progetto** immettere "Web Python" nel campo di ricerca in alto, scegliere **Progetto Web** nell'elenco al centro, quindi selezionare **Avanti**:

    ![Schermata Crea un nuovo progetto con l'opzione Python Web Project selezionata Se non vengono visualizzati i modelli di progetto Python, eseguire il Programma di installazione di Visual Studio , selezionare Altro modifica, selezionare il carico di lavoro Sviluppo Python e quindi scegliere ](media/quickstart-python-00-web-project-2019a.png)   >  **Modifica.** 

    ![Carico di lavoro Sviluppo Python nel programma di installazione di Visual Studio](../python/media/installation-python-workload.png)

4. Nella finestra di dialogo seguente **Configura il nuovo progetto** immettere "HelloPython" in **Nome del progetto**, specificare un percorso e selezionare **Crea**. Il valore in **Nome soluzione** viene impostato automaticamente in modo che corrisponda a **Nome del progetto**.

    ![Finestra Configura il nuovo progetto](media/quickstart-python-00-web-project-2019b.png)

5. Il nuovo progetto viene aperto in **Esplora soluzioni** nel riquadro a destra. In questa fase il progetto è vuoto perché non contiene altri file.

    ![Sreenshot che mostra il progetto vuoto appena creato nella Esplora soluzioni.](media/quickstart-python-01-empty-project-2019.png)

::: moniker-end

::: moniker range=">=vs-2022"
1. Aprire Visual Studio 2022.
1. Nella schermata iniziale selezionare **Crea un nuovo progetto**.
1. Nella finestra **di dialogo Crea un nuovo** progetto immettere "Web Python" nel campo di ricerca nella parte superiore. Scegliere **Web Project** dall'elenco e quindi selezionare **Avanti:**
   
   ![Screenshot che mostra la schermata Crea un nuovo progetto con l'opzione Project Python selezionata.](media/vs-2022/python-web-project.png)
   
   Se i modelli di progetto Web Python non sono visualizzati, selezionare Strumenti Ottieni strumenti e funzionalità per eseguire il  >   Programma di installazione di Visual Studio. Nel programma di installazione selezionare il carico **di lavoro Sviluppo Python** e in Dettagli **installazione** selezionare Supporto **Web Python.** Selezionare quindi **Modifica**.

1. Nella finestra **di dialogo Configura** il nuovo progetto immettere "HelloPython" Project nome, specificare un percorso e quindi selezionare **Crea.**  Il **nome della soluzione** viene aggiornato automaticamente in modo che corrisponda Project nome **.**

   ![Screenshot che mostra la finestra di dialogo Configura il nuovo progetto.](media/vs-2022/configure-project.png)

Il nuovo progetto viene aperto in **Esplora soluzioni** nel riquadro a destra. In questa fase il progetto è vuoto perché non contiene altri file.

![Screenshot che mostra la Esplora soluzioni con il progetto vuoto appena creato.](media/vs-2022/solution-explorer.png)
::: moniker-end

**Domanda: Qual è il vantaggio della creazione di un progetto in Visual Studio per un'applicazione Python?**

**Risposta:** Le applicazioni Python vengono in genere definite usando solo cartelle e file, ma questa semplice struttura può diventare problematica con l'aumentare delle dimensioni delle applicazioni. Le applicazioni possono includere file generati automaticamente, JavaScript per applicazioni Web e altri componenti. Un progetto di Visual Studio aiuta a gestire questa complessità.

Il progetto, un file *con estensione pyproj,* identifica tutti i file di origine e di contenuto associati al progetto. Il file *con estensione pyproj* contiene informazioni di compilazione per ogni file, gestisce le informazioni per l'integrazione con i sistemi di controllo del codice sorgente e consente di organizzare l'applicazione in componenti logici.

**Domanda: qual è la "soluzione" visualizzata in Esplora soluzioni?**

**Risposta:** una Visual Studio soluzione è un contenitore che consente di gestire uno o più progetti correlati come gruppo. La soluzione archivia le impostazioni di configurazione non specifiche di un progetto. I progetti in una soluzione possono anche fare riferimento l'uno all'altro. Ad esempio, l'esecuzione di un progetto di app Python può compilare automaticamente un secondo progetto, ad esempio un'estensione C++ che viene utilizzata dall'app Python.

## <a name="install-the-flask-library"></a>Installare la libreria Flask

Le app Web in Python usano quasi sempre una delle molte librerie Python disponibili per la gestione dei dettagli di basso livello, quali l'inoltro delle richieste Web e la definizione delle risposte. Visual Studio offre molti modelli per le app Web. Uno di questi modelli verrà utilizzato più avanti in questa guida introduttiva.

Usare la procedura seguente per installare la libreria Flask nell'ambiente globale predefinito *che* Visual Studio per questo progetto.

::: moniker range="vs-2017"
1. Espandere il nodo **Ambienti Python** del progetto per visualizzare l'ambiente predefinito per il progetto.

    ![Ambiente predefinito visualizzato in Esplora soluzioni](media/quickstart-python-02-default-environment.png)

2. Fare clic con il pulsante destro del mouse **sull'ambiente e scegliere Installa pacchetto Python.** Questo comando apre la finestra **Ambienti Python** nella scheda **Pacchetti**.

3. Immettere "flask" nel campo di ricerca e selezionare **pip install flask from PyPI**. Accettare le richieste relative ai privilegi di amministratore e osservare nella finestra **Output** di Visual Studio lo stato dell'operazione. (Un prompt dei comandi per l'elevazione dei privilegi viene visualizzato quando la cartella dei pacchetti per l'ambiente globale si trova all'interno di un'area protetta come *C:\Programmi*.)

    ![Installazione della libreria Flask con pip](media/quickstart-python-03-install-package.png)
::: moniker-end
::: moniker range="vs-2019"
1. Espandere il nodo **Ambienti Python** del progetto per visualizzare l'ambiente predefinito per il progetto.

    ![Ambiente predefinito visualizzato in Esplora soluzioni](media/quickstart-python-02-default-environment-2019.png)

2. Fare clic con il pulsante destro del mouse **sull'ambiente e scegliere Gestisci pacchetti Python.** Questo comando apre la **finestra Ambienti Python** nella scheda Pacchetti **(PyPI).**

3. Immettere "flask" nel campo di ricerca. Se **Flask** viene visualizzato sotto la casella di ricerca, è possibile ignorare questo passaggio. In caso contrario, selezionare **Esegui comando: pip install flask**. Accettare le richieste relative ai privilegi di amministratore e osservare nella finestra **Output** di Visual Studio lo stato dell'operazione. (Un prompt dei comandi per l'elevazione dei privilegi viene visualizzato quando la cartella dei pacchetti per l'ambiente globale si trova all'interno di un'area protetta come *C:\Programmi*.)

    ![Installazione della libreria Flask con pip](media/quickstart-python-03-install-package-2019.png)
::: moniker-end

::: moniker range=">=vs-2022"
1. Espandere il nodo **Ambienti Python** del progetto per visualizzare l'ambiente predefinito per il progetto.

    ![Screenshot che mostra l'ambiente predefinito in Esplora soluzioni.](media/vs-2022/python-environment.png)

1. Fare clic con il pulsante destro del mouse **sull'ambiente e scegliere Gestisci pacchetti Python**. Questo comando aprirà la finestra **Ambienti Python** nella scheda **Pacchetti (PyPI)**.

1. Immettere "flask" nel campo di ricerca. Se **Flask** viene visualizzato sotto la casella di ricerca, è possibile ignorare questo passaggio. In caso contrario, **selezionare Esegui comando: pip install flask**.

    ![Screenshot che mostra l'installazione della libreria Flask con pip install.](media/vs-2022/install-flask.png)

    Se la cartella dei pacchetti dell'ambiente globale si trova in un'area protetta, ad esempio *C:\Programmi*, viene visualizzata una richiesta di elevazione dei privilegi. Accettare tutte le indicazioni per i privilegi di amministratore. Osservare la finestra Visual Studio **Output** per lo stato di avanzamento.

::: moniker-end

Dopo l'installazione, la libreria viene visualizzata **nell'ambiente Esplora soluzioni**, il che significa che è possibile usarla nel codice Python.

::: moniker range="vs-2017"
![Libreria Flask installata e visualizzata in Esplora soluzioni](media/quickstart-python-04-package-installed.png)
::: moniker-end
::: moniker range="vs-2019"
![Libreria Flask installata e visualizzata in Esplora soluzioni](media/quickstart-python-04-package-installed-2019.png)
::: moniker-end
::: moniker range=">=vs-2022"
![Screenshot che mostra la libreria Flask installata e visualizzata in Esplora soluzioni.](media/vs-2022/flask-installed.png)
::: moniker-end

> [!Note]
> Invece di installare le librerie nell'ambiente globale, gli sviluppatori in genere creano un "ambiente virtuale" in cui installare le librerie per un progetto specifico. I modelli di Visual Studio offrono in genere questa opzione, come descritto in [Guida introduttiva: creare un progetto Python da un modello](../python/quickstart-02-python-in-visual-studio-project-from-template.md).

**Domanda: dove è possibile trovare altre informazioni su altri pacchetti Python disponibili?**

**Risposta**: visitare la pagina [Python Package Index](https://pypi.org/) (Indice dei pacchetti Python).

## <a name="add-a-code-file"></a>Aggiungere un file di codice

A questo punto si aggiunge un frammento di codice Python per implementare un'app Web elementare.

::: moniker range="<=vs-2019"
1. Fare clic con il pulsante destro del mouse **sul Esplora soluzioni** e **scegliere Aggiungi** > **nuovo elemento.**

1. Nella finestra di dialogo visualizzata selezionare **File Python vuoto**, assegnare al file il nome *app.py* e selezionare **Aggiungi**. Visual Studio apre automaticamente il file in una finestra dell'editor.

1. Copiare il codice seguente e incollarlo in *app.py*:

    ```python
    from flask import Flask

    # Create an instance of the Flask class that is the WSGI application.
    # The first argument is the name of the application module or package,
    # typically __name__ when using a single module.
    app = Flask(__name__)

    # Flask route decorators map / and /hello to the hello function.
    # To add other resources, create functions that generate the page contents
    # and add decorators to define the appropriate resource locators for them.

    @app.route('/')
    @app.route('/hello')
    def hello():
        # Render the page
        return "Hello Python!"

    if __name__ == '__main__':
        # Run the app server on localhost:4449
        app.run('localhost', 4449)
    ```
::: moniker-end
::: moniker range=">= vs-2022"

1. Fare clic con il pulsante destro del mouse **sul Esplora soluzioni** e **scegliere Aggiungi** > **nuovo elemento.**

1. Nella finestra di dialogo visualizzata selezionare **vuoto.** Per **Nome** immettere *app.py* e quindi selezionare **Aggiungi.** Visual Studio apre automaticamente il file in una finestra dell'editor.

1. Copiare il codice seguente e incollarlo in *app.py*:

    ```python
    from flask import Flask

    # Create an instance of the Flask class that is the WSGI application.
    # The first argument is the name of the application module or package,
    # typically __name__ when using a single module.
    app = Flask(__name__)

    # Flask route decorators map / and /hello to the hello function.
    # To add other resources, create functions that generate the page contents
    # and add decorators to define the appropriate resource locators for them.

    @app.route('/')
    @app.route('/hello')
    def hello():
        # Render the page
        return "Hello Python!"

    if __name__ == '__main__':
        # Run the app server on localhost:4449
        app.run('localhost', 4449)
    ```
::: moniker-end

Si sarà notato che la finestra di dialogo Aggiungi nuovo elemento visualizza molti altri tipi di file che è possibile aggiungere a un progetto Python, tra cui una classe Python, un pacchetto Python, un unit test Python, fileweb.confige altro  >   ancora.  In generale, questi *modelli di elemento* sono un ottimo modo per creare rapidamente file con codice boilerplate utile.

**Domanda: dove si possono trovare altre informazioni su Flask?**

**Risposta**: fare riferimento alla documentazione di Flask, iniziando dalla [guida introduttiva di Flask](https://flask.palletsprojects.com/quickstart/#quickstart).

## <a name="run-the-application"></a>Eseguire l'applicazione

1. In **Esplora soluzioni** fare clic con il pulsante destro *del* app.py e quindi scegliere Imposta **come file** di avvio dal menu a discesa. Questo comando identifica il file di codice da avviare in Python quando si esegue l'app.

    ::: moniker range="vs-2017"
    ![Impostazione del file di avvio per un progetto in Esplora soluzioni](media/quickstart-python-05-set-as-startup-file.png)
    ::: moniker-end
    ::: moniker range="vs-2019"
    ![Impostazione del file di avvio per un progetto in Esplora soluzioni](media/quickstart-python-05-set-as-startup-file-2019.png)
    ::: moniker-end
    ::: moniker range=">=vs-2022"
    ![Screenshot che mostra l'impostazione del file di avvio per un progetto in Esplora soluzioni.](media/vs-2022/set-startup-file.png)
    ::: moniker-end

2. Fare clic con il pulsante destro del mouse **sul Esplora soluzioni** e **scegliere Proprietà.** Selezionare la **scheda Debug** dal menu **Proprietà** e impostare la proprietà **Numero di** porta su `4449` . Questa impostazione garantisce che Visual Studio avvii un browser con in modo che `localhost:4449` corrisponda agli argomenti nel `app.run` codice.

3. Selezionare **Avvia**  >  **debug senza eseguire** debug o premere **CTRL** + **F5** per salvare le modifiche ai file ed eseguire l'app.

4. Viene visualizzata una finestra di comando con il **messaggio In esecuzione in https: \/ /localhost:4449**. Viene visualizzata una finestra del browser `localhost:4449` in cui viene visualizzato il messaggio **Hello, Python!** La `GET` richiesta viene visualizzata anche nella finestra di comando con stato `200` .

    Se un browser non si apre automaticamente, avviare il browser preferito e passare a `localhost:4449` .

    Se nella finestra di comando viene visualizzata solo la shell interattiva di Python o  se la finestra lampeggia brevemente sullo schermo, assicurarsi che app.py sia impostato come file di avvio.

5. Passare a `localhost:4449/hello` per verificare che anche l'elemento Decorator per la risorsa `/hello` funzioni. Anche in questo `GET` caso, la richiesta viene visualizzata nella finestra di comando con stato `200` . Provare anche altri URL per verificare che mostrino i `404` codici di stato nella finestra di comando.

6. Chiudere la finestra di comando per arrestare l'app e quindi chiudere la finestra del browser.

**Domanda: Qual è la differenza tra i comandi Avvia senza eseguire debug e Avvia debug?**

**Risposta:** Usare Avvia **debug per** eseguire l'app nel contesto del debugger [Visual Studio .](../python/debugging-python-in-visual-studio.md) Con il debugger è possibile impostare punti di interruzione, esaminare le variabili ed eseguire il codice riga per riga. Le app potrebbero risultare più lente nel debugger a causa degli hook che rendono possibile il debug.

**Avvia senza eseguire debug** esegue l'app direttamente, come se fosse stata eseguita dalla riga di comando, senza contesto di debug. **Avvia senza eseguire debug** avvia automaticamente anche un browser e passa all'URL specificato nella scheda Debug delle **proprietà del** progetto.

## <a name="next-steps"></a>Passaggi successivi

Congratulazioni per l'esecuzione della prima app Python da Visual Studio. Si è appreso un po' di come usare Visual Studio come IDE Python.

> [!div class="nextstepaction"]
> [Distribuire l'app nel servizio app di Azure](../python/publishing-python-web-applications-to-azure-from-visual-studio.md)

I passaggi eseguiti in questa guida introduttiva sono piuttosto generici e si è probabilmente capito che questi passaggi possono e devono essere automatizzati. Tale automazione è il ruolo dei modelli di progetto di Visual Studio. Vedere [Avvio rapido - Creare un](../python/quickstart-02-python-in-visual-studio-project-from-template.md) progetto Python usando un modello per creare un'app Web simile a quella descritta in questo articolo, ma con meno passaggi.

Per continuare con un'esercitazione più completa su Python in Visual Studio, tra cui l'uso della finestra interattiva, il debug, la visualizzazione dei dati e l'uso di Git, seguire [Esercitazione:](../python/tutorial-working-with-python-in-visual-studio-step-01-create-project.md)Introduzione a Python in Visual Studio .

Per esplorare in modo più approfondito ciò che Visual Studio può offrire, selezionare i collegamenti seguenti.

- Informazioni sui [modelli di app Web Python in Visual Studio](../python/python-web-application-project-templates.md).
- Informazioni su [debug Python](../python/debugging-python-in-visual-studio.md)
- Altre informazioni sull'[ambiente di sviluppo integrato di Visual Studio](../get-started/visual-studio-ide.md) in genere.
