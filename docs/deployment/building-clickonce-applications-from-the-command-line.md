---
title: Compilazione di applicazioni ClickOnce dalla riga di comando | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 065eea058ffa78c84428e031832e24837eb81d08
ms.sourcegitcommit: af9bbf9116a63c0631ff2f4f3a878564aa63cd8c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/04/2019
ms.locfileid: "74797208"
---
# <a name="build-clickonce-applications-from-the-command-line"></a>Compilare applicazioni ClickOnce dalla riga di comando
In [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], è possibile compilare i progetti dalla riga di comando, anche se vengono creati nell'Integrated Development Environment (IDE). Infatti, è possibile ricompilare un progetto creato con [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] in un altro computer in cui è installato solo il .NET Framework. In questo modo è possibile riprodurre una compilazione utilizzando un processo automatizzato, ad esempio, in un Lab di compilazione centrale o utilizzando tecniche di scripting avanzate oltre all'ambito della compilazione del progetto stesso.

## <a name="use-msbuild-to-reproduce-clickonce-application-deployments"></a>Usare MSBuild per riprodurre le distribuzioni di applicazioni ClickOnce
 Quando si richiama MSBuild/target: Publish dalla riga di comando, indica al sistema MSBuild di compilare il progetto e creare un'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nella cartella di pubblicazione. Questa operazione equivale alla selezione del comando **Publish** nell'IDE.

 Questo comando esegue *MSBuild. exe*, che si trova nel percorso dell'ambiente del prompt dei comandi di Visual Studio.

 Una "destinazione" è un indicatore di MSBuild sull'elaborazione del comando. Le destinazioni principali sono la destinazione "Build" e la destinazione "Publish". La destinazione di compilazione equivale alla selezione del comando di compilazione (o alla pressione di F5) nell'IDE. Se si vuole solo compilare il progetto, è possibile ottenere questo risultato digitando `msbuild`. Questo comando funziona perché la destinazione di compilazione è la destinazione predefinita per tutti i progetti generati da [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]. Ciò significa che non è necessario specificare in modo esplicito la destinazione di compilazione. Pertanto, digitando `msbuild` è la stessa operazione che digitando `msbuild /target:build`.

 Il comando `/target:publish` indica a MSBuild di richiamare la destinazione di pubblicazione. La destinazione di pubblicazione dipende dalla destinazione di compilazione. Ciò significa che l'operazione di pubblicazione è un superset dell'operazione di compilazione. Se, ad esempio, è stata apportata una modifica a uno C# dei file di Visual Basic o di origine, l'assembly corrispondente verrà ricompilato automaticamente dall'operazione di pubblicazione.

 Per informazioni sulla generazione di una distribuzione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] completa usando lo strumento da riga di comando Mage. exe per creare il manifesto [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], vedere [procedura dettagliata: distribuire manualmente un'applicazione ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).

## <a name="create-and-build-a-basic-clickonce-application-with-msbuild"></a>Creare e compilare un'applicazione ClickOnce di base con MSBuild

#### <a name="to-create-and-publish-a-clickonce-project"></a>Per creare e pubblicare un progetto ClickOnce

1. Aprire Visual Studio e creare un nuovo progetto.

    Scegliere il modello di progetto **applicazione desktop di Windows** e denominare il progetto `CmdLineDemo`.

1. Scegliere il comando **pubblica** dal menu **Compila** .

    Questo passaggio garantisce che il progetto sia configurato correttamente per produrre una distribuzione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione.

    Verrà visualizzata la pubblicazione guidata.

1. Nella pubblicazione guidata, fare clic su **fine**.

    Visual Studio genera e visualizza la pagina Web predefinita, denominata *Publish. htm*.

1. Salvare il progetto e prendere nota del percorso della cartella in cui è archiviato.

   I passaggi precedenti creano un progetto di [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] che è stato pubblicato per la prima volta. A questo punto è possibile riprodurre la compilazione all'esterno dell'IDE.

#### <a name="to-reproduce-the-build-from-the-command-line"></a>Per riprodurre la compilazione dalla riga di comando

1. Chiudere [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].

2. Dal menu **Start** di Windows fare clic su **tutti i programmi**, quindi **Microsoft Visual Studio**, quindi **strumenti di Visual Studio**, quindi prompt dei **comandi di Visual Studio**. Verrà visualizzato un prompt dei comandi nella cartella radice dell'utente corrente.

3. Al **prompt dei comandi di Visual Studio**, impostare la directory corrente sul percorso del progetto appena creato. Ad esempio, immettere `chdir My Documents\Visual Studio\Projects\CmdLineDemo`.

4. Per rimuovere i file esistenti prodotti in "per creare e pubblicare un progetto di [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]", digitare `rmdir /s publish`.

    Questo passaggio è facoltativo, ma garantisce che i nuovi file siano tutti prodotti dalla compilazione da riga di comando.

5. Digitare `msbuild /target:publish`.

   I passaggi precedenti produrranno una distribuzione completa [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione in una sottocartella del progetto denominato **Publish**. *CmdLineDemo. Application* è il manifesto della distribuzione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. La cartella *CmdLineDemo_1.0.0.0* contiene i file *CmdLineDemo. exe* e *CmdLineDemo. exe. manifest*, il manifesto dell'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. *Setup. exe* è il programma di avvio automatico, che per impostazione predefinita è configurato per installare il .NET Framework. La cartella DotNetFX contiene i ridistribuibili per la .NET Framework. Si tratta dell'intero set di file necessari per distribuire l'applicazione sul Web o tramite UNC o CD/DVD.
   
> [!NOTE]
> Il sistema MSBuild usa l'opzione **PublishDir** per specificare il percorso per l'output, ad esempio `msbuild /t:publish /p:PublishDir="<specific location>"`.

## <a name="publish-properties"></a>Pubblica proprietà
 Quando si pubblica l'applicazione nelle procedure precedenti, le proprietà seguenti vengono inserite nel file di progetto tramite la pubblicazione guidata. Queste proprietà influiscono direttamente sulla modalità di produzione dell'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].

 In *CmdLineDemo.vbproj* / *CmdLineDemo.csproj*:

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

 È possibile eseguire l'override di una qualsiasi di queste proprietà nella riga di comando senza modificare il file di progetto stesso. Ad esempio, di seguito viene compilata la distribuzione dell'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] senza il programma di avvio automatico:

