---
title: Informazioni sull'esercitazione Django in Visual Studio, passaggio 5, autenticazione
titleSuffix: ''
description: Procedura dettagliata sui concetti di base relativi a Django nel contesto dei progetti di Visual Studio, che illustra, in particolare, le funzionalità di autenticazione fornite dai modelli di progetto Web Django.
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
ms.openlocfilehash: 17a6ee7cbf622eb90debd961ba36f159bf7fbc6c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122156526"
---
# <a name="step-5-authenticate-users-in-django"></a>Passaggio 5: Autenticare gli utenti in Django

**Passaggio precedente: [Usare il modello Progetto Web Django completo](learn-django-in-visual-studio-step-04-full-django-project-template.md)**

::: moniker range="vs-2017"
Poiché l'autenticazione è un'esigenza comune per le app Web, il modello "Progetto Web Django" include un flusso di autenticazione di base. Anche il modello "Polls Django Web Project" illustrato nel passaggio 6 di questa esercitazione include lo stesso flusso. Quando si usa uno dei modelli di progetto Django, Visual Studio include tutti i moduli necessari per l'autenticazione nel settings.py *Django.*
::: moniker-end

::: moniker range=">=vs-2019"
Poiché l'autenticazione è un'esigenza comune per le app Web, il modello "Progetto Web Django" include un flusso di autenticazione di base. Quando si usa uno dei modelli di progetto Django, Visual Studio include tutti i moduli necessari per l'autenticazione nel file *settings.py* del progetto Django.
::: moniker-end

In questo passaggio viene descritto come:

> [!div class="checklist"]
> - Usare il flusso di autenticazione fornito nei modelli di Visual Studio (passaggio 5-1)

## <a name="step-5-1-use-the-authentication-flow"></a>Passaggio 5-1: Usare il flusso di autenticazione

I passaggi seguenti permettono di provare il flusso di autenticazione e descrivono le parti del progetto interessate:

1. Se non si sono ancora seguite le istruzioni contenute nel file *readme.html* all'interno della radice del progetto per creare un utente con privilegi avanzati (amministratore), farlo ora.

