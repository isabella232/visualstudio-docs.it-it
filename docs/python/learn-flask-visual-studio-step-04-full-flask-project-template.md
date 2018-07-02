---
title: Esercitazione - Informazioni su Flask in Visual Studio, passaggio 4
description: Procedura dettagliata sui concetti di base relativi a Flask nel contesto dei progetti di Visual Studio, che illustra, in particolare, le funzionalità offerte dai modelli Progetto Web Flask e Progetto Web Flask/Jade.
ms.date: 05/25/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: a4c50a7b6e3fe14f27bfd78e6814f9e120864d60
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34752160"
---
# <a name="tutorial-step-4-use-the-full-flask-web-project-template"></a>Passaggio 4 della procedura: Usare il modello Progetto Web Flask completo

**Passaggio precedente: [Rendere disponibili file statici, aggiungere pagine e usare l'ereditarietà dei modelli](learn-flask-visual-studio-step-03-serve-static-files-add-pages.md)**

Dopo aver esplorato i concetti di base relativi a Flask creando un'app basata sul modello "Progetto Web Flask vuoto" in Visual Studio, è possibile comprendere facilmente l'app più completa prodotta dal modello "Progetto Web Flask".

In questo passaggio:

> [!div class="checklist"]
> - Viene creata un'app Web Flask più completa usando il modello "Progetto Web Flask" e si esamina la struttura del progetto (passaggio 4-1)
> - Si comprenderanno le visualizzazioni e i modelli di pagina creati dal modello di progetto, costituito da tre pagine che ereditano da un modello di pagina di base e che usa librerie JavaScript statiche come jQuery e Bootstrap (passaggio 4-2)
> - Si comprenderà il routing degli URL fornito dal modello (passaggio 4-3)

Questo articolo vale anche per il modello "Progetto Web Flask/Jade", che produce un'app identica a quella del "Progetto Web Flask" usando il motore per la creazione di modelli Jade anziché Jinja. Altri dettagli sono inclusi alla fine di questo articolo.

## <a name="step-4-1-create-a-project-from-the-template"></a>Passaggio 4-1: Creare un progetto da un modello

1. In Visual Studio passare a **Esplora soluzioni**, fare clic con il pulsante destro del mouse sulla soluzione "LearningFlask" creata in precedenza in questa esercitazione e scegliere **Aggiungi** > **Nuovo progetto**. In alternativa, se si vuole usare una nuova soluzione, selezionare **File** > **Nuovo** > **Progetto**.

1. Nella finestra di dialogo Nuovo progetto cercare e selezionare il modello "Progetto Web Flask", assegnare al progetto il nome "FlaskWeb" e selezionare **OK**.

1. Poiché il modello include di nuovo un file `requirements.txt`, Visual Studio chiede dove installare queste dipendenze. Scegliere l'opzione **Installa in un ambiente virtuale** e nella finestra di dialogo **Aggiungi ambiente virtuale** selezionare **Crea** per accettare le impostazioni predefinite.

1. Quando Visual Studio termina la configurazione dell'ambiente virtuale, impostare il progetto "FlaskWeb" come predefinito per la soluzione di Visual Studio facendo clic con il pulsante destro del mouse sul progetto in **Esplora soluzioni** e selezionando **Imposta come progetto di avvio**. Il progetto di avvio, indicato in grassetto, è quello che viene eseguito quando si avvia il debugger.

    ![Progetto FlaskWeb visualizzato in Esplora soluzioni come progetto di avvio](media/flask/step04-second-project-in-solution-set-as-startup-project.png)

1. Selezionare **Debug** > **Avvia debug** (F5) o usare il pulsante **Server Web** sulla barra degli strumenti per eseguire il server:

    ![Pulsante di esecuzione del server Web della barra degli strumenti in Visual Studio](media/flask/run-web-server-toolbar-button.png)

1. L'app creata dal modello ha tre pagine, Home, About e Contact, tra cui è possibile spostarsi usando la barra di spostamento. Dedicare un minuto o due a esaminare le diverse parti dell'app. Per eseguire l'autenticazione con l'app tramite il comando **Accedi**, usare le credenziali di utente avanzato create in precedenza.

    ![Visualizzazione completa nel browser dell'app Progetto Web Flask](media/flask/step04-full-app-desktop-view.png)

1. L'app creata dal modello "Progetto Web Flask" usa Bootstrap per ottenere un layout reattivo che si adatta ai fattori di forma per dispositivi mobili. Per osservare questa velocità di risposta, ridimensionare il browser in base a una visualizzazione ridotta, in modo che il rendering del contenuto venga eseguito in verticale e che la barra di spostamento si trasformi in icona di menu:

    ![Visualizzazione per dispositivi mobili (ridotta) dell'app Progetto Web Flask](media/flask/step04-full-app-mobile-view.png)

1. È possibile lasciare l'app in esecuzione per le sezioni seguenti.

    Se si vuole arrestare l'app ed [eseguire il commit delle modifiche nel controllo del codice sorgente](learn-flask-visual-studio-step-02-create-app.md#commit-to-source-control), aprire prima di tutto la pagina **Modifiche** in **Team Explorer**, fare clic con il pulsante destro del mouse sulla cartella per l'ambiente virtuale (generalmente `env`) e scegliere **Ignora questi elementi locali**.

### <a name="examine-what-the-template-creates"></a>Esaminare gli elementi creati dal modello

Il modello "Progetto Web Flask" crea la struttura riportata di seguito. Il contenuto è molto simile a quello creato nei passaggi precedenti. La differenza è che il modello "Progetto Web Flask" contiene più struttura nella cartella `static` perché include jQuery e Bootstrap per la progettazione reattiva. Il modello aggiunge inoltre una pagina di contatto. In generale, se sono stati eseguiti i passaggi precedenti di questa esercitazione, tutti gli elementi del modello sono familiari.

- File nella radice del progetto:
  - `runserver.py`, uno script per eseguire l'app in un server di sviluppo.
  - `requirements.txt`, che contiene una dipendenza da Flask 0.x.
- La cartella `FlaskWeb` contiene tutti i file dell'app:
  - `__init.py__` contrassegna il codice dell'app come modulo Python, crea l'oggetto Flask e importa le visualizzazioni dell'app.
  - `views.py` contiene il codice per il rendering delle pagine.
  - La cartella `static` contiene sottocartelle denominate `content` (file CSS), `fonts` (file del tipo di carattere) e `scripts` (file JavaScript).
  - La cartella `templates` contiene un modello `layout.html` di base oltre a `about.html`, `contact.html` e `index.html` per pagine specifiche che estendono `layout.html`.

### <a name="question-is-it-possible-to-share-a-virtual-environment-between-visual-studio-projects"></a>Domanda: È possibile condividere un ambiente virtuale tra progetti di Visual Studio?

Risposta: Sì, ma tenere presente che diversi progetti probabilmente usano pacchetti diversi nel tempo e di conseguenza un ambiente virtuale condiviso deve contenere tutti i pacchetti per tutti i progetti che lo usano.

Ciononostante, per usare un ambiente virtuale esistente, eseguire le operazioni seguenti:

1. Quando viene richiesto di installare le dipendenze in Visual Studio, selezionare l'opzione **Installazione manuale**.
1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo **Ambienti Python** e scegliere **Aggiungi ambiente virtuale esistente**.
1. Individuare e selezionare la cartella contenente l'ambiente virtuale, quindi selezionare **OK**.

## <a name="step-4-2-understand-the-views-and-page-templates-created-by-the-project-template"></a>Passaggio 4-2: Comprendere le visualizzazioni e i modelli di pagina creati dal modello di progetto

Come si può osservare quando si esegue il progetto, l'app contiene tre visualizzazioni: Home, About e Contact. Il codice per queste visualizzazioni è disponibile in `FlaskWeb/views.py`. Ogni funzione di visualizzazione chiama `flask.render_template` con il percorso a un modello e un elenco variabile di argomenti per i valori da assegnare al modello. Ad esempio, la pagina di informazioni è gestita dalla funzione `about`, il cui elemento Decorator specifica il routing dell'URL:

```python
@app.route('/about')
def about():
    """Renders the about page."""
    return render_template(
        'about.html',
        title='About',
        year=datetime.now().year,
        message='Your application description page.'
    )
```

Le funzioni `home` e `contact` sono quasi identiche, con elementi Decorator simili e argomenti leggermente diversi.

I modelli si trovano nella cartella `templates` dell'app. Il modello di base, `layout.html`, è il più ampio. Fa riferimento a tutti i file statici necessari (JavaScript e CSS), definisce un blocco denominato "content" di cui altre pagine eseguono l'override e fornisce un altro blocco denominato "scripts". Gli estratti annotati di `layout.html` indicati di seguito mostrano queste aree specifiche:

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8" />

    <!-- Define a viewport for Bootstrap's responsive rendering -->
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>{{ title }} - My Flask Application</title>

    <link rel="stylesheet" type="text/css" href="/static/content/bootstrap.min.css" />
    <link rel="stylesheet" type="text/css" href="/static/content/site.css" />
    <script src="/static/scripts/modernizr-2.6.2.js"></script>
</head>

<body>
    <!-- Navbar omitted -->

    <div class="container body-content">
        <!-- "content" block that pages are expected to override -->
        {% block content %}{% endblock %}
        <hr />
        <footer>
            <p>&copy; {{ year }} - My Flask Application</p>
        </footer>
    </div>

    <!-- Additional scripts; use the "scripts" block to add page-specific scripts.  -->
    <script src="/static/scripts/jquery-1.10.2.js"></script>
    <script src="/static/scripts/bootstrap.js"></script>
    <script src="/static/scripts/respond.js"></script>
    {% block scripts %}{% endblock %}

</body>
</html>
```

Singoli modelli di pagina `about.html`, `contact.html` e `index.html`, ciascuno dei quali estende il modello di base `layout.html`. `about.html` è il più semplice e mostra i tag `{% extends %}` e `{% block content %}`:

```html
{% extends "app/layout.html" %}

{% block content %}

<h2>{{ title }}.</h2>
<h3>{{ message }}</h3>

<p>Use this area to provide additional information.</p>

{% endblock %}
```

`index.html` e `contact.html` usano la stessa struttura e forniscono contenuto più lungo nel blocco "content".

## <a name="the-flaskjade-web-project-template"></a>Il modello Progetto Web Flask/Jade

Come indicato all'inizio di questo articolo, Visual Studio offre un modello "Progetto Web Flask/Jade", che consente di creare un'applicazione visivamente identica a quella generata da "Progetto Web Flask". La differenza principale è che in questo caso viene usato il motore del modello Jade, che è un'estensione Jinja che implementa gli stessi concetti con un linguaggio più conciso. In particolare, Jade usa parole chiave anziché tag racchiusi tra delimitatori, ad esempio {% %}, e consente di fare riferimento agli stili CSS e agli elementi HTML che usano le parole chiave.

Per abilitare Jade, il modello di progetto per prima cosa include il pacchetto pyjade in `requirements.txt`. 

Il file `__init__.py` dell'app contiene la riga

    ```python
    app.jinja_env.add_extension('pyjade.ext.jinja.PyJadeExtension')
    ```
Nella cartella `templates` appaiono file `.jade` anziché modelli `.html` e le visualizzazioni in `views.py` fanno riferimento a questi file nelle chiamate a `flask.render_template`. Per il resto il codice delle visualizzazioni è lo stesso.

Aprendo uno dei file `.jade`, è possibile visualizzare l'espressione più concisa di un modello. Ad esempio, ecco il contenuto di `templates/layout.jade` creato dal modello "Progetto Web Flask/Jade":

    ```jade
    doctype html
    html
      head
        meta(charset='utf-8')
        meta(name='viewport', content='width=device-width, initial-scale=1.0')
        title #{title} - My Flask/Jade Application
        link(rel='stylesheet', type='text/css', href='/static/content/bootstrap.min.css')
        link(rel='stylesheet', type='text/css', href='/static/content/site.css')
        script(src='/static/scripts/modernizr-2.6.2.js')
      body
        .navbar.navbar-inverse.navbar-fixed-top
          .container
            .navbar-header
              button.navbar-toggle(type='button', data-toggle='collapse', data-target='.navbar-collapse')
                span.icon-bar
                span.icon-bar
                span.icon-bar
              a.navbar-brand(href='/') Application name
            .navbar-collapse.collapse
              ul.nav.navbar-nav
                li
                  a(href='/') Home
                li
                  a(href='/about') About
                li
                  a(href='/contact') Contact
        .container.body-content
          block content
          hr
          footer
            p &copy; #{year} - My Flask/Jade Application

        script(src='/static/scripts/jquery-1.10.2.js')
        script(src='/static/scripts/bootstrap.js')
        script(src='/static/scripts/respond.js')

        block scripts
    ```

Ed ecco il contenuto di `templates/about.jade`, che illustra l'uso di `#{ <name>}` per i segnaposto:

    ```jade
    extends layout

    block content
      h2 #{title}.
      h3 #{message}
      p Use this area to provide additional information.
    ```

Provare a usare entrambe le sintassi, Jinja e Jade, per vedere quale delle due è più adatta alle proprie esigenze.

## <a name="next-steps"></a>Passaggi successivi

> [!div class="nextstepaction"]
> [Il modello Progetto Web Flask di sondaggi](learn-flask-visual-studio-step-05-polls-flask-web-project-template.md)

## <a name="going-deeper"></a>Approfondimenti

- [Writing your first Flask app, part 4 - forms and generic views](https://docs.djangoproject.com/en/2.0/intro/tutorial04/) (Scrittura della prima app Flask - moduli e visualizzazioni generiche) (docs.djangoproject.com)
- [Jade su GitHib (documentazione)](https://github.com/liuliqiang/pyjade) (github.com)
- Codice sorgente per l'esercitazione su GitHub: [Microsoft/python-sample-vs-learn-flask](https://github.com/Microsoft/python-sample-vs-learn-flask)