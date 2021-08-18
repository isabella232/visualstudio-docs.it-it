---
title: Informazioni sull'esercitazione Django in Visual Studio, passaggio 6, modello di progetto di sondaggi
titleSuffix: ''
description: Procedura dettagliata sui concetti di base relativi a Django nel contesto dei progetti di Visual Studio, che illustra, in particolare, le funzionalità del modello Progetto Web Django di sondaggi, come la personalizzazione dell'area di amministrazione.
ms.date: 11/19/2018
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.technology: vs-python
ms.custom: seodec18
monikerRange: vs-2017
ms.workload:
- python
- data-science
ms.openlocfilehash: 69b675f19060cf57d8c9dca03414709de5545199
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122054483"
---
# <a name="step-6-use-the-polls-django-web-project-template"></a>Passaggio 6: Usare il modello Progetto Web Django di sondaggi

**Passaggio precedente: [Autenticare gli utenti in Django](learn-django-in-visual-studio-step-05-django-authentication.md)**

Dopo aver compreso il modello "Progetto Web Django" di Visual Studio, è ora possibile esaminare il terzo modello Django, "Progetto Web Django di sondaggi", che si basa sulla stessa codebase e illustra come usare un database.

In questo passaggio viene descritto come:

> [!div class="checklist"]
> - Creare un progetto dal modello e inizializzare il database (passaggio 6-1)
> - Comprendere i modelli di dati (passaggio 6-2)
> - Applicare le migrazioni (passaggio 6-3)
> - Comprendere le visualizzazioni e i modelli di pagina creati dal modello di progetto (passaggio 6-4)
> - Creare un'interfaccia di amministrazione personalizzata (passaggio 6-5)

Un progetto creato usando questo modello è simile a quello che si ottiene seguendo l'esercitazione Scrittura della prima [app Django](https://docs.djangoproject.com/en/2.0/intro/tutorial01/) nella documentazione di Django. L'app Web è costituita da un sito pubblico che consente agli utenti di visualizzare i sondaggi e votarli, insieme a un'interfaccia amministrativa personalizzata tramite la quale è possibile gestire i sondaggi. Viene usato lo stesso sistema di autenticazione usato per il modello "Progetto Web Django" e viene usato in modo più estensivo il database mediante l'implementazione di modelli Django come illustrato nelle sezioni seguenti.

## <a name="step-6-1-create-the-project-and-initialize-the-database"></a>Passaggio 6-1: Creare il progetto e inizializzare il database

1. In Visual Studio passare a **Esplora soluzioni**, fare clic con il pulsante destro del mouse sulla soluzione **LearningDjango** creata in precedenza in questa esercitazione e scegliere **Aggiungi** > **Nuovo progetto**. In alternativa, se si vuole usare una nuova soluzione, selezionare **File**  >  **Nuovo**  >  **Project** invece.

1. Nella finestra di dialogo Nuovo progetto cercare e selezionare il modello **Progetto Web Django di sondaggi**, assegnare al progetto il nome "DjangoPolls" e selezionare **OK**.

1. Come gli altri modelli di progetto in Visual Studio, il modello "Progetto Web Django di sondaggi" include un file *requirements.txt* e Visual Studio chiede dove installare le dipendenze. Scegliere l'opzione **Installa in un ambiente virtuale** e nella finestra di dialogo **Aggiungi ambiente virtuale** selezionare **Crea** per accettare le impostazioni predefinite.

1. Al termine della configurazione dell'ambiente virtuale in Python, seguire le istruzioni nel file *readme.html* visualizzato per inizializzare il database e creare un utente Django con privilegi avanzati, ovvero un amministratore. La procedura è innanzitutto fare clic con il pulsante destro del mouse sul progetto **DjangoPolls** **in Esplora soluzioni,** selezionare il comando **Python**  >  **Django Migrate,** quindi fare di nuovo clic con il pulsante destro del mouse sul progetto, selezionare il comando **Python**  >  **Django Create Superuser** e seguire le istruzioni. Se si prova a creare prima di tutto un utente con privilegi avanzati, viene generato un errore perché il database non è stato inizializzato.

1. Impostare il progetto **DjangoPolls** come predefinito per la soluzione di Visual Studio facendo clic con il pulsante destro del mouse su tale progetto in **Esplora soluzioni** e selezionando **Imposta come progetto di avvio**. Il progetto di avvio, indicato in grassetto, è quello che viene eseguito quando si avvia il debugger.

1. Selezionare **Debug**  >  **Avvia debug** (**F5**) o usare il pulsante **Server Web** sulla barra degli strumenti per eseguire il server:

    ![Pulsante di esecuzione del server Web della barra degli strumenti in Visual Studio](media/django/run-web-server-toolbar-button.png)

1. L'app creata dal modello ha tre pagine, Home, About e Contact, tra cui è possibile spostarsi usando la barra di spostamento superiore. Dedicare uno o due minuti a esaminare le diverse parti dell'app. Le pagine About e Contact sono molto simili a quelle in "Progetto Web Django" e non vengono illustrate ulteriormente.

    ![Visualizzazione completa nel browser dell'app Progetto Web Django di sondaggi](media/django/step06-full-app-view.png)

1. Selezionare anche il collegamento **Administration** sulla barra di navigazione per visualizzare una schermata di accesso che dimostra che l'interfaccia di amministrazione è autorizzata solo per gli amministratori autenticati. Usare le credenziali di utente con privilegi avanzati per essere indirizzati alla pagina "/admin", abilitata per impostazione predefinita quando si usa questo modello di progetto.

    ![Visualizzazione dell'area di amministrazione dell'app Progetto Web Django di sondaggi](media/django/step06-polls-administrative-interface.png)

1. È possibile lasciare l'app in esecuzione per le sezioni seguenti.

    Se si vuole arrestare l'app ed [eseguire il commit delle modifiche nel controllo del codice sorgente](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control), aprire prima di tutto la pagina **Modifiche** in **Team Explorer**, fare clic con il pulsante destro del mouse sulla cartella per l'ambiente virtuale (generalmente **env**) e scegliere **Ignora questi elementi locali**.

### <a name="examine-the-project-contents"></a>Esaminare i contenuti del progetto

Come accennato prima, molte parti di un progetto creato dal modello "Progetto Web Django di sondaggi" dovrebbero risultare familiari se sono stati analizzati altri modelli di progetto in Visual Studio. I passaggi aggiuntivi in questo articolo riepilogano le modifiche e le aggiunte più significative, in particolare i modelli di dati e le visualizzazioni aggiuntive.

### <a name="question-what-does-the-django-migrate-command-do"></a>Domanda: A cosa serve il comando Migrazione Django?

Risposta: Il comando **Migrazione Django** esegue nello specifico il comando `manage.py migrate`, che esegue a sua volta eventuali script nella cartella *app/migrations* non eseguiti in precedenza. In questo caso, il comando esegue lo script *0001_initial.py* in questa cartella per configurare lo schema necessario nel database.

Lo script di migrazione viene creato dal comando `manage.py makemigrations`, che analizza il file *models.py* dell'app, lo confronta con lo stato corrente del database e quindi genera gli script necessari per eseguire la migrazione dello schema del database in modo che corrisponda ai modelli correnti. Questa funzionalità di Django è estremamente utile quando si aggiornano e si modificano i modelli nel tempo. Generando ed eseguendo le migrazioni, si mantengono sincronizzati i modelli e il database con un lavoro minimo.

La migrazione verrà eseguita nel passaggio 6-3 più avanti in questo articolo.

## <a name="step-6-2-understand-data-models"></a>Passaggio 6-2: Comprendere i modelli di dati

I modelli per l'app, denominati Poll e Choice, sono definiti in *app/models.py*. Ognuno è una classe Python che deriva da `django.db.models.Model` e usa i metodi della classe `models`, ad esempio `CharField` e `IntegerField`, per definire i campi nel modello, mappati alle colonne del database.

```python
from django.db import models
from django.db.models import Sum

class Poll(models.Model):
    """A poll object for use in the application views and repository."""
    text = models.CharField(max_length=200)
    pub_date = models.DateTimeField('date published')

    def total_votes(self):
        """Calculates the total number of votes for this poll."""
        return self.choice_set.aggregate(Sum('votes'))['votes__sum']

    def __unicode__(self):
        """Returns a string representation of a poll."""
        return self.text

class Choice(models.Model):
    """A poll choice object for use in the application views and repository."""
    poll = models.ForeignKey(Poll)
    text = models.CharField(max_length=200)
    votes = models.IntegerField(default=0)

    def votes_percentage(self):
        """Calculates the percentage of votes for this choice."""
        total = self.poll.total_votes()
        return self.votes / float(total) * 100 if total > 0 else 0

    def __unicode__(self):
        """Returns a string representation of a choice."""
        return self.text
```

Come si può notare, un modello Poll include una descrizione nel campo `text` e una data di pubblicazione in `pub_date`. Questi campi sono gli unici disponibili per il polling nel database. Il `total_votes` campo viene calcolato in fase di esecuzione.

Un modello Choice è correlato a un modello Poll tramite il campo `poll`, contiene una descrizione in `text` e conserva un conteggio per l'opzione specifica in `votes`. Il `votes_percentage` campo viene calcolato in fase di esecuzione e non viene trovato nel database.

L'elenco completo di tipi di campo è `CharField` (testo limitato) `TextField` (testo illimitato), `EmailField`, `URLField`, `DateTimeField`, `IntegerField`, `DecimalField`, `BooleanField`, `ForeignKey` e `ManyToMany`. Ogni campo accetta alcuni attributi, ad esempio `max_length`. L'attributo `blank=True` indica che il campo è facoltativo. `null=true` indica che un valore è facoltativo. C'è anche un attributo `choices` che limita i valori a quelli inclusi in una matrice di tuple valore dati/valore visualizzato. Vedere [Model field reference](https://docs.djangoproject.com/en/2.0/ref/models/fields/) (Informazioni di riferimento sui campi dei modelli) nella documentazione di Django.

È possibile determinare esattamente ciò che viene archiviato nel database esaminando il file *db.sqlite3* nel progetto tramite uno strumento come il [browser SQLite](https://sqlitebrowser.org/). Nel database è possibile notare che un campo di chiave esterna come `poll` nel modello Choice è archiviato come `poll_id`. Django gestisce il mapping automaticamente.

In generale, usare il database in Django significa lavorare esclusivamente tramite i modelli, in modo che Django possa gestire il database sottostante per conto dell'utente.

### <a name="seed-the-database-from-samplesjson"></a>Assegnare valori di inizializzazione al database da samples.json

Inizialmente, il database non contiene sondaggi. È possibile usare l'interfaccia di amministrazione in corrispondenza dell'URL "/admin" per aggiungere sondaggi manualmente oppure visitare la pagina "/seed" nel sito in esecuzione per aggiungere valori di inizializzazione nel database con sondaggi definiti nel file *samples.json* dell'app.

Il file *urls.py* del progetto Django ha un modello di URL aggiunto, `url(r'^seed$', app.views.seed, name='seed'),`. La visualizzazione `seed` in *app/views.py* carica il file *samples.json* e crea gli oggetti modello necessari. Django crea quindi automaticamente i record corrispondenti nel database sottostante.

Si noti l'uso dell'elemento Decorator `@login_required` per indicare il livello di autorizzazione per la visualizzazione.

```python
@login_required
def seed(request):
    """Seeds the database with sample polls."""
    samples_path = path.join(path.dirname(__file__), 'samples.json')
    with open(samples_path, 'r') as samples_file:
        samples_polls = json.load(samples_file)

    for sample_poll in samples_polls:
        poll = Poll()
        poll.text = sample_poll['text']
        poll.pub_date = timezone.now()
        poll.save()

        for sample_choice in sample_poll['choices']:
            choice = Choice()
            choice.poll = poll
            choice.text = sample_choice
            choice.votes = 0
            choice.save()

    return HttpResponseRedirect(reverse('app:home'))
```

Per vedere l'effetto, eseguire prima di tutto l'app per vedere che non sono ancora presenti sondaggi. Visitare quindi l'URL "/seed" e, quando l'app torna alla home page, si dovrebbe notare che sono diventati disponibili alcuni sondaggi. Esaminare anche in questo caso il file *db.sqlite3* non elaborato con uno strumento come il [browser SQLite](https://sqlitebrowser.org/).

![App Progetto Web Django di sondaggi con database con valori di inizializzazione](media/django/step06-app-with-seeded-database.png)

### <a name="question-is-it-possible-to-initialize-the-database-using-the-django-administrative-utility"></a>Domanda: È possibile inizializzare il database usando l'utilità di amministrazione Django?

Risposta: Sì, è possibile usare il [comando loaddata di django-admin](https://docs.djangoproject.com/en/2.0/ref/django-admin/#loaddata) per eseguire la stessa attività della pagina di seeding nell'app. Quando si usa un'app Web completa, è possibile usare una combinazione dei due metodi: inizializzare un database dalla riga di comando, quindi convertire la pagina con i valori di inizializzazione in un'API a cui è possibile inviare qualsiasi altro file JSON arbitrario, invece di ricorrere a un file hardcoded.

## <a name="step-6-3-use-migrations"></a>Passaggio 6-3: Usare le migrazioni

Quando è stato eseguito il comando `manage.py makemigrations` (usando il menu di scelta rapida in Visual Studio) dopo la creazione del progetto, Django ha creato il file *app/migrations/0001_initial.py*. Questo file contiene uno script che crea le tabelle di database iniziali.

Poiché inevitabilmente si apporteranno modifiche ai modelli nel tempo, Django consente di mantenere aggiornato lo schema del database sottostante con tali modelli in modo semplice. Il flusso di lavoro generale è il seguente:

1. Apportare modifiche ai modelli nel file *models.py*.
1. In Visual Studio fare clic con il pulsante destro del mouse sul progetto in **Esplora soluzioni** e quindi scegliere **Python** > **Creazione migrazioni Django**. Come descritto in precedenza, questo comando genera script in *app/migrations* per eseguire la migrazione del database dallo stato corrente al nuovo stato.
1. Per applicare gli script al database effettivo, fare di nuovo clic con il pulsante destro del mouse sul progetto e scegliere **Python**  >  **Django Migrate**.

Django tiene traccia delle migrazioni applicate a uno specifico database, in modo che quando si esegue il comando di migrazione, Django applica le migrazioni necessarie. Se si crea un nuovo database vuoto, ad esempio, eseguendo il comando di migrazione il database viene aggiornato con i modelli correnti applicando ogni script di migrazione. Analogamente, se si apportano più modifiche ai modelli e si generano le migrazioni in un computer di sviluppo, è quindi possibile applicare le migrazioni cumulative al database di produzione eseguendo il comando di migrazione nel server di produzione. Anche in questo caso, Django applica solo gli script di migrazione che sono stati generati dall'ultima migrazione del database di produzione.

Per vedere l'effetto della modifica di un modello, seguire questa procedura:

1. In *app/models.py* aggiungere la riga seguente dopo il campo `pub_date` per aggiungere un campo `author` facoltativo al modello Poll:

    ```python
    author = models.CharField(max_length=100, blank=True)
    ```

1. Salvare il file, fare clic con il pulsante destro del mouse sul progetto **DjangoPolls** in **Esplora soluzioni** e quindi selezionare **Python** > **Creazione migrazioni Django**.
1. Selezionare il **Project** comando Mostra tutti i file per visualizzare lo script appena generato nella cartella  >   **migrations** il cui nome inizia **con 002_auto_**. Fare clic con il pulsante destro del mouse sul file e scegliere **Includi nel progetto**. È quindi possibile **selezionare** Project mostra tutti i  >  **file** per ripristinare la visualizzazione originale. Per informazioni dettagliate su questo passaggio, vedere la seconda domanda di seguito.
1. Se lo si desidera, aprire il file per esaminare come sono cambiati gli script Django dallo stato del modello precedente al nuovo stato.
1. Fare di nuovo clic con il Visual Studio progetto e selezionare **Python**  >  **Django Migrate** per applicare le modifiche al database.
1. Se si desidera, aprire il database in un visualizzatore appropriato per verificare la modifica.

In generale, grazie alla funzionalità di migrazione di Django non è mai necessario gestire manualmente lo schema del database. È sufficiente apportare le modifiche ai modelli, generare gli script di migrazione e applicarli con il comando di migrazione.

### <a name="question-what-happens-if-i-forget-to-run-the-migrate-command-after-making-changes-to-models"></a>Domanda: Cosa accade se si dimentica di eseguire il comando di migrazione dopo aver apportato modifiche ai modelli?

Risposta: Se i modelli non corrispondono a quanto contenuto nel database, Django ha esito negativo in fase di esecuzione con le eccezioni appropriate. Ad esempio, se si dimentica di eseguire la migrazione della modifica del modello illustrata nella sezione precedente, viene visualizzato un errore che non contiene tale **colonna: app_poll.author**:

![Errore visualizzato quando non è stata eseguita la migrazione di una modifica del modello](media/django/step06-exception-when-forgetting-to-migrate.png).

### <a name="question-why-doesnt-solution-explorer-show-newly-generated-scripts-after-running-django-make-migrations"></a>Domanda: Perché Esplora soluzioni non mostra gli script appena generati dopo l'esecuzione del comando Creazione migrazioni Django?

Risposta: Anche se gli script appena generati sono presenti nella cartella *app/migrations* e vengono applicati quando si esegue il comando **Migrazione Django**, non vengono visualizzati automaticamente in **Esplora soluzioni** perché non sono stati aggiunti al progetto di Visual Studio. Per renderli visibili, selezionare prima il Project di menu Mostra tutti i file o il pulsante della barra degli strumenti illustrato  >   nell'immagine seguente. Questo comando determina la visualizzazione in **Esplora soluzioni** di tutti i file nella cartella di progetto, con un'icona con contorno punteggiato per gli elementi che non sono stati aggiunti al progetto. Fare clic con il pulsante destro del mouse sui file da aggiungere e scegliere **Includi nel progetto** per includerli anche nel controllo del codice sorgente al successivo commit.

![Comando Includi nel progetto in Esplora soluzioni](media/django/step06-include-migrations-script-in-project.png)

### <a name="question-can-i-see-what-migrations-would-be-applied-before-running-the-migrate-command"></a>Domanda: È possibile vedere quali migrazioni verranno applicate prima di eseguire il comando di migrazione?

Risposta: Sì, usando il [comando showmigrations di django-admin](https://docs.djangoproject.com/en/2.0/ref/django-admin/#showmigrations).

## <a name="step-6-4-understand-the-views-and-page-templates-created-by-the-project-template"></a>Passaggio 6-4: Comprendere le visualizzazioni e i modelli di pagina creati dal modello di progetto

La maggior parte delle visualizzazioni generate dal modello "Progetto Web Django di sondaggi", ad esempio quelle delle pagine About e Contact, sono piuttosto simili alle visualizzazioni create dal modello "Progetto Web Django" usato in precedenza in questa esercitazione. La differenza, nell'app dei sondaggi, è legata al fatto che la home page usa i modelli, come pure diverse pagine aggiunte per votare e per visualizzare i risultati dei sondaggi.

Prima di tutto, la prima riga della matrice `urlpatterns` nel file *urls.py* del progetto Django è molto più di un semplice routing a una visualizzazione dell'app. La riga esegue infatti il pull del file *urls.py* dell'app:

```python
from django.conf.urls import url, include
import app.views

urlpatterns = [
    url(r'^', include('app.urls', namespace="app")),
    # ..
]
```

Il file *app/urls.py* contiene quindi codice di routing più interessante (sono stati aggiunti commenti esplicativi):

```python
urlpatterns = [
    # Home page routing
    url(r'^$',
        app.views.PollListView.as_view(
            queryset=Poll.objects.order_by('-pub_date')[:5],
            context_object_name='latest_poll_list',
            template_name='app/index.html',),
        name='home'),

    # Routing for a poll page, which use URLs in the form <poll_id>/,
    # where the id number is captured as a group named "pk".
    url(r'^(?P<pk>\d+)/$',
        app.views.PollDetailView.as_view(
            template_name='app/details.html'),
        name='detail'),

    # Routing for <poll_id>/results pages, again using a capture group
    # named pk.
    url(r'^(?P<pk>\d+)/results/$',
        app.views.PollResultsView.as_view(
            template_name='app/results.html'),
        name='results'),

    # Routing for <poll_id>/vote pages, with the capture group named
    # poll_id this time, which becomes an argument passed to the view.
    url(r'^(?P<poll_id>\d+)/vote/$', app.views.vote, name='vote'),
]
```

Se non si ha familiarità con le espressioni regolari più complesse usate in questo argomento, è possibile incollare l'espressione in [regex101.com](https://regex101.com/) per una spiegazione in un linguaggio semplice. È necessario aggiungere un carattere di escape per la barra `/` facendola precedere da una barra rovesciata, `\`. L'uso di caratteri di escape non è necessario in Python perché è presente il prefisso `r` nella stringa, che indica "raw" (non elaborato).

In Django la sintassi `?P<name>pattern` crea un gruppo denominato `name`, che viene passato come argomento nelle visualizzazioni, nell'ordine in cui appaiono. Nel codice riportato in precedenza, `PollsDetailView` e `PollsResultsView` ricevono un argomento denominato `pk` e `app.views.vote` riceve un argomento denominato `poll_id`.

È anche possibile vedere che la maggior parte delle visualizzazioni non è un semplice riferimento diretto a una funzione di visualizzazione in *app/views.py*. La maggior parte fa invece riferimento a una classe nello stesso file che deriva da `django.views.generic.ListView` o `django.views.generic.DetailView`. Le classi di base forniscono i metodi `as_view`, che accettano un argomento `template_name` per identificare il modello. La classe di base `ListView`, usata per la home page, richiede anche una proprietà `queryset` che contiene i dati e una proprietà `context_object_name` con il nome della variabile tramite cui si vuole fare riferimento ai dati nel modello, in questo caso `latest_poll_list`.

È ora possibile esaminare l'elemento `PollListView` per la home page, definito come segue in *app/views.py*:

```python
class PollListView(ListView):
    """Renders the home page, with a list of all polls."""
    model = Poll

    def get_context_data(self, **kwargs):
        context = super(PollListView, self).get_context_data(**kwargs)
        context['title'] = 'Polls'
        context['year'] = datetime.now().year
        return context
```

Ciò che viene fatto in questo caso è identificare il modello usato dalla visualizzazione (Poll) ed eseguire l'override del metodo `get_context_data` per aggiungere i valori `title` e `year` nel contesto.

La parte principale del modello (*templates/app/index.html*) è illustrata di seguito:

```html
{% if latest_poll_list %}
<table class="table table-hover">
    <tbody>
        {% for poll in latest_poll_list %}
        <tr>
            <td>
                <a href="{% url 'app:detail' poll.id %}">{{poll.text}}</a>
            </td>
        </tr>
        {% endfor %}
    </tbody>
</table>
{% else %}
<!-- ... other content omitted ... -->
{% endif %}
```

In breve, il modello riceve l'elenco di oggetti Poll in `latest_poll_list` e quindi scorre tale elenco per creare una riga di tabella contenente un collegamento a ogni sondaggio usando il valore `text` del sondaggio. Nel tag `{% url %}`, "app:detail" fa riferimento al modello di URL in *app/urls.py* denominato "detail", usando `poll.id` come argomento. Di conseguenza, Django crea un URL usando il modello appropriato e lo usa per tale collegamento. Grazie a questo codice, è possibile modificare il modello di URL in qualsiasi momento e i collegamenti generati verranno aggiornati automaticamente di conseguenza.

Le classi `PollDetailView` e `PollResultsView` in *app/views.py* (non illustrate qui) sono quasi identiche a `PollListView`, ad eccezione del fatto che derivano da `DetailView`. I rispettivi modelli, *app/templates/details.html* e *app/templates/results.html*, posizionano quindi i campi appropriati dai modelli in diversi controlli HTML. Una caratteristica unica di *details.html* è il fatto che le opzioni disponibili per un sondaggio sono incluse in un modulo HTML che, quando inviato, esegue un comando POST nell'URL /vote. Come visto in precedenza, il modello di URL viene indirizzato a `app.views.vote`, implementato come indicato di seguito (si noti l'argomento `poll_id`, che rappresenta un gruppo denominato nell'espressione regolare usato nel routing per questa visualizzazione):

```python
def vote(request, poll_id):
    """Handles voting. Validates input and updates the repository."""
    poll = get_object_or_404(Poll, pk=poll_id)
    try:
        selected_choice = poll.choice_set.get(pk=request.POST['choice'])
    except (KeyError, Choice.DoesNotExist):
        return render(request, 'app/details.html', {
            'title': 'Poll',
            'year': datetime.now().year,
            'poll': poll,
            'error_message': "Please make a selection.",
    })
    else:
        selected_choice.votes += 1
        selected_choice.save()
        return HttpResponseRedirect(reverse('app:results', args=(poll.id,)))
```

In questo caso, la visualizzazione non ha un modello corrispondente come le altre pagine. Convalida invece il sondaggio selezionato, mostrando un errore 404 se il sondaggio non esiste (solo nel caso in cui un utente immette un URL, ad esempio "vote/1a2b3c"). Verifica quindi che l'opzione votata sia valida per il sondaggio. In caso contrario, il blocco `except` esegue semplicemente di nuovo il rendering della pagina dei dettagli con un messaggio di errore. Se l'opzione è valida, la visualizzazione registra il voto ed esegue il reindirizzamento alla pagina dei risultati.

## <a name="step-6-5-create-a-custom-administration-interface"></a>Passaggio 6-5: Creare un'interfaccia di amministrazione personalizzata

Le ultime parti del modello "Progetto Web Django di sondaggi" sono estensioni personalizzate dell'interfaccia di amministrazione Django predefinita, come illustrato in precedenza in questo articolo nel passaggio 6-1. L'interfaccia predefinita consente la gestione di utenti e gruppi, ma non molto altro. Il modello di progetto di sondaggi aggiunge funzionalità che consentono di gestire anche i sondaggi.

Prima di tutto, i modelli di URL nel file *urls.py* del progetto Django includono `url(r'^admin/', include(admin.site.urls)),` per impostazione predefinita. È incluso anche il modello "admin/doc", impostato come commento.

L'app contiene quindi il file *admin.py*, che Django esegue automaticamente quando l'utente visita l'interfaccia di amministrazione grazie all'inclusione di `django.contrib.admin` nella matrice `INSTALLED_APPS` di *settings.py*. Il codice in tale file, come specificato dal modello di progetto, è il seguente:

```python
from django.contrib import admin
from app.models import Choice, Poll

class ChoiceInline(admin.TabularInline):
    """Choice objects can be edited inline in the Poll editor."""
    model = Choice
    extra = 3

class PollAdmin(admin.ModelAdmin):
    """Definition of the Poll editor."""
    fieldsets = [
        (None, {'fields': ['text']}),
        ('Date information', {'fields': ['pub_date']}),
    ]
    inlines = [ChoiceInline]
    list_display = ('text', 'pub_date')
    list_filter = ['pub_date']
    search_fields = ['text']
    date_hierarchy = 'pub_date'

admin.site.register(Poll, PollAdmin)
```

Come si può notare, la classe `PollAdmin` deriva da `django.contrib.admin.ModelAdmin` e personalizza numerosi dei relativi campi usando i nomi del modello `Poll`, gestito dalla classe stessa. Questi campi sono descritti in [ModelAdmin options](https://docs.djangoproject.com/en/2.0/ref/contrib/admin/#modeladmin-options) (Opzioni di ModelAdmin) nella documentazione di Django.

La chiamata a `admin.site.register` connette quindi la classe al modello (`Poll`) e la include nell'interfaccia di amministrazione. Il risultato complessivo è illustrato di seguito:

![Visualizzazione dell'area di amministrazione dell'app Progetto Web Django di sondaggi](media/django/step06-polls-administrative-interface.png)

## <a name="next-steps"></a>Passaggi successivi

> [!Note]
> Durante l'esercitazione è stato eseguito il commit della soluzione di Visual Studio nel controllo del codice sorgente. A questo punto è utile eseguire un altro commit. La soluzione dovrebbe corrispondere al codice sorgente per l'esercitazione su GitHub: [Microsoft/python-sample-vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django).

A questo punto, sono stati esaminati i modelli "Progetto Web Django vuoto", "Progetto Web Django" e "Progetto Web Django di sondaggi". Sono state apprese le nozioni di base di Django, ad esempio l'uso di visualizzazioni e modelli, e sono stati analizzati il routing, l'autenticazione e l'uso di modelli di database. A questo punto, si dovrebbe essere in grado di creare un'app Web con tutti i modelli e le visualizzazioni necessari.

L'esecuzione di un'app Web nel computer di sviluppo è solo un passaggio per rendere disponibile l'app ai clienti. I passaggi successivi possono includere le attività seguenti:

- Distribuire l'app Web in un server di produzione, ad esempio Servizio app di Azure. Vedere [Eseguire la pubblicazione in Servizio app di Azure](publishing-python-web-applications-to-azure-from-visual-studio.md).

- Personalizzare la pagina 404 creando un modello denominato *templates/404.html*. Quando questo modello è presente, Django lo usa al posto di quello predefinito. Per altre informazioni, vedere [Error views](https://docs.djangoproject.com/en/2.0/ref/views/#error-views) (Visualizzazioni di errore) nella documentazione di Django.

- Scrivere unit test in *tests.py*. I modelli di progetto di Visual Studio costituiscono il punto di partenza per questa attività. Per altre informazioni, vedere [Writing your first Django app, part 5 - testing](https://docs.djangoproject.com/en/2.0/intro/tutorial05/) (Scrittura della prima app Django, parte 5 - test) e [Testing in Django](https://docs.djangoproject.com/en/2.0/topics/testing/) (Test in Django) nella documentazione di Django.

- Modificare l'app da SQLite a un archivio dati a livello di produzione, ad esempio PostgreSQL, MySQL e SQL Server (che possono tutti essere ospitati in Azure). Come descritto in [When to use SQLite](https://www.sqlite.org/whentouse.html) (Quando usare SQLite) (sqlite.org), SQLite è appropriato per i siti con traffico medio o basso, con meno di 100.000 accessi al giorno, ma non è consigliato per volumi più elevati. È anche limitato a un unico computer, quindi non può essere usato in scenari con più server, ad esempio con il bilanciamento del carico e la replica geografica. Per informazioni sul supporto di Django per altri database, vedere [Database setup](https://docs.djangoproject.com/en/2.0/intro/tutorial02/#database-setup) (Configurazione del database). È anche possibile usare [Azure SDK per Python](/azure/python/) per usare servizi di archiviazione di Azure, ad esempio tabelle e BLOB.

- Configurare una pipeline di integrazione continua/distribuzione continua in un servizio come Azure DevOps. Oltre a usare il controllo del codice sorgente (in Azure Repos, GitHub o altrove), è possibile configurare un progetto di Azure DevOps in modo che esegua automaticamente gli unit test come prerequisito per il rilascio, oltre che configurare la pipeline per la distribuzione in un server di gestione temporanea per eseguire test aggiuntivi prima della distribuzione in produzione. Azure DevOps inoltre si integra con soluzioni di monitoraggio, ad esempio App Insights, chiudendo così l'intero ciclo con strumenti di pianificazione Agile. Per altre informazioni, vedere [Creare una pipeline di CI/CD per Python con il progetto Azure DevOps](/azure/devops-project/azure-devops-project-python?view=vsts&preserve-view=true) e la [documentazione generale di Azure DevOps](/azure/devops/?view=vsts&preserve-view=true).
