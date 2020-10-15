---
title: Informazioni sull'esercitazione Flask in Visual Studio, passaggio 5, modello di progetto di sondaggi
titleSuffix: ''
description: Procedura dettagliata sui concetti di base relativi a Flask nel contesto dei progetti di Visual Studio, che illustra, in particolare, le funzionalità dei modelli Progetto Web Flask di sondaggi e Progetto Web Flask/Jade di sondaggi.
ms.date: 01/07/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: c9adda5eb9edba5e1ba62097d55c033be6c85d2e
ms.sourcegitcommit: 9c57730000d5ced37d3887f3928b17076f49d0f7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2020
ms.locfileid: "92099362"
---
# <a name="step-5-use-the-polls-flask-web-project-template"></a>Passaggio 5: Usare il modello di progetto Web Flask di sondaggi

**Passaggio precedente: [Usare il modello Progetto Web Flask completo](learn-flask-visual-studio-step-04-full-flask-project-template.md)**

Dopo aver compreso il modello "Progetto Web Flask" di Visual Studio, è ora possibile esaminare il terzo modello Flask, "Progetto Web Flask di sondaggi", che si basa sulla stessa codebase.

In questo passaggio viene descritto come:

> [!div class="checklist"]
> - Creare un progetto dal modello e inizializzare il database (passaggio 5-1)
> - Comprendere i modelli di dati (passaggio 5-2)
> - Comprendere gli archivi dati di backup (passaggio 5-3)
> - Comprendere i dettagli dei sondaggi e le visualizzazioni risultati (passaggio 5-4)

Visual Studio include anche il modello "Progetto Web Flask/Jade di sondaggi" che produce un'app identica ma usa l'estensione Jade per il motore per la creazione di modelli Jinja. Per informazioni dettagliate, vedere il [passaggio 4, relativo al modello di Progetto Web Flask/Jade](learn-flask-visual-studio-step-04-full-flask-project-template.md#the-flaskjade-web-project-template).

## <a name="step-5-1-create-the-project"></a>Passaggio 5-1: Creare il progetto

1. In Visual Studio passare a **Esplora soluzioni**, fare clic con il pulsante destro del mouse sulla soluzione **LearningFlask** creata in precedenza in questa esercitazione e scegliere **Aggiungi** > **Nuovo progetto**. In alternativa, se si vuole usare una nuova soluzione, selezionare **file**  >  **Nuovo**  >  In alternativa, **progetto** ).

1. Nella finestra di dialogo nuovo progetto cercare e selezionare il modello di **progetto Web di polling Flask** , chiamare il progetto "FlaskPolls" e fare clic su **OK**.

1. Come gli altri modelli di progetto in Visual Studio, il modello "Progetto Web Flask di sondaggi" include un file *requirements.txt* e Visual Studio chiede dove installare le dipendenze. Scegliere l'opzione **Installa in un ambiente virtuale** e nella finestra di dialogo **Aggiungi ambiente virtuale** selezionare **Crea** per accettare le impostazioni predefinite. Questo modello richiede l'uso di Flask nonché dei pacchetti azure-storage e pymongo. Il "Progetto Web Flask/Jade di sondaggi" richiede anche pyjade.

1. Impostare il progetto **FlaskPolls** come predefinito per la soluzione di Visual Studio facendo clic con il pulsante destro del mouse sul progetto in **Esplora soluzioni** e selezionando **Imposta come progetto di avvio**. Il progetto di avvio, indicato in grassetto, è quello che viene eseguito quando si avvia il debugger.

1. Selezionare **debug**  >  **Avvia debug** (**F5**) o usare il pulsante **server Web** sulla barra degli strumenti per eseguire il server:

    ![Pulsante di esecuzione del server Web della barra degli strumenti in Visual Studio](media/django/run-web-server-toolbar-button.png)