```cmd
msbuild /target:publish /property:BootstrapperEnabled=false
```

 Le proprietà di pubblicazione sono controllate in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dalle pagine delle proprietà **pubblica**, **sicurezza**e **firma** di **Progettazione progetti**. Di seguito è riportata una descrizione delle proprietà di pubblicazione, insieme a un'indicazione del modo in cui ciascuna è impostata nelle varie pagine delle proprietà di progettazione applicazione:

- `AssemblyOriginatorKeyFile` determina il file di chiave usato per firmare i manifesti dell'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. Questa stessa chiave può essere usata anche per assegnare un nome sicuro agli assembly. Questa proprietà è impostata nella pagina **firma** di **Progettazione progetti**.

  Nella pagina **sicurezza** sono impostate le proprietà seguenti:

- **Abilita impostazioni di sicurezza ClickOnce** determina se vengono generati [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifesti. Quando un progetto viene creato inizialmente, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] generazione del manifesto è disattivata per impostazione predefinita. La procedura guidata attiva automaticamente questo flag quando si pubblica per la prima volta.

- **TargetZone** determina il livello di attendibilità da emettere nel manifesto dell'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. I valori possibili sono "Internet", "LocalIntranet" e "Custom". Internet e LocalIntranet comporteranno l'emissione di un set di autorizzazioni predefinito nel manifesto dell'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. LocalIntranet è l'impostazione predefinita e significa fondamentalmente attendibilità totale. Custom specifica che solo le autorizzazioni specificate in modo esplicito nel file *app. manifest* di base devono essere emesse nel manifesto dell'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. Il file *app. manifest* è un file manifesto parziale che contiene solo le definizioni delle informazioni di attendibilità. Si tratta di un file nascosto, aggiunto automaticamente al progetto quando si configurano le autorizzazioni nella pagina **sicurezza** .

  Nella pagina **pubblica** sono impostate le proprietà seguenti:

- `PublishUrl` è il percorso in cui verrà pubblicata l'applicazione nell'IDE. Viene inserito nel manifesto dell'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] se non viene specificata la proprietà `InstallUrl` o `UpdateUrl`.

- `ApplicationVersion` specifica la versione dell'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. Si tratta di un numero di versione a quattro cifre. Se l'ultima cifra è "*", il `ApplicationRevision` viene sostituito con il valore inserito nel manifesto in fase di compilazione.

