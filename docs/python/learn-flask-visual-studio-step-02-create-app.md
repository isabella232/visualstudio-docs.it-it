---
title: Informazioni sull'esercitazione Flask in Visual Studio, passaggio 2, visualizzazioni e modelli
titleSuffix: ''
description: Procedura dettagliata dei concetti di base relativi a Flask nel contesto dei progetti di Visual Studio, che illustra in particolare i passaggi della creazione di un'app e dell'uso di visualizzazioni e modelli.
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
ms.openlocfilehash: 124245b4fb0a711fcf680d53b7fc75bc46cbbaaf
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625379"
---
# <a name="step-2-create-a-flask-app-with-views-and-page-templates"></a>Passaggio 2: Creare un'app Flask con visualizzazioni e modelli di pagina

**Passaggio precedente: [Creare un progetto e una soluzione di Visual Studio](learn-flask-visual-studio-step-01-project-solution.md)**

Il risultato del passaggio 1 di questa esercitazione è un'app Flask con una sola pagina e tutto il codice in un unico file. Per consentire lo sviluppo futuro, è consigliabile effettuare il refactoring del codice e creare una struttura per i modelli di pagina. In particolare, è opportuno separare il codice per le visualizzazioni dell'app da altri aspetti, ad esempio il codice di avvio.

In questo passaggio viene descritto come:

> [!div class="checklist"]
> - Effettuare il refactoring del codice dell'app per separare le visualizzazioni dal codice di avvio (passaggio 2-1)
> - Eseguire il rendering di una visualizzazione usando un modello di pagina (passaggio 2-2)

## <a name="step-2-1-refactor-the-project-to-support-further-development"></a>Passaggio 2-1: Effettuare il refactoring del progetto per supportare un ulteriore sviluppo

Nel codice creato usando il modello "Progetto Web Flask vuoto" si ha un unico file *app.py* che contiene il codice di avvio insieme a una singola visualizzazione. Per consentire un ulteriore sviluppo di un'app con più visualizzazioni e modelli, è consigliabile separare questi concetti.

1. Nella cartella del progetto creare una cartella dell'app denominata `HelloFlask` facendo clic con il pulsante destro del mouse sul progetto in **Esplora soluzioni** e selezionando **Aggiungi** > **Nuova cartella**.

2. Nella cartella *HelloFlask* creare un file denominato *\_ \_ init \_ \_ .py* con il contenuto seguente che crea l'istanza e carica le visualizzazioni `Flask` dell'app (create nel passaggio successivo):

    ```python
    from flask import Flask
    app = Flask(__name__)

    import HelloFlask.views
    ```

3. Nella cartella *HelloFlask* creare un file denominato *views.py* con il contenuto seguente. Il nome *views.py* è importante perché è stato usato `import HelloFlask.views` all'interno *\_ \_ di init \_ \_ .py.* Verrà visualizzato un errore in fase di esecuzione se i nomi non corrispondono.

    ```python
    from flask import Flask
    from HelloFlask import app

    @app.route('/')
    @app.route('/home')
    def home():
        return "Hello Flask!"
    ```

    Oltre a rinominare la funzione e la route in , questo codice contiene il codice di rendering della pagina da app.py e importa `home` l'oggetto dichiarato in  `app` *\_ \_ init \_ \_ .py*.

4. In *HelloFlask* creare la sottocartella *templates*, che per il momento rimane vuota.

5. Nella cartella radice del progetto rinominare *app.py* in *runserver.py* e fare in modo che il contenuto corrisponda al codice seguente:

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

6. La struttura del progetto avrà un aspetto simile all'immagine seguente:

    ![Struttura del progetto dopo il refactoring del codice](media/flask/step02-project-structure.png)

7. Selezionare **Debug**  >  **Avvia debug** (**F5**) o usare il pulsante **Server Web** sulla barra degli strumenti (il browser visualizzato può variare) per avviare l'app e aprire un browser. Provare entrambe le route dell'URL / e /home.

8. È inoltre possibile impostare punti di interruzione in varie parti del codice e riavviare l'app per seguire la sequenza di avvio. Ad esempio, impostare un punto di interruzione nelle prime righe di *runserver.py* *e \_ HelloFlask* init_ *.py* e sulla riga `return "Hello Flask!"` in *views.py*. Riavviare quindi l'app (**Riavvio** del debug, CTRL MAIUSC F5 o il pulsante della barra degli strumenti illustrato di seguito) ed eseguire il codice  >    +  + (**F10)** o eseguire da ogni punto di interruzione **usando F5**.

    ![Pulsante di riavvio sulla barra degli strumenti per il debug in Visual Studio](media/debugging-restart-toolbar-button.png)

9. Al termine, arrestare l'app.

### <a name="commit-to-source-control"></a>Eseguire il commit nel controllo del codice sorgente

Poiché sono state apportate modifiche al codice e il test delle modifiche è riuscito, questo è il momento più appropriato per esaminare le modifiche ed eseguirne il commit nel controllo del codice sorgente. I passaggi successivi di questa esercitazione indicano i momenti appropriati in cui eseguire un nuovo commit nel controllo del codice sorgente e rimandano a questa sezione.

1. Selezionare il pulsante Modifiche nella parte inferiore di Visual Studio (opzione cerchiata di seguito), che consente di passare a **Team Explorer**.

    ![Pulsante Modifiche per il controllo del codice sorgente sulla barra di stato di Visual Studio](media/flask/step02-source-control-changes-button.png)

1. In **Team Explorer** immettere un messaggio per il commit, ad esempio "Refactoring del codice" e selezionare **Esegui commit di tutto**. Al termine del commit, viene visualizzato un messaggio **Commit \<hash> creato in locale. Eseguire la sincronizzazione per condividere le modifiche con il server.** Se si vuole eseguire il push delle modifiche nel repository remoto, selezionare **Sync** e quindi **Push** in **Commit in uscita**. È anche possibile accumulare più commit locali prima di eseguire il push in remoto.

    ![Eseguire il push dei commit in remoto in Team Explorer](media/flask/step02-source-control-push-to-remote.png)

### <a name="question-how-frequently-should-one-commit-to-source-control"></a>Domanda: Con quale frequenza è consigliabile eseguire il commit nel controllo del codice sorgente?

Risposta: Il commit delle modifiche nel controllo del codice sorgente crea un record nel registro modifiche e un punto in corrispondenza del quale è possibile ripristinare il repository, se necessario. Ogni commit può anche essere esaminato per verificare modifiche specifiche. Poiché i commit in Git sono poco costosi, è preferibile eseguire spesso più commit piuttosto che accumulare un numero elevato di modifiche in un singolo commit. Ovviamente non è necessario eseguire il commit di ogni piccola modifica apportata a singoli file. In genere si esegue un commit quando si aggiunge una funzionalità, si modifica di una struttura come in questo passaggio o si effettua il refactoring del codice. Verificare inoltre con gli altri utenti del proprio team qual è il livello di granularità del commit più adatto per tutti.

La frequenza con cui si esegue il commit e la frequenza con cui si esegue il push del commit a un repository remoto sono due concetti diversi. È possibile accumulare più commit nel repository locale prima eseguirne il push al repository remoto. Anche in questo caso, la frequenza con cui si esegue il commit dipende dal modo in cui il team vuole gestire il repository.

## <a name="step-2-2-use-a-template-to-render-a-page"></a>Passaggio 2-2: Usare un modello per il rendering di una pagina

La funzione `home` presente finora in *views.py* genera solo una risposta HTTP in testo normale per la pagina. Tuttavia, la maggior parte delle pagine Web di scenari reali risponde con pagine HTML formattate che spesso includono dati in tempo reale. In effetti, il motivo principale per cui si definisce una visualizzazione usando una funzione è la possibilità di generare il contenuto in modo dinamico.

Poiché il valore restituito per la visualizzazione è una stringa, è possibile compilare qualsiasi codice HTML all'interno di una stringa usando contenuto dinamico. Poiché tuttavia è preferibile separare il markup dai dati, è meglio posizionare il markup in un modello e mantenere i dati nel codice.

1. I principianti possono modificare *views.py* in modo che contenga il codice seguente che usa HTML inline per la pagina con contenuto dinamico:

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

1. Per convertire il rendering della pagina in modo che usi un modello, creare un file denominato *index.html* nella cartella *templates* con il contenuto seguente, dove `{{ content }}` è un segnaposto o un token di sostituzione (detto anche *variabile del modello*) per il quale si specifica un valore nel codice:

    ```html
    <html>
        <head><title>Hello Flask</title></head>

        <body>
            {{ content }}
        </body>
    </html>
    ```

1. Modificare la funzione `home` in modo da usare `render_template` per caricare il modello e specificare un valore per "content", operazione che viene eseguita usando un argomento denominato corrispondente al nome del segnaposto. Flask cerca automaticamente i modelli nella cartella *templates*, quindi il percorso del modello è relativo a questa cartella:

    ```python
    def home():
        now = datetime.now()
        formatted_now = now.strftime("%A, %d %B, %Y at %X")

        return render_template(
            "index.html",
            content = "<strong>Hello, Flask!</strong> on " + formatted_now)
    ```

1. Eseguire l'app per visualizzare i risultati e osservare che l'HTML inline nel valore `content` non esegue il rendering *come* HTML perché il motore per la creazione dei modelli (Jinja) usa automaticamente caratteri di escape per il contenuto HTML. La sequenza di escape automatica evita vulnerabilità accidentali agli attacchi injection: gli sviluppatori spesso raccolgono l'input da una pagina e lo usano come valore in un'altra usando un segnaposto di modello. L'escape funge anche da promemoria per ricordare che è meglio tenere l'HTML fuori dal codice.

    Di conseguenza, verificare che *templates\index.html* contenga segnaposti distinti per ogni blocco di dati all'interno del markup:

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

Risposta: L'estensione *html* per i file di modello di pagina è del tutto facoltativa, perché il percorso relativo esatto del file viene sempre identificato nel primo argomento della funzione `render_template`. Per i file con estensione *html*, tuttavia, Visual Studio e altri editor offrono in genere funzionalità quali il completamento del codice e la colorazione della sintassi, che compensano il fatto che i modelli di pagina non siano rigorosamente HTML.

In realtà, quando si lavora a un progetto Flask, Visual Studio rileva automaticamente se il file HTML che si sta modificando è un modello Flask e offre alcune funzionalità di completamento automatico. Ad esempio, quando si inizia a digitare un commento in un modello di pagina Flask, `{#`, Visual Studio suggerisce automaticamente i caratteri di chiusura `#}`. Anche i comandi **Commenta selezione** e **Rimuovi commento selezione** (nel menu **Modifica** > **Avanzate** e sulla barra degli strumenti) usano i commenti dei modelli anziché i commenti HTML.

### <a name="question-can-templates-be-organized-into-further-subfolders"></a>Domanda: I modelli possono essere organizzati in ulteriori sottocartelle?

Risposta: Sì, è possibile usare sottocartelle e quindi fare riferimento al percorso relativo in *templates* nelle chiamate a `render_template`. In questo modo si possono creare in modo efficace gli spazi dei nomi per i modelli.

## <a name="next-steps"></a>Passaggi successivi

> [!div class="nextstepaction"]
> [Rendere disponibili file statici, aggiungere pagine e usare l'ereditarietà dei modelli](learn-flask-visual-studio-step-03-serve-static-files-add-pages.md)

## <a name="go-deeper"></a>Approfondimento

- [Flask Quickstart - Rendering Templates](https://flask.palletsprojects.com/en/1.0.x/quickstart/#rendering-templates) (Avvio rapido di Flask - Rendering dei modelli) (flask.pocoo.org)
- Codice sorgente per l'esercitazione su GitHub: [Microsoft/python-sample-vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask)
