---
title: Usare PowerShell per la pubblicazione in ambienti di sviluppo e test
description: Informazioni su come utilizzare gli script di Windows PowerShell da Visual Studio per pubblicare allo sviluppo e gli ambienti di prova.
ms.custom: SEO-VS-2020
author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2016
ms.author: ghogen
ms.openlocfilehash: 2e7b04c0411f5e07933cf4286edfcb112d6377e7
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122105847"
---
# <a name="using-windows-powershell-scripts-to-publish-to-dev-and-test-environments"></a>Uso degli script di Windows PowerShell per la pubblicazione in ambienti di sviluppo e test

Quando si crea un'applicazione web in Visual Studio, è possibile generare uno script Windows PowerShell che può essere utilizzato in un secondo momento per automatizzare la pubblicazione del sito Web in Azure come un'applicazione Web nel servizio App Azure o una macchina virtuale. È possibile modificare ed estendere lo script di Windows PowerShell nell'editor di Visual Studio in base alle proprie esigenze o integrare lo script di compilazione esistente, il test e la pubblicazione di script.

Utilizzando questi script, è possibile eseguire il provisioning (noto anche come ambienti di sviluppo e test) di versioni personalizzate del sito per un utilizzo temporaneo. Ad esempio, si potrebbe impostare una particolare versione del sito Web in una macchina virtuale di Azure o in una slot di gestione temporanea in un sito Web per eseguire un gruppo di test, riprodurre un bug, testare una correzione di bug, una versione di valutazione di una modifica proposta o configurare un ambiente personalizzato per una dimostrazione o una presentazione. Dopo aver creato uno script che pubblica il progetto, è possibile ricreare ambienti identici eseguendo nuovamente lo script in base alle esigenze o eseguire lo script con la build dell'applicazione Web per creare un ambiente di test personalizzato.

## <a name="prerequisites"></a>Prerequisiti

* Visual Studio 2015 o versione successiva con il **carico di lavoro di Azure** installato oppure Visual Studio 2013 e Azure SDK 2.3 o versioni successive. Vedere [Download di Visual Studio](https://visualstudio.microsoft.com/downloads). Non è necessario Azure SDK per generare script per i progetti Web. Questa funzionalità è riservata ai progetti Web, non ai ruoli Web nei servizi cloud.
* Azure PowerShell 0.7.4 o versione successiva Vedere [Come installare e configurare Azure PowerShell](/powershell/azure/overview).
* [Windows PowerShell 3.0](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc770458(v=ws.10)) o versione successiva.

## <a name="additional-tools"></a>Strumenti aggiuntivi

Sono disponibili altri strumenti e risorse per l'utilizzo di PowerShell in Visual Studio per lo sviluppo in Azure. Vedere [PowerShell Tools per Visual Studio](https://marketplace.visualstudio.com/items?itemName=AdamRDriscoll.PowerShellToolsforVisualStudio2015).

## <a name="generating-the-publish-scripts"></a>Come generare script di pubblicazione

È possibile generare gli script di pubblicazione per una macchina virtuale che ospita il sito Web quando si crea un nuovo progetto seguendo [queste istruzioni](/azure/virtual-machines/windows/classic/web-app-visual-studio). È possibile anche [generare script di pubblicazione per le app Web del Servizio app di Azure](/azure/app-service/scripts/app-service-powershell-deploy-github).

## <a name="scripts-that-visual-studio-generates"></a>Script generati da Visual Studio

Visual Studio genera una cartella a livello di soluzione denominata **PublishScripts** che contiene due file di Windows PowerShell, uno script di pubblicazione per la macchina virtuale o il sito Web e un modulo che contiene funzioni che è possibile usare negli script. Visual Studio genera inoltre un file in formato JSON che specifica i dettagli del progetto in distribuzione.

### <a name="windows-powershell-publish-script"></a>Pubblicazione di script da parte di Windows PowerShell

Lo script di pubblicazione contiene specifici passaggi di pubblicazione per la distribuzione in una macchina virtuale o in un sito Web. Visual Studio fornisce la colorazione della sintassi per lo sviluppo di Windows PowerShell . La Guida per le funzioni è disponibile, ed è possibile modificare liberamente le funzioni nello script per adattarle ai propri requisiti.

### <a name="windows-powershell-module"></a>Modulo di Windows PowerShell

Il modulo Windows PowerShell generato da Visual Studio contiene funzioni che utilizzano lo script di pubblicazione. Queste funzioni di Azure PowerShell non possono essere modificate. Vedere [Come installare e configurare Azure PowerShell](/powershell/azure/overview).

### <a name="json-configuration-file"></a>File di configurazione JSON.

Il file JSON viene creato nella cartella delle configurazioni e contiene i dati di configurazione che specificano le risorse esatte da distribuire in Azure. Il nome del file generato da Visual Studio è project-name-WAWS-dev. json se è stato creato un sito Web, o project name-VM-dev.json se è stata creata una macchina virtuale. Di seguito è riportato un esempio di un file di configurazione JSON generato quando si crea un sito Web. La maggior parte dei valori è facilmente comprensibile. Il nome del sito Web viene generato da Azure, pertanto potrebbe non corrispondere al nome del progetto.

```json
{
    "environmentSettings": {
        "webSite": {
            "name": "WebApplication26632",
            "location": "West US"
        },
        "databases": [{
            "connectionStringName": "DefaultConnection",
            "databaseName": "WebApplication26632_db",
            "serverName": "YourDatabaseServerName",
            "user": "sqluser2",
            "password": "",
            "edition": "",
            "size": "",
            "collation": "",
            "location": "West US"
        }]
    }
}
```

Quando si crea una macchina virtuale, il file di configurazione JSON è simile al seguente. Viene creato un servizio cloud come contenitore per la macchina virtuale. La macchina virtuale contiene i consueti endpoint per l'accesso web tramite HTTP e HTTPS, come pure gli endpoint per distribuzione Web, che consente di pubblicare nel sito Web dal computer locale, Desktop remoto e Windows PowerShell.

```json
{
    "environmentSettings": {
        "cloudService": {
            "name": "myusernamevm1",
            "affinityGroup": "",
            "location": "West US",
            "virtualNetwork": "",
            "subnet": "",
            "availabilitySet": "",
            "virtualMachine": {
                "name": "myusernamevm1",
                "vhdImage": "a699494373c04fc0bc8f2bb1389d6106__Win2K8R2SP1-Datacenter-201403.01-en.us-127GB.vhd",
                "size": "Small",
                "user": "vmuser1",
                "password": "",
                "enableWebDeployExtension": true,
                "endpoints": [{
                        "name": "Http",
                        "protocol": "TCP",
                        "publicPort": "80",
                        "privatePort": "80"
                    },
                    {
                        "name": "Https",
                        "protocol": "TCP",
                        "publicPort": "443",
                        "privatePort": "443"
                    },
                    {
                        "name": "WebDeploy",
                        "protocol": "TCP",
                        "publicPort": "8172",
                        "privatePort": "8172"
                    },
                    {
                        "name": "Remote Desktop",
                        "protocol": "TCP",
                        "publicPort": "3389",
                        "privatePort": "3389"
                    },
                    {
                        "name": "Powershell",
                        "protocol": "TCP",
                        "publicPort": "5986",
                        "privatePort": "5986"
                    }
                ]
            }
        },
        "databases": [{
            "connectionStringName": "",
            "databaseName": "",
            "serverName": "",
            "user": "",
            "password": ""
        }],
        "webDeployParameters": {
            "iisWebApplicationName": "Default Web Site"
        }
    }
}
```

È possibile modificare la configurazione JSON per modificare l'operazione eseguita quando si eseguono gli script di pubblicazione. Le sezioni `cloudService` e `virtualMachine` sono necessarie, ma è possibile eliminare la sezione `databases` se non è necessario. Le proprietà che sono vuote nel file di configurazione predefinito generato da Visual Studio sono facoltative, mentre quelle in cui sono presenti valori sono obbligatorie.

Se si dispone di un sito Web che dispone di più ambienti di distribuzione (noti come slot) anziché di un unico sito di produzione in Azure, è possibile includere il nome dello slot nel nome del sito Web nel file di configurazione JSON. Se ad esempio si dispone di un sito Web denominato **mysite** e di uno slot correlato denominato **test**, l'URI corrispondente è `mysite-test.cloudapp.net`, ma il nome corretto da usare nel file di configurazione è mysite(test). È possibile eseguire questo solo se il sito Web e gli slot sono già presenti nella sottoscrizione. Se non sono presenti, creare il sito Web eseguendo lo script senza specificare lo slot, quindi creare lo slot nel [portale di Azure](https://portal.azure.com/) e successivamente eseguire lo script con il nome del sito Web modificato. Per altre informazioni sugli slot di distribuzione per le app Web, vedere [Configurare ambienti di gestione temporanea per le app Web del Servizio app di Azure](/azure/app-service/web-sites-staged-publishing).

## <a name="how-to-run-the-publish-scripts"></a>Come eseguire gli script di pubblicazione

Se non è stato eseguito prima uno script Windows PowerShell, è innanzitutto necessario impostare i criteri di esecuzione per consentire l'esecuzione di script. I criteri costituiscono una funzionalità di sicurezza volta a impedire agli utenti di eseguire script di Windows PowerShell se sono vulnerabili a malware o virus che comportano l'esecuzione di script.

### <a name="run-the-script"></a>Eseguire lo script

1. Creare il pacchetto di distribuzione Web per il progetto. Un pacchetto di distribuzione Web è un archivio compresso (con estensione zip) che contiene i file che si desidera copiare in una macchina virtuale o il sito Web. È possibile creare pacchetti di distribuzione Web in Visual Studio per qualsiasi applicazione web.

   ![Creare pacchetto di distribuzione web](./media/vs-azure-tools-publishing-using-powershell-scripts/IC767885.png)

   Per ulteriori informazioni, vedere [Procedura: Creare un pacchetto di distribuzione Web in Visual Studio](/previous-versions/aspnet/dd465323(v=vs.110)). È anche possibile automatizzare la creazione del pacchetto di Distribuzione Web, come descritto nella sezione [Personalizzazione ed estensione degli script di pubblicazione](#customizing-and-extending-the-publish-scripts).

1. In **Esplora soluzioni** aprire il menu di scelta rapida per lo script e quindi scegliere **Apri con PowerShell ISE**.
1. Se gli script di Windows PowerShell vengono eseguiti su questo computer per la prima volta, aprire una finestra del prompt dei comandi con privilegi di amministratore e digitare il comando seguente:

    ```powershell
    Set-ExecutionPolicy RemoteSigned
    ```

1. Accedere ad Azure usando il comando seguente.

    ```powershell
    Add-AzureAccount
    ```

    Quando richiesto, fornire nome utente e password.

    Osservare come, quando si automatizza lo script, questo metodo di assegnazione delle credenziali di Azure non funzioni. Per l'assegnazione delle credenziali usare invece il file `.publishsettings`. Una sola volta, si usa il comando **Get-AzurePublishSettingsFile** per scaricare il file da Azure e quindi **Import-AzurePublishSettingsFile** per importare il file. Per istruzioni dettagliate, vedere [Come installare e configurare Azure PowerShell](/powershell/azure/overview).

1. (Facoltativo) Se si vuole creare risorse con Azure, ad esempio la macchina virtuale, il database e il sito Web senza pubblicare l'applicazione Web, usare il comando **Publish-WebApplication.ps1** con l'argomento **-Configuration** impostato sul file di configurazione JSON. Questa riga di comando utilizza il file di configurazione JSON per determinare le risorse da creare. Poiché utilizza le impostazioni predefinite per gli altri argomenti della riga di comando, crea le risorse, ma non pubblica l'applicazione web. L’opzione Verbose  fornisce ulteriori informazioni sulle attività in corso.

    ```powershell
    Publish-WebApplication.ps1 -Verbose –Configuration C:\Path\WebProject-WAWS-dev.json
    ```

1. Utilizzare il comando **Pubblica WebApplication.ps1** come indicato in uno dei seguenti esempi per richiamare lo script e pubblicare l'applicazione web. Se è necessario eseguire l'override delle impostazioni predefinite per gli altri argomenti, ad esempio il nome della sottoscrizione, pubblicare il nome del pacchetto, le credenziali di macchina virtuale o le credenziali del server database, è possibile specificare tali parametri. Utilizzare l’opzione **– Verbose** per visualizzare ulteriori informazioni sullo stato di avanzamento del processo di pubblicazione.

    ```powershell
    Publish-WebApplication.ps1 –Configuration C:\Path\WebProject-WAWS-dev-json `
    –SubscriptionName Contoso `
    -WebDeployPackage C:\Documents\Azure\ADWebApp.zip `
    -DatabaseServerPassword @{Name="dbServerName";Password="adminPassword"} `
    -Verbose
    ```

    Se si crea una macchina virtuale, il comando è simile al seguente. In questo esempio viene inoltre illustrato come specificare le credenziali per più database. Per le macchine virtuali create da questi script, il certificato SSL non è da un'autorità radice attendibile. Pertanto, è necessario utilizzare l’opzione **-AllowUntrusted** .

    ```powershell
    Publish-WebApplication.ps1 `
    -Configuration C:\Path\ADVM-VM-test.json `
    -SubscriptionName Contoso `
    -WebDeployPackage C:\Path\ADVM.zip `
    -AllowUntrusted `
    -VMPassword @{name = "vmUserName"; password = "YourPasswordHere"} `
    -DatabaseServerPassword @{Name="server1";Password="adminPassword1"}, @{Name="server2";Password="adminPassword2"} `
    -Verbose
    ```

    Lo script può creare database, ma non crea server di database. Se si desidera creare un server di database, è possibile utilizzare la funzione **New-AzureSqlDatabaseServer** nel modulo di Azure.

## <a name="customizing-and-extending-the-publish-scripts"></a>Personalizzazione ed estensione degli script di pubblicazione

È possibile personalizzare lo script di pubblicazione e i file di configurazione JSON. Le funzioni nel modulo Windows PowerShell **AzureWebAppPublishModule.psm1** non possono essere modificati. Se si desidera specificare un database diverso o modificare alcune delle proprietà della macchina virtuale, modificare il file di configurazione JSON. Se si desidera estendere le funzionalità dello script per automatizzare la compilazione e il test del progetto, è possibile implementare stub di funzioni in **Pubblica WebApplication.ps1**.

Per automatizzare la compilazione del progetto, aggiungere il codice che chiama MSBuild `New-WebDeployPackage` come illustrato nell'esempio di codice. Il percorso del comando MSBuild è diverso a seconda della versione di Visual Studio installata. Per ottenere il percorso corretto, è possibile utilizzare la funzione **Get-msbuildcmd come**, come illustrato nell'esempio seguente.

### <a name="to-automate-building-your-project"></a>Per automatizzare la compilazione del progetto

1. Aggiungere il parametro `$ProjectFile` nella sezione param globale.

    ```powershell
    [Parameter(Mandatory = $false)]
    [ValidateScript({Test-Path $_ -PathType Leaf})]
    [String]
    $ProjectFile,
    ```

1. Copiare la funzione `Get-MSBuildCmd` nel file di script.

    ```powershell
    function Get-MSBuildCmd
    {
            process
    {

                $path =  Get-ChildItem "HKLM:\SOFTWARE\Microsoft\MSBuild\ToolsVersions\" |
                                    Sort-Object {[double]$_.PSChildName} -Descending |
                                    Select-Object -First 1 |
                                    Get-ItemProperty -Name MSBuildToolsPath |
                                    Select -ExpandProperty MSBuildToolsPath

                $path = (Join-Path -Path $path -ChildPath 'msbuild.exe')

            return Get-Item $path
        }
    }
    ```

1. Sostituire `New-WebDeployPackage` con il seguente codice e sostituire i segnaposto per la costruzione di riga `$msbuildCmd`. Questo codice è per Visual Studio 2019. Se si usa Visual Studio 2017, modificare la proprietà **VisualStudioVersion** in `15.0`, '14.0' per Visual Studio 2015 o `12.0` per Visual Studio 2013.

    ```powershell
    function New-WebDeployPackage
    {
        #Write a function to build and package your web application
    ```

    Per compilare l'applicazione Web, usare MsBuild.exe. Per informazioni, vedere informazioni [di MSBuild Command-Line riferimento](../msbuild/msbuild-command-line-reference.md)

    ```powershell
    Write-VerboseWithTime 'Build-WebDeployPackage: Start'

    $msbuildCmd = '"{0}" "{1}" /T:Rebuild;Package /P:VisualStudioVersion=16.0 /p:OutputPath="{2}\MSBuildOutputPath" /flp:logfile=msbuild.log,v=d' -f (Get-MSBuildCmd), $ProjectFile, $scriptDirectory

    Write-VerboseWithTime ('Build-WebDeployPackage: ' + $msbuildCmd)
    ```

### <a name="start-execution-of-the-build-command"></a>Avviare l'esecuzione del comando di compilazione

```powershell
$job = Start-Process cmd.exe -ArgumentList('/C "' + $msbuildCmd + '"') -WindowStyle Normal -Wait -PassThru

if ($job.ExitCode -ne 0) {
    throw('MsBuild exited with an error. ExitCode:' + $job.ExitCode)
}

#Obtain the project name
$projectName = (Get-Item $ProjectFile).BaseName

#Construct the path to web deploy zip package
$DeployPackageDir =  '.\MSBuildOutputPath\_PublishedWebsites\{0}_Package\{0}.zip' -f $projectName

#Get the full path for the web deploy zip package. This is required for MSDeploy to work
$WebDeployPackage = Resolve-Path –LiteralPath $DeployPackageDir

Write-VerboseWithTime 'Build-WebDeployPackage: End'

return $WebDeployPackage
}
```

1. Chiamare la funzione `New-WebDeployPackage` prima di questa riga: `$Config = Read-ConfigFile $Configuration` per le applicazioni web o `$Config = Read-ConfigFile $Configuration -HasWebDeployPackage:([Bool]$WebDeployPackage)` per le macchine virtuali.

    ```powershell
    if($ProjectFile)
    {
    $WebDeployPackage = New-WebDeployPackage
    }
    ```

1. Richiamare uno script personalizzato dalla riga di comando mediante il passaggio dell'argomento `$Project`, come illustrato nell'esempio seguente.

    ```powershell
    .\Publish-WebApplicationVM.ps1 -Configuration .\Configurations\WebApplication5-VM-dev.json `
    -ProjectFile ..\WebApplication5\WebApplication5.csproj `
    -VMPassword @{Name="VMUser";Password="Test.123"} `
    -AllowUntrusted `
    -Verbose
    ```

    Per automatizzare il test dell'applicazione, aggiungere codice al `Test-WebApplication`. Assicurarsi di rimuovere il commento dalle righe in **Pubblica WebApplication.ps1** dove queste funzioni vengono chiamate. Se non si fornisce un'implementazione, è possibile compilare manualmente il progetto con Visual Studio e quindi eseguire lo script per pubblicare in Azure.

## <a name="publishing-function-summary"></a>Riepilogo della funzione di pubblicazione
Per visualizzare la Guida per le funzioni è possibile utilizzare il prompt dei comandi Windows PowerShell, utilizzare il comando `Get-Help function-name`. Nella Guida sono inclusi esempi e informazioni sui parametri. Lo stesso testo della Guida in linea è presente anche nei file di origine script **AzureWebAppPublishModule.psm1** e **Publish-WebApplication.ps1**. Lo script e la Guida si trovano nella lingua di Visual Studio.

**AzureWebAppPublishModule**

| Nome della funzione | Descrizione |
| --- | --- |
| Aggiungere AzureSQLDatabase |Creare un nuovo database SQL di Azure. |
| Aggiungere AzureSQLDatabases |Crea database SQL di Azure da valori nel file di configurazione JSON generato da Visual Studio. |
| Aggiungere-AzureVM |Crea una macchina virtuale di Azure e restituisce l'URL della macchina virtuale distribuita. La funzione imposta i prerequisiti e quindi chiama la funzione **New-AzureVM** (modulo di Azure) per creare una nuova macchina virtuale. |
| Aggiungere AzureVMEndpoints |Aggiunge nuovi endpoint di input a una macchina virtuale e restituisce la macchina virtuale con il nuovo endpoint. |
| Aggiungere AzureVMStorage |Crea un nuovo account di archiviazione di Azure nella sottoscrizione corrente. Il nome dell'account inizia con "devtest" seguito da una stringa alfanumerica univoca. La funzione restituisce il nome del nuovo account di archiviazione. Specificare un percorso o un gruppo di affinità per il nuovo account di archiviazione. |
| Aggiungere-AzureWebsite |Crea un sito Web con nome e percorso specificati. Questa funzione chiama la funzione **New-AzureWebsite** nel modulo di Azure. Se la sottoscrizione non include già un sito Web con il nome specificato, questa funzione crea il sito Web e restituisce un oggetto sito Web. In caso contrario, viene restituito `$null`. |
| Backup-Sottoscrizione |Salva la sottoscrizione di Azure corrente nella variabile `$Script:originalSubscription` nell'ambito dello script. Questa funzione salva nell'ambito dello script la sottoscrizione di Azure corrente, ottenuta da `Get-AzureSubscription -Current`, e il relativo account di archiviazione, nonché la sottoscrizione modificata da questo script, contenuto nella variabile `$UserSpecifiedSubscription`, e il relativo account di archiviazione. Salvando i valori, è possibile usare una funzione, ad esempio `Restore-Subscription`, per ripristinare allo stato corrente la sottoscrizione e l'account di archiviazione corrente originale se è stato modificato lo stato corrente. |
| Trovare-AzureVM |Ottiene la macchina virtuale di Azure specificata. |
| Formato DevTestMessageWithTime |Antepone la data e l’ora a un messaggio. Questa funzione è progettata per i messaggi scritti ai flussi di errore e dettagliati. |
| Get-AzureSQLDatabaseConnectionString |Assembla una stringa di connessione per connettersi a un database SQL di Azure. |
| Get-AzureVMStorage |Restituisce il nome del primo account di archiviazione con il modello di nome "devtest" (senza distinzione tra maiuscole e minuscole) nel percorso o nel gruppo *di affinità specificato. Se l'account di archiviazione "devtest"* non corrisponde al percorso o al gruppo di affinità, la funzione lo ignora. Specificare un percorso o un gruppo di affinità. |
| Get-MSDeployCmd |Restituisce un comando per eseguire lo strumento MsDeploy.exe. |
| Nuovo AzureVMEnvironment |Trova o crea una macchina virtuale nella sottoscrizione che corrisponde ai valori nel file di configurazione JSON. |
| Pubblicare-WebPackage |Utilizza MsDeploy.exe e un file Zip del pacchetto di pubblicazione web per distribuire le risorse a un sito Web. Questa funzione non genera alcun output. Se la chiamata a MSDeploy.exe non riesce, la funzione genera un'eccezione. Per ottenere un output più dettagliato, utilizzare l’opzione **-Verbose** . |
| Pubblicar-WebPackageToVM |Verifica i valori di parametro e chiama quindi la funzione **Publish-WebPackage** . |
| Leggere-configFile |Convalida il file di configurazione JSON e restituisce una tabella hash di valori selezionati. |
| Ripristina-Subscription |Reimposta la sottoscrizione corrente a quella originale. |
| Test-AzureModule |Restituisce `$true` se la versione del modulo Azure installata è 0.7.4 o successiva. Restituisce `$false` Se il modulo non è installato o è una versione precedente. Questa funzione non ha parametri. |
| Test-AzureModuleVersion |Restituisce `$true` se la versione del modulo Azure è 0.7.4 o successiva. Restituisce `$false` Se il modulo non è installato o è una versione precedente. Questa funzione non ha parametri. |
| Test-HttpsUrl |Converte l'URL di input in un oggetto System. Uri. Restituisce `$True` se l'URL è assoluto e il relativo schema è https. Restituisce `$false` se l'URL è relativo, lo schema non è HTTPS o la stringa di input non può essere convertita in un URL. |
| Test- Member |Restituisce `$true` se una proprietà o metodo è un membro dell'oggetto. In caso contrario, restituisce `$false`. |
| Scrivere-ErrorWithTime |Scrive un messaggio di errore prefisso con l'ora corrente. Questa funzione chiama la funzione **Format-DevTestMessageWithTime** per anteporre il tempo prima della scrittura del messaggio per il flusso di errore. |
| Scrivere-HostWithTime |Scrive un messaggio nel programma host (**Write-Host**) prestabilito con l'ora corrente. L'effetto della scrittura nel programma host varia. La maggior parte dei programmi che ospitano Windows PowerShell scrive questi messaggi nell'output standard. |
| Scrivere-VerboseWithTime |Scrive un messaggio dettagliato con l'ora corrente. Poiché chiama **Write-Verbose**, il messaggio viene visualizzato solo quando lo script viene eseguito con il parametro **Verbose** o quando la preferenza **VerbosePreference** è impostata su **Continua**. |

**Pubblicare-WebApplication**

| Nome della funzione | Descrizione |
| --- | --- |
| Nuovo-AzureWebApplicationEnvironment |Crea risorse di Azure, ad esempio una macchina virtuale o un sito Web. |
| Nuovo-WebDeployPackage |Questa funzione non è implementata. È possibile aggiungere comandi in questa funzione per compilare il progetto. |
| Pubblicare-AzureWebApplication |Pubblicare un'applicazione Web in Azure |
| Pubblicare-WebApplication |Crea e distribuisce le app Web, le macchine virtuali, i database SQL e gli account di archiviazione per un progetto web Visual Studio. |
| Test-WebApplication |Questa funzione non è implementata. È possibile aggiungere comandi in questa funzione per testare l’applicazione. |

## <a name="next-steps"></a>Passaggi successivi
Per altre informazioni sulla creazione di script PowerShell, leggere [Scripting con Windows PowerShell](/powershell/scripting/overview) e vedere gli altri script di Azure PowerShell nello [Script Center](https://azure.microsoft.com/documentation/scripts/).