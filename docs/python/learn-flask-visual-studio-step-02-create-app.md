---
title: Esercitazione - Informazioni su Flask in Visual Studio, passaggio 2
description: Procedura dettagliata dei concetti di base relativi a Flask nel contesto dei progetti di Visual Studio, che illustra in particolare i passaggi della creazione di un'app e dell'uso di visualizzazioni e modelli.
ms.date: 06/04/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 9aeba681e1a4ab7bae77197d8af10a90f49a40d0
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34752159"
---
# <a name="tutorial-step-2-create-a-flask-app-with-views-and-page-templates"></a>Esercitazione, passaggio 2: Creare un'app Flask con visualizzazioni e modelli di pagina

**Passaggio precedente: [Creare un progetto e una soluzione di Visual Studio](learn-flask-visual-studio-step-01-project-solution.md)**

Il risultato del passaggio 1 di questa esercitazione è un'app Flask con una sola pagina e tutto il codice in un unico file. Per consentire lo sviluppo futuro, è consigliabile effettuare il refactoring del codice e creare una struttura per i modelli di pagina. In particolare, è opportuno separare il codice per le visualizzazioni dell'app da altri aspetti, ad esempio il codice di avvio.

In questo passaggio viene descritto come:

> [!div class="checklist"]
> - Effettuare il refactoring del codice dell'app per separare le visualizzazioni dal codice di avvio (passaggio 2-1)
> - Eseguire il rendering di una visualizzazione usando un modello di pagina (passaggio 2-2)

## <a name="step-2-1-refactor-the-project-to-support-further-development"></a>Passaggio 2-1: Effettuare il refactoring del progetto per supportare un ulteriore sviluppo

Nel codice creato usando il modello "Progetto Web Flask vuoto" si ha un unico file `app.py` che contiene il codice di avvio insieme a una singola visualizzazione. Per consentire un ulteriore sviluppo di un'app con più visualizzazioni e modelli, è consigliabile separare questi concetti.

1. Nella cartella del progetto creare una cartella dell'app denominata `HelloFlask` facendo clic con il pulsante destro del mouse sul progetto in **Esplora soluzioni** e selezionando **Aggiungi** > **Nuova cartella**.

1. Nella cartella `HelloFlask` creare un file denominato `__init.py__` con il contenuto seguente, che crea l'istanza `Flask` e carica le visualizzazioni dell'app (create nel passaggio successivo):

    ```python
    from flask import Flask
    app = Flask(__name__)

    import HelloFlask.views
    ```

1. Nella cartella `HelloFlask` creare un file denominato `views.py` con il seguente contenuto. Il nome `views.py` è importante perché si è usato `import HelloFlask.views` all'interno di `__init__.py`: se i nomi non corrispondono, verrà visualizzato un errore in fase di esecuzione.

    ```python
    from flask import Flask
    from HelloFlask import app

    @app.route('/')
    @app.route('/home')
    def home():
        return "Hello Flask!"
    ```

    Oltre alla rinominare la funzione e la route in `home`, questo codice contiene il codice di rendering della pagina di app.py e importa l'oggetto `app` dichiarato in `__init__.py`.

1. In `HelloFlask` creare la sottocartella `templates`, che per il momento rimane vuota.

1. Nella cartella radice del progetto rinominare `app.py` in `runserver.py` e fare in modo che il contenuto corrisponda al codice seguente:

    ```python
    import os
    from HelloFlask import app    # Imports the code from HelloFlask/__init__.py

    if __name__ == '__main__':
        HOST = os.environ.get('SERVER_HOST', 'localhost')

        try:
            PORT = int(os.environ.get('SERVER_PORT', '5555'))
        except ValueError:
            PORT = 5555

        app.run(HOST, PORT)
    ```
1. La struttura del progetto avrà un aspetto simile all'immagine seguente:

    ![Struttura del progetto dopo il refactoring del codice](media/flask/step02-project-structure.png)

1. Selezionare **Debug** > **Avvia debug** (F5) o usare il pulsante **Server Web** sulla barra degli strumenti (il browser visualizzato può variare) per avviare l'app e aprire un browser. Provare entrambe le route dell'URL / e /home.

1. È inoltre possibile impostare punti di interruzione in varie parti del codice e riavviare l'app per seguire la sequenza di avvio. Ad esempio, impostare un punto di interruzione nelle prime righe di `runserver.py` e `HelloFlask\__init__.py` e nella riga `return "Hello Flask!"` in `views.py`. Quindi riavviare l'app (**Debug** > **Riavvia**, CTRL+F5 o il pulsante della barra degli strumenti illustrato di seguito) e scorrere il codice (F10) o eseguire l'app da ogni punto di interruzione premendo F5.

    ![Pulsante di riavvio sulla barra degli strumenti per il debug in Visual Studio](media/debugging-restart-toolbar-button.png)

1. Al termine, arrestare l'app.

### <a name="commit-to-source-control"></a>Eseguire il commit nel controllo del codice sorgente

Poiché sono state apportate modifiche al codice e il test delle modifiche è riuscito, questo è il momento più appropriato per esaminare le modifiche ed eseguirne il commit nel controllo del codice sorgente. I passaggi successivi di questa esercitazione indicano i momenti appropriati in cui eseguire un nuovo commit nel controllo del codice sorgente e rimandano a questa sezione.

1. Selezionare il pulsante Modifiche nella parte inferiore di Visual Studio (opzione cerchiata di seguito), che consente di passare a **Team Explorer**.

    ![Pulsante Modifiche per il controllo del codice sorgente sulla barra di stato di Visual Studio](media/flask/step02-source-control-changes-button.png)

1. In **Team Explorer** immettere un messaggio per il commit, ad esempio "Refactoring del codice" e selezionare **Esegui commit di tutto**. Al termine del commit, verrà visualizzato il messaggio "Commit <hash> creato in locale. Sync per condividere le modifiche con il server". Se si vuole eseguire il push delle modifiche nel repository remoto, selezionare **Sync** e quindi **Push** in **Commit in uscita**. È anche possibile accumulare più commit locali prima di eseguire il push in remoto.

    ![Eseguire il push dei commit in remoto in Team Explorer](media/flask/step02-source-control-push-to-remote.png)

### <a name="question-how-frequently-should-one-commit-to-source-control"></a>Domanda: con che frequenza si deve eseguire il commit per il controllo del codice sorgente?

Risposta: il commit delle modifiche del controllo del codice sorgente crea un record nel registro modifiche e un punto in cui è possibile ripristinare il repository, se necessario. Ogni commit può anche essere esaminato per verificare modifiche specifiche. Poiché i commit in Git sono poco costosi, è preferibile eseguire spesso più commit piuttosto che accumulare un numero elevato di modifiche in un singolo commit. Ovviamente non è necessario eseguire il commit di ogni piccola modifica apportata a singoli file. In genere si esegue un commit quando si aggiunge una funzionalità, si modifica di una struttura come in questo passaggio o si effettua il refactoring del codice. Verificare inoltre con gli altri utenti del proprio team qual è il livello di granularità del commit più adatto per tutti.

La frequenza con cui si esegue il commit e la frequenza con cui si esegue il push del commit a un repository remoto sono due concetti diversi. È possibile accumulare più commit nel repository locale prima eseguirne il push al repository remoto. Anche in questo caso, la frequenza con cui si esegue il commit dipende dal modo in cui il team vuole gestire il repository.

## <a name="step-2-2-use-a-template-to-render-a-page"></a>Passaggio 2-2: Usare un modello per il rendering di una pagina

La funzione `home` presente finora in `views.py` genera una sola risposta HTTP in testo normale per la pagina. Tuttavia, la maggior parte delle pagine Web di scenari reali risponde con pagine HTML formattate che spesso includono dati in tempo reale. In effetti, il motivo principale per cui si definisce una visualizzazione usando una funzione è la possibilità di generare il contenuto in modo dinamico.

Poiché il valore restituito per la visualizzazione è una stringa, è possibile compilare qualsiasi codice HTML all'interno di una stringa usando contenuto dinamico. Poiché tuttavia è preferibile separare il markup dai dati, è meglio posizionare il markup in un modello e mantenere i dati nel codice.

1. Per i principianti, modificare `views.py` in modo che contenga il codice seguente che utilizza HTML inline per la pagina con del contenuto dinamico:

    ```python
    from datetime import datetime
    from flask import render_template
    from HelloFlask import app

    @app.route('/')
    @app.route('/home')
    def home():
        now = datetime.now()
        formatted_now = now.strftime("%A, %d %B, %Y at %X")

        html_content = "<html><head><title>Hello Flask</title></head><body>"
        html_content += "<strong>Hello Flask!</strong> on " + formatted_now
        html_content += "</body></html>"

        return html_content
    ```

1. Eseguire l'app e aggiornare la pagina alcune volte per verificare che la data e l'ora siano aggiornate. Al termine, arrestare l'app.

1. Per convertire il rendering della pagina in modo che usi un modello, creare un file denominato `index.html` nella cartella `templates` con il contenuto seguente, dove `{{ content }}` è un segnaposto o un token di sostituzione (detto anche *variabile del modello*) per cui si specifica un valore nel codice:

    ```html
    <html>
        <head><title>Hello Flask</title></head>

        <body>
            {{ content }}
        </body>
    </html>
    ```

1. Modificare la funzione `home` in modo da usare `render_template` per caricare il modello e specificare un valore per "content", operazione che viene eseguita usando un argomento denominato corrispondente al nome del segnaposto. Flask cerca automaticamente i modelli nella cartella `templates`, quindi il token OATH per il modello è relativo a quella cartella:

    ```python
    def home():
        now = datetime.now()
        formatted_now = now.strftime("%A, %d %B, %Y at %X")

        return render_template(
            "index.html",
            content = "<strong>Hello, Flask!</strong> on " + formatted_now)
    ```

