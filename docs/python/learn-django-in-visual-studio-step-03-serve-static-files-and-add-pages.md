---
title: Informazioni sull'esercitazione Django in Visual Studio, passaggio 3, file statici e pagine
titleSuffix: ''
description: Procedura dettagliata sui concetti di base relativi a Django nel contesto dei progetti di Visual Studio, che illustra, in particolare, come rendere disponibili file statici, aggiungere pagine all'app e usare l'ereditarietà dei modelli
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
ms.openlocfilehash: 286f32477e67013b9766eba18b7ae0325e905d84
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122038513"
---
# <a name="step-3-serve-static-files-add-pages-and-use-template-inheritance-with-django-app"></a>Passaggio 3: Gestire file statici, aggiungere pagine e usare l'ereditarietà dei modelli con l'app Django

**Passaggio precedente: [Creare un'app Django con visualizzazioni e modelli di pagina](learn-django-in-visual-studio-step-02-create-an-app.md)**

Nei passaggi precedenti di questa esercitazione si è appreso come creare un'app Django di base con una singola pagina di codice HTML autonomo. Le app Web moderne, tuttavia, sono in genere costituite da numerose pagine e usano risorse condivise, come file CSS e JavaScript, per offrire un comportamento e uno stile coerenti.

In questo passaggio viene descritto come:

> [!div class="checklist"]
> - Usare i modelli di elementi di Visual Studio per aggiungere rapidamente nuovi file di tipi diversi con un comodo codice boilerplate (passaggio 3-1)
> - Configurare il progetto Django per rendere disponibili file statici (passaggio 3-2)
> - Aggiungere altre pagine all'app (passaggio 3-3)
> - Usare l'ereditarietà dei modelli per creare un'intestazione e una barra di spostamento usate in più pagine (passaggio 3-4)

## <a name="step-3-1-become-familiar-with-item-templates"></a>Passaggio 3-1: Acquisire familiarità con i modelli di elementi

Quando si sviluppa un'app Django, si aggiungono in genere molti altri file Python, HTML, CSS e JavaScript. Per ogni tipo di file (come pure per altri file, come *web.config*, che potrebbero essere necessari per la distribuzione), Visual Studio offre comodi [modelli di elementi](python-item-templates.md) da cui iniziare.

Per visualizzare i modelli disponibili, passare a **Esplora soluzioni**, fare clic con il pulsante destro del mouse sulla cartella in cui si vuole creare l'elemento e scegliere **Aggiungi** > **Nuovo elemento**:

![Finestra di dialogo Aggiungi nuovo elemento in Visual Studio](media/django/step03-add-new-item-dialog.png)

Per usare un modello, selezionare il modello desiderato, specificare un nome per il file e selezionare **OK**. Aggiungendo un elemento in questo modo il file viene aggiunto automaticamente al progetto di Visual Studio e vengono contrassegnate le modifiche per il controllo del codice sorgente.

### <a name="question-how-does-visual-studio-know-which-item-templates-to-offer"></a>Domanda: In che modo Visual Studio individua i modelli di elementi da offrire?

Risposta: Il file di progetto di Visual Studio (con estensione *pyproj*) contiene un identificatore del tipo di progetto che lo contrassegna come progetto Python. Visual Studio usa questo identificatore di tipo per mostrare solo i modelli di elementi appropriati per il tipo di progetto. In questo modo, Visual Studio può fornire un set completo di modelli di elementi per numerosi tipi di progetti senza che sia necessario che l'utente li esamini tutti ogni volta.

## <a name="step-3-2-serve-static-files-from-your-app"></a>Passaggio 3-2: Rendere disponibili file statici dall'app

In un'app Web compilata con Python (usando qualsiasi framework), i file Python vengono sempre eseguiti nel server dell'host Web e non vengono mai trasmessi al computer dell'utente. Altri file, tuttavia, ad esempio CSS e JavaScript, vengono usati esclusivamente dal browser, quindi il server host si limita a fornirli così come sono ogni volta che vengono richiesti. Tali file sono detti file "statici" e Django può fornirli automaticamente senza che sia necessario scrivere codice.

Per impostazione predefinita, un progetto Django è configurato in modo da rendere disponibili i file statici dalla cartella *static* dell'app, grazie alle righe di codice seguenti nel file *settings.py* del progetto Django:

```python
# Static files (CSS, JavaScript, Images)
# https://docs.djangoproject.com/en/1.9/howto/static-files/

STATIC_URL = '/static/'

STATIC_ROOT = posixpath.join(*(BASE_DIR.split(os.path.sep) + ['static']))
```

È possibile organizzare i file usando qualsiasi struttura di cartelle in *static* e quindi usare percorsi relativi all'interno di tale cartella per fare riferimento ai file. Per illustrare questo processo, i passaggi seguenti aggiungono un file CSS all'app. Il foglio di stile viene quindi usato nel modello *index.html*:

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sulla cartella **HelloDjangoApp** nel progetto Visual Studio, scegliere Aggiungi nuova cartella e assegnare alla cartella il nome   >   `static` .

1. Fare clic con il pulsante destro del mouse sulla cartella **static** e scegliere **Aggiungi** > **Nuovo elemento**. Nella finestra di dialogo visualizzata selezionare il modello **Foglio di** stile, assegnare al file il nome e `site.css` selezionare **OK.** Il file **site.css** viene visualizzato nel progetto e aperto nell'editor. La struttura di cartelle dovrebbe essere simile a quella nella figura seguente:

    ![Struttura di file statici come visualizzato in Esplora soluzioni](media/django/step03-static-file-structure.png)

1. Sostituire il contenuto di *site.css* con il codice seguente e salvare il file:

    ```css
    .message {
        font-weight: 600;
        color: blue;
    }
    ```

1. Sostituire il contenuto del file *templates/HelloDjangoApp/index.html* dell'app con il codice seguente che sostituisce l'elemento `<strong>` usato nel passaggio 2 con un elemento `<span>` che fa riferimento alla classe di stile `message`. L'uso di una classe di stile in questo modo offre maggiore flessibilità nell'applicazione degli stili all'elemento. Se il file *index.html* non è stato spostato in una sottocartella in *modelli* durante l'uso di VS 2017 15.7 e versioni successive, fare riferimento allo [spazio dei nomi del modello](learn-django-in-visual-studio-step-02-create-an-app.md#template-namespacing) nel passaggio 2-4.

    ```html
    <html>
        <head>
            <title>{{ title }}</title>
            {% load staticfiles %} <!-- Instruct Django to load static files -->
            <link rel="stylesheet" type="text/css" href="{% static 'site.css' %}" />
        </head>
        <body>
            <span class="message">{{ message }}</span>{{ content }}
        </body>
    </html>
    ```

1. Eseguire il progetto per osservare i risultati. Al termine, arrestare il server ed eseguire il commit delle modifiche nel controllo del codice sorgente, se lo si desidera (come illustrato nel [passaggio 2](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control)).

### <a name="question-what-is-the-purpose-of-the--load-staticfiles--tag"></a>Domanda: Qual è lo scopo del tag {% load staticfiles %}?

Risposta: La riga `{% load staticfiles %}` è necessaria prima di fare riferimento ai file statici in elementi come `<head>` e `<body>`. Nell'esempio illustrato in questa sezione "staticfiles" fa riferimento a un set di tag di un modello Django personalizzato, che è ciò consente di usare la sintassi `{% static %}` per fare riferimento ai file statici.  In assenza di `{% load staticfiles %}`, verrà generata un'eccezione quando viene eseguita l'app.

### <a name="question-are-there-any-conventions-for-organizing-static-files"></a>Domanda: Ci sono convenzioni per organizzare i file statici?

Risposta: È possibile aggiungere altri file CSS, JavaScript e HTML nella cartella *static* come si vuole. Un modo tipico per organizzare i file statici consiste nel creare sottocartelle denominate *fonts*, *scripts* e *content* (per i fogli di stile e qualsiasi altro file). In ogni caso, ricordarsi di includere tali sottocartelle nel percorso relativo del file nei riferimenti `{% static %}`.

### <a name="question-can-i-complete-the-same-task-without-using-the--load-staticfiles--tag"></a>Domanda: È possibile completare la stessa attività senza usare il tag {% load staticfiles %}?

Risposta: Sì, è possibile.

```html
<html>
    <head>
        <title>{{ title }}</title>
        <link rel="stylesheet" type="text/css" href="../../static/site.css" />
    </head>
    <body>
        <span class="message">{{ message }}</span>{{ content }}
    </body>
</html>
```

## <a name="step-3-3-add-a-page-to-the-app"></a>Passaggio 3-3: Aggiungere una pagina all'app

L'aggiunta di un'altra pagina all'app comporta quanto segue:

- Aggiunta di una funzione Python che definisce la visualizzazione.
- Aggiunta di un modello per il markup della pagina.
- Aggiunta del routing necessario al file *urls.py* del progetto Django.

I passaggi seguenti aggiungono una pagina "About" al progetto "HelloDjangoApp", oltre che collegamenti a tale pagina dalla home page:

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sulla cartella **templates/HelloDjangoApp**, selezionare **Aggiungi** > **Nuovo elemento**, selezionare il modello di elemento **Pagina HTML**, assegnare al file il nome `about.html` e selezionare **OK**.

    > [!Tip]
    > Se il comando **Nuovo elemento** non è visualizzato nel menu **Aggiungi**, assicurarsi di aver arrestato il server in modo che Visual Studio esca dalla modalità di debug.

1. Sostituire il contenuto di *about.html* con il markup seguente (il collegamento esplicito alla home page viene sostituito con una barra di spostamento semplice nel passaggio 3-4):

    ```html
    <html>
        <head>
            <title>{{ title }}</title>
            {% load staticfiles %}
            <link rel="stylesheet" type="text/css" href="{% static 'site.css' %}" />
        </head>
        <body>
            <div><a href="home">Home</a></div>
            {{ content }}
        </body>
    </html>
    ```

1. Aprire il file *views.py* dell'app e aggiungere una funzione denominata `about` che usa il modello:

    ```python
    def about(request):
        return render(
            request,
            "HelloDjangoApp/about.html",
            {
                'title' : "About HelloDjangoApp",
                'content' : "Example app page for Django."
            }
        )
    ```

1. Aprire il file *urls.py* del progetto Django e aggiungere la riga seguente alla matrice `urlPatterns`:

    ```python
    url(r'^about$', HelloDjangoApp.views.about, name='about'),
    ```

1. Aprire il file *templates/HelloDjangoApp/index.html* e aggiungere la riga seguente sotto l'elemento `<body>` per inserire un collegamento alla pagina About (anche in questo caso il collegamento viene sostituito con una barra di spostamento nel passaggio 3-4):

    ```html
    <div><a href="about">About</a></div>
    ```

1. Salvare tutti i file usando il **comando di** menu Salva tutto oppure premere  >   SEMPLICEMENTE **CTRL** + **MAIUSC** + **S.** Tecnicamente, questo passaggio non è necessario in quanto eseguendo il progetto in Visual Studio i file vengono salvati automaticamente. Ciononostante, si tratta di un comando utile da conoscere.

1. Eseguire il progetto per osservare i risultati e controllare lo spostamento tra le pagine. Al termine, arrestare il server.

### <a name="question-i-tried-using-index-for-the-link-to-the-home-page-but-it-didnt-work-why"></a>Domanda: Se si cerca usare "index" per il collegamento alla home page, non funziona. Perché?

Risposta: Anche se la funzione di visualizzazione in *views.py* è denominata `index`, i modelli di routing degli URL nel file *urls.py* del progetto Django non contengono un'espressione regolare che trova la corrispondenza con la stringa "index". Per trovare la corrispondenza con tale stringa, è necessario aggiungere un'altra voce per il modello `^index$`.

Come illustrato nella sezione seguente, è decisamente preferibile usare il tag `{% url '<pattern_name>' %}` nel modello di pagina per fare riferimento al *nome* di un modello. In questo caso, Django crea automaticamente l'URL appropriato. Sostituire, ad esempio, `<div><a href="home">Home</a></div>` in *about.html* con `<div><a href="{% url 'index' %}">Home</a></div>`. L'uso di 'index' in questo caso funziona perché il primo modello di URL in *urls.py* è in effetti denominato 'index' (in virtù dell'argomento `name='index'`). È anche possibile usare "home" per fare riferimento al secondo modello.

## <a name="step-3-4-use-template-inheritance-to-create-a-header-and-nav-bar"></a>Passaggio 3-4: Usare l'ereditarietà dei modelli per creare un'intestazione e una barra di spostamento

Invece di usare collegamenti di spostamento espliciti in ogni pagina, le app Web moderne usano in genere un'intestazione personalizzata e una barra di spostamento che fornisce i collegamenti alle pagine più importanti, i menu di scelta rapida e così via. Per assicurarsi che l'intestazione e la barra di spostamento siano uguali in tutte le pagine, tuttavia, non è necessario ripetere lo stesso codice in ogni modello di pagina. È invece possibile definire le parti comuni di tutte le pagine in un'unica posizione.

Il sistema di modelli di Django offre due modi per riutilizzare elementi specifici in più modelli: le inclusioni e l'ereditarietà.

- Le *inclusioni* sono altri modelli di pagina che vengono inseriti in un punto specifico nel modello di riferimento usando la sintassi `{% include <template_path> %}`. È anche possibile usare una variabile se si vuole modificare il percorso in modo dinamico nel codice. Le inclusioni vengono in genere usate nel corpo di una pagina per eseguire il pull nel modello condiviso in una posizione specifica della pagina.

- L'*ereditarietà* usa l'elemento `{% extends <template_path> %}` all'inizio di un modello di pagina per specificare un modello di base condiviso su cui è basato il modello di riferimento. L'ereditarietà viene comunemente usata per definire un layout condiviso, la barra di spostamento e altre strutture per le pagine dell'app, in modo che i modelli di riferimento debbano solo aggiungere o modificare aree specifiche del modello di base, dette *blocchi*.

In entrambi i casi `<template_path>` è relativo alla cartella *templates* dell'app (è consentito anche l'uso di `../` o `./`).

Un modello di base delinea i blocchi usando i tag `{% block <block_name> %}` e `{% endblock %}`. Se un modello di riferimento usa quindi tag con lo stesso nome di blocco, il contenuto del blocco esegue l'override di quello del modello di base.

I passaggi seguenti illustrano l'ereditarietà:

1. Nella cartella *modelli/HelloDjangoApp* dell'app creare un nuovo file HTML denominato *layout.html*, usando il menu di scelta rapida **Aggiungi** > **Nuovo elemento** o **Aggiungi** > **Pagina HTML**, e sostituirne il contenuto con il markup riportato di seguito. È possibile notare che questo modello contiene un blocco denominato "content" che è quello che le pagine di riferimento devono sostituire:

    ```html
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="utf-8" />
        <title>{{ title }}</title>
        {% load staticfiles %}
        <link rel="stylesheet" type="text/css" href="{% static 'site.css' %}" />
    </head>

    <body>
        <div class="navbar">
           <a href="/" class="navbar-brand">Hello Django</a>
           <a href="{% url 'home' %}" class="navbar-item">Home</a>
           <a href="{% url 'about' %}" class="navbar-item">About</a>
        </div>

        <div class="body-content">
    {% block content %}{% endblock %}
            <hr/>
            <footer>
                <p>&copy; 2018</p>
            </footer>
        </div>
    </body>
    </html>
    ```

1. Aggiungere gli stili seguenti al file *static/site.css* dell'app (questa procedura dettagliata non mira a illustrare la progettazione reattiva e questi stili servono semplicemente per generare un risultato interessante):

    ```css
    .navbar {
        background-color: lightslategray;
        font-size: 1em;
        font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
        color: white;
        padding: 8px 5px 8px 5px;
    }

    .navbar a {
        text-decoration: none;
        color: inherit;
    }

    .navbar-brand {
        font-size: 1.2em;
        font-weight: 600;
    }

    .navbar-item {
        font-variant: small-caps;
        margin-left: 30px;
    }

    .body-content {
        padding: 5px;
        font-family:'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    }
    ```

1. Modificare *templates/HelloDjangoApp/index.html* per fare riferimento al modello di base ed eseguire l'override del blocco di contenuto. È possibile notare che usando l'ereditarietà questo modello diventa semplice:

    ```html
    {% extends "HelloDjangoApp/layout.html" %}
    {% block content %}
    <span class="message">{{ message }}</span>{{ content }}
    {% endblock %}
    ```

1. Modificare anche *templates/HelloDjangoApp/about.html* per fare riferimento al modello di base ed eseguire l'override del blocco di contenuto:

    ```html
    {% extends "HelloDjangoApp/layout.html" %}
    {% block content %}
    {{ content }}
    {% endblock %}
    ```

1. Eseguire il server per osservare i risultati. Al termine, arrestare il server.

    ![App in esecuzione con la barra di spostamento](media/django/step03-nav-bar.png)

1. Poiché verranno apportate modifiche sostanziali all'app, è di nuovo il momento di [eseguire il commit delle modifiche nel controllo del codice sorgente](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control).

## <a name="next-steps"></a>Passaggi successivi

> [!div class="nextstepaction"]
> [Usare il modello di progetto Web Django completo](learn-django-in-visual-studio-step-04-full-django-project-template.md)

## <a name="go-deeper"></a>Approfondimento

- [Distribuire l'app Web nel Servizio app di Azure](publishing-python-web-applications-to-azure-from-visual-studio.md)
- [Writing your first Django app, part 3 (views)](https://docs.djangoproject.com/en/2.0/intro/tutorial03/) (Scrittura della prima app Django, parte 3 - visualizzazioni) (docs.djangoproject.com)
- Per altre funzionalità dei modelli Django, ad esempio il flusso di controllo, vedere [The Django template language](https://docs.djangoproject.com/en/2.0/ref/templates/language/) (Linguaggio dei modelli Django) (docs.djangoproject.com)
- Per informazioni dettagliate sull'uso del tag `{% url %}`, vedere la sezione [url](https://docs.djangoproject.com/en/2.0/ref/templates/builtins/#url) in [Built-in template tags and filters for Django templates reference](https://docs.djangoproject.com/en/2.0/ref/templates/builtins/) (Filtri e tag dei modelli predefiniti per i riferimenti dei modelli Django) (docs.djangoproject.com)
- Codice sorgente per l'esercitazione su GitHub: [Microsoft/python-sample-vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django)
