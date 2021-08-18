---
title: Compilazione ClickOnce applicazioni dalla riga di comando | Microsoft Docs
description: Informazioni su come compilare Visual Studio dalla riga di comando, che consente di riprodurre una compilazione usando un processo automatizzato.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, from command line
- publishing
- publishing, ClickOnce
ms.assetid: d9bc6212-c584-4f72-88c9-9a4b998c555e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 6bb7d455bf85ef9ba1776956330ac217b73cd2dd
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122160907"
---
# <a name="build-clickonce-applications-from-the-command-line"></a>Compilare applicazioni ClickOnce dalla riga di comando

In è possibile compilare progetti dalla riga di comando, anche se vengono [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] creati nell'ambiente di sviluppo integrato (IDE). In realtà, è possibile ricompilare un progetto creato con in un altro computer in cui è installato [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] solo il .NET Framework. In questo modo è possibile riprodurre una compilazione usando un processo automatizzato, ad esempio in un lab di compilazione centrale o usando tecniche di scripting avanzate che esemplino l'ambito di compilazione del progetto stesso.

## <a name="use-msbuild-to-reproduce-net-framework-clickonce-application-deployments"></a>Usare MSBuild per riprodurre .NET Framework ClickOnce di applicazioni

 Quando si richiama msbuild /target:publish dalla riga di comando, indica al sistema MSBuild di compilare il progetto e creare un'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nella cartella di pubblicazione. Equivale a selezionare il **comando Pubblica** nell'IDE.

 Questo comando esegue *msbuild.exe*, che si trova nel percorso nell'Visual Studio del prompt dei comandi.

 Una "destinazione" è un indicatore per MSBuild su come elaborare il comando. Le destinazioni principali sono la destinazione "build" e la destinazione "publish". La destinazione di compilazione equivale a selezionare il comando Compila (o premere F5) nell'IDE. Se si vuole solo compilare il progetto, è possibile ottenere questo risultato digitando `msbuild` . Questo comando funziona perché la destinazione di compilazione è la destinazione predefinita per tutti i progetti generati da [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] . Ciò significa che non è necessario specificare in modo esplicito la destinazione di compilazione. Di conseguenza, la `msbuild` digitazione è la stessa operazione della digitazione `msbuild /target:build` di .

 Il `/target:publish` comando indica MSBuild richiamare la destinazione di pubblicazione. La destinazione di pubblicazione dipende dalla destinazione di compilazione. Ciò significa che l'operazione di pubblicazione è un superset dell'operazione di compilazione. Ad esempio, se è stata apportata una modifica a uno dei file di origine Visual Basic o C#, l'assembly corrispondente verrà ricompilato automaticamente dall'operazione di pubblicazione.

 Per informazioni sulla generazione di una distribuzione completa usando lo strumento Mage.exe della riga di comando per creare il manifesto, vedere Procedura dettagliata: Distribuire manualmente [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] un'applicazione ClickOnce distribuzione [.](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)

## <a name="create-and-build-a-basic-clickonce-application-with-msbuild"></a>Creare e compilare un'ClickOnce di base con MSBuild

### <a name="to-create-and-publish-a-clickonce-project"></a>Per creare e pubblicare un ClickOnce progetto

1. Aprire Visual Studio e creare un nuovo progetto.

    Scegliere il **modello Windows progetto Applicazione desktop** e assegnare al progetto il nome `CmdLineDemo` .

1. Scegliere il **comando** Pubblica **dal** menu Compila.

    Questo passaggio garantisce che il progetto sia configurato correttamente per produrre una distribuzione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dell'applicazione.

    Verrà visualizzata la Pubblicazione guidata.

1. Nella Pubblicazione guidata fare clic su **Fine.**

    Visual Studio genera e visualizza la pagina Web predefinita, denominata *Publish.htm*.

1. Salvare il progetto e prendere nota del percorso della cartella in cui è archiviato.

   I passaggi precedenti creano [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] un progetto che è stato pubblicato per la prima volta. È ora possibile riprodurre la compilazione all'esterno dell'IDE.

#### <a name="to-reproduce-the-build-from-the-command-line"></a>Per riprodurre la compilazione dalla riga di comando