1. L'app creata dal modello ha tre pagine, Home, About e Contact, tra cui è possibile spostarsi usando la barra di spostamento superiore. Dedicare uno o due minuti a esaminare le diverse parti dell'app. Le pagine About e Contact sono molto simili a quelle in "Progetto Web Flask" e non vengono illustrate ulteriormente.

    ![Visualizzazione completa dell'app del progetto Web Flask di sondaggi](media/flask/step06-full-app-view.png)

1. Nella home page il pulsante di **creazione di sondaggi di esempio** consente di inizializzare l'archivio dati dell'app con tre diversi sondaggi descritti nella pagina *models/samples.json*. Per impostazione predefinita, l'app usa un database in memoria, come illustrato nella pagina di informazioni, che viene reimpostato ogni volta che l'app viene riavviata. L'app contiene anche codice per funzionare con Archiviazione di Azure e Mongo DB, come descritto più avanti in questo articolo.

1. Dopo avere inizializzato l'archivio dati, è possibile votare nei vari sondaggi come indicato nella home page (la barra di navigazione e il piè di pagina sono stati omessi per brevità):

    ![Visualizzazione dell'app dei sondaggi dopo l'inizializzazione dell'archivio dati](media/flask/step06-polls-initialized.png)

1. Selezionare un sondaggio per visualizzarne le scelte specifiche:

    ![Interfaccia di voto per un sondaggio](media/flask/step06-polls-voting-interface.png)

1. Quando si vota, l'app visualizza una pagina di risultati e consente di votare di nuovo:

    ![Visualizzazione dei risultati dopo il voto](media/flask/step06-polls-results.png)

1. È possibile lasciare l'app in esecuzione per le sezioni seguenti.

    Se si vuole arrestare l'app ed [eseguire il commit delle modifiche nel controllo del codice sorgente](learn-flask-visual-studio-step-02-create-app.md#commit-to-source-control), aprire prima di tutto la pagina **Modifiche** in **Team Explorer**, fare clic con il pulsante destro del mouse sulla cartella per l'ambiente virtuale (generalmente **env**) e scegliere **Ignora questi elementi locali**.

### <a name="examine-the-project-contents"></a>Esaminare i contenuti del progetto

Come accennato prima, molte parti di un progetto creato dal modello "Progetto Web Flask di sondaggi" (e dal modello "Progetto Flask/Jade di sondaggi") dovrebbero risultare familiari se sono stati analizzati altri modelli di progetto in Visual Studio. I passaggi aggiuntivi in questo articolo riepilogano le modifiche e le aggiunte più significative, in particolare i modelli di dati e le visualizzazioni aggiuntive.

## <a name="step-5-2-understand-the-data-models"></a>Passaggio 5-2: Comprendere i modelli di dati

I modelli di dati per l'app sono classi Python denominate polling e Choice, definite in *models/ \_ \_ init \_ \_ . py*. La classe Poll rappresenta una domanda, per la quale una raccolta di istanze di Choice rappresenta l'insieme delle risposte disponibili. Poll gestisce inoltre il numero totale di voti (per ogni scelta) e un metodo per calcolare le statistiche usate per la generazione di visualizzazioni:

```python
class Poll(object):
    """A poll object for use in the application views and repository."""
    def __init__(self, key=u'', text=u''):
        """Initializes the poll."""
        self.key = key
        self.text = text
        self.choices = []
        self.total_votes = None

    def calculate_stats(self):
        """Calculates some statistics for use in the application views."""
        total = 0
        for choice in self.choices:
            total += choice.votes
        for choice in self.choices:
            choice.votes_percentage = choice.votes / float(total) * 100 \
                if total > 0 else 0
        self.total_votes = total

class Choice(object):
    """A poll choice object for use in the application views and repository."""
    def __init__(self, key=u'', text=u'', votes=0):
        """Initializes the poll choice."""
        self.key = key
        self.text = text
        self.votes = votes
        self.votes_percentage = None
```

Questi modelli di dati sono astrazioni generiche che consentono alle visualizzazioni dell'app di funzionare con diversi tipi di archivi dati di backup, descritti nel passaggio successivo.

## <a name="step-5-3-understand-the-backing-data-stores"></a>Passaggio 5-3: Comprendere gli archivi dati di backup

L'app creata dal modello "Progetto Web Flask di sondaggi" può essere eseguita rispetto a un archivio dati in memoria, nell'archiviazione tabelle di Azure o in un database Mongo DB.

Il meccanismo di archiviazione dei dati funziona nel modo seguente:

1. Il tipo di repository viene specificato attraverso la variabile di ambiente `REPOSITORY_NAME`, che può essere impostata su "memory", "azuretablestore" o "mongodb". Un frammento di codice in *settings.py* recupera il nome, usando "memory" come valore predefinito. Se si vuole modificare l'archivio di backup, è necessario impostare la variabile di ambiente e riavviare l'app.

    ```python
    from os import environ
    REPOSITORY_NAME = environ.get('REPOSITORY_NAME', 'memory')
    ```

1. Il codice *settings.py* inizializza quindi un oggetto `REPOSITORY_SETTINGS`. Per usare l'archiviazione tabelle di Azure o Mongo DB, per prima cosa è necessario inizializzare tali archivi dati in un'altra posizione, quindi impostare le variabili di ambiente necessarie che indicano all'app come connettersi all'archivio:

    ```python
    if REPOSITORY_NAME == 'azuretablestorage':
        REPOSITORY_SETTINGS = {
            'STORAGE_NAME': environ.get('STORAGE_NAME', ''),
            'STORAGE_KEY': environ.get('STORAGE_KEY', ''),
            'STORAGE_TABLE_POLL': environ.get('STORAGE_TABLE_POLL', 'polls'),
            'STORAGE_TABLE_CHOICE': environ.get('STORAGE_TABLE_CHOICE', 'choices'),
        }
    elif REPOSITORY_NAME == 'mongodb':
        REPOSITORY_SETTINGS = {
            'MONGODB_HOST': environ.get('MONGODB_HOST', None),
            'MONGODB_DATABASE': environ.get('MONGODB_DATABASE', 'polls'),
            'MONGODB_COLLECTION': environ.get('MONGODB_COLLECTION', 'polls'),
        }
    elif REPOSITORY_NAME == 'memory':
        REPOSITORY_SETTINGS = {}
    else:
        raise ValueError('Unknown repository.')
    ```

1. In *views.py* l'app chiama un metodo factory per inizializzare un oggetto `Repository` con il nome e le impostazioni dell'archivio dati:

    ```python
    from FlaskPolls.models import PollNotFound
    from FlaskPolls.models.factory import create_repository
    from FlaskPolls.settings import REPOSITORY_NAME, REPOSITORY_SETTINGS

    repository = create_repository(REPOSITORY_NAME, REPOSITORY_SETTINGS)
    ```

1. Il metodo `factory.create_repository` viene rilevato in *models\factory.py*, che si limita a importare il modulo di repository appropriato, quindi crea un'istanza di `Repository`:

    ```python
    def create_repository(name, settings):
        """Creates a repository from its name and settings. The settings
        is a dictionary where the keys are different for every type of repository.
        See each repository for details on the required settings."""
        if name == 'azuretablestorage':
            from .azuretablestorage import Repository
        elif name == 'mongodb':
            from .mongodb import Repository
        elif name == 'memory':
            from .memory import Repository
        else:
            raise ValueError('Unknown repository.')

        return Repository(settings)
    ```

1. Le implementazioni della classe `Repository` specifiche per ogni archivio dati sono reperibili in *models\azuretablestorage.py*, *models\mongodb.py* e *models\memory.py*. L'implementazione di Archiviazione di Azure usa il pacchetto azure-storage, l'implementazione di Mongo DB usa il pacchetto pymongo. Come indicato nel passaggio 5-1, entrambi i pacchetti sono inclusi nel file *requirements.txt* del modello di progetto. L'esplorazione dei dettagli viene lasciata come esercizio per il lettore.

In breve, la classe `Repository` estrae le specifiche dell'archivio dati e l'app usa le variabili di ambiente in fase di esecuzione per selezionare e configurare una delle tre implementazioni da usare.

I passaggi seguenti aggiungono il supporto per un archivio dati diverso dai tre specificati dal modello di progetto, se necessario:

1. Copiare *memory.py* in un nuovo file in modo da avere l'interfaccia di base per la classe `Repository`.
1. Modificare l'implementazione della classe in base all'archivio dati in uso.
1. Modificare *factory.py* per aggiungere un altro caso `elif` che riconosce il nome dell'archivio dati aggiunto e importa il modulo appropriato.
1. Modificare *settings.py* per riconoscere un altro nome nella variabile di ambiente `REPOSITORY_NAME` e inizializzare `REPOSITORY_SETTINGS` di conseguenza.

### <a name="seed-the-data-store-from-samplesjson"></a>Assegnare valori di inizializzazione all'archivio dati da samples.json

Inizialmente, l'archivio dati scelto non contiene sondaggi, quindi il home page dell'app mostra il messaggio **non sono disponibili polling** insieme al pulsante **Crea polling di esempio** . Quando si seleziona il pulsante, tuttavia, la visualizzazione cambia e appaiono i sondaggi disponibili. Questo cambiamento è dovuto ai tag condizionali in *templates\index.html* (alcune righe vuote sono state omesse per brevità):

```html
{% extends "layout.html" %}
{% block content %}
<h2>{{title}}.</h2>

{% if polls %}
<table class="table table-hover">
    <tbody>
        {% for poll in polls %}
        <tr>
            <td>
                <a href="/poll/{{poll.key}}">{{poll.text}}</a>
            </td>
        </tr>
        {% endfor %}
    </tbody>
</table>
{% else %}
<p>No polls available.</p>
<br />
<form action="/seed" method="post">
    <button class="btn btn-primary" type="submit">Create Sample Polls</button>
</form>
{% endif %}
{% endblock %}
```

La variabile `polls` nel modello proviene da una chiamata a `repository.get_polls`, che non restituisce nulla finché l'archivio dati non viene inizializzato.

Selezionando il pulsante di **creazione di sondaggi di esempio** si passa all'URL /seed. Il gestore per la route è definito in *views.py*:

```python
@app.route('/seed', methods=['POST'])
def seed():
    """Seeds the database with sample polls."""
    repository.add_sample_polls()
    return redirect('/')
```

La chiamata a `repository.add_sample_polls()` termina in una delle implementazioni specifiche di `Repository` per l'archivio dati scelto. Ogni implementazione chiama il `_load_samples_json` Metodo trovato nei *modelli \_ \_ init \_ \_ . py* per caricare il *models\samples.js* nel file in memoria, quindi scorre i dati per creare gli `Poll` oggetti e necessari `Choice` nell'archivio dati.

Al termine del processo, l'istruzione `redirect('/')` nel metodo `seed` torna alla home page. Poiché `repository.get_polls` ora restituisce un oggetto dati, i tag condizionali in *templates\index.html* eseguono il rendering di una tabella che contiene i sondaggi.

### <a name="question-how-does-one-add-new-polls-to-the-app"></a>Domanda: come si aggiungono nuovi sondaggi all'app?

Risposta: l'app disponibile attraverso il modello di progetto non include una funzionalità per l'aggiunta o la modifica dei sondaggi. È possibile modificare *models\samples.json* per creare nuovi dati di inizializzazione, ma tale operazione comporterebbe la reimpostazione dell'archivio dati. Per implementare le funzionalità di modifica, è necessario estendere l'interfaccia della classe `Repository` con metodi per la creazione delle istanze `Choice` e `Poll` necessarie, quindi implementare un'interfaccia utente in altre pagine che usano quei metodi.

## <a name="step-5-4-understand-the-poll-detail-and-results-views"></a>Passaggio 5-4: Comprendere i dettagli dei sondaggi e le visualizzazioni risultati

La maggior parte delle visualizzazioni generate dal modello "Progetto Web Flask/Jade di sondaggi", ad esempio quelle delle pagine About e Contact, sono piuttosto simili alle visualizzazioni create dal modello "Progetto Web Flask" (o "progetto Web Flask/Jade") usato in precedenza in questa esercitazione. Nella sezione precedente si è appreso anche come la home page venga implementata in modo da visualizzare il pulsante di inizializzazione o l'elenco dei sondaggi.

A questo punto non resta che esaminare i voti (dettagli) e la visualizzazione dei risultati di un singolo sondaggio.

Quando si seleziona un polling dalla home page, l'app passa all'URL/poll/ \<key\> dove *Key* è il identificatore univoco per un sondaggio. In *views.py* si può vedere che la funzione `details` viene assegnata per gestire il routing di tale URL sia per GET che per le richieste. È anche possibile vedere che l'uso di `<key>` nel routing dell'URL consente di eseguire il mapping di tutte le route di quel modulo alla stessa funzione e genera un argomento alla funzione con lo stesso nome:

```python
@app.route('/poll/<key>', methods=['GET', 'POST'])
def details(key):
    """Renders the poll details page."""
    error_message = ''
    if request.method == 'POST':
        try:
            choice_key = request.form['choice']
            repository.increment_vote(key, choice_key)
            return redirect('/results/{0}'.format(key))
        except KeyError:
            error_message = 'Please make a selection.'

    return render_template(
        'details.html',
        title='Poll',
        year=datetime.now().year,
        poll=repository.get_poll(key),
        error_message=error_message,
    )
```

Per visualizzare un sondaggio (richieste GET), questa funzione chiama semplicemente *templates\details.html*, che esegue l'iterazione nella matrice `choices` del sondaggio, creando un pulsante di opzione per ogni scelta.

```html
{% extends "layout.html" %}

{% block content %}

<h2>{{poll.text}}</h2>
<br />

{% if error_message %}
<p class="text-danger">{{error_message}}</p>
{% endif %}

<form action="/poll/{{poll.key}}" method="post">
    {% for choice in poll.choices %}
    <div class="radio">
        <label>
            <input type="radio" name="choice" id="choice{{choice.key}}" value="{{choice.key}}" />
            {{ choice.text }}
        </label>
    </div>
    {% endfor %}
    <br />
    <button class="btn btn-primary" type="submit">Vote</button>
</form>

{% endblock %}
```

Poiché il pulsante di **voto** ha `type="submit"`, selezionandolo si genera una richiesta POST allo stesso URL, che viene di nuovo indirizzato alla funzione `details`. Questa volta, tuttavia, estrae la scelta dai dati del modulo e reindirizza a/results/ \<choice\> .

L' \<key\> URL/Results/viene quindi indirizzato alla `results` funzione in *views.py*, che quindi chiama il metodo del polling `calculate_stats` e USA *templates\results.html* per il rendering:

```python
@app.route('/results/<key>')
def results(key):
    """Renders the results page."""
    poll = repository.get_poll(key)
    poll.calculate_stats()
    return render_template(
        'results.html',
        title='Results',
        year=datetime.now().year,
        poll=poll,
    )
```

Il modello *results.html*, a sua volta, esegue semplicemente l'iterazione nelle scelte del sondaggio e genera un indicatore di stato per ogni scelta:

```html
{% extends "layout.html" %}

{% block content %}

<h2>{{poll.text}}</h2>
<br />

{% for choice in poll.choices %}
<div class="row">
    <div class="col-sm-5">{{choice.text}}</div>
    <div class="col-sm-5">
        <div class="progress">
            <div class="progress-bar" role="progressbar" aria-valuenow="{{choice.votes}}" aria-valuemin="0" aria-valuemax="{{poll.total_votes}}" style="width: {{choice.votes_percentage}}%;">
                {{choice.votes}}
            </div>
        </div>
    </div>
</div>
{% endfor %}

<br />
<a class="btn btn-primary" href="/poll/{{poll.key}}">Vote again?</a>

{% endblock %}
```

## <a name="next-steps"></a>Passaggi successivi

> [!Note]
> Durante l'esercitazione è stato eseguito il commit della soluzione di Visual Studio nel controllo del codice sorgente. A questo punto è utile eseguire un altro commit. La soluzione dovrebbe corrispondere al codice sorgente per l'esercitazione su GitHub: [Microsoft/python-sample-vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask).

A questo punto, sono stati esaminati tutti i modelli "Progetto Web Flask vuoto", "Progetto Web Flask/[Jade]" e "Progetto Web Flask[/Jade] di sondaggi" di Visual Studio. Sono stati esaminati tutti gli elementi fondamentali di Flask, ad esempio l'uso delle visualizzazioni, i modelli e il routing ed è stato spiegato come usare gli archivi dati di backup. A questo punto, si dovrebbe essere in grado di iniziare a usare un'app Web con tutti i modelli e le visualizzazioni necessari.

L'esecuzione di un'app Web nel computer di sviluppo è solo un passaggio per rendere disponibile l'app ai clienti. I passaggi successivi possono includere le attività seguenti:

- Distribuire l'app Web in un server di produzione, ad esempio Servizio app di Azure. Vedere [Eseguire la pubblicazione in Servizio app di Azure](publishing-python-web-applications-to-azure-from-visual-studio.md).

- Aggiungere un'implementazione di repository che usa un altro archivio dati a livello di produzione, ad esempio PostgreSQL, MySQL e SQL Server (che possono tutti essere ospitati in Azure). È anche possibile usare [Azure SDK per Python](/azure/python/) per usare servizi di archiviazione di Azure, ad esempio tabelle e BLOB, nonché Cosmos DB.

- Configurare una pipeline di integrazione continua/distribuzione continua in un servizio come Azure DevOps. Oltre a usare il controllo del codice sorgente (in Azure Repos, GitHub o altrove), è possibile configurare un progetto di Azure DevOps in modo che esegua automaticamente gli unit test come prerequisito per il rilascio, oltre che configurare la pipeline per la distribuzione in un server di gestione temporanea per eseguire test aggiuntivi prima della distribuzione in produzione. Azure DevOps inoltre si integra con soluzioni di monitoraggio, ad esempio App Insights, chiudendo così l'intero ciclo con strumenti di pianificazione Agile. Per altre informazioni, vedere [Creare una pipeline CI/CD per Python con Azure DevOps Projects](/azure/devops-project/azure-devops-project-python?view=vsts&preserve-view=true) e la [documentazione generale di Azure DevOps](/azure/devops/?view=vsts&preserve-view=true).
