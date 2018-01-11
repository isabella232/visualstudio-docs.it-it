---
title: 'Guida introduttiva: Creare per la prima volta un''app Web Python con Visual Studio | Microsoft Docs'
ms.custom: 
ms.date: 12/1/2017"
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: quickstart
ms.devlang: python
author: kraigb
ms.author: kraigb
manager: ghogen
dev_langs: python
ms.workload: python
ms.openlocfilehash: bf0a6e187a98a03d3beed33537fe5244ecd5d35d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="quickstart-use-visual-studio-to-create-your-first-python-web-app"></a>Guida introduttiva: Creare per la prima volta un'app Web Python con Visual Studio

In questa introduzione di 5-10 minuti all'ambiente di sviluppo integrato (IDE) di Visual Studio si creerà una semplice applicazione Web Python. Se non è ancora stato installato Visual Studio, installarlo gratuitamente [qui](http://www.visualstudio.com).

## <a name="create-the-project"></a>Creare il progetto

1. Aprire Visual Studio 2017.

1. Nella barra dei menu scegliere **File > Nuovo > Progetto**.

1. Nel riquadro sinistro della finestra di dialogo **Nuovo progetto** espandere **Altri linguaggi** e selezionare **Python**. Nel riquadro centrale scegliere **Progetto Web**, assegnare al progetto un nome come "HelloPython" e scegliere **OK**.

    Se non vengono visualizzati i modelli di progetto Python, chiudere la finestra di dialogo **Nuovo progetto** e nella barra dei menu in alto scegliere **Strumenti > Ottieni strumenti e funzionalità...** per aprire il programma di installazione di Visual Studio. Scegliere il carico di lavoro **Sviluppo Python**, quindi scegliere **Modifica**.

    ![Carico di lavoro Sviluppo Python nel programma di installazione di Visual Studio](../python/media/installation-python-workload.png)

1. Il nuovo progetto viene aperto in **Esplora soluzioni** nel riquadro a destra. In questa fase il progetto è vuoto perché non contiene altri file.

    ![Esplora soluzioni con il progetto vuoto appena creato](media/quickstart-python-01-empty-project.png)

## <a name="install-the-falcon-library"></a>Installare la libreria Falcon

Le app Web in Python usano quasi sempre una delle molte librerie Python disponibili per la gestione dei dettagli di basso livello, quali l'inoltro delle richieste Web e la definizione delle risposte. Il carico di lavoro di sviluppo Python in Visual Studio offre [un'ampia gamma di modelli per app Web](../python/template-web.md) basati sulle librerie Bottle, Flask e Django.