1. Eseguire l'app per visualizzare i risultati e osservare che l'HTML inline nel valore `content` non esegue il rendering *come* HTML perché il motore per la creazione dei modelli (Jinja) usa automaticamente caratteri di escape per il contenuto HTML. La sequenza di escape automatica evita vulnerabilità accidentali agli attacchi injection: gli sviluppatori spesso raccolgono l'input da una pagina e lo usano come valore in un'altra usando un segnaposto di modello. L'escape funge anche da promemoria per ricordare che è meglio tenere l'HTML fuori dal codice.

    Di conseguenza, verificare che `templates\index.html` contenga segnaposti distinti per ogni blocco di dati all'interno del markup:

    ```html
    <html>
        <head>
            <title>{{ title }}</title>
        </head>
        <body>
            <strong>{{ message }}</strong>{{ content }}
        </body>
    </html>
    ```

    Aggiornare quindi la funzione `home` per specificare i valori per tutti i segnaposto:

    ```python
    def home():
        now = datetime.now()
        formatted_now = now.strftime("%A, %d %B, %Y at %X")

        return render_template(
            "index.html",
            title = "Hello Flask",
            message = "Hello, Flask!",
            content = " on " + formatted_now)
    ```

1. Eseguire di nuovo l'app per visualizzare l'output correttamente sottoposto a rendering.

    ![Esecuzione dell'app tramite il modello](media/flask/step02-result.png)

1. Eseguire il commit delle modifiche nel controllo del codice sorgente e aggiornare il repository remoto, se si vuole, come descritto nel [passaggio 2-1](#commit-to-source-control).

### <a name="question-do-page-templates-have-to-be-in-a-separate-file"></a>Domanda: I modelli di pagina devono trovarsi in un file separato?

Risposta: Anche se i modelli vengono in genere mantenuti in file HTML separati, è possibile usare anche un modello inline. L'uso di un file distinto è l'opzione consigliata, tuttavia, per mantenere una netta separazione tra il markup e il codice.

### <a name="question-must-templates-use-the-html-file-extension"></a>Domanda: I modelli devono usare l'estensione di file html?

Risposta: l'estensione `.html` per i file di modello di pagina è completamente facoltativa, perché è sempre possibile identificare esattamente il percorso relativo del file nel primo argomento della funzione `render_template`. Tuttavia, Visual Studio (e altri editor) in genere fornisce alcune funzionalità, tra cui il completamento del codice e la colorazione della sintassi, per i file `.html`, che compensano il fatto che i modelli di pagina non sono rigorosamente file HTML.

Infatti, quando si lavora con un progetto Django, Visual Studio rileva automaticamente quando il file HTML che si sta modificando è effettivamente un modello Django e fornisce alcune funzionalità di completamento automatico. Ad esempio, quando si inizia a digitare un commento in un modello di pagina Django, `{#`, Visual Studio fornisce automaticamente i caratteri `#}` di chiusura. Anche i comandi **Commenta selezione** e **Rimuovi commento selezione** (nel menu **Modifica** > **Avanzate** e sulla barra degli strumenti) usano i commenti dei modelli anziché i commenti HTML.

### <a name="question-when-i-run-the-project-i-see-an-error-that-the-template-cannot-be-found-whats-wrong"></a>Domanda: Quando si esegue il progetto, viene visualizzato un errore che indica che non è possibile trovare il modello. Qual è il problema?

Risposta: Se vengono visualizzati errori che indicano che non è possibile trovare il modello, assicurarsi di aver aggiunto l'app al file `settings.py` del progetto Django all'elenco `INSTALLED_APPS`. Senza questa voce, Django non sarà in grado di cercare nella cartella `templates` dell'app.

### <a name="question-can-templates-be-organized-into-further-subfolders"></a>Domanda: i modelli possono essere organizzati in ulteriori sottocartelle?

Risposta: sì, è possibile usare sottocartelle e quindi fare riferimento al percorso relativo in `templates` nelle chiamate a `render_template`. In questo modo si possono creare in modo efficace gli spazi dei nomi per i modelli.

## <a name="next-steps"></a>Passaggi successivi

> [!div class="nextstepaction"]
> [Rendere disponibili file statici, aggiungere pagine e usare l'ereditarietà dei modelli](learn-flask-visual-studio-step-03-serve-static-files-add-pages.md)

## <a name="going-deeper"></a>Approfondimenti

- [Flask Quickstart - Rendering Templates](http://flask.pocoo.org/docs/1.0/quickstart/#rendering-templates) (Avvio rapido di Flask - Rendering dei modelli) (flask.pocoo.org)
- Codice sorgente per l'esercitazione su GitHub: [Microsoft/python-sample-vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask)