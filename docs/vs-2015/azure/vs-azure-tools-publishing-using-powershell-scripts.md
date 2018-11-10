---
title: Uso degli script di PowerShell di Windows per la pubblicazione in ambienti di Test e sviluppo | Microsoft Docs
description: Informazioni su come usare gli script di Windows PowerShell da Visual Studio per pubblicare allo sviluppo e ambienti di test.
author: ghogen
manager: douge
assetId: 5fff1301-5469-4d97-be88-c85c30f837c1
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2016
ms.author: ghogen
ms.openlocfilehash: 9d0142c52fbe40256fc0ab6ec0d5d9fdade243b7
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002720"
---
# <a name="using-windows-powershell-scripts-to-publish-to-dev-and-test-environments"></a>Uso degli script di Windows PowerShell per la pubblicazione in ambienti di sviluppo e test

Quando si crea un'applicazione web in Visual Studio, è possibile generare uno script di Windows PowerShell che è possibile usare in un secondo momento per automatizzare la pubblicazione del sito Web in Azure come App Web nel servizio App di Azure o una macchina virtuale. È possibile modificare ed estendere lo script di Windows PowerShell nell'editor di Visual Studio in base alle proprie esigenze oppure integrare lo script di compilazione esistente, test e pubblicazione di script.

Utilizzando questi script, è possibile eseguire il provisioning (noto anche come ambienti di sviluppo e test) di versioni personalizzate del sito per un utilizzo temporaneo. Ad esempio, potrebbe configurare una particolare versione del sito Web in una macchina virtuale di Azure o nello slot di staging in un sito Web per eseguire un gruppo di test, riprodurre un bug, testare una correzione di bug, valutare una modifica proposta o configurare un ambiente personalizzato per una demo o una presentazione. Dopo aver creato uno script che pubblica il progetto, è possibile ricreare ambienti identici eseguendo nuovamente lo script in base alle esigenze o eseguire lo script con la build dell'applicazione web per creare un ambiente di test personalizzato.

## <a name="prerequisites"></a>Prerequisiti