In questa Guida introduttiva si usa una libreria diversa, [Falcon](https://falconframework.org/), per sperimentare il processo di installazione di un pacchetto e creazione di un'app Web da zero. Per semplicità la procedura seguente installa Falcon nell'ambiente globale predefinito.

1. Espandere il nodo **Ambienti Python** del progetto per visualizzare l'ambiente predefinito per il progetto.

    ![Ambiente predefinito visualizzato in Esplora soluzioni](media/quickstart-python-02-default-environment.png)

1. Fare clic con il pulsante destro del mouse sull'ambiente e scegliere **Installa pacchetto Python**. Questo comando apre la finestra **Ambienti Python** nella scheda **Pacchetti**. Immettere "falcon" nel campo di ricerca e selezionare **"pip install falcon" from PyPI**. Accettare le richieste relative ai privilegi di amministratore e osservare nella finestra **Output** di Visual Studio lo stato dell'operazione.

    ![Installare la libreria Falcon](media/quickstart-python-03-install-package.png)

1. Dopo l'installazione la libreria appare nell'ambiente in **Esplora soluzioni** e ciò indica che è possibile usarla nel codice Python.

    ![Libreria Falcon installata](media/quickstart-python-04-package-installed.png)

Si noti che invece di installare le librerie nell'ambiente globale, gli sviluppatori in genere creano un "ambiente virtuale" in cui installare le librerie per un progetto specifico. Molti modelli di progetto Python in Visual Studio includono un file `requirements.txt` che elenca le librerie da cui dipende il modello. Se si crea un progetto da uno di questi modelli viene attivata automaticamente la creazione di un ambiente virtuale in cui vengono installate le librerie. Per altre informazioni, vedere [Python environments - Virtual environments](../python/python-environments.md#virtual-environments) (Ambienti Python - Ambienti virtuali).

## <a name="add-a-code-file"></a>Aggiungere un file di codice

A questo punto si aggiunge un frammento di codice Python per implementare un'app Web elementare.

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul progetto e scegliere **Aggiungi > Nuovo elemento**. Nella finestra di dialogo visualizzata selezionare **File Python vuoto**, assegnare al file il nome `hello.py` e scegliere **OK**. Visual Studio apre automaticamente il file in una finestra dell'editor. In genere, il comando **Aggiungi > Nuovo elemento** è un modo ideale per aggiungere diversi tipi di file a un progetto, in quanto i modelli di elemento includono spesso codice boilerplate utile.

1. Copiare e incollare o digitare il codice seguente in `hello.py`:

    ```python
    import falcon
    api = falcon.API()

    # In Falcon, define a class for each resource; the on_get 
    # method then handles any GET requests.

    class HelloResource:
        def on_get(self, req, resp):
            resp.status = falcon.HTTP_200  # 200 is the default
            resp.body = "Hello, Python!"

    # Resources are represented by long-lived class instances
    hello = HelloResource()

    # Instruct Falcon to route / and /hello to the HelloResource
    api.add_route('/', hello)
    api.add_route('/hello', hello)

    if __name__ == "__main__":
        from wsgiref.simple_server import make_server

        # Run the web server on localhost:8080
        print("Starting web app server")
        srv = make_server('localhost', 8080, api)
        srv.serve_forever()
    ```

Per altre informazioni su Falcon, vedere la [Guida introduttiva di Falcon](https://falcon.readthedocs.io/en/stable/user/quickstart.html) (falcon.readthedocs.io).

## <a name="run-the-application"></a>Esecuzione dell'applicazione

1. Fare clic con il pulsante destro del mouse su `hello.py` in **Esplora soluzioni** e scegliere **Imposta come file di avvio**. Il comando identifica il file di codice da avviare in Python quando si esegue l'app.

1. Fare clic con il pulsante destro del mouse sul progetto "Hello Python" in **Esplora soluzioni** e scegliere **Proprietà**. Selezionare quindi la scheda **Debug** e impostare la proprietà **Numero porta** su `8080`. Questo passaggio garantisce che Visual Studio avvierà un browser con `localhost:8080` anziché con una porta casuale.

1. Selezionare **Debug > Avvia senza eseguire debug** (CTRL+F5) per salvare le modifiche ai file ed eseguire l'app.

1. Viene visualizzata una finestra di comando con il messaggio "Starting web app server" (Avvio del server app Web in corso), quindi si apre una finestra del browser su `localhost:8080` in cui viene visualizzato il messaggio "Hello, Python!" Nella finestra di comando viene visualizzata anche la richiesta GET. Se la finestra di comando visualizza solo la shell interattiva Python o se la finestra lampeggia brevemente sullo schermo, verificare di aver impostato `hello.py` come file di avvio nel passaggio 1 precedente.

1. Chiudere la finestra di comando per arrestare l'applicazione.

## <a name="next-steps"></a>Passaggi successivi

La procedura della Guida introduttiva è stata completata: si sono appresi alcuni elementi dell'IDE di Visual Studio con Python. Per continuare con un'esercitazione completa relativa a Python in Visual Studio, che include l'uso della finestra interattiva, il debug, la visualizzazione dei dati e l'uso di Git, selezionare il pulsante in basso.

> [!div class="nextstepaction"]
> [Esercitazione: Introduzione a Python in Visual Studio](../python/vs-tutorial-01-01.md).

- Informazioni sui [modelli di app Web Python in Visual Studio](../python/template-web.md)
- Altre informazioni sull'[IDE di Visual Studio](../ide/visual-studio-ide.md)
- Informazioni sull'uso del [debugger di Visual Studio](../debugger/debugger-feature-tour.md)