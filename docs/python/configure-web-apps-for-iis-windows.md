---
title: Configurare app Web Python per IIS
description: Come configurare app Web Python per l'esecuzione con Internet Information Services da una macchina virtuale Windows.
ms.date: 12/06/2018
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
ms.openlocfilehash: 86d4d897fb7ea4000ed60f4c9c1047a21ab74c7f
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126637011"
---
# <a name="configure-python-web-apps-for-iis"></a>Configurare app Web Python per IIS

Quando si usa Internet Information Services (IIS) come server Web in un computer Windows (con [macchine virtuali Windows in Azure](/azure/architecture/reference-architectures/n-tier/windows-vm)), le app Python devono includere impostazioni specifiche nei file *web.config* per permettere a IIS di elaborare correttamente il codice Python. Nel computer deve anche essere installato Python con tutti i pacchetti richiesti dall'app Web.

> [!Note]
> Questo articolo in precedenza conteneva informazioni per la configurazione di Python in Servizio app di Azure in Windows. Le estensioni Python e gli host Windows usati in tale scenario sono stati deprecati a favore di Servizio app di Azure in Linux. Per altre informazioni, vedere [Pubblicazione di app Python in Servizio app di Azure (Linux)](publishing-python-web-applications-to-azure-from-visual-studio.md). L'articolo precedente, tuttavia, è ancora disponibile in [Gestione del servizio app in Windows con le estensioni Python](managing-python-on-azure-app-service.md).

## <a name="install-python-on-windows"></a>Installare Python in Windows

Per eseguire un'app Web, installare prima di tutto la versione di Python necessaria direttamente nel computer host Windows come descritto in [Installare gli interpreti Python](installing-python-interpreters.md).

Registrare il percorso dell'interprete `python.exe` per i passaggi successivi. Per comodità, aggiungere quindi tale percorso alla variabile di ambiente PATH.

## <a name="install-packages"></a>Installare i pacchetti

Quando si usa un host dedicato, è possibile usare l'ambiente Python globale per eseguire l'app invece di un ambiente virtuale. Di conseguenza, è possibile installare tutti i requisiti dell'app nell'ambiente globale semplicemente eseguendo `pip install -r requirements.txt` a un prompt dei comandi.

## <a name="set-webconfig-to-point-to-the-python-interpreter"></a>Configurare web.config per fare riferimento all'interprete di Python

Il file *web.config* dell'app indica al server Web IIS (7+) in esecuzione in Windows come gestire le richieste Python tramite HttpPlatform (consigliato) o FastCGI. Visual Studio versioni 2015 e precedenti apportano automaticamente queste modifiche. Quando si usa Visual Studio 2017 e versioni successive è necessario modificare il file *web.config* manualmente.

### <a name="configure-the-httpplatform-handler"></a>Configurare il gestore HttpPlatform

Il modulo HttpPlatform passa le connessioni socket direttamente a un processo di Python autonomo. Questo pass-through consente di eseguire qualsiasi server Web, ma richiede uno script di avvio che esegue un server Web locale. Specificare lo script nell'elemento `<httpPlatform>` di *web.config*, dove l'attributo `processPath` punta all'interprete Python dell'estensione del sito e l'attributo `arguments` punta allo script e a eventuali argomenti che si vogliono specificare:

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.webServer>
    <handlers>
      <add name="PythonHandler" path="*" verb="*" modules="httpPlatformHandler" resourceType="Unspecified"/>
    </handlers>
    <httpPlatform processPath="c:\python36-32\python.exe"
                  arguments="c:\home\site\wwwroot\runserver.py --port %HTTP_PLATFORM_PORT%"
                  stdoutLogEnabled="true"
                  stdoutLogFile="c:\home\LogFiles\python.log"
                  startupTimeLimit="60"
                  processesPerApplication="16">
      <environmentVariables>
        <environmentVariable name="SERVER_PORT" value="%HTTP_PLATFORM_PORT%" />
      </environmentVariables>
    </httpPlatform>
  </system.webServer>
</configuration>
```

La variabile di ambiente `HTTP_PLATFORM_PORT` qui illustrata contiene la porta sulla quale il server locale deve essere in ascolto per le connessioni da localhost. In questo esempio viene anche illustrato come creare un'altra eventuale variabile di ambiente, in questo caso `SERVER_PORT`.

### <a name="configure-the-fastcgi-handler"></a>Configurare il gestore FastCGI

FastCGI è un'interfaccia che funziona a livello di richiesta. IIS riceve le connessioni in ingresso e inoltra ogni richiesta a un'app WSGI in esecuzione in uno o più processi Python persistenti.

Per l'uso, prima di tutto installare e configurare il pacchetto wfastcgi come descritto in [pypi.org/project/wfastcgi/](https://pypi.io/project/wfastcgi).

Modificare quindi il file *web.config* dell'app per includere i percorsi completi di *python.exe* e *wfastcgi.py* nella chiave `PythonHandler`. I passaggi seguenti presuppongono che Python sia installato in *c:\python36-32* e che il codice dell'app si trovi in *c:\home\site\wwwroot*. Apportare le modifiche necessarie in base ai percorsi in uso:

1. Modificare la voce `PythonHandler` in *web.config* in modo che il percorso corrisponda al percorso di installazione di Python. Vedere [IIS Configuration Reference](https://www.iis.net/configreference) (Informazioni di riferimento sulla configurazione di IIS) (iis.net) per tutti i dettagli.

    ```xml
    <system.webServer>
      <handlers>
        <add name="PythonHandler" path="*" verb="*" modules="FastCgiModule"
            scriptProcessor="c:\python36-32\python.exe|c:\python36-32\wfastcgi.py"
            resourceType="Unspecified" requireAccess="Script"/>
      </handlers>
    </system.webServer>
    ```

1. `<appSettings>`All'interno della sezione *web.config* aggiungere le chiavi per `WSGI_HANDLER` , `WSGI_LOG` (facoltativo) e `PYTHONPATH` :

    ```xml
    <appSettings>
      <add key="PYTHONPATH" value="c:\home\site\wwwroot"/>
      <!-- The handler here is specific to Bottle; see the next section. -->
      <add key="WSGI_HANDLER" value="app.wsgi_app()"/>
      <add key="WSGI_LOG" value="c:\home\LogFiles\wfastcgi.log"/>
    </appSettings>
    ```

    Questi valori di `<appSettings>` sono disponibili come variabili di ambiente per l'app:

    - Il valore per `PYTHONPATH` può essere esteso liberamente, ma deve includere la directory radice dell'app.
    - `WSGI_HANDLER` deve puntare a un'app WSGI importabile dall'app.
    - `WSGI_LOG` è facoltativo ma consigliato per il debug dell'app.

1. Impostare la voce `WSGI_HANDLER` in *web.config* in base al framework in uso:

    - **Bottle**: assicurarsi di aggiungere le parentesi dopo `app.wsgi_app`, come illustrato di seguito. Questa operazione è necessaria perché l'oggetto è una funzione (vedere *app.py*) anziché una variabile:

        ```xml
        <!-- Bottle apps only -->
        <add key="WSGI_HANDLER" value="app.wsgi_app()"/>
        ```

    - **Flask**: modificare il valore `WSGI_HANDLER` in `<project_name>.app` dove `<project_name>` corrisponde al nome del progetto. È possibile trovare l'identificatore esatto esaminando l'istruzione `from <project_name> import app` in *runserver.py*. Ad esempio, se il progetto è denominato "FlaskAzurePublishExample", la voce sarà la seguente:

        ```xml
        <!-- Flask apps only: change the project name to match your app -->
        <add key="WSGI_HANDLER" value="flask_iis_example.app"/>
        ```

    - **Django**: per i progetti Django è necessario apportare due modifiche al file *web.config*. Per prima cosa, impostare il valore `WSGI_HANDLER` su `django.core.wsgi.get_wsgi_application()` (l'oggetto è incluso nel file *wsgi.py*):

        ```xml
        <!-- Django apps only -->
        <add key="WSGI_HANDLER" value="django.core.wsgi.get_wsgi_application()"/>
        ```

        Aggiungere quindi la voce seguente sotto la voce per `WSGI_HANDLER`, sostituendo `DjangoAzurePublishExample` con il nome del progetto:

        ```xml
        <add key="DJANGO_SETTINGS_MODULE" value="django_iis_example.settings" />
        ```

1. **Solo app Django**: nel file *settings.py* del progetto Django aggiungere il dominio dell'URL del sito o l'indirizzo IP in `ALLOWED_HOSTS`, come illustrato di seguito, sostituendo "1.2.3.4" con il proprio URL o indirizzo IP:

    ```python
    # Change the URL or IP address to your specific site
    ALLOWED_HOSTS = ['1.2.3.4']
    ```

    Se non si aggiunge l'URL alla matrice, viene restituito l'errore **DisallowedHost at/Invalid HTTP_HOST header: ' \<site URL\> '. Potrebbe essere necessario aggiungere ' \<site URL\> ' a ALLOWED_HOSTS.**

    Si noti che, quando la matrice è vuota, Django autorizza automaticamente "localhost" e "127.0.0.1", ma se si aggiunge l'URL di produzione questa funzionalità viene rimossa. Per questo motivo è consigliabile mantenere copie separate di *settings.py* per sviluppo e produzione, oppure usare le variabili di ambiente per controllare i valori della fase di esecuzione.

## <a name="deploy-to-iis-or-a-windows-vm"></a>Eseguire la distribuzione in IIS o in una macchina virtuale Windows

Con il file *web.config* corretto nel progetto, è possibile eseguire la pubblicazione nel computer che esegue IIS usando il comando **Pubblica** del menu di scelta rapida del progetto in **Esplora soluzioni** e selezionando l'opzione **IIS, FTP e così via**. In questo caso, Visual Studio copia semplicemente i file di progetto nel server, mentre l'utente deve eseguire tutte le attività di configurazione sul lato server.