* Azure SDK 2.3 o versione successiva. Visualizzare [download di Visual Studio](http://go.microsoft.com/fwlink/?LinkID=624384). (Non è necessario Azure SDK per generare script per i progetti web. Questa funzione è per i progetti web, non i ruoli web nei servizi cloud).
* Azure PowerShell 0.7.4 o versione successiva. Visualizzare [come installare e configurare Azure PowerShell](/powershell/azure/overview).
* [Windows PowerShell 3.0](http://go.microsoft.com/?linkid=9811175) o versione successiva.

## <a name="additional-tools"></a>Altri strumenti

Sono disponibili altri strumenti e risorse per l'uso di PowerShell in Visual Studio per lo sviluppo di Azure. Visualizzare [PowerShell Tools per Visual Studio](http://go.microsoft.com/fwlink/?LinkId=404012).

## <a name="generating-the-publish-scripts"></a>Generare script di pubblicazione

È possibile generare gli script di pubblicazione per una macchina virtuale che ospita il sito Web quando si crea un nuovo progetto seguendo [queste istruzioni](/azure/virtual-machines/windows/classic/web-app-visual-studio.md?toc=%2fazure%2fvirtual-machines%2fwindows%2fclassic%2ftoc.json). È anche possibile [generare script di pubblicazione per le app web in servizio App di Azure](/azure/app-service/scripts/app-service-powershell-deploy-github).

## <a name="scripts-that-visual-studio-generates"></a>Script generato da Visual Studio

Visual Studio genera una cartella a livello di soluzione denominata **PublishScripts** che contiene due file di Windows PowerShell, uno script di pubblicazione per la macchina virtuale o sito Web e un modulo che contiene funzioni che è possibile utilizzare il inserisce nello script. Visual Studio genera inoltre un file in formato JSON che specifica i dettagli del progetto che si sta distribuendo.

### <a name="windows-powershell-publish-script"></a>Script di pubblicazione di Windows PowerShell

Lo script di pubblicazione contiene specifici passaggi di pubblicazione per la distribuzione in una macchina virtuale o un sito Web. Visual Studio offre colorazione della sintassi per lo sviluppo di Windows PowerShell. La Guida per le funzioni è disponibile e si possono modificare liberamente le funzioni nello script per soddisfare mutevoli esigenze specifiche.

### <a name="windows-powershell-module"></a>Modulo Windows PowerShell

Il modulo Windows PowerShell generato da Visual Studio contiene funzioni che usa lo script di pubblicazione. Queste funzioni di Azure PowerShell non sono destinate a essere modificato. Visualizzare [come installare e configurare Azure PowerShell](/powershell/azure/overview).

### <a name="json-configuration-file"></a>File di configurazione JSON

Il file JSON viene creato nel **configurazioni** cartella e contiene i dati di configurazione che specifica le risorse esatte da distribuire in Azure. Il nome del file generato da Visual Studio è project-name-WAWS-DEV. JSON se è stato creato un sito Web o progetto nome-VM-DEV. JSON se è stata creata una macchina virtuale. Ecco un esempio di un file di configurazione JSON generato quando si crea un sito Web. La maggior parte dei valori è facilmente comprensibile. Il nome del sito Web viene generato da Azure, pertanto potrebbe non corrispondere al nome del progetto.

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

Quando si crea una macchina virtuale, il file di configurazione JSON è simile al seguente. Viene creato un servizio cloud come contenitore per la macchina virtuale. La macchina virtuale contiene i consueti endpoint per l'accesso al web tramite HTTP e HTTPS, come pure gli endpoint per distribuzione Web, che consente di pubblicare il sito Web dal computer locale, Desktop remoto e Windows PowerShell.

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

È possibile modificare la configurazione JSON per cambiare cosa accade quando si eseguono gli script di pubblicazione. Il `cloudService` e `virtualMachine` le sezioni sono obbligatorie, ma è possibile eliminare il `databases` sezione se non è necessario. Le proprietà che sono vuote nel file di configurazione predefinito generato da Visual Studio sono facoltative. le proprietà con i valori nel file di configurazione predefinite sono necessarie.

Se si dispone di un sito Web che dispone di più ambienti di distribuzione (noti come slot) anziché un unico sito di produzione in Azure, è possibile includere il nome dello slot nel nome del sito Web nel file di configurazione JSON. Ad esempio, se si dispone di un sito Web denominato **mysite** e uno slot denominato **testare** l'URI è `mysite-test.cloudapp.net`, ma il nome corretto da usare nel file di configurazione è MySite (test). È possibile eseguire questo solo se il sito Web e slot è già presente nella sottoscrizione. Se non sono presenti, creare il sito Web eseguendo lo script senza specificare lo slot, quindi creare lo slot nel [portale di Azure](https://portal.azure.com/), e successivamente eseguire lo script con il nome di sito Web modificato. Per altre informazioni sugli slot di distribuzione per le app web, vedere [configurare ambienti di staging per le app web nel servizio App di Azure](/azure/app-service/web-sites-staged-publishing).

## <a name="how-to-run-the-publish-scripts"></a>Come eseguire gli script di pubblicazione

Se è mai stato eseguito uno script di Windows PowerShell prima di, è innanzitutto necessario impostare i criteri di esecuzione per consentire l'esecuzione di script. I criteri sono una funzionalità di sicurezza per impedire agli utenti di eseguire gli script di Windows PowerShell se sono vulnerabili a malware o virus che comportano l'esecuzione di script.

### <a name="run-the-script"></a>Eseguire lo script

1. Creare il pacchetto di distribuzione Web per il progetto. Un pacchetto di distribuzione Web è un archivio compresso (con estensione zip) che contengono i file che si desidera copiare in una macchina virtuale o nel sito Web. È possibile creare pacchetti di distribuzione Web in Visual Studio per qualsiasi applicazione web.

   ![Creazione di Web Distribuisci pacchetto](./media/vs-azure-tools-publishing-using-powershell-scripts/IC767885.png)

   Per altre informazioni, vedere [procedura: creare un pacchetto di distribuzione Web in Visual Studio](https://msdn.microsoft.com/library/dd465323.aspx). È anche possibile automatizzare la creazione del pacchetto di distribuzione Web, come descritto in [personalizzazione ed estensione degli script di pubblicazione](#customizing-and-extending-publish-scripts).

1. Nelle **Esplora soluzioni**, aprire il menu di scelta rapida per lo script e quindi scegliere **Apri con PowerShell ISE**.
1. Se l'esecuzione di script di Windows PowerShell nel computer per la prima volta, aprire una finestra del prompt dei comandi con privilegi di amministratore e digitare il comando seguente:

    ```powershell
    Set-ExecutionPolicy RemoteSigned
    ```

1. Accedere ad Azure usando il comando seguente.

    ```powershell
    Add-AzureAccount
    ```

    Quando richiesto, specificare il nome utente e password.

    Si noti che quando si automatizza lo script, questo metodo per fornire le credenziali di Azure non funziona. È necessario utilizzare invece il `.publishsettings` file per fornire le credenziali. Una volta, è sufficiente usare il comando **Get-AzurePublishSettingsFile** per scaricare il file di Azure e successivamente usare **Import-AzurePublishSettingsFile** per importare il file. Per istruzioni dettagliate, vedere [come installare e configurare Azure PowerShell](/powershell/azure/overview).

1. (Facoltativo) Se si desidera creare le risorse di Azure, ad esempio la macchina virtuale, il database e siti Web senza pubblicare l'applicazione web, usare il **Publish-WebApplication.ps1** con il **-Configuration**argomento impostato per il file di configurazione JSON. Questa riga di comando Usa il file di configurazione JSON per determinare le risorse da creare. Perché Usa le impostazioni predefinite per gli altri argomenti della riga di comando, crea le risorse, ma non pubblicare l'applicazione web. – Verbose opzione offre altre informazioni sulle attività in corso.

    ```powershell
    Publish-WebApplication.ps1 -Verbose –Configuration C:\Path\WebProject-WAWS-dev.json
    ```

1. Usare la **Publish-WebApplication.ps1** seguente come mostrato in uno dei seguenti esempi per richiamare lo script e pubblicare l'applicazione web. Se è necessario eseguire l'override le impostazioni predefinite per uno qualsiasi degli altri argomenti, ad esempio il nome della sottoscrizione, nome del pacchetto, le credenziali della macchina virtuale o le credenziali del server database di pubblicazione, è possibile specificare tali parametri. Usare la **– Verbose** opzione per visualizzare altre informazioni sullo stato di avanzamento del processo di pubblicazione.

    ```powershell
    Publish-WebApplication.ps1 –Configuration C:\Path\WebProject-WAWS-dev-json `
    –SubscriptionName Contoso `
    -WebDeployPackage C:\Documents\Azure\ADWebApp.zip `
    -DatabaseServerPassword @{Name="dbServerName";Password="adminPassword"} `
    -Verbose
    ```

    Se si crea una macchina virtuale, il comando simile al seguente. In questo esempio viene inoltre illustrato come specificare le credenziali per più database. Per le macchine virtuali create da questi script, il certificato SSL non da un'autorità radice attendibile. Pertanto, è necessario usare il **-AllowUntrusted** opzione.

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

    Lo script può creare database, ma non determina la creazione di server di database. Se si desidera creare un server di database, è possibile usare la **New-AzureSqlDatabaseServer** funzione nel modulo di Azure.

## <a name="customizing-and-extending-the-publish-scripts"></a>Personalizzazione ed estensione degli script di pubblicazione

È possibile personalizzare lo script di pubblicazione e i file di configurazione JSON. Le funzioni nel modulo Windows PowerShell **AzureWebAppPublishModule.psm1** non possono essere modificati. Se si desidera semplicemente specificare un database diverso o modificare alcune delle proprietà della macchina virtuale, modificare il file di configurazione JSON. Se si desidera estendere le funzionalità dello script per automatizzare la compilazione e test del progetto, è possibile implementare stub di funzioni in **Publish-WebApplication.ps1**.

Per automatizzare la compilazione del progetto, aggiungere il codice che chiama MSBuild `New-WebDeployPackage` come illustrato nell'esempio di codice. Il percorso del comando MSBuild è diverso a seconda della versione di Visual Studio installata. Per ottenere il percorso corretto, è possibile usare la funzione **Get-msbuildcmd come**, come illustrato in questo esempio.

### <a name="to-automate-building-your-project"></a>Per automatizzare la compilazione del progetto

1. Aggiungere il `$ProjectFile` parametro nella sezione param globale.

    ```powershell
    [Parameter(Mandatory = $false)]
    [ValidateScript({Test-Path $_ -PathType Leaf})]
    [String]
    $ProjectFile,
    ```

1. La funzione Copy `Get-MSBuildCmd` nel file di script.

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

1. Sostituire `New-WebDeployPackage` con il codice seguente e sostituire i segnaposto la costruzione di riga `$msbuildCmd`. Questo codice è per Visual Studio 2015. Se si usa Visual Studio 2017, modificare il **VisualStudioVersion** proprietà `15.0` (`12.0` per Visual Studio 2013).

    ```powershell
    function New-WebDeployPackage
    {
        #Write a function to build and package your web application
    ```

    Per compilare l'applicazione web, usare MsBuild.exe. Per altre informazioni, vedere Riferimenti alla riga di comando di MSBuild in: [http://go.microsoft.com/fwlink/?LinkId=391339](http://go.microsoft.com/fwlink/?LinkId=391339)

    ```powershell
    Write-VerboseWithTime 'Build-WebDeployPackage: Start'

    $msbuildCmd = '"{0}" "{1}" /T:Rebuild;Package /P:VisualStudioVersion=14.0 /p:OutputPath="{2}\MSBuildOutputPath" /flp:logfile=msbuild.log,v=d' -f (Get-MSBuildCmd), $ProjectFile, $scriptDirectory

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

1. Chiamare il `New-WebDeployPackage` funzione prima di questa riga: `$Config = Read-ConfigFile $Configuration` per le app web o `$Config = Read-ConfigFile $Configuration -HasWebDeployPackage:([Bool]$WebDeployPackage)` per le macchine virtuali.

    ```powershell
    if($ProjectFile)
    {
    $WebDeployPackage = New-WebDeployPackage
    }
    ```

1. Richiamare uno script personalizzato dalla riga di comando mediante il passaggio di `$Project` argomento, come nell'esempio seguente:

    ```powershell
    .\Publish-WebApplicationVM.ps1 -Configuration .\Configurations\WebApplication5-VM-dev.json `
    -ProjectFile ..\WebApplication5\WebApplication5.csproj `
    -VMPassword @{Name="VMUser";Password="Test.123"} `
    -AllowUntrusted `
    -Verbose
    ```

    Per automatizzare il test dell'applicazione, aggiungere codice al `Test-WebApplication`. Assicurarsi di rimuovere il commento le righe nel **Publish-WebApplication.ps1** dove queste funzioni vengono chiamate. Se non si fornisce un'implementazione, è possibile creare manualmente il progetto con Visual Studio e quindi eseguire lo script di pubblicazione per la pubblicazione in Azure.

## <a name="publishing-function-summary"></a>Riepilogo della funzione di pubblicazione
Per ottenere assistenza per le funzioni è possibile usare al prompt dei comandi Windows PowerShell, usare il comando `Get-Help function-name`. La Guida include esempi e informazioni sui parametri. Lo stesso testo della Guida in linea è anche nel file di origine script **AzureWebAppPublishModule.psm1** e **Publish-WebApplication.ps1**. Lo script e della Guida è localizzata nel tuo linguaggio di Visual Studio.

**AzureWebAppPublishModule**

| Nome funzione | Descrizione |
| --- | --- |
| Add-AzureSQLDatabase |Crea un nuovo database SQL di Azure. |
| Add-AzureSQLDatabases |Crea database SQL di Azure dai valori nel file di configurazione JSON generato da Visual Studio. |
| Add-AzureVM |Crea una macchina virtuale di Azure e restituisce l'URL della macchina virtuale distribuita. La funzione imposta i prerequisiti e quindi chiama il **New-AzureVM** funzione (modulo Azure) per creare una nuova macchina virtuale. |
| Add-AzureVMEndpoints |Aggiunge nuovi endpoint di input a una macchina virtuale e restituisce la macchina virtuale con il nuovo endpoint. |
| Add-AzureVMStorage |Crea un nuovo account di archiviazione di Azure nella sottoscrizione corrente. Il nome dell'account inizia con "devtest" seguito da una stringa alfanumerica univoca. La funzione restituisce il nome del nuovo account di archiviazione. Specificare un percorso o un gruppo di affinità per il nuovo account di archiviazione. |
| Add-AzureWebsite |Crea un sito Web con il nome e percorso specificati. Questa funzione chiama il **New-AzureWebsite** funzione nel modulo di Azure. Se la sottoscrizione non include già un sito Web con il nome specificato, questa funzione crea il sito Web e restituisce un oggetto sito Web. In caso contrario restituirà `$null`. |
| Backup-Subscription |Salva la sottoscrizione Azure corrente nella `$Script:originalSubscription` variabili nell'ambito dello script. Questa funzione Salva la sottoscrizione Azure corrente (ottenuta da `Get-AzureSubscription -Current`) e il relativo account di archiviazione e la sottoscrizione modificata dallo script (archiviata nella variabile `$UserSpecifiedSubscription`) e il relativo account di archiviazione, nell'ambito dello script. Salvando i valori, è possibile usare una funzione, ad esempio `Restore-Subscription`, per ripristinare lo stato corrente account di sottoscrizione e di archiviazione corrente originale se è stato modificato lo stato corrente. |
| Find-AzureVM |Ottiene la macchina virtuale di Azure specificata. |
| Format-DevTestMessageWithTime |Antepone la data e ora a un messaggio. Questa funzione è progettata per i messaggi scritti ai flussi di errore e dettagliati. |
| Get-AzureSQLDatabaseConnectionString |Assembla una stringa di connessione per connettersi a un database SQL di Azure. |
| Get-AzureVMStorage |Restituisce il nome del primo account di archiviazione con il modello di nome "devtest *" (maiuscole e minuscole) nel percorso specificato o nel gruppo di affinità. Se la "devtest*" account di archiviazione non corrisponde alla posizione o un gruppo di affinità, la funzione lo ignora. Specificare un percorso o un gruppo di affinità. |
| Get-MSDeployCmd |Restituisce un comando per eseguire lo strumento MsDeploy.exe. |
| New-AzureVMEnvironment |Trova o crea una macchina virtuale nella sottoscrizione che corrisponde ai valori nel file di configurazione JSON. |
| Publish-WebPackage |MsDeploy.exe utilizza e una web di pubblicazione del pacchetto. File ZIP per distribuire risorse in un sito Web. Questa funzione non genera alcun output. Se la chiamata a MSDeploy.exe non riesce, la funzione genera un'eccezione. Per ottenere un output più dettagliato, usare il **-Verbose** opzione. |
| Publish-WebPackageToVM |Verifica i valori dei parametri e quindi chiama il **Publish-WebPackage** (funzione). |
| Read-ConfigFile |Convalida il file di configurazione JSON e restituisce una tabella hash di valori selezionati. |
| Restore-Subscription |Reimposta la sottoscrizione corrente a quella originale. |
| Test-AzureModule |Restituisce `$true` se la versione del modulo Azure installato è 0.7.4 o versione successiva. Restituisce `$false` se il modulo non è installato o è una versione precedente. Questa funzione non ha parametri. |
| Test-AzureModuleVersion |Restituisce `$true` se la versione del modulo Azure è 0.7.4 o versione successiva. Restituisce `$false` se il modulo non è installato o è una versione precedente. Questa funzione non ha parametri. |
| Test-HttpsUrl |Converte l'URL di input in un oggetto System. Uri. Restituisce `$True` se l'URL è assoluto e relativo schema è https. Restituisce `$false` se l'URL è relativo, lo schema non è HTTPS o la stringa di input non può essere convertita in un URL. |
| Membro di test |Restituisce `$true` se una proprietà o metodo è un membro dell'oggetto. In caso contrario, restituisce `$false`. |
| Scrittura ErrorWithTime |Scrive un messaggio di errore con preceduto con l'ora corrente. Questa funzione chiama il **Format-DevTestMessageWithTime** per anteporre il tempo prima della scrittura del messaggio per il flusso di errore. |
| Scrittura HostWithTime |Scrive un messaggio nel programma host (**Write-Host**) con prefisso con l'ora corrente. L'effetto della scrittura nel programma host varia. La maggior parte dei programmi che ospitano Windows PowerShell scrive questi messaggi nell'output standard. |
| Scrittura VerboseWithTime |Scrive un messaggio dettagliato con l'ora corrente. Poiché chiama **Write-Verbose**, viene visualizzato il messaggio solo quando lo script viene eseguito con il **Verbose** parametro o quando il **VerbosePreference** preferenza è impostata su  **Continuare**. |

**Pubblicare-WebApplication**

| Nome funzione | Descrizione |
| --- | --- |
| Nuovo AzureWebApplicationEnvironment |Crea risorse di Azure, ad esempio una macchina virtuale o un sito Web. |
| Nuovo WebDeployPackage |Questa funzione non è implementata. È possibile aggiungere comandi in questa funzione per compilare il progetto. |
| AzureWebApplication pubblicare |Pubblica un'applicazione web in Azure. |
| Pubblicare-WebApplication |Crea e distribuisce le app Web, macchine virtuali, database SQL e gli account di archiviazione per un progetto web Visual Studio. |
| Test-WebApplication |Questa funzione non è implementata. È possibile aggiungere comandi in questa funzione per testare l'applicazione. |

## <a name="next-steps"></a>Passaggi successivi
Altre informazioni sugli script di PowerShell, leggere [Scripting con Windows PowerShell](https://technet.microsoft.com/library/bb978526.aspx) e vedere altri script di Azure PowerShell nel [Script Center](https://azure.microsoft.com/documentation/scripts/).
