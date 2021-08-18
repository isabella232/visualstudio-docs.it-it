---
title: "Guida introduttiva: Creare un'app Web Python con Visual Studio"
titleSuffix: ''
description: In questa guida introduttiva vengono usati Visual Studio e il framework Flask per compilare un'app Web semplice in Python.
ms.date: 03/07/2019
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
ms.openlocfilehash: fdb269679162d988db1b90bdb20dae18c2d78ed077742884c2887dc961fae31d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121431381"
---
# <a name="quickstart-create-your-first-python-web-app-using-visual-studio"></a>Guida introduttiva: Creare per la prima volta un'app Web Python con Visual Studio

In questa introduzione di 5-10 minuti a Visual Studio come ambiente di sviluppo integrato di Python viene creata una semplice applicazione Web Python basata sul framework Flask. Il progetto viene creato tramite passaggi discreti che consentono di apprendere le funzionalità di base di Visual Studio.

::: moniker range="vs-2017"

Se non è ancora stato installato Visual Studio, passare alla pagina [Visual Studio download](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) per installarlo gratuitamente. Verificare di selezionare il carico di lavoro **Sviluppo Python** nel programma di installazione.

::: moniker-end

::: moniker range=">=vs-2019"

Se non è ancora stato installato Visual Studio, passare alla pagina [Visual Studio download](https://visualstudio.microsoft.com/downloads) per installarlo gratuitamente. Verificare di selezionare il carico di lavoro **Sviluppo Python** nel programma di installazione.

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

::: moniker range=">=vs-2019"
1. Aprire Visual Studio 2019.
2. Nella schermata iniziale selezionare **Crea un nuovo progetto**.
3. Nella finestra di dialogo **Crea un nuovo progetto** immettere "Web Python" nel campo di ricerca in alto, scegliere **Progetto Web** nell'elenco al centro, quindi selezionare **Avanti**:

    ![Schermata Crea nuovo progetto con visualizzati i progetti Web Python](media/quickstart-python-00-web-project-2019a.png)

    Se i modelli di progetto Python non sono visualizzati,  eseguire il Programma di installazione di Visual Studio , selezionare **Altro** modifica, selezionare il carico di lavoro Sviluppo >  **Python** e quindi **scegliere Modifica.**

    ![Carico di lavoro Sviluppo Python nel programma di installazione di Visual Studio](../python/media/installation-python-workload.png)

4. Nella finestra di dialogo seguente **Configura il nuovo progetto** immettere "HelloPython" in **Nome del progetto**, specificare un percorso e selezionare **Crea**. Il valore in **Nome soluzione** viene impostato automaticamente in modo che corrisponda a **Nome del progetto**.

    ![Finestra Configura il nuovo progetto](media/quickstart-python-00-web-project-2019b.png)

5. Il nuovo progetto viene aperto in **Esplora soluzioni** nel riquadro a destra. In questa fase il progetto è vuoto perché non contiene altri file.

    ![Esplora soluzioni con il progetto vuoto appena creato](media/quickstart-python-01-empty-project-2019.png)
::: moniker-end

**Domanda: Qual è il vantaggio della creazione di un progetto in Visual Studio per un'applicazione Python?**

**Risposta**: per definire le applicazioni Python, si usano in genere solo file e cartelle, ma questa semplice struttura può diventare complessa se le dimensioni delle applicazioni aumentano e interessano magari anche file generati automaticamente, JavaScript per le applicazioni Web e così via. Un progetto di Visual Studio aiuta a gestire questa complessità. Il progetto, un file con estensione *pyproj*, identifica tutti i file di origine e di contenuto associati al progetto, contiene le informazioni di compilazione relative a ogni file, gestisce le informazioni per l'integrazione con sistemi di controllo del codice sorgente e consente di organizzare l'applicazione in componenti logici.

**Domanda: qual è la "soluzione" visualizzata in Esplora soluzioni?**

**Risposta**: la soluzione di Visual Studio è un contenitore che consente di gestire uno o più progetti correlati come gruppo e archivia le impostazioni di configurazione non specifiche di un solo progetto. I progetti in una soluzione possono anche fare riferimento l'uno all'altro, facendo sì che l'esecuzione di un progetto (un'app Python) compili automaticamente un secondo progetto (ad esempio, un'estensione C++ usata nell'app Python).

## <a name="install-the-flask-library"></a>Installare la libreria Flask

Le app Web in Python usano quasi sempre una delle molte librerie Python disponibili per la gestione dei dettagli di basso livello, quali l'inoltro delle richieste Web e la definizione delle risposte. A tale scopo, Visual Studio offre una varietà di modelli per le app Web, uno dei quali verrà usato più avanti in questa guida introduttiva.