1. Chiudere [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].

2. Dal menu Windows **Start** fare clic su Tutti i programmi **,** **quindi** Microsoft Visual Studio , Strumenti di Visual Studio **,** quindi Visual Studio prompt dei **comandi**. Verrà aperto un prompt dei comandi nella cartella radice dell'utente corrente.

3. Nel **prompt Visual Studio comando** modificare la directory corrente nel percorso del progetto appena compilato in precedenza. Ad esempio digitare `chdir My Documents\Visual Studio\Projects\CmdLineDemo`.

4. Per rimuovere i file esistenti prodotti in "Per creare e pubblicare un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] progetto", digitare `rmdir /s publish` .

    Questo passaggio è facoltativo, ma garantisce che i nuovi file siano stati tutti prodotti dalla compilazione della riga di comando.

5. Digitare `msbuild /target:publish`.

   I passaggi precedenti produrranno una distribuzione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] completa dell'applicazione in una sottocartella del progetto denominata **Publish**. *CmdLineDemo.application è* il manifesto [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] della distribuzione. La cartella *CmdLineDemo_1.0.0.0 contiene* i file *CmdLineDemo.exe* *eCmdLineDemo.exe.manifest*, il manifesto [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dell'applicazione. *Setup.exe* è il programma di avvio automatico, che per impostazione predefinita è configurato per installare il .NET Framework. La cartella DotNetFX contiene i componenti ridistribuibili per il .NET Framework. Si tratta dell'intero set di file necessari per distribuire l'applicazione sul Web o tramite UNC o CD/DVD.

> [!NOTE]
> Il MSBuild usa **l'opzione PublishDir** per specificare il percorso per l'output, ad esempio `msbuild /t:publish /p:PublishDir="<specific location>"` .

::: moniker range=">=vs-2019"

## <a name="build-net-clickonce-applications-from-the-command-line"></a>Compilare applicazioni .NET ClickOnce dalla riga di comando

La compilazione di applicazioni .NET ClickOnce dalla riga di comando è un'esperienza simile, ad eccezione del fatto che è necessario fornire una proprietà aggiuntiva per il profilo di pubblicazione MSBuild riga di comando. Il modo più semplice per creare un profilo di pubblicazione è usare Visual Studio.  Per altre informazioni, vedere Deploy [a .NET Windows application using ClickOnce](quickstart-deploy-using-clickonce-folder.md) (Distribuire un'applicazione Windows .NET ClickOnce per altre informazioni.

Dopo aver creato il profilo di pubblicazione, è possibile specificare il file pubxml come proprietà nella riga di comando di msbuild. Esempio:

```cmd
    msbuild /t:publish /p:PublishProfile=<pubxml file> /p:PublishDir="<specific location>"
```
::: moniker-end

## <a name="publish-properties"></a>Pubblica proprietà

 Quando si pubblica l'applicazione nelle procedure precedenti, le proprietà seguenti vengono inserite nel file di progetto dalla Pubblicazione guidata o nel file del profilo di pubblicazione per i progetti .NET Core 3.1 o versioni successive. Queste proprietà influiscono direttamente sul modo [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] in cui viene prodotta l'applicazione.

 In *CmdLineDemo.vbproj*  /  *CmdLineDemo.csproj*:

```xml
<AssemblyOriginatorKeyFile>WindowsApplication3.snk</AssemblyOriginatorKeyFile>
<GenerateManifests>true</GenerateManifests>
<TargetZone>LocalIntranet</TargetZone>
<PublisherName>Microsoft</PublisherName>
<ProductName>CmdLineDemo</ProductName>
<PublishUrl>http://localhost/CmdLineDemo</PublishUrl>
<Install>true</Install>
<ApplicationVersion>1.0.0.*</ApplicationVersion>
<ApplicationRevision>1</ApplicationRevision>
<UpdateEnabled>true</UpdateEnabled>
<UpdateRequired>false</UpdateRequired>
<UpdateMode>Foreground</UpdateMode>
<UpdateInterval>7</UpdateInterval>
<UpdateIntervalUnits>Days</UpdateIntervalUnits>
<UpdateUrlEnabled>false</UpdateUrlEnabled>
<IsWebBootstrapper>true</IsWebBootstrapper>
<BootstrapperEnabled>true</BootstrapperEnabled>
```

 Per .NET Framework, è possibile eseguire l'override di una di queste proprietà dalla riga di comando senza modificare il file di progetto stesso. Ad esempio, di seguito viene compilata la distribuzione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dell'applicazione senza il programma di avvio automatico:

