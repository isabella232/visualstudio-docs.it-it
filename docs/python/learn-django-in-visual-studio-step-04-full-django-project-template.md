---
title: Informazioni sull'esercitazione Django in Visual Studio, passaggio 4, modello di progetto Web
titleSuffix: ''
description: Procedura dettagliata sui concetti di base relativi a Django nel contesto dei progetti di Visual Studio, che illustra, in particolare, le funzionalità del modello Progetto Web Django.
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
ms.openlocfilehash: b95f4dec53abb1e4a02790b2434f6b8577115ec2
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625391"
---
# <a name="step-4-use-the-full-django-web-project-template"></a>Passaggio 4: Usare il modello di progetto Web Django completo

**Passaggio precedente: [Rendere disponibili file statici, aggiungere pagine e usare l'ereditarietà dei modelli](learn-django-in-visual-studio-step-03-serve-static-files-and-add-pages.md)**

Dopo aver esplorato i concetti di base relativi a Django creando un'app basata sul modello "Progetto Web Django vuoto" in Visual Studio, è possibile comprendere facilmente l'app più completa prodotta dal modello "Progetto Web Django".

In questo passaggio:

> [!div class="checklist"]
> - Si creerà un'app Web Django completa usando il modello "Progetto Web Django" e si esaminerà la struttura del progetto (passaggio 4-1)
> - Si comprenderanno le visualizzazioni e i modelli di pagina creati dal modello di progetto, costituito da tre pagine che ereditano da un modello di pagina di base e che usa librerie JavaScript statiche come jQuery e Bootstrap (passaggio 4-2)
> - Si comprenderà il routing degli URL fornito dal modello (passaggio 4-3)

Il modello offre anche l'autenticazione di base, come descritto nel passaggio 5.

## <a name="step-4-1-create-a-project-from-the-template"></a>Passaggio 4-1: Creare un progetto da un modello

1. In Visual Studio passare a **Esplora soluzioni**, fare clic con il pulsante destro del mouse sulla soluzione **LearningDjango** creata in precedenza in questa esercitazione e scegliere **Aggiungi** > **Nuovo progetto**. In alternativa, se si vuole usare una nuova soluzione, selezionare **File**  >  **Nuovo**  >  **Project** invece.

1. Nella finestra di dialogo del nuovo progetto cercare e selezionare il modello **Django Web Project,** chiamare il progetto "DjangoWeb" e selezionare **OK.**

1. Poiché il modello include di nuovo un file *requirements.txt*, Visual Studio chiede dove installare queste dipendenze. Scegliere l'opzione **Installa in un ambiente virtuale** e nella finestra di dialogo **Aggiungi ambiente virtuale** selezionare **Crea** per accettare le impostazioni predefinite.

1. Al termine della configurazione dell'ambiente virtuale in Visual Studio, seguire le istruzioni nel file *readme.html* visualizzato per creare un utente Django con privilegi avanzati, ovvero un amministratore. È sufficiente fare clic con il Visual Studio progetto e selezionare il comando **Python**  >  **Django Create Superuser (Crea superutente Python Django),** quindi seguire le istruzioni visualizzate. Assicurarsi di registrare il nome utente e la password, perché verranno usati per provare le funzionalità di autenticazione dell'app.

1. Impostare il **progetto DjangoWeb** come predefinito per la soluzione Visual Studio facendo clic con il pulsante destro del mouse sul progetto **in** Esplora soluzioni e selezionando Imposta come avvio **Project**. Il progetto di avvio, indicato in grassetto, è quello che viene eseguito quando si avvia il debugger.

    ![Progetto DjangoWeb mostrato in Esplora soluzioni come progetto di avvio](media/django/step04-second-project-in-solution-set-as-startup-project.png)

1. Selezionare **Debug**  >  **Avvia debug** (**F5**) o usare il pulsante **Server Web** sulla barra degli strumenti per eseguire il server:

    ![Pulsante di esecuzione del server Web della barra degli strumenti in Visual Studio](media/django/run-web-server-toolbar-button.png)

1. L'app creata dal modello ha tre pagine, Home, About e Contact, tra cui è possibile spostarsi usando la barra di spostamento. Dedicare un minuto o due a esaminare le diverse parti dell'app. Per eseguire l'autenticazione con l'app tramite il comando **Accedi**, usare le credenziali di utente avanzato create in precedenza.

    ![Visualizzazione completa nel browser dell'app Progetto Web Django](media/django/step04-full-app-desktop-view.png)

1. L'app creata dal modello "Progetto Web Django" usa Bootstrap per ottenere un layout reattivo che si adatta ai fattori di forma per dispositivi mobili. Per osservare questa velocità di risposta, ridimensionare il browser in base a una visualizzazione ridotta, in modo che il rendering del contenuto venga eseguito in verticale e che la barra di spostamento si trasformi in icona di menu:

    ![Visualizzazione per dispositivi mobili (ridotta) dell'app Progetto Web Django](media/django/step04-full-app-mobile-view.png)

1. È possibile lasciare l'app in esecuzione per le sezioni seguenti.

    Se si vuole arrestare l'app ed [eseguire il commit delle modifiche nel controllo del codice sorgente](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control), aprire prima di tutto la pagina **Modifiche** in **Team Explorer**, fare clic con il pulsante destro del mouse sulla cartella per l'ambiente virtuale (generalmente **env**) e scegliere **Ignora questi elementi locali**.

### <a name="examine-what-the-template-creates"></a>Esaminare gli elementi creati dal modello

Al livello più ampio il modello "Progetto Web Django" crea la struttura seguente:

- File nella radice del progetto:
  - *manage.py*, l' utilità di amministrazione Django.
  - *db.sqlite3*, un database SQLite predefinito.
  - *requirements.txt*, che contiene una dipendenza da Django 1.x.
  - *readme.html*, un file visualizzato in Visual Studio dopo la creazione del progetto. Come indicato nella sezione precedente, seguire le istruzioni riportate qui per creare un account utente con privilegi avanzati (amministratore) per l'app.
- La cartella *app* contiene tutti i file dell'app, tra cui le visualizzazioni, i modelli, i test, i moduli, e i file statici (vedere il passaggio 4-2). È in genere opportuno rinominare questa cartella per usare un nome di app più distintivo.
- La *cartella DjangoWeb* (progetto Django) contiene i file di progetto Django tipici: *\_ \_ init \_ \_ .py,* *settings.py,* *urls.py* e *wsgi.py*. Tramite il modello di progetto, *settings.py* è già configurato per l'app e il file di database, mentre *urls.py* è già configurato con route a tutte le pagine dell'app, incluso il modulo di accesso.

### <a name="question-is-it-possible-to-share-a-virtual-environment-between-visual-studio-projects"></a>Domanda: È possibile condividere un ambiente virtuale tra progetti di Visual Studio?

Risposta: Sì, ma tenere presente che diversi progetti probabilmente usano pacchetti diversi nel tempo e di conseguenza un ambiente virtuale condiviso deve contenere tutti i pacchetti per tutti i progetti che lo usano.

Ciononostante, per usare un ambiente virtuale esistente, eseguire le operazioni seguenti:

1. Quando viene richiesto di installare le dipendenze in Visual Studio, selezionare l'opzione **Installazione manuale**.
1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo **Ambienti Python** e scegliere **Aggiungi ambiente virtuale esistente**.
1. Individuare e selezionare la cartella contenente l'ambiente virtuale, quindi selezionare **OK**.

## <a name="step-4-2-understand-the-views-and-page-templates-created-by-the-project-template"></a>Passaggio 4-2: Comprendere le visualizzazioni e i modelli di pagina creati dal modello di progetto

Come si può osservare quando si esegue il progetto, l'app contiene tre visualizzazioni: Home, About e Contact. Il codice per queste visualizzazioni è disponibile nella cartella *app/views*. Ogni funzione di visualizzazione chiama semplicemente `django.shortcuts.render` con il percorso di un modello e un semplice oggetto dizionario. Ad esempio, la pagina About viene gestita dalla funzione `about`:

```python
def about(request):
    """Renders the about page."""
    assert isinstance(request, HttpRequest)
    return render(
        request,
        'app/about.html',
        {
            'title':'About',
            'message':'Your application description page.',
            'year':datetime.now().year,
        }
    )
```

I modelli si trovano nella cartella *templates/app* dell'app e in genere è consigliabile rinominare *app* in base al nome effettivo dell'app. Il modello di base, *layout.html*, è il più completo. Fa riferimento a tutti i file statici necessari (JavaScript e CSS), definisce un blocco denominato "content" di cui altre pagine eseguono l'override e fornisce un altro blocco denominato "scripts". Gli estratti annotati di *layout.html* indicati di seguito illustrano queste aree specifiche:

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8" />

    <!-- Define a viewport for Bootstrap's responsive rendering -->
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>{{ title }} - My Django Application</title>

    {% load staticfiles %}
    <link rel="stylesheet" type="text/css" href="{% static 'app/content/bootstrap.min.css' %}" />
    <link rel="stylesheet" type="text/css" href="{% static 'app/content/site.css' %}" />
    <script src="{% static 'app/scripts/modernizr-2.6.2.js' %}"></script>
</head>
<body>
    <!-- Navbar omitted -->

    <div class="container body-content">

<!-- "content" block that pages are expected to override -->
{% block content %}{% endblock %}
        <hr/>
        <footer>
            <p>&copy; {{ year }} - My Django Application</p>
        </footer>
    </div>

<!-- Additional scripts; use the "scripts" block to add page-specific scripts.  -->
    <script src="{% static 'app/scripts/jquery-1.10.2.js' %}"></script>
    <script src="{% static 'app/scripts/bootstrap.js' %}"></script>
    <script src="{% static 'app/scripts/respond.js' %}"></script>
{% block scripts %}{% endblock %}

</body>
</html>
```

I singoli modelli di pagina *about.html*, *contact.html* e *index.html* estendono il modello di base *layout.html*. *about.html* è il più semplice e contiene i tag `{% extends %}` e `{% block content %}`:

```html
{% extends "app/layout.html" %}

{% block content %}

<h2>{{ title }}.</h2>
<h3>{{ message }}</h3>

<p>Use this area to provide additional information.</p>

{% endblock %}
```

*index.html* e *contact.html* usano la stessa struttura e consentono un contenuto più lungo nel blocco "content".

Nella cartella *templates/app* è presente anche una quarta pagina *login.html*, insieme a *loginpartial.html*, che viene inserita in *layout.html* usando `{% include %}`. Questi file di modello vengono descritti nel passaggio 5 sull'autenticazione.

### <a name="question-can--block--and--endblock--be-indented-in-the-django-page-template"></a>Domanda: È possibile applicare un rientro a {% block %} e a {% endblock %} nel modello di pagina Django?

Risposta: Sì, i modelli di pagina Django funzionano correttamente se si applica un rientro ai tag di blocco, forse per allinearli all'interno degli elementi padre appropriati. I rientri non vengono applicati nei modelli di pagina generati dal modello di progetto di Visual Studio, per poterne individuare immediatamente la posizione.

## <a name="step-4-3-understand-the-url-routing-created-by-the-template"></a>Passaggio 4-3: Comprendere il routing degli URL creato dal modello

Il file *urls.py* del progetto Django creato dal modello "Progetto Web Django" contiene il codice seguente:

```python
from datetime import datetime
from django.conf.urls import url
import django.contrib.auth.views

import app.forms
import app.views

urlpatterns = [
    url(r'^$', app.views.home, name='home'),
    url(r'^contact$', app.views.contact, name='contact'),
    url(r'^about$', app.views.about, name='about'),
    url(r'^login/$',
        django.contrib.auth.views.login,
        {
            'template_name': 'app/login.html',
            'authentication_form': app.forms.BootstrapAuthenticationForm,
            'extra_context':
            {
                'title': 'Log in',
                'year': datetime.now().year,
            }
        },
        name='login'),
    url(r'^logout$',
        django.contrib.auth.views.logout,
        {
            'next_page': '/',
        },
        name='logout'),
]
```

I primi tre modelli di URL sono direttamente associati alle visualizzazioni `home`, `contact` e `about` nel file *views.py* dell'app. I modelli `^login/$` e `^logout$`, d'altro canto, usano visualizzazioni Django predefinite invece di visualizzazioni definite dall'applicazione. Le chiamate al metodo `url` includono anche dati aggiuntivi per personalizzare la visualizzazione. Il passaggio 5 esplora queste chiamate.

### <a name="question-in-the-project-i-created-why-does-the-about-url-pattern-uses-about-instead-of-about-as-shown-here"></a>Domanda: Perché nel progetto creato il modello di URL "about" usa '^about' anziché '^about$' come illustrato qui?

Risposta: La mancanza del carattere '$' finale nell'espressione regolare è una semplice disattenzione in molte versioni del modello di progetto. Il modello di URL funziona perfettamente per una pagina denominata "about", ma senza il carattere '$' finale il modello di URL corrisponde anche a URL come "about=django", "about09876", "aboutoflaughter" e così via. Il carattere '$' finale è mostrato qui per creare un modello di URL che corrisponde *solo* ad "about".

## <a name="next-steps"></a>Passaggi successivi

> [!div class="nextstepaction"]
> [Autenticare gli utenti in Django](learn-django-in-visual-studio-step-05-django-authentication.md)

## <a name="go-deeper"></a>Approfondimento

- [Distribuire l'app Web nel Servizio app di Azure](publishing-python-web-applications-to-azure-from-visual-studio.md)
- [Writing your first Django app, part 4 - views](https://docs.djangoproject.com/en/2.0/intro/tutorial04/) (Scrittura della prima app Django, parte 4 - Visualizzazioni) (docs.djangoproject.com)
- Codice sorgente per l'esercitazione su GitHub: [Microsoft/python-sample-vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django)