Con la procedura seguente verrà installata la libreria Flask nell'"ambiente globale"predefinito usato da Visual Studio per questo progetto.

::: moniker range="vs-2017"
1. Espandere il nodo **Ambienti Python** del progetto per visualizzare l'ambiente predefinito per il progetto.

    ![Ambiente predefinito visualizzato in Esplora soluzioni](media/quickstart-python-02-default-environment.png)

2. Fare clic con il pulsante destro del mouse **sull'ambiente e scegliere Installa pacchetto Python.** Questo comando apre la finestra **Ambienti Python** nella scheda **Pacchetti**.

3. Immettere "flask" nel campo di ricerca e selezionare **pip install flask from PyPI**. Accettare le richieste relative ai privilegi di amministratore e osservare nella finestra **Output** di Visual Studio lo stato dell'operazione. (Un prompt dei comandi per l'elevazione dei privilegi viene visualizzato quando la cartella dei pacchetti per l'ambiente globale si trova all'interno di un'area protetta come *C:\Programmi*.)

    ![Installazione della libreria Flask con pip](media/quickstart-python-03-install-package.png)
::: moniker-end
::: moniker range=">=vs-2019"
1. Espandere il nodo **Ambienti Python** del progetto per visualizzare l'ambiente predefinito per il progetto.

    ![Ambiente predefinito visualizzato in Esplora soluzioni](media/quickstart-python-02-default-environment-2019.png)

2. Fare clic con il pulsante destro del mouse **sull'ambiente e scegliere Gestisci pacchetti Python.** Questo comando apre la **finestra Ambienti Python** nella scheda Pacchetti **(PyPI).**

3. Immettere "flask" nel campo di ricerca. Se **Flask** viene visualizzato sotto la casella di ricerca, è possibile ignorare questo passaggio. In caso contrario, selezionare **Esegui comando: pip install flask**. Accettare le richieste relative ai privilegi di amministratore e osservare nella finestra **Output** di Visual Studio lo stato dell'operazione. (Un prompt dei comandi per l'elevazione dei privilegi viene visualizzato quando la cartella dei pacchetti per l'ambiente globale si trova all'interno di un'area protetta come *C:\Programmi*.)

    ![Installazione della libreria Flask con pip](media/quickstart-python-03-install-package-2019.png)
::: moniker-end

4. Dopo l'installazione la libreria appare nell'ambiente in **Esplora soluzioni** e ciò indica che è possibile usarla nel codice Python.

    ::: moniker range="vs-2017"
    ![Libreria Flask installata e visualizzata in Esplora soluzioni](media/quickstart-python-04-package-installed.png)
    ::: moniker-end
    ::: moniker range=">=vs-2019"
    ![Libreria Flask installata e visualizzata in Esplora soluzioni](media/quickstart-python-04-package-installed-2019.png)
    ::: moniker-end

> [!Note]
> Invece di installare le librerie nell'ambiente globale, gli sviluppatori in genere creano un "ambiente virtuale" in cui installare le librerie per un progetto specifico. I modelli di Visual Studio offrono in genere questa opzione, come descritto in [Guida introduttiva: creare un progetto Python da un modello](../python/quickstart-02-python-in-visual-studio-project-from-template.md).

**Domanda: dove è possibile trovare altre informazioni su altri pacchetti Python disponibili?**

**Risposta**: visitare la pagina [Python Package Index](https://pypi.org/) (Indice dei pacchetti Python).

## <a name="add-a-code-file"></a>Aggiungere un file di codice

A questo punto si aggiunge un frammento di codice Python per implementare un'app Web elementare.

1. Fare clic con il pulsante destro del mouse **sul Esplora soluzioni** e scegliere > **Nuovo elemento**.

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

1. Si è forse notato che nella finestra di dialogo **Aggiungi > Nuovo elemento** vengono visualizzati molti altri tipi di file che è possibile aggiungere a un progetto Python: classe Python, pacchetto Python, unit test Python, file *web.config* e altro ancora. Questi modelli di elemento, come vengono chiamati, rappresentano in genere un ottimo modo per creare rapidamente file con codice boilerplate utile.

**Domanda: dove si possono trovare altre informazioni su Flask?**

**Risposta**: fare riferimento alla documentazione di Flask, iniziando dalla [guida introduttiva di Flask](https://flask.palletsprojects.com/en/1.1.x/quickstart/#quickstart).

## <a name="run-the-application"></a>Eseguire l'applicazione

1. Fare clic con il pulsante destro del mouse su *app.py* in **Esplora soluzioni** e selezionare **Imposta come file di avvio**. Questo comando identifica il file di codice da avviare in Python quando si esegue l'app.

    ::: moniker range="vs-2017"
    ![Impostazione del file di avvio per un progetto in Esplora soluzioni](media/quickstart-python-05-set-as-startup-file.png)
    ::: moniker-end
    ::: moniker range=">=vs-2019"
    ![Impostazione del file di avvio per un progetto in Esplora soluzioni](media/quickstart-python-05-set-as-startup-file-2019.png)
    ::: moniker-end

2. Fare clic con il pulsante destro del mouse **sul Esplora soluzioni** e **scegliere Proprietà.** Selezionare quindi la scheda **Debug** e impostare la proprietà **Numero porta** su `4449`. Questo passaggio garantisce che Visual Studio avvii un browser con `localhost:4449` per creare una corrispondenza con gli argomenti `app.run` nel codice.

3. Selezionare **Debug > Avvia senza eseguire debug** (**CTRL**+**F5**) che consente di salvare le modifiche ai file ed esegue l'app.

4. Viene visualizzata una finestra di comando con il messaggio In esecuzione **in https: \/ /localhost:4449** e viene aperta una finestra del browser in cui viene visualizzato il messaggio `localhost:4449` "Hello, Python!" Nella finestra di comando viene visualizzata anche la richiesta GET con stato uguale a 200.

    Se il browser non si apre automaticamente, avviare un browser a scelta e passare a `localhost:4449`.

    Se la finestra di comando visualizza solo la shell interattiva Python o se la finestra lampeggia brevemente sullo schermo, verificare di aver impostato *app.py* come file di avvio nel passaggio 1 precedente.

5. Passare a `localhost:4449/hello` per verificare che anche l'elemento Decorator per la risorsa `/hello` funzioni. Nella finestra di comando viene visualizzata di nuovo la richiesta GET con stato uguale a 200. È possibile provare anche altri URL. Sì vedrà che nella finestra di comando viene visualizzato il codice di stato 404.

6. Chiudere la finestra di comando per arrestare l'applicazione, quindi chiudere la finestra del browser.

**Domanda: qual è la differenza tra i comandi Avvia senza eseguire debug e Avvia debug?**

**Risposta**: **Avvia debug** si usa per eseguire l'app nel contesto del [debugger di Visual Studio](../python/debugging-python-in-visual-studio.md), che consente di impostare punti di interruzione, esaminare le variabili ed eseguire il codice riga per riga. Nel debugger le app possono essere più lente a causa dei vari hook che rendono possibile il debug. **Avvia senza eseguire debug**, al contrario, esegue l'app direttamente come se la si eseguisse dalla riga di comando, senza alcun contesto di debug, avviando anche automaticamente un browser e passando all'URL specificato nella scheda **Debug** delle proprietà del progetto.

## <a name="next-steps"></a>Passaggi successivi

È stata eseguita la prima app Python in Visual Studio. In questo modo si sono apprese alcune informazioni sull'uso di Visual Studio come ambiente di sviluppo integrato per Python.

> [!div class="nextstepaction"]
> [Distribuire l'app nel servizio app di Azure](../python/publishing-python-web-applications-to-azure-from-visual-studio.md)

I passaggi eseguiti in questa guida introduttiva sono piuttosto generici e si è probabilmente capito che questi passaggi possono e devono essere automatizzati. Tale automazione è il ruolo dei modelli di progetto di Visual Studio. Scegliere la [Guida introduttiva: Creare un progetto Python da un modello](../python/quickstart-02-python-in-visual-studio-project-from-template.md) per una dimostrazione in cui viene creata un'app Web simile a quella creata in questo articolo, ma con un numero minore di passaggi.

Per proseguire con un'esercitazione completa relativa a Python in Visual Studio, che include l'uso della finestra interattiva, il debug, la visualizzazione dei dati e l'uso di Git, scegliere l'esercitazione [Uso di Python in Visual Studio](../python/tutorial-working-with-python-in-visual-studio-step-01-create-project.md).

Per esplorare in modo più approfondito ciò che Visual Studio può offrire, selezionare i collegamenti seguenti.

- Informazioni sui [modelli di app Web Python in Visual Studio](../python/python-web-application-project-templates.md).
- Informazioni su [debug Python](../python/debugging-python-in-visual-studio.md)
- Altre informazioni sull'[ambiente di sviluppo integrato di Visual Studio](../get-started/visual-studio-ide.md) in genere.