```cmd
msbuild /target:publish /property:BootstrapperEnabled=false
 ```

::: moniker range=">=vs-2019"
Per i progetti .NET Core 3.1 o versioni successive, queste impostazioni vengono fornite nel file pubxml.

 Le proprietà di pubblicazione vengono controllate nelle pagine delle proprietà [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **Pubblica,** **Sicurezza** e Firma di **Project Designer**.  Di seguito è riportata una descrizione delle proprietà di pubblicazione, insieme a un'indicazione della modalità di impostazione di ognuna nelle diverse pagine delle proprietà di Progettazione applicazioni:

> [!NOTE]
> Per i progetti desktop Windows .NET, queste impostazioni sono ora disponibili nella Pubblicazione guidata
::: moniker-end

- `AssemblyOriginatorKeyFile` determina il file di chiave usato per firmare i [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifesti dell'applicazione. Questa stessa chiave può essere usata anche per assegnare un nome sicuro agli assembly. Questa proprietà viene impostata nella **pagina Firma** di Progettazione **Project .**
::: moniker range=">=vs-2019"
Per le applicazioni windows .NET, questa impostazione rimane nel file di progetto
::: moniker-end

  Nella pagina Sicurezza vengono impostate **le proprietà** seguenti:

- **Abilita ClickOnce sicurezza Impostazioni** determina se [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] vengono generati manifesti. Quando un progetto viene creato inizialmente, la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] generazione del manifesto è disattivata per impostazione predefinita. La procedura guidata attiva automaticamente questo flag quando si esegue la pubblicazione per la prima volta.

- **TargetZone** determina il livello di attendibilità da emettere nel manifesto [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dell'applicazione. I valori possibili sono "Internet", "LocalIntranet" e "Custom". Internet e LocalIntranet causeranno la generazione di un set di autorizzazioni predefinito nel manifesto [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dell'applicazione. LocalIntranet è l'impostazione predefinita e significa fondamentalmente attendibilità totale. Custom specifica che nel manifesto dell'applicazione devono essere generate solo le autorizzazioni specificate in modo esplicito nel file *app.manifest* [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] di base. Il *file app.manifest* è un file manifesto parziale che contiene solo le definizioni delle informazioni sull'attendibilità. Si tratta di un file nascosto, aggiunto automaticamente al progetto quando si configurano le autorizzazioni nella **pagina** Sicurezza.
-
::: moniker range=">=vs-2019"
> [!NOTE]
> Per .NET Core 3.1 o versioni successive, Windows desktop, queste impostazioni di sicurezza non sono supportate.
::: moniker-end

  Nella pagina Pubblica vengono impostate **le proprietà** seguenti:

- `PublishUrl` è il percorso in cui verrà pubblicata l'applicazione nell'IDE. Viene inserito nel manifesto [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dell'applicazione se non viene specificata `InstallUrl` la proprietà o `UpdateUrl` .

- `ApplicationVersion` specifica la versione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dell'applicazione. Si tratta di un numero di versione a quattro cifre. Se l'ultima cifra è "*", viene sostituito il valore inserito nel `ApplicationRevision` manifesto in fase di compilazione.

- `ApplicationRevision` specifica la revisione. Si tratta di un numero intero che viene incrementato ogni volta che si pubblica nell'IDE. Si noti che non viene incrementato automaticamente per le compilazioni eseguite nella riga di comando.

- `Install` determina se l'applicazione è un'applicazione installata o un'applicazione run-from-Web.

- `InstallUrl` (non visualizzato) è il percorso da cui gli utenti installeranno l'applicazione. Se specificato, questo valore viene inserito nel *setup.exe* bootstrap se la `IsWebBootstrapper` proprietà è abilitata. Viene inserito anche nel manifesto dell'applicazione se `UpdateUrl` non è specificato .

- `SupportUrl` (non visualizzato) è il percorso collegato nella finestra **di dialogo** Installazione applicazioni per un'applicazione installata.

  Le proprietà seguenti vengono impostate nella finestra **di dialogo Aggiornamenti** applicazione , accessibile dalla **pagina** Pubblica .

- `UpdateEnabled` indica se l'applicazione deve verificare la disponibilità di aggiornamenti.

- `UpdateMode` specifica aggiornamenti in primo piano o aggiornamenti in background.
::: moniker range=">=vs-2019"
   Per i progetti .NET Core 3.1 o versioni successive, Background non è supportato.  
::: moniker-end
- `UpdateInterval` specifica la frequenza con cui l'applicazione deve verificare la disponibilità di aggiornamenti.
::: moniker range=">=vs-2019"
   Per .NET Core 3.1 o versione successiva, questa impostazione non è supportata.
::: moniker-end

- `UpdateIntervalUnits` specifica se il `UpdateInterval` valore è in unità di ore, giorni o settimane.
::: moniker range=">=vs-2019"
   Per .NET Core 3.1 o versione successiva, questa impostazione non è supportata.
::: moniker-end

- `UpdateUrl` (non visualizzato) è il percorso da cui l'applicazione riceverà gli aggiornamenti. Se specificato, questo valore viene inserito nel manifesto dell'applicazione.

  Le proprietà seguenti vengono impostate nella finestra **di dialogo Opzioni** di pubblicazione a cui si accede dalla **pagina** Pubblica.

- `PublisherName` specifica il nome dell'autore visualizzato nel prompt visualizzato durante l'installazione o l'esecuzione dell'applicazione. Nel caso di un'applicazione installata, viene usato anche per specificare il nome della cartella nel menu **Start.**

- `ProductName` specifica il nome del prodotto visualizzato nel prompt visualizzato durante l'installazione o l'esecuzione dell'applicazione. Nel caso di un'applicazione installata, viene usata anche per specificare il nome del collegamento nel menu **Start.**

  Le proprietà seguenti vengono impostate nella **finestra di** dialogo Prerequisiti a cui si accede dalla **pagina** Pubblica.

- `BootstrapperEnabled` determina se generare il programma di *setup.exe* bootstrap.

- `IsWebBootstrapper` determina se il *setup.exe* di avvio automatico funziona sul Web o in modalità basata su disco.

## <a name="installurl-supporturl-publishurl-and-updateurl"></a>InstallURL, SupportUrl, PublishURL e UpdateURL

 La tabella seguente illustra le quattro opzioni URL per la ClickOnce distribuzione.

|Opzione URL|Descrizione|
|----------------|-----------------|
|`PublishURL`|Obbligatorio se si pubblica l'applicazione ClickOnce in un sito Web.|
|`InstallURL`|facoltativo. Impostare questa opzione URL se il sito di installazione è diverso da `PublishURL` . Ad esempio, è possibile impostare `PublishURL` su un percorso FTP e impostare su un URL `InstallURL` Web.|
|`SupportURL`|facoltativo. Impostare questa opzione URL se il sito di supporto è diverso da `PublishURL` . Ad esempio, è possibile impostare sul sito Web del supporto clienti `SupportURL` dell'azienda.|
|`UpdateURL`|facoltativo. Impostare questa opzione URL se il percorso di aggiornamento è diverso da `InstallURL` . Ad esempio, è possibile impostare `PublishURL` su un percorso FTP e impostare su un URL `UpdateURL` Web.|

## <a name="see-also"></a>Vedi anche

- <xref:Microsoft.Build.Tasks.GenerateBootstrapper>
- <xref:Microsoft.Build.Tasks.GenerateApplicationManifest>
- <xref:Microsoft.Build.Tasks.GenerateDeploymentManifest>
- [Sicurezza e distribuzione di ClickOnce](../deployment/clickonce-security-and-deployment.md)
- [Procedura dettagliata: Distribuire manualmente un'applicazione ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
