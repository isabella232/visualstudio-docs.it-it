---
title: Pubblicazione di un'app Python in Servizio app di Azure in Windows
description: Come pubblicare un'applicazione Web Python direttamente in Servizio app di Azure in Windows da Visual Studio, incluso il contenuto necessario per il file web.config.
ms.date: 01/07/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.technology: vs-python
ms.custom: seodec18
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: 0865be9aadc7991dda8597b3bb418d058ced43b4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122076243"
---
# <a name="publishing-to-azure-app-service-on-windows"></a>Pubblicazione in Servizio app di Azure in Windows

> [!Note]
> Le funzionalità e i contenuti descritti sono deprecati ma continuano a funzionare. Si invitano gli sviluppatori Python a eseguire la migrazione al [servizio app in Linux](publishing-python-web-applications-to-azure-from-visual-studio.md), se possibile.

Visual Studio consente di pubblicare un'app Web Python direttamente in Servizio app di Azure in Windows. La pubblicazione in Servizio app di Azure in Windows prevede la copia dei file necessari nel server e la configurazione del file `web.config` appropriato che indica al server Web come avviare l'app.

Il processo di pubblicazione è diverso in Visual Studio 2017 e versioni successive e in Visual Studio 2015. In particolare, Visual Studio 2015 automatizza alcuni passaggi, inclusa la creazione di `web.config`, ma questa automazione limita la flessibilità e il controllo a lungo termine. Visual Studio 2017 e versioni successive richiedono più passaggi manuali ma offrono un controllo più preciso sull'ambiente Python. Entrambe le opzioni sono descritte di seguito.

> [!Note]
> Per informazioni sulle differenze tra Visual Studio 2015 e Visual Studio 2017 e versioni successive, vedere il post di blog [Publish to Azure in Visual Studio 2017](https://devblogs.microsoft.com/python/publish-to-azure-in-vs-2017/) (Pubblicare in Azure in Visual Studio 2017).

## <a name="prerequisites"></a>Prerequisiti

Per questa procedura dettagliata è necessario un progetto di app Web basato sui framework Bottle, Flask o Django. Se non è ancora stato creato un progetto e si vuole provare il processo di pubblicazione, creare un progetto di test semplice come descritto di seguito:

1. In Visual Studio selezionare **File > New > Project**(Nuovo > Project), cercare "Bottle", selezionare **il Project Web Bottle,** specificare e nome e un percorso per il progetto, quindi **selezionare OK.** (Il modello Bottle è incluso nel carico di lavoro di sviluppo Python; vedere [Installazione](installing-python-support-in-visual-studio.md)).

1. Seguire le istruzioni per installare i pacchetti esterni, selezionando **Installa in un ambiente virtuale** e l'interprete di base preferito per l'ambiente virtuale. L'opzione selezionata corrisponde in genere alla versione di Python installata nel servizio app.

1. Testare il progetto in locale premendo F5 o selezionando **Debug > Avvia debug**.

## <a name="create-an-azure-app-service"></a>Creare un servizio app di Azure

La pubblicazione in Azure richiede un servizio app di destinazione. A questo scopo è possibile creare un servizio app mediante una sottoscrizione di Azure oppure è possibile usare un sito temporaneo.

Se non si ha già una sottoscrizione, iniziare con un [account Azure completo gratuito](https://azure.microsoft.com/free/) che include un credito sufficiente per i servizi di Azure. Valutare anche la possibilità di iscriversi [Visual Studio Dev Essentials](https://azure.microsoft.com/pricing/member-offers/vs-dev-essentials/), che offre un credito di $ 25 al mese per un intero anno.

> [!Tip]
> Sebbene Azure richieda una carta di credito per verificare l'account, non viene addebitato alcun costo sulla carta. È anche possibile impostare un [limite di spesa](/azure/billing/billing-spending-limit) uguale al credito gratuito per garantire che non vengano addebitate spese aggiuntive. Azure offre anche un piano gratuito per il servizio app particolarmente adatto alle app di test semplici descritte nella sezione che segue.

### <a name="using-a-subscription"></a>Usando una sottoscrizione

Con una sottoscrizione Azure attiva, creare un servizio app con un'app Web vuota come segue:

1. Accedere a [portal.azure.com](https://portal.azure.com).
1. Selezionare **+Nuovo**, quindi **Web e dispositivi mobili** e **App Web**.
1. Specificare un nome per l'app Web, lasciare **Gruppo di risorse** su "Crea nuovo" e scegliere **Windows** come sistema operativo.
1. Selezionare **Piano di servizio app/Località**, **Crea nuovo** e specificare un nome e una località. Selezionare quindi **Piano tariffario**, scorrere verso il basso e selezionare il piano **F1 Gratuito**, scegliere **Seleziona**, **OK** e quindi **Crea**.
1. (Facoltativo) Dopo aver creato il servizio app, passare al servizio, selezionare **Recupera profilo di pubblicazione** e salvare il file in locale.

### <a name="using-a-temporary-app-service"></a>Usando un servizio app temporaneo

Per creare un servizio app temporaneo che non richiede una sottoscrizione di Azure eseguire le operazioni seguenti:

1. Aprire il browser in [https://azure.microsoft.com/try/app-service/web/](https://azure.microsoft.com/try/app-service/web/) .
1. Selezionare **App Web** come tipo di applicazione e quindi selezionare **Successivi**.
1. Selezionare **Empty Site** (Sito vuoto) e quindi **Crea**.
1. Accedere con un qualsiasi account di accesso di social networking e dopo qualche istante il sito sarà pronto all'URL visualizzato.
1. Selezionare **Scarica profilo di pubblicazione** e salvare il file `.publishsettings`, da usare più tardi.

## <a name="configure-python-on-azure-app-service"></a>Configurare Python nel servizio app di Azure

Dopo aver creato un servizio app con un'app Web vuota in esecuzione nella propria sottoscrizione o in un sito gratuito, installare una versione di Python come descritto in [Gestione di Python nel servizio app di Azure](managing-python-on-azure-app-service.md). Per la pubblicazione da Visual Studio 2017 e versioni successive, registrare il percorso esatto dell'interprete Python installato con l'estensione del sito, come descritto nell'articolo.

È anche possibile installare il pacchetto `bottle` usando il processo descritto in queste istruzioni poiché il pacchetto viene installato in altri passaggi di questa procedura dettagliata.

## <a name="publish-to-app-service---visual-studio-2017-and-later"></a>Pubblicare nel servizio app - Visual Studio 2017 e versioni successive

Durante la pubblicazione nel servizio app di Azure da Visual Studio 2017 e versioni successive vengono copiati solo i file del progetto nel server. Per questa ragione. è necessario creare i file per configurare l'ambiente del server.

1. In Visual Studio **Esplora soluzioni** fare clic con il pulsante destro del mouse sul progetto e **scegliere > Nuovo elemento...**. Nella finestra di dialogo visualizzata selezionare il modello "Azure web.config (Fast CGI)" e selezionare OK. Verrà creato un file `web.config` nella radice del progetto.

1. Modificare la voce `PythonHandler` in `web.config` in modo che il percorso corrisponda a quello dell'installazione Python nel server (vedere [Riferimento alla configurazione di IIS](https://www.iis.net/configreference) (iis.net) per tutti i dettagli). Ad esempio, per Python 3.6.1 x64 la voce sarà la seguente:

    ```xml
    <system.webServer>
      <handlers>
        <add name="PythonHandler" path="*" verb="*" modules="FastCgiModule"
            scriptProcessor="D:\home\Python361x64\python.exe|D:\home\Python361x64\wfastcgi.py"
            resourceType="Unspecified" requireAccess="Script"/>
      </handlers>
    </system.webServer>
    ```

1. Impostare la voce `WSGI_HANDLER` in `web.config` per il framework in uso:

    - **Bottle**: aggiungere le parentesi dopo `app.wsgi_app` come illustrato di seguito. Ciò è necessario perché l'oggetto è una funzione (vedere `app.py`) anziché una variabile:

        ```xml
        <!-- Bottle apps only -->
        <add key="WSGI_HANDLER" value="app.wsgi_app()"/>
        ```

    - **Flask**: modificare il valore `WSGI_HANDLER` in `<project_name>.app` dove `<project_name>` corrisponde al nome del progetto. È possibile trovare l'identificatore esatto esaminando l'istruzione `from <project_name> import app` in `runserver.py`. Ad esempio, se il progetto è denominato "FlaskAzurePublishExample", la voce sarà la seguente:

        ```xml
        <!-- Flask apps only: change the project name to match your app -->
        <add key="WSGI_HANDLER" value="FlaskAzurePublishExample.app"/>
        ```

    - **Django**: per i progetti Django sono necessarie due modifiche a `web.config`. Modificare innanzitutto il valore`WSGI_HANDLER` in `django.core.wsgi.get_wsgi_application()` (l'oggetto è incluso nel file `wsgi.py`):

        ```xml
        <!-- Django apps only -->
        <add key="WSGI_HANDLER" value="django.core.wsgi.get_wsgi_application()"/>
        ```

        Aggiungere quindi la voce seguente sotto la voce per `WSGI_HANDLER`, sostituendo `DjangoAzurePublishExample` con il nome del progetto:

        ```xml
        <add key="DJANGO_SETTINGS_MODULE" value="DjangoAzurePublishExample.settings" />
        ```

1. **Solo app Django**: nel file `settings.py` del progetto Django aprire e aggiungere il dominio dell'URL del sito in `ALLOWED_HOSTS` come illustrato di seguito, sostituendo 'vspython-test-02.azurewebsites.net' con il proprio URL:

    ```python
    # Change the URL to your specific site
    ALLOWED_HOSTS = ['vspython-test-02.azurewebsites.net']
    ```

    Se non si aggiunge l'URL alla matrice, viene visualizzato l'errore "DisallowedHost at/Invalid HTTP_HOST header: ' \<site URL\> '. Potrebbe essere necessario aggiungere ' \<site URL\> ' a ALLOWED_HOSTS."

    Si noti che quando la matrice è vuota, Django autorizza automaticamente 'localhost', ma l'aggiunta dell'URL di produzione rimuove tale funzionalità. Per questo motivo si potrebbe voler mantenere copie separate di `settings.py` per sviluppo e produzione, oppure utilizzare le variabili di ambiente per controllare i valori della fase di esecuzione.

1. In **Esplora soluzioni** espandere la cartella con lo stesso nome del progetto, fare clic con il pulsante destro del mouse sulla cartella `static`, selezionare **Aggiungi > Nuovo elemento...**, selezionare il modello "web.config di file statici di Azure" e scegliere **OK**. Questa azione crea un altro file `web.config` nella cartella `static` che disabilita l'elaborazione Python per la cartella. Questa configurazione invia richieste di file statici al server Web predefinito, anziché usare l'applicazione Python.

1. Salvare il progetto, quindi in Visual Studio in **Esplora soluzioni** fare clic con il pulsante destro del mouse sul progetto e selezionare **Pubblica**.

    ![Comando Pubblica nel menu di scelta rapida di un progetto](media/template-web-publish-command.png)

1. Nella scheda **Pubblica** visualizzata selezionare la destinazione della pubblicazione:

    a. La sottoscrizione di Azure: selezionare **Servizio app di Microsoft Azure**, quindi **Seleziona esistente** e infine **Pubblica**. Viene visualizzata una finestra di dialogo in cui è possibile selezionare la sottoscrizione appropriata e il servizio app. Se il servizio app non viene visualizzato, usare il profilo di pubblicazione scaricato come descritto di seguito per un servizio app temporaneo.

    ![Pubblicare in Azure, passaggio 1, Visual Studio 2017 e versioni successive, sottoscrizioni esistenti](media/tutorials-common-publish-1a-2017.png)

    b. Se si usa un servizio app temporaneo in try.azurewebsites.net o se è necessario usare un profilo di pubblicazione, selezionare il controllo per trovare Importa profilo, selezionare l'opzione e quindi **>** **pubblicare** . Viene richiesto di specificare il percorso del file `.publishsettings` scaricato in precedenza.

    ![Pubblicare in Azure, passaggio 1, Visual Studio 2017 e versioni successive, servizio app temporaneo](media/tutorials-common-publish-1b-2017.png)

1. Visual Studio visualizza lo stato della pubblicazione in una finestra "Attività pubblicazione sul Web" e nella finestra Pubblica. Al termine della pubblicazione, viene aperto il browser predefinito nell'URL del sito. L'URL è visualizzato anche nella finestra Pubblica.

1. All'apertura del browser è possibile che venga visualizzato il messaggio "Impossibile visualizzare la pagina a causa di un errore interno del server". Questo messaggio indica che l'ambiente Python nel server non è configurato completamente. In tal caso, seguire questa procedura:

    a. Fare di nuovo riferimento a [Gestione di Python nel servizio app di Azure](managing-python-on-azure-app-service.md) e assicurarsi di aver installato un'estensione del sito Python appropriata.

    b. Controllare il percorso dell'interprete Python nel file `web.config`. Il percorso deve corrispondere esattamente al percorso di installazione dell'estensione del sito selezionata.

    c. Usare la console Kudu per aggiornare tutti i pacchetti elencati nel file `requirements.txt` dell'app: passare alla stessa cartella Python usata in `web.config`, ad esempio `/home/python361x64`, ed eseguire il comando seguente come descritto nella sezione relativa alla [console Kudu](managing-python-on-azure-app-service.md#azure-app-service-kudu-console):

    ```command
    python -m pip install --upgrade -r /home/site/wwwroot/requirements.txt
    ```

    Se si verificano errori di autorizzazione quando si esegue questo comando, verificare che il comando venga eseguito nella cartella dell'estensione del sito e *non* nella cartella di una delle installazioni Python predefinite del servizio app. Poiché non è possibile modificare gli ambienti predefiniti, il tentativo di installare i pacchetti ha sicuramente esito negativo.

    d. Per l'output dell'errore dettagliato, aggiungere la riga seguente a `web.config` all'interno del nodo `<system.webServer>` che visualizza un output dell'errore più dettagliato:

    ```xml
    <httpErrors errorMode="Detailed"></httpErrors>
    ```

    e. Provare a riavviare il servizio app dopo l'installazione dei nuovi pacchetti. Quando si modifica `web.config` non è necessario riavviare poiché il servizio app esegue un riavvio automatico ogni volta che `web.config` viene modificato.

    > [!Tip]
    > Se si apportano modifiche al file `requirements.txt` dell'app, assicurarsi di usare di nuovo la console di Kudu per installare i pacchetti che sono ora elencati nel file.

1. Dopo aver configurato completamente l'ambiente del server, aggiornare la pagina nel browser. Verrà visualizzata l'app Web.

    ![Risultati della pubblicazione di app Bottle, Flask e Django nel servizio app](media/azure-publish-results.png)

## <a name="publishing-to-app-service---visual-studio-2015"></a>Pubblicare nel servizio app - Visual Studio 2015

> [!Note]
> Un breve video di questo processo è disponibile in [Visual Studio Python Tutorial: Building a Website](https://www.youtube.com/watch?v=FJx5mutt1uk&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=6) (Esercitazione su Python in Visual Studio: Creazione di un sito Web) su youtube.com (durata: 3 minuti e 10 secondi).

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul progetto e scegliere **Pubblica**.

1. Nella finestra di dialogo **Pubblica** selezionare **Servizio app di Microsoft Azure**:

  ![Passaggio 1 della pubblicazione in Azure](media/tutorials-common-publish-1.png)

1. Selezionare una destinazione:

    - Se si dispone di una sottoscrizione di Azure, selezionare **Servizio app di Microsoft Azure** come destinazione di pubblicazione e quindi nella finestra di dialogo successiva selezionare un servizio app esistente oppure selezionare **Nuovo** per crearne uno nuovo.
    - Se si usa un sito temporaneo creato su try.azurewebsites.net, selezionare **Importa** come destinazione di pubblicazione, cercare il file `.publishsettings` scaricato dal sito e quindi fare clic su **OK**.

1. I dettagli del servizio app vengono visualizzati nella scheda **Connessione** della finestra di dialogo **Pubblica** seguente.

  ![Passaggio 2 della pubblicazione in Azure](media/tutorials-common-publish-2.png)

1. Se necessario, selezionare **Avanti >** per esaminare le impostazioni aggiuntive.

1. Selezionare **Pubblica**. Dopo la distribuzione dell'applicazione in Azure, il sito viene visualizzato nel browser predefinito.

Come parte di questo processo, Visual Studio esegue anche i passaggi seguenti:

- Creare un file `web.config` nel server che contiene i puntatori appropriati alla funzione `wsgi_app` dell'app e all'interprete Python 3.4 predefinito del servizio app.
- Disattivare l'elaborazione per i file della cartella `static` del progetto (le regole si trovano in `web.config`).
- Pubblicare l'ambiente virtuale nel server.
- Aggiungere un `web.debug.config` file e gli strumenti di debug per abilitare il debug remoto. Per Visual Studio 2019 versione 16.4 e precedenti, gli strumenti di debug sono ptvsd. Per Visual Studio 2019 versione 16.5 e successive, gli strumenti di debug sono debugpy.

Come segnalato in precedenza, questi passaggi automatici semplificano il processo di pubblicazione ma rendono più difficile il controllo dell'ambiente Python. Ad esempio, il file `web.config` viene creato solo nel server ma non viene aggiunto al progetto. Anche il processo di pubblicazione richiede più tempo poiché copia l'intero ambiente virtuale dal computer di sviluppo anziché basarsi sulla configurazione del server.

È possibile che si voglia mantenere il proprio file `web.config` e usare `requirements.txt` per mantenere i pacchetti direttamente nel server. L'uso di `requirements.txt`, in particolare, garantisce che l'ambiente di sviluppo e l'ambiente del server corrispondano sempre.