1. Eseguire l'app da Visual Studio **debug**  >  **avvia debug** (**F5**). Quando l'app viene visualizzata nel browser, osservare che l'opzione di **accesso** viene visualizzata nell'angolo in alto a destra della barra di spostamento.

    ![Controllo di accesso nella pagina dell'app Progetto Web Django](media/django/step05-login-control.png)

1. Aprire *templates/app/layout.html*. Si noti che l'elemento `<div class="navbar ...>` contiene il tag `{% include app/loginpartial.html %}`. Il tag `{% include %}` indica al sistema di modelli di Django di eseguire il pull del contenuto del file incluso a questo punto nel modello che lo contiene.

1. Aprire *templates/app/loginpartial.html* e osservare il modo in cui viene usato il tag condizionale `{% if user.is_authenticated %}` insieme a un tag `{% else %}` per il rendering di diversi elementi dell'interfaccia utente a seconda che l'utente abbia o meno eseguito l'autenticazione:

    ```html
    {% if user.is_authenticated %}
    <form id="logoutForm" action="/logout" method="post" class="navbar-right">
        {% csrf_token %}
        <ul class="nav navbar-nav navbar-right">
            <li><span class="navbar-brand">Hello {{ user.username }}!</span></li>
            <li><a href="javascript:document.getElementById('logoutForm').submit()">Log off</a></li>
        </ul>
    </form>

    {% else %}

    <ul class="nav navbar-nav navbar-right">
        <li><a href="{% url 'login' %}">Log in</a></li>
    </ul>

    {% endif %}
    ```

1. Poiché nessun utente ha eseguito l'autenticazione quando l'app è stata avviata per la prima volta, il codice di questo modello esegue il rendering solo del collegamento di accesso al percorso relativo "login". Come specificato in *urls.py* e come illustrato nella sezione precedente, viene eseguito il mapping di questa route alla visualizzazione `django.contrib.auth.views.login`, cui vengono forniti i dati seguenti:

    ```python
    {
        'template_name': 'app/login.html',
        'authentication_form': app.forms.BootstrapAuthenticationForm,
        'extra_context':
        {
            'title': 'Log in',
            'year': datetime.now().year,
        }
    }
    ```

    Qui `template_name` identifica il modello della pagina di accesso, in questo caso *templates/app/login.html*. La proprietà `extra_context` viene aggiunta ai dati del contesto predefinito specificati per il modello. `authentication_form`, infine, specifica una classe modulo da usare con la pagina di accesso. Nel modello viene visualizzata come oggetto `form`. Il valore predefinito è `AuthenticationForm` (da `django.contrib.auth.views`). Il modello di progetto di Visual Studio usa invece il modulo definito nel file *forms.py* dell'app:

    ```python
    from django import forms
    from django.contrib.auth.forms import AuthenticationForm
    from django.utils.translation import ugettext_lazy as _

    class BootstrapAuthenticationForm(AuthenticationForm):
        """Authentication form which uses boostrap CSS."""
        username = forms.CharField(max_length=254,
                                   widget=forms.TextInput({
                                       'class': 'form-control',
                                       'placeholder': 'User name'}))
        password = forms.CharField(label=_("Password"),
                                   widget=forms.PasswordInput({
                                       'class': 'form-control',
                                       'placeholder':'Password'}))
    ```

    Come si può notare, questa classe modulo deriva da `AuthenticationForm` ed esegue l'override in modo specifico dei campi relativi a nome utente e password per aggiungere testo segnaposto. Il modello di Visual Studio include questo codice esplicito in base al presupposto che si voglia probabilmente personalizzare il modulo, ad esempio aggiungendo una convalida della complessità della password.

1. Quando si passa alla pagina di accesso, quindi, l'app esegue il rendering del modello *login.html*. Le variabili `{{ form.username }}` e `{{ form.password }}` eseguono il rendering dei moduli `CharField` da `BootstrapAuthenticationForm`. Sono anche presenti una sezione predefinita per visualizzare gli errori di convalida e un elemento già pronto per gli account di accesso social se si sceglie di aggiungere questi servizi.

    ```html
    {% extends "app/layout.html" %}

    {% block content %}

    <h2>{{ title }}</h2>
    <div class="row">
        <div class="col-md-8">
            <section id="loginForm">
                <form action="." method="post" class="form-horizontal">
                    {% csrf_token %}
                    <h4>Use a local account to log in.</h4>
                    <hr />
                    <div class="form-group">
                        <label for="id_username" class="col-md-2 control-label">User name</label>
                        <div class="col-md-10">
                            {{ form.username }}
                        </div>
                    </div>
                    <div class="form-group">
                        <label for="id_password" class="col-md-2 control-label">Password</label>
                        <div class="col-md-10">
                            {{ form.password }}
                        </div>
                    </div>
                    <div class="form-group">
                        <div class="col-md-offset-2 col-md-10">
                            <input type="hidden" name="next" value="/" />
                            <input type="submit" value="Log in" class="btn btn-default" />
                        </div>
                    </div>
                    {% if form.errors %}
                    <p class="validation-summary-errors">Please enter a correct user name and password.</p>
                    {% endif %}
                </form>
            </section>
        </div>
        <div class="col-md-4">
            <section id="socialLoginForm"></section>
        </div>
    </div>

    {% endblock %}
    ```

1. Quando si invia il modulo, Django tenta di autenticare le credenziali specificate dall'utente, ad esempio le credenziali dell'utente con privilegi avanzati. Se l'autenticazione non riesce, resta visualizzata la stessa pagina, ma `form.errors` viene impostato su true. Se l'autenticazione riesce, Django passa all'URL relativo nel campo "next", `<input type="hidden" name="next" value="/" />`, che in questo caso è la home page (`/`).

1. A questo punto, quando viene eseguito di nuovo il rendering della home page, la proprietà `user.is_authenticated` è true quando viene eseguito il rendering del modello *loginpartial.html*. Di conseguenza, vengono visualizzati il messaggio **Hello (nome utente)** e **Log off** (Disconnetti). È possibile usare `user.is_authenticated` in altre parti dell'app per controllare l'autenticazione.

    ![Messaggio Hello e controllo di disconnessione nella pagina dell'app Progetto Web Django](media/django/step05-logoff-control.png)

1. Per controllare se l'utente autenticato è autorizzato ad accedere a determinate risorse, è necessario recuperare le autorizzazioni specifiche dell'utente dal database. Per altre informazioni, vedere [Using the Django authentication system](https://docs.djangoproject.com/en/2.0/topics/auth/default/#permissions-and-authorization) (Uso del sistema di autenticazione Django) nella documentazione di Django.

1. L'utente con privilegi avanzati o amministratore, in particolare, è autorizzato ad accedere alle interfacce di amministrazione Django predefinite mediante gli URL relativi "/admin/" e "/ admin/doc /". Per abilitare queste interfacce, eseguire le operazioni seguenti:

    1. Installare il pacchetto Python docutils nell'ambiente. È consigliabile aggiungere "docutils" al file *requirements.txt*, in **Esplora soluzioni** espandere il progetto, espandere il nodo **Ambienti Python**, quindi fare clic con il pulsante destro del mouse sull'ambiente in uso e selezionare **Installa da requirements.txt**.

    1. Aprire il file *urls.py* del progetto Django e rimuovere i commenti predefiniti dalle voci seguenti:

        ```python
        from django.conf.urls import include
        from django.contrib import admin
        admin.autodiscover()

        # ...
        urlpatterns = [
            # ...
            url(r'^admin/doc/', include('django.contrib.admindocs.urls')),
            url(r'^admin/', include(admin.site.urls)),
        ]
        ```

    1. Nel file *settings.py* del progetto Django passare alla raccolta `INSTALLED_APPS` e aggiungere `'django.contrib.admindocs'`.

    1. Quando si riavvia l'app, è possibile passare ad "/admin/" e "/ admin/doc /" ed eseguire attività come la creazione di account utente aggiuntivi.

        ![Interfaccia di amministrazione Django](media/django/step05-administrator-interface.png)

1. La parte finale per il flusso di autenticazione è la disconnessione. Come si può notare in *loginpartial.html*, il collegamento **Log off** (Disconnetti) invia semplicemente una richiesta POST all'URL relativo "/login", gestito dalla visualizzazione predefinita `django.contrib.auth.views.logout`. Questa visualizzazione non è dotata di un'interfaccia utente e si limita a passare alla home page, come illustrato in *urls.py* per il modello "^ logout$". Se si vuole visualizzare una pagina di disconnessione, modificare prima di tutto il modello di URL nel modo seguente per aggiungere una proprietà "template_name" e rimuovere la proprietà "next_page":

    ```python
    url(r'^logout$',
        django.contrib.auth.views.logout,
        {
            'template_name': 'app/loggedoff.html',
            # 'next_page': '/',
        },
        name='logout')
    ```

    Creare quindi *templates/app/loggedoff.html* con il contenuto (minimo) seguente:

    ```html
    {% extends "app/layout.html" %}
    {% block content %}
    <h3>You have been logged off</h3>
    {% endblock %}
    ```

    Il risultato sarà simile al seguente:

    ![Pagina di disconnessione aggiunta](media/django/step05-logged-off-page.png)

1. Al termine, arrestare il server ed eseguire di nuovo il commit delle modifiche nel controllo del codice sorgente.

### <a name="question-what-is-the-purpose-of-the--csrf_token--tag-that-appears-in-the-form-elements"></a>Domanda: Qual è lo scopo del tag {% csrf_token %} visualizzato negli \<form\> elementi?

Risposta: Il tag `{% csrf_token %}` include la [protezione da richieste intersito false (crsf, cross-site request forgery)](https://docs.djangoproject.com/en/2.0/ref/csrf/) predefinita di Django (documentazione di Django). Questo tag viene aggiunto in genere a qualsiasi elemento che prevede metodi di richiesta POST, PUT o DELETE, ad esempio un modulo. La funzione di rendering del modello (`render`) inserisce quindi la protezione necessaria.

## <a name="next-steps"></a>Passaggi successivi

::: moniker range="vs-2017"
- [Usare il modello Progetto Web Django di sondaggi](learn-django-in-visual-studio-step-06-polls-django-web-project-template.md)
::: moniker-end

::: moniker range=">=vs-2019"
> [!Note]
> Durante l'esercitazione è stato eseguito il commit della soluzione di Visual Studio nel controllo del codice sorgente. A questo punto è utile eseguire un altro commit. La soluzione dovrebbe corrispondere al codice sorgente per l'esercitazione su GitHub: [Microsoft/python-sample-vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django).

Sono stati ora esaminati tutti i modelli "Blank Django Web Project" e "Django Web Project" in Visual Studio. Sono state apprese le nozioni di base di Django, ad esempio l'uso di visualizzazioni e modelli, e sono stati analizzati il routing, l'autenticazione e l'uso di modelli di database. A questo punto, si dovrebbe essere in grado di creare un'app Web con tutti i modelli e le visualizzazioni necessari.

L'esecuzione di un'app Web nel computer di sviluppo è solo un passaggio per rendere disponibile l'app ai clienti. I passaggi successivi possono includere le attività seguenti:

- Distribuire l'app Web in un server di produzione, ad esempio Servizio app di Azure. Vedere [Eseguire la pubblicazione in Servizio app di Azure](publishing-python-web-applications-to-azure-from-visual-studio.md).

- Personalizzare la pagina 404 creando un modello denominato *templates/404.html*. Quando questo modello è presente, Django lo usa al posto di quello predefinito. Per altre informazioni, vedere [Error views](https://docs.djangoproject.com/en/2.0/ref/views/#error-views) (Visualizzazioni di errore) nella documentazione di Django.

- Scrivere unit test in *tests.py*. I modelli di progetto di Visual Studio costituiscono il punto di partenza per questa attività. Per altre informazioni, vedere [Writing your first Django app, part 5 - testing](https://docs.djangoproject.com/en/2.0/intro/tutorial05/) (Scrittura della prima app Django, parte 5 - test) e [Testing in Django](https://docs.djangoproject.com/en/2.0/topics/testing/) (Test in Django) nella documentazione di Django.

- Modificare l'app da SQLite a un archivio dati a livello di produzione, ad esempio PostgreSQL, MySQL e SQL Server (che possono tutti essere ospitati in Azure). Come descritto in [When to use SQLite](https://www.sqlite.org/whentouse.html) (Quando usare SQLite) (sqlite.org), SQLite è appropriato per i siti con traffico medio o basso, con meno di 100.000 accessi al giorno, ma non è consigliato per volumi più elevati. È anche limitato a un unico computer, quindi non può essere usato in scenari con più server, ad esempio con il bilanciamento del carico e la replica geografica. Per informazioni sul supporto di Django per altri database, vedere [Database setup](https://docs.djangoproject.com/en/2.0/intro/tutorial02/#database-setup) (Configurazione del database). È anche possibile usare [Azure SDK per Python](/azure/python/) per usare servizi di archiviazione di Azure, ad esempio tabelle e BLOB.

- Configurare una pipeline di integrazione continua/distribuzione continua in un servizio come Azure DevOps. Oltre a usare il controllo del codice sorgente (in Azure Repos, GitHub o altrove), è possibile configurare un progetto di Azure DevOps in modo che esegua automaticamente gli unit test come prerequisito per il rilascio, oltre che configurare la pipeline per la distribuzione in un server di gestione temporanea per eseguire test aggiuntivi prima della distribuzione in produzione. Azure DevOps inoltre si integra con soluzioni di monitoraggio, ad esempio App Insights, chiudendo così l'intero ciclo con strumenti di pianificazione Agile. Per altre informazioni, vedere [Creare una pipeline di CI/CD per Python con il progetto Azure DevOps](/azure/devops-project/azure-devops-project-python?view=vsts&preserve-view=true) e la [documentazione generale di Azure DevOps](/azure/devops/?view=vsts&preserve-view=true).
::: moniker-end
## <a name="go-deeper"></a>Approfondimento

- [User authentication in Django](https://docs.djangoproject.com/en/2.0/topics/auth/) (Autenticazione utente in Django) (docs.djangoproject.com)
- Codice sorgente per l'esercitazione su GitHub: [Microsoft/python-sample-vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django)