- `ApplicationRevision` specifica la revisione. Si tratta di un numero intero che viene incrementato ogni volta che si pubblica nell'IDE. Si noti che non viene incrementato automaticamente per le compilazioni eseguite dalla riga di comando.

- `Install` determina se si tratta di un'applicazione installata o di un'applicazione Web di esecuzione.

- `InstallUrl` (non visualizzato) è il percorso da cui gli utenti installeranno l'applicazione. Se specificato, questo valore viene bruciato nel programma di avvio automatico *Setup. exe* se la proprietà `IsWebBootstrapper` è abilitata. Viene inserito anche nel manifesto dell'applicazione se il `UpdateUrl` non è specificato.

- `SupportUrl` (non visualizzato) è il percorso collegato nella finestra di dialogo **installazione** applicazioni per un'applicazione installata.

  Le proprietà seguenti vengono impostate nella finestra di dialogo **Aggiornamenti applicazione** , accessibile dalla pagina **pubblica** .

- `UpdateEnabled` indica se l'applicazione deve verificare la disponibilità di aggiornamenti.

- `UpdateMode` specifica gli aggiornamenti in primo piano o gli aggiornamenti in background.

- `UpdateInterval` specifica la frequenza con cui l'applicazione deve verificare la disponibilità di aggiornamenti.

- `UpdateIntervalUnits` specifica se il valore di `UpdateInterval` è in unità di ore, giorni o settimane.

- `UpdateUrl` (non visualizzato) è il percorso dal quale l'applicazione riceverà gli aggiornamenti. Se specificato, questo valore viene inserito nel manifesto dell'applicazione.

  Le proprietà seguenti vengono impostate nella finestra di dialogo **Opzioni di pubblicazione** a cui si accede dalla pagina **pubblica** .

- `PublisherName` specifica il nome del server di pubblicazione visualizzato nel prompt visualizzato durante l'installazione o l'esecuzione dell'applicazione. Nel caso di un'applicazione installata, viene usato anche per specificare il nome della cartella nel menu **Start** .

- `ProductName` specifica il nome del prodotto visualizzato nel prompt visualizzato durante l'installazione o l'esecuzione dell'applicazione. Nel caso di un'applicazione installata, viene usato anche per specificare il nome del collegamento nel menu **Start** .

  Le proprietà seguenti sono impostate nella finestra di dialogo **prerequisiti** a cui si accede dalla pagina di **pubblicazione** .

- `BootstrapperEnabled` determina se generare il programma di avvio automatico *Setup. exe* .

- `IsWebBootstrapper` determina se il programma di avvio automatico *Setup. exe* funziona sul Web o in modalità basata su disco.

## <a name="installurl-supporturl-publishurl-and-updateurl"></a>InstallURL, SupportUrl, PublishURL e UpdateURL
 La tabella seguente illustra le quattro opzioni URL per la distribuzione ClickOnce.

|Opzione URL|Descrizione|
|----------------|-----------------|
|`PublishURL`|Obbligatorio se si pubblica l'applicazione ClickOnce in un sito Web.|
|`InstallURL`|Parametro facoltativo. Impostare questa opzione URL se il sito di installazione è diverso dal `PublishURL`. Ad esempio, è possibile impostare il `PublishURL` su un percorso FTP e impostare il `InstallURL` su un URL Web.|
|`SupportURL`|Parametro facoltativo. Impostare questa opzione URL se il sito di supporto è diverso dal `PublishURL`. Ad esempio, è possibile impostare il `SupportURL` sul sito Web di supporto tecnico della società.|
|`UpdateURL`|Parametro facoltativo. Impostare questa opzione URL se il percorso di aggiornamento è diverso da quello del `InstallURL`. Ad esempio, è possibile impostare il `PublishURL` su un percorso FTP e impostare il `UpdateURL` su un URL Web.|

## <a name="see-also"></a>Vedere anche
- <xref:Microsoft.Build.Tasks.GenerateBootstrapper>
- <xref:Microsoft.Build.Tasks.GenerateApplicationManifest>
- <xref:Microsoft.Build.Tasks.GenerateDeploymentManifest>
- [Sicurezza e distribuzione di ClickOnce](../deployment/clickonce-security-and-deployment.md)
- [Procedura dettagliata: Distribuire manualmente un'applicazione ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
