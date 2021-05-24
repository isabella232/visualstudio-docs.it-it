---
title: Esercitazione su Django nel Visual Studio passaggio 2, visualizzazioni e modello di pagina
titleSuffix: ''
description: Procedura dettagliata dei concetti di base relativi a Django nel contesto dei progetti di Visual Studio, che illustra in particolare i passaggi della creazione di un'app e dell'uso di visualizzazioni e modelli.
ms.date: 11/19/2018
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18, SEO-VS-2020
ms.workload:
- python
- data-science
ms.openlocfilehash: 196b15dff25681a23c05118a02f19109e09e3959
ms.sourcegitcommit: 5fe2462ffc33c7ece9cf3a179fb598354c916e1f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/21/2021
ms.locfileid: "110320472"
---
# <a name="step-2-create-a-django-app-with-views-and-page-templates"></a>Passaggio 2: Creare un'app Django con visualizzazioni e modelli di pagina

**Passaggio precedente: [Creare un progetto e una soluzione di Visual Studio](learn-django-in-visual-studio-step-01-project-and-solution.md)**

Fino a questo punto, il progetto di Visual Studio include solo i componenti a livello di sito di un *progetto* Django, che può eseguire una o più *app* Django. Il passaggio successivo consiste nella creazione della prima app con un'unica pagina.

In questo passaggio viene descritto come:

> [!div class="checklist"]
> - Creare un'app Django con un'unica pagina (passaggio 2-1)
> - Eseguire l'app dal progetto Django (passaggio 2-2)
> - Eseguire il rendering di una visualizzazione tramite HTML (passaggio 2-3)
> - Eseguire il rendering di una visualizzazione usando un modello di pagina Django (passaggio 2-4)

## <a name="step-2-1-create-an-app-with-a-default-structure"></a>Passaggio 2-1: Creare un'app con una struttura predefinita

Un'app Django è un pacchetto Python separato che contiene un set di file correlati per uno scopo specifico. Un progetto Django può contenere un numero qualsiasi di app e questa caratteristica corrisponde al fatto che un host Web può gestire un numero qualsiasi di punti di ingresso da un unico nome di dominio. Ad esempio, un progetto Django per un dominio come contoso.com può contenere un'app per `www.contoso.com`, una seconda app per support.contoso.com e una terza per docs.contoso.com. In questo caso, il progetto Django gestisce le impostazioni e il routing degli URL a livello di sito (nei rispettivi file *urls.py* e *settings.py*), mentre ogni app ha stile e comportamento distinti tramite il routing interno, i modelli, le visualizzazioni, i file statici e l'interfaccia amministrativa corrispondenti.

Un'app Django inizia in genere con un set standard di file. Visual Studio fornisce modelli di elemento per inizializzare un'app Django all'interno di un progetto Django, insieme a un comando di menu integrato che ha lo stesso scopo:

- Modelli: in **Esplora soluzioni** fare clic con il pulsante destro del mouse sul progetto e scegliere **Aggiungi** > **Nuovo elemento**. Nella finestra di dialogo **Aggiungi nuovo elemento** selezionare il modello **App Django 1.9**, specificare il nome dell'applicazione nel campo **Nome** e selezionare **OK**.

- Comando integrato: in **Esplora soluzioni** fare clic sul progetto e selezionare **Aggiungi** > **App Django**. Questo comando chiede di immettere il nome e crea un'app Django 1.9.

    ![Comando di menu per l'aggiunta di un'app Django](media/django/step02-add-django-app-command.png)

Usando uno dei due metodi, creare un'app denominata "HelloDjangoApp". Il risultato è una cartella nel progetto con questo nome che contiene gli elementi descritti nella tabella seguente.

![File dell'app Django in Esplora soluzioni](media/django/step02-django-app-in-solution-explorer.png)

::: moniker range="vs-2017"
| Elemento | Descrizione |
| --- | --- |
| **\_\_init \_ \_ .py** | File che identifica l'app come pacchetto. |
| **Migrazioni** | Cartella in cui Django archivia gli script che aggiornano il database per l'allineamento alle modifiche apportate ai modelli. Gli strumenti di migrazione di Django applicano quindi le modifiche necessarie a qualsiasi versione precedente del database in modo che corrisponda ai modelli correnti. Usando le migrazioni, è possibile concentrarsi sui modelli e lasciare a Django la gestione dello schema di database sottostante. Le migrazioni sono descritte nel passaggio 6. per il momento, la cartella contiene semplicemente un file con estensione *\_ \_ \_ \_ py init* (che indica che la cartella definisce il proprio pacchetto Python). |
| **templates** | Cartella per i modelli di pagina Django contenente un unico file, *index.html* all'interno di una cartella che corrisponde al nome dell'app. In Visual Studio 2017 15.7 e versioni precedenti, il  file è contenuto direttamente nei modelli e il passaggio 2-4 indica di creare la sottocartella. I modelli sono blocchi di codice HTML in cui le visualizzazioni possono aggiungere informazioni per il rendering dinamico di una pagina. Le "variabili" del modello di pagina, ad esempio `{{ content }}` in *index.html*, sono segnaposto per i valori dinamici, come descritto più avanti in questo articolo (passaggio 2). In genere le app Django creano uno spazio dei nomi per i rispettivi modelli inserendoli in una sottocartella corrispondente al nome dell'app. |
| **admin.py** | File Python in cui viene estesa l'interfaccia amministrativa dell'app (vedere il passaggio 6) usato per distribuire e modificare i dati in un database. Inizialmente, questo file contiene solo l'istruzione `from django.contrib import admin`. Per impostazione predefinita, Django include un'interfaccia amministrativa standard tramite le voci presenti nel file *settings.py* del progetto Django, che è possibile attivare rimuovendo i commenti dalle voci esistenti in *urls.py*. |
| **apps.py** | File Python che definisce una classe di configurazione per l'app. Vedere di seguito, dopo questa tabella. |
| **models.py** | I modelli sono oggetti dati, identificati da funzioni, attraverso i quali le visualizzazioni interagiscono con il database sottostante dell'app (vedere il passaggio 6). Django fornisce il livello di connessione di database in modo che le app non debbano gestire questi dettagli. Il file *models.py* è una posizione predefinita in cui creare i modelli e contiene inizialmente solo l'istruzione `from django.db import models`. |
| **tests.py** | File Python che contiene la struttura di base degli unit test. |
| **views.py** | In genere le visualizzazioni vengono considerate pagine Web, che accettano una richiesta HTTP e restituiscono una risposta HTTP. Il rendering delle visualizzazioni viene eseguito in genere come HTML, che i Web browser sanno come visualizzare, ma una visualizzazione non deve necessariamente essere visibile, ad esempio se si tratta di un modulo intermedio. Una visualizzazione viene definita da una funzione Python, il cui compito consiste nell'eseguire il rendering del codice HTML da inviare al browser. Il file *views.py* è una posizione predefinita in cui creare le visualizzazioni e contiene inizialmente solo l'istruzione `from django.shortcuts import render`. |
::: moniker-end

::: moniker range=">=vs-2019"
| Elemento | Descrizione |
| --- | --- |
| **\_\_init \_ \_ .py** | File che identifica l'app come pacchetto. |
| **Migrazioni** | Cartella in cui Django archivia gli script che aggiornano il database per l'allineamento alle modifiche apportate ai modelli. Gli strumenti di migrazione di Django applicano quindi le modifiche necessarie a qualsiasi versione precedente del database in modo che corrisponda ai modelli correnti. Usando le migrazioni, è possibile concentrarsi sui modelli e lasciare a Django la gestione dello schema di database sottostante. Le migrazioni sono descritte nella documentazione [di Django.](https://docs.djangoproject.com/en/3.2/topics/migrations/) per il momento, la cartella contiene semplicemente un file con estensione *\_ \_ \_ \_ py init* (che indica che la cartella definisce il proprio pacchetto Python). |
| **templates** | Cartella per i modelli di pagina Django contenente un unico file, *index.html* all'interno di una cartella che corrisponde al nome dell'app. In Visual Studio 2017 15.7 e versioni precedenti, il  file è contenuto direttamente nei modelli e il passaggio 2-4 indica di creare la sottocartella. I modelli sono blocchi di codice HTML in cui le visualizzazioni possono aggiungere informazioni per il rendering dinamico di una pagina. Le "variabili" del modello di pagina, ad esempio `{{ content }}` in *index.html*, sono segnaposto per i valori dinamici, come descritto più avanti in questo articolo (passaggio 2). In genere le app Django creano uno spazio dei nomi per i rispettivi modelli inserendoli in una sottocartella corrispondente al nome dell'app. |
| **admin.py** | File Python in cui si estende l'interfaccia amministrativa dell'app, usata per eseguire il seed e modificare i dati in un database. Inizialmente, questo file contiene solo l'istruzione `from django.contrib import admin`. Per impostazione predefinita, Django include un'interfaccia amministrativa standard tramite le voci presenti nel file *settings.py* del progetto Django, che è possibile attivare rimuovendo i commenti dalle voci esistenti in *urls.py*. |
| **apps.py** | File Python che definisce una classe di configurazione per l'app. Vedere di seguito, dopo questa tabella. |
| **models.py** | I modelli sono oggetti dati, identificati dalle funzioni, tramite cui le viste interagiscono con il database sottostante dell'app. Django fornisce il livello di connessione di database in modo che le app non debbano gestire questi dettagli. Il file *models.py* è una posizione predefinita in cui creare i modelli e contiene inizialmente solo l'istruzione `from django.db import models`. |
| **tests.py** | File Python che contiene la struttura di base degli unit test. |
| **views.py** | In genere le visualizzazioni vengono considerate pagine Web, che accettano una richiesta HTTP e restituiscono una risposta HTTP. Il rendering delle visualizzazioni viene eseguito in genere come HTML, che i Web browser sanno come visualizzare, ma una visualizzazione non deve necessariamente essere visibile, ad esempio se si tratta di un modulo intermedio. Una visualizzazione viene definita da una funzione Python, il cui compito consiste nell'eseguire il rendering del codice HTML da inviare al browser. Il file *views.py* è una posizione predefinita in cui creare le visualizzazioni e contiene inizialmente solo l'istruzione `from django.shortcuts import render`. |
::: moniker-end

Il contenuto di *apps.py* viene visualizzato come segue quando si usa il nome "HelloDjangoApp":

```python
from django.apps import AppConfig

class HelloDjangoAppConfig(AppConfig):
    name = 'HelloDjango'
```

### <a name="question-is-creating-a-django-app-in-visual-studio-any-different-from-creating-an-app-on-the-command-line"></a>Domanda: La creazione di un'app Django in Visual Studio è diversa dalla creazione di un'app nella riga di comando?

Risposta: l'esecuzione **del** comando  >  **Aggiungi app Django** o l'uso di Aggiungi nuovo elemento con un modello di app Django genera gli stessi file   >   del comando Django `manage.py startapp <app_name>` . Il vantaggio della creazione dell'app in Visual Studio è che la cartella dell'app e tutti i file vengono integrati automaticamente nel progetto. È possibile usare lo stesso comando di Visual Studio per creare un numero qualsiasi di app nel progetto.

## <a name="step-2-2-run-the-app-from-the-django-project"></a>Passaggio 2-2: Eseguire l'app dal progetto Django

A questo punto, se si esegue di nuovo il progetto in Visual Studio (usando il pulsante della barra degli strumenti o Debug Avvia debug ), viene comunque visualizzata  >  la pagina predefinita. Non viene visualizzato alcun contenuto dell'app perché è necessario definire una pagina specifica dell'app e aggiungere l'app al progetto Django:

1. Nella cartella *HelloDjangoApp* modificare *views.py* in modo che corrisponda al codice riportato di seguito, che definisce una visualizzazione denominata "index":

    ```python
    from django.shortcuts import render
    from django.http import HttpResponse

    def index(request):
        return HttpResponse("Hello, Django!")
    ```

1. Nella cartella *BasicProject* (creata nel passaggio 1) modificare *urls.py* in modo che corrisponda almeno al codice seguente (è possibile mantenere i commenti esplicativi, se lo si desidera):

    ```python
    from django.conf.urls import include, url
    import HelloDjangoApp.views

    # Django processes URL patterns in the order they appear in the array
    urlpatterns = [
        url(r'^$', HelloDjangoApp.views.index, name='index'),
        url(r'^home$', HelloDjangoApp.views.index, name='home'),
    ]
    ```

    Ogni modello di URL descrive le visualizzazioni a cui Django instrada URL relativi al sito specifici, ovvero la parte che segue `https://www.domain.com/`. La prima voce in `urlPatterns` che inizia con l'espressione regolare `^$` è il routing per la radice del sito, "/". La seconda voce, `^home$`, instrada espressamente a "/home". La stessa visualizzazione può contenere un numero qualsiasi di routing.

1. Eseguire di nuovo il progetto per visualizzare il messaggio **Hello, Django!** come definito dalla visualizzazione. Al termine, arrestare il server.

### <a name="commit-to-source-control"></a>Eseguire il commit nel controllo del codice sorgente

Poiché sono state apportate modifiche al codice e il test delle modifiche è riuscito, questo è il momento più appropriato per esaminare le modifiche ed eseguirne il commit nel controllo del codice sorgente. I passaggi successivi di questa esercitazione indicano i momenti appropriati in cui eseguire un nuovo commit nel controllo del codice sorgente e rimandano a questa sezione.

1. Selezionare il pulsante Modifiche nella parte inferiore di Visual Studio (opzione cerchiata di seguito), che consente di passare a **Team Explorer**.

    ![Pulsante Modifiche per il controllo del codice sorgente sulla barra di stato di Visual Studio](media/django/step02-source-control-changes-button.png)

1. In **Team Explorer** immettere un messaggio per il commit, come "Creazione dell'app Django iniziale" e selezionare **Esegui commit di tutto**. Al termine del commit, viene visualizzato un messaggio **Commit \<hash> creato in locale. Eseguire la sincronizzazione per condividere le modifiche con il server.** Se si vuole eseguire il push delle modifiche nel repository remoto, selezionare **Sync** e quindi **Push** in **Commit in uscita**. È anche possibile accumulare più commit locali prima di eseguire il push in remoto.

    ![Eseguire il push dei commit in remoto in Team Explorer](media/django/step02-source-control-push-to-remote.png)

### <a name="question-what-is-the-r-prefix-before-the-routing-strings-for"></a>Domanda: Che cosa significa il prefisso "r" prima delle stringhe di routing?

Risposta: Il prefisso "r" in una stringa in Python significa "raw", ovvero "non elaborato", per indicare a Python di non aggiungere escape ad alcun carattere nella stringa. Poiché le espressioni regolari usano molti caratteri speciali, l'uso del prefisso "r" semplifica notevolmente la lettura delle stringhe rispetto a quando contengono diversi caratteri di escape '\\'.

### <a name="question-what-do-the--and--characters-mean-in-the-url-routing-entries"></a>Domanda: che cosa significano i caratteri ^ e $ nelle voci di routing degli URL?

Risposta: Nelle espressioni regolari che definiscono modelli di URL, ^ significa "inizio della riga" e $ significa "fine della riga" e gli URL, come già detto, sono relativi alla radice del sito, ovvero la parte che segue `https://www.domain.com/`. L'espressione regolare `^$` significa "vuoto" e di conseguenza corrisponde all'URL completo `https://www.domain.com/` (senza aggiunte alla radice del sito). Il modello `^home$` corrisponde esattamente a `https://www.domain.com/home/`. Django non usa il carattere / finale nella corrispondenza dei modelli.

Se non si usa un carattere $ finale in un'espressione regolare, come in `^home`, il modello di URL corrisponde a *qualsiasi* URL che inizia con "home", ad esempio "home", "homework", "homestead" e "home192837".

Per sperimentare diverse espressioni regolari, provare gli strumenti online, ad esempio [regex101.com](https://regex101.com) all'indirizzo [pythex.org](https://www.pythex.org).

## <a name="step-2-3-render-a-view-using-html"></a>Passaggio 2-3: Eseguire il rendering di una visualizzazione tramite HTML

La funzione `index` presente finora in *views.py* genera solo una risposta HTTP in testo normale per la pagina. La maggior parte delle pagine Web di scenari reali, naturalmente, risponde con pagine HTML formattate che spesso includono dati in tempo reale. In effetti, il motivo principale per definire una visualizzazione tramite una funzione è il fatto di poter generare il contenuto in modo dinamico.

Poiché l'argomento per `HttpResponse` è semplicemente una stringa, è possibile creare tutto il codice HTML desiderato all'interno di una stringa. Come semplice esempio, sostituire la funzione `index` con il codice seguente (mantenendo le istruzioni `from` esistenti), che genera una risposta HTML usando contenuto dinamico aggiornato ogni volta che si aggiorna la pagina:

```python
from datetime import datetime

def index(request):
    now = datetime.now()

    html_content = "<html><head><title>Hello, Django</title></head><body>"
    html_content += "<strong>Hello Django!</strong> on " + now.strftime("%A, %d %B, %Y at %X")
    html_content += "</body></html>"

    return HttpResponse(html_content)
```

Eseguire di nuovo il progetto per visualizzare un messaggio simile a "**Hello, Django!** lunedì 16 aprile 2018 alle 16:28:10". Aggiornare la pagina per aggiornare l'ora e verificare che il contenuto venga generato con ogni richiesta. Al termine, arrestare il server.

> [!Tip]
> Un collegamento per arrestare e riavviare il progetto è usare il comando di menu Riavvia debug  >   (**CTRL** + **MAIUSC** + **F5**)  o il pulsante Riavvia sulla barra degli strumenti di debug:
>
> ![Pulsante di riavvio sulla barra degli strumenti per il debug in Visual Studio](media/debugging-restart-toolbar-button.png)

## <a name="step-2-4-render-a-view-using-a-page-template"></a>Passaggio 2-4: Eseguire il rendering di una visualizzazione usando un modello di pagina

La generazione di parti HTML nel codice funziona correttamente per pagine molto piccole, ma se le pagine diventano più complesse è in genere preferibile mantenere le parti HTML statiche della pagina (insieme ai riferimenti ai file CSS e JavaScript) come "modelli di pagina", in cui inserire quindi contenuto dinamico generato dal codice. Nella sezione precedente solo la data e l'ora della chiamata `now.strftime` sono dinamiche, ovvero il resto del contenuto può essere inserito in un modello di pagina.

Un modello di pagina Django è un blocco di codice HTML che può contenere un numero qualsiasi di token di sostituzione denominati "variabili", indicati da `{{` e `}}`, come in `{{ content }}`. Il modulo di creazione di modelli di Django sostituisce quindi le variabili con il contenuto dinamico fornito nel codice.

I passaggi seguenti descrivono l'uso dei modelli di pagina:

1. Nella cartella *BasicProject*, che contiene il progetto Django, aprire il file *settings.py* e aggiungere il nome dell'app "HelloDjangoApp" all'elenco `INSTALLED_APPS`. L'aggiunta dell'app all'elenco indica al progetto Django che è presente una cartella con questo nome che contiene un'app:

    ```python
    INSTALLED_APPS = [
        'HelloDjangoApp',
        # Other entries...
    ]
    ```

1. In *settings.py* assicurarsi anche che l'oggetto `TEMPLATES` contenga la riga seguente (inclusa per impostazione predefinita), che indica a Django di cercare i modelli nella cartella *templates* dell'app installata:

    ```json
    'APP_DIRS': True,
    ```

1. Nella cartella *HelloDjangoApp* aprire il file del modello di pagina *modelli/HelloDjangoApp/index.html* oppure *modelli/index.html* in VS 2017 15.7 e versioni precedenti. Si noti che contiene una variabile, `{{ content }}`:

    ```html
    <html>
    <head><title></title></head>

    <body>

    {{ content }}

    </body>
    </html>
    ```

1. Nella cartella *HelloDjangoApp* aprire *views.py* e sostituire la funzione `index` con il codice seguente che usa la funzione helper `django.shortcuts.render`. La funzione di supporto `render` fornisce un'interfaccia semplificata da usare con i modelli di pagina. Assicurarsi di mantenere tutte le istruzioni `from` esistenti.

    ```python
    from django.shortcuts import render   # Added for this step

    def index(request):
        now = datetime.now()

        return render(
            request,
            "HelloDjangoApp/index.html",  # Relative path from the 'templates' folder to the template file
            # "index.html", # Use this code for VS 2017 15.7 and earlier
            {
                'content': "<strong>Hello Django!</strong> on " + now.strftime("%A, %d %B, %Y at %X")
            }
        )
    ```

    Il primo argomento per `render`, come si può notare, è l'oggetto richiesta, seguito dal percorso relativo del file di modello all'interno della cartella *templates* dell'app. Un file modello è denominato in base alla visualizzazione che supporta, se appropriato. Il terzo argomento per `render` è quindi un dizionario di variabili cui fa riferimento il modello. È possibile includere oggetti nel dizionario e in questo caso una variabile nel modello può fare riferimento a `{{ object.property }}`.

1. Eseguire il progetto e osservare l'output. Dovrebbe essere visualizzato un messaggio simile a quello mostrato nel passaggio 2-2, che indica che il modello funziona.

    Osservare, tuttavia, che il rendering del file HTML usato nella proprietà `content` viene eseguito solo come testo normale, perché la funzione `render` esce automaticamente dal file HTML. La sequenza di escape automatica evita vulnerabilità accidentali agli attacchi injection: gli sviluppatori spesso raccolgono l'input da una pagina e lo usano come valore in un'altra usando un segnaposto di modello. L'escape funge anche da promemoria per ricordare che è meglio tenere l'HTML nel modello di pagina e fuori dal codice. Per fortuna è semplice creare variabili aggiuntive in caso di necessità. Modificare ad esempio *index.html* con i *modelli* in modo che corrisponda al markup seguente, che aggiunge un titolo di pagina e mantiene tutta la formattazione nel modello di pagina:

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

    Scrivere quindi la funzione di visualizzazione `index` come indicato di seguito, per fornire valori per tutte le variabili nel modello di pagina:

    ```python
    def index(request):
        now = datetime.now()

        return render(
            request,
            "HelloDjangoApp/index.html",  # Relative path from the 'templates' folder to the template file
            # "index.html", # Use this code for VS 2017 15.7 and earlier
            {
                'title' : "Hello Django",
                'message' : "Hello Django!",
                'content' : " on " + now.strftime("%A, %d %B, %Y at %X")
            }
        )
    ```

1. Arrestare il server e riavviare il progetto e osservare che il rendering della pagina avviene ora correttamente:

    ![Esecuzione dell'app tramite il modello](media/django/step02-result.png)

1. <a name="template-namespacing"></a>Visual Studio 2017 versione 15.7 e versioni precedenti: come passaggio finale, spostare i modelli in una sottocartella con lo stesso nome dell'app, operazione che crea uno spazio dei nomi ed evita i potenziali conflitti con altre app eventualmente aggiunte al progetto. I modelli in VISUAL Studio 2017 15.8+ ese cosa fare automaticamente. In altre informazioni,  creare una sottocartella nei modelli denominata *HelloDjangoApp,* spostare *index.html in* tale sottocartella e modificare la funzione di visualizzazione in modo che faccia riferimento al nuovo percorso del `index` modello, *HelloDjangoApp/index.html*. Eseguire quindi il progetto, verificare che il rendering della pagina avvenga correttamente e arrestare il server.

1. Eseguire il commit delle modifiche nel controllo del codice sorgente e aggiornare il repository remoto, se si vuole, come descritto nel [passaggio 2-2](#commit-to-source-control).

### <a name="question-do-page-templates-have-to-be-in-a-separate-file"></a>Domanda: I modelli di pagina devono trovarsi in un file separato?

Risposta: Anche se i modelli vengono in genere mantenuti in file HTML separati, è possibile usare anche un modello inline. L'uso di un file distinto è l'opzione consigliata, tuttavia, per mantenere una netta separazione tra il markup e il codice.

### <a name="question-must-templates-use-the-html-file-extension"></a>Domanda: I modelli devono usare l'estensione di file html?

Risposta: L'estensione *html* per i file di modello di pagina è completamente facoltativa, perché è sempre possibile identificare esattamente il percorso relativo del file nel secondo argomento della funzione `render`. Per i file con estensione *html*, tuttavia, Visual Studio e altri editor offrono in genere funzionalità quali il completamento del codice e la colorazione della sintassi, che compensano il fatto che i modelli di pagina non siano rigorosamente HTML.

Infatti, quando si lavora con un progetto Django, Visual Studio rileva automaticamente quando il file HTML che si sta modificando è effettivamente un modello Django e fornisce alcune funzionalità di completamento automatico. Ad esempio, quando si inizia a digitare un commento in un modello di pagina Django, `{#`, Visual Studio fornisce automaticamente i caratteri `#}` di chiusura. Anche i comandi **Commenta selezione** e **Rimuovi commento selezione** (nel menu **Modifica** > **Avanzate** e sulla barra degli strumenti) usano i commenti dei modelli anziché i commenti HTML.

### <a name="question-when-i-run-the-project-i-see-an-error-that-the-template-cannot-be-found-whats-wrong"></a>Domanda: Quando si esegue il progetto, viene visualizzato un errore che indica che non è possibile trovare il modello. Qual è il problema?

Risposta: Se vengono visualizzati errori che indicano che non è possibile trovare il modello, verificare di aver aggiunto l'app al file *settings.py* del progetto Django nell'elenco `INSTALLED_APPS`. Senza questa voce, Django non sa di dover cercare nella cartella *templates* dell'app.

### <a name="question-why-is-template-namespacing-important"></a>Domanda: Perché gli spazi dei nomi dei modelli sono importanti?

Risposta: Quando Django cerca un modello cui viene fatto riferimento nella funzione `render`, usa qualsiasi file trovato per primo che corrisponde al percorso relativo. Se nello stesso progetto sono presenti più app Django che usano le stesse strutture di cartelle per i modelli, è probabile che un'app userà involontariamente un modello di un'altra app. Per evitare errori di questo tipo, all'interno della cartella *templates* di un'app creare una sottocartella corrispondente al nome dell'app, in modo da evitare la duplicazione di alcuni o di tutti gli elementi.

## <a name="next-steps"></a>Passaggi successivi

> [!div class="nextstepaction"]
> [Rendere disponibili file statici, aggiungere pagine e usare l'ereditarietà dei modelli](learn-django-in-visual-studio-step-03-serve-static-files-and-add-pages.md)

## <a name="go-deeper"></a>Approfondimento

- [Writing your first Django app, part 1 - views](https://docs.djangoproject.com/en/2.0/intro/tutorial01/#write-your-first-view) (Scrittura della prima app Django, parte 1 - Visualizzazioni) (docs.djangoproject.com)
- Per informazioni sulle altre funzionalità dei modelli Django, tra cui le inclusioni e l'ereditarietà, vedere [The Django template language](https://docs.djangoproject.com/en/2.0/ref/templates/language/) (Linguaggio dei modelli Django) (docs.djangoproject.com)
- [Regular expression training on inLearning](https://www.linkedin.com/learning/topics/regular-expressions) (Formazione sulle espressioni regolari in inLearning) (LinkedIn)
- Codice sorgente per l'esercitazione su GitHub: [Microsoft/python-sample-vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django)
