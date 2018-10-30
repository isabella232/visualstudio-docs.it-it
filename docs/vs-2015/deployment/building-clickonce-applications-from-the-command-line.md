---
title: Creazione di applicazioni ClickOnce dalla riga di comando | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, from command line
- publishing
- publishing, ClickOnce
ms.assetid: d9bc6212-c584-4f72-88c9-9a4b998c555e
caps.latest.revision: 25
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: c9a9b2e248e4f10e9b5d3f045c67a9622edd2c2b
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/29/2018
ms.locfileid: "50220017"
---
# <a name="building-clickonce-applications-from-the-command-line"></a>Compilazione di applicazioni ClickOnce dalla riga di comando
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)], è possibile compilare progetti dalla riga di comando, anche se sono stati creati nell'ambiente di sviluppo integrato (IDE). In effetti, è possibile ricompilare un progetto creato con [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] in un altro computer che dispone solo di [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] installato. In questo modo di riprodurre una build con un processo automatizzato, ad esempio, in una compilazione centrale lab o tramite tecniche di scripting avanzate esula dall'ambito di compilazione del progetto stesso.  
  
## <a name="using-msbuild-to-reproduce-clickonce-application-deployments"></a>Uso di MSBuild per riprodurre le distribuzioni di applicazioni ClickOnce  
 Quando si richiama /target: Publish msbuild dalla riga di comando, indica al sistema di MSBuild per compilare il progetto e creare un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] applicazione nella cartella di pubblicazione. Ciò equivale a selezionare il **pubblica** comando nell'IDE.  
  
 Questo comando esegue msbuild.exe, che si trova nel percorso nell'ambiente di prompt dei comandi di Visual Studio.  
  
 "Destinazione" è un indicatore a MSBuild su come elaborare il comando. Le destinazioni principali sono la destinazione "build" e la destinazione "pubblica". La destinazione della compilazione è equivalente alla selezione della compilazione comando (o premendo F5) nell'IDE. Se si desidera solo creare il progetto, è possibile ottenere questo risultato digitando `msbuild`. Questo comando funziona perché la destinazione della compilazione è la destinazione predefinita per tutti i progetti generati da [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]. Ciò significa che non è necessario in modo esplicito specificare la destinazione della compilazione. Pertanto, la digitazione `msbuild` è la stessa operazione digitando `msbuild /target:build`.  
  
 Il `/target:publish` comando indica a MSBuild per richiamare la destinazione di pubblicazione. La destinazione di pubblicazione dipende dalla destinazione di compilazione. Ciò significa che l'operazione di pubblicazione è un superset dell'operazione di compilazione. Ad esempio, se si apporta una modifica a uno dei file di origine Visual Basic o c#, l'assembly corrispondente verrà rigenerato automaticamente dall'operazione di pubblicazione.  
  
 Per informazioni sulla generazione di una procedura completa [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] distribuzione utilizzando lo strumento da riga di comando Mage.exe per creare le [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifesto, vedere [procedura dettagliata: distribuzione manuale di un'applicazione ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
## <a name="creating-and-building-a-basic-clickonce-application-using-msbuild"></a>Creazione e compilazione di un'applicazione ClickOnce di base utilizzando MSBuild  
  
#### <a name="to-create-and-publish-a-clickonce-project"></a>Per creare e pubblicare un progetto di ClickOnce  
  
1. Fare clic su **nuovo progetto** dalle **File** menu. Verrà visualizzata la finestra di dialogo **Nuovo progetto** .  
  
2. Selezionare **applicazione di Windows** e denominarlo `CmdLineDemo`.  
  
3. Dal **compilare** menu, fare clic sul **Publish** comando.  
  
    Questo passaggio assicura che il progetto sia configurato correttamente per produrre un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] distribuzione dell'applicazione.  
  
    Verrà visualizzata la Pubblicazione guidata.  
  
4. Nella pubblicazione guidata, fare clic su **fine**.  
  
    Visual Studio genera e Visualizza la pagina Web predefinita, chiamata Publish. htm.  
  
5. Salvare il progetto e assicurarsi di annotare il percorso della cartella in cui viene archiviato.  
  
   Crea la procedura descritta sopra un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] progetto in cui è stato pubblicato per la prima volta. A questo punto è possibile riprodurre la compilazione all'esterno dell'IDE.  
  
#### <a name="to-reproduce-the-build-from-the-command-line"></a>Per ripetere la compilazione dalla riga di comando  
  
1. Chiudere [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].  
  
2. Dalla finestra di Windows **avviare** menu, fare clic su **tutti i programmi**, quindi **Microsoft Visual Studio**, quindi **Visual Studio Tools**, quindi **Prompt dei comandi di visual Studio**. Questo dovrebbe aprire un prompt dei comandi nella cartella radice dell'utente corrente.  
  
3. Nel **Prompt dei comandi di Visual Studio**, modificare la directory corrente nel percorso del progetto appena compilato. Ad esempio, digitare `chdir My Documents\Visual Studio\Projects\CmdLineDemo`.  
  
4. Per rimuovere i file esistenti generati "creare e pubblicare un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] progetti," tipo `rmdir /s publish`.  
  
    Questo passaggio è facoltativo, ma garantisce che tutti i nuovi file sono stati prodotti dalla compilazione da riga di comando.  
  
5. Digitare `msbuild /target:publish`.  
  
   I passaggi precedenti produrrà una procedura completa [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] distribuzione di applicazioni in una sottocartella del progetto denominato **Publish**. CmdLineDemo. Application è il [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifesto della distribuzione. La cartella CmdLineDemo 1.0.0.0 contiene i file CmdLineDemo.exe e CmdLineDemo.exe.manifest, ossia il [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifesto dell'applicazione. Setup.exe è il programma di bootstrap, che per impostazione predefinita è configurato per installare il [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. La cartella DotNetFX contiene i file ridistribuibili per i [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Questo è l'intero set di file che necessari per distribuire l'applicazione sul Web o tramite CD/DVD o UNC.  
  
## <a name="publishing-properties"></a>Le opzioni di pubblicazione  
 Quando si pubblica l'applicazione nelle procedure precedenti, le proprietà seguenti vengono inserite nel file di progetto per la pubblicazione guidata. Queste proprietà influiscono direttamente sul modo in cui il [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] viene prodotto l'applicazione.  
  
 In CmdLineDemo.vbproj / CmdLineDemo.csproj:  
  
```  
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
  
 È possibile eseguire l'override di una di queste proprietà nella riga di comando senza alterare il file di progetto stesso. Ad esempio, i seguenti compilerà il [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] distribuzione dell'applicazione senza il programma di bootstrap:  
  
```  
msbuild /target:publish /property:BootstrapperEnabled=false  
```  
  
 Le opzioni di pubblicazione vengono controllate nei [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] dal **Publish**, **sicurezza**, e **firma** pagine delle proprietà del **Progettazione progetti** . Di seguito è riportata una descrizione delle proprietà di pubblicazione, insieme a un'indicazione della ognuno come verrà impostata nelle varie pagine delle proprietà della finestra di progettazione dell'applicazione:  
  
- `AssemblyOriginatorKeyFile` Determina il file di chiave usato per firmare il [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifesti dell'applicazione. Questa stessa chiave inoltre consente di assegnare un nome sicuro all'assembly. Questa proprietà è impostata sul **Signing** pagina della **creazione progetti**.  
  
  Le proprietà seguenti vengono impostate per il **sicurezza** pagina:  
  
- **Abilitare le impostazioni di sicurezza ClickOnce** determina se [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] vengono generati i manifesti. Quando un progetto viene creato inizialmente, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] generazione del manifesto è disattivata per impostazione predefinita. La procedura guidata verrà attivato automaticamente questo flag viene pubblicato per la prima volta.  
  
- **TargetZone** determina il livello di attendibilità per essere emessa nel [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifesto dell'applicazione. I valori possibili sono "Internet", "Intranet locale" e "Custom". Internet e Intranet locale causerà un'autorizzazione predefinita impostata per essere emessa nel [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifesto dell'applicazione. Il valore predefinito è LocalIntranet ed essenzialmente ciò implica l'attendibilità totale. Personalizzata specifica che solo le autorizzazioni specificate in modo esplicito nel file manifest base devono essere emessa nel [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifesto dell'applicazione. Il file app. manifest è un file manifesto parziale che contiene solo le definizioni di informazioni di attendibilità. Si tratta di un file nascosto automaticamente aggiunto al progetto quando si configurano le autorizzazioni nel **sicurezza** pagina.  
  
  Le proprietà seguenti vengono impostate per il **pubblica** pagina:  
  
- `PublishUrl` è la posizione in cui verrà pubblicata per l'applicazione nell'IDE. Viene inserito nella [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifesto dell'applicazione se non si specifica il `InstallUrl` o `UpdateUrl` è specificata la proprietà.  
  
- `ApplicationVersion` Specifica la versione del [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dell'applicazione. Si tratta di un numero di versione a quattro cifre. Se l'ultima cifra è un "*", quindi il `ApplicationRevision` viene sostituito con il valore inserito nel manifesto in fase di compilazione.  
  
- `ApplicationRevision` Specifica la revisione. Questo è un integer viene incrementato ogni volta che si pubblica nell'IDE. Si noti che non viene automaticamente incrementato per le compilazioni eseguite dalla riga di comando.  
  
- `Install` Determina se l'applicazione è un'applicazione installata o un'applicazione eseguita dal Web.  
  
- `InstallUrl` (non mostrato) è il percorso in cui gli utenti installeranno l'applicazione da. Se specificato, questo valore verrà copiato nel programma di avvio automatico setup.exe se il `IsWebBootstrapper` proprietà è abilitata. Viene inoltre inserito nel manifesto dell'applicazione, se il `UpdateUrl` non è specificato.  
  
- `SupportUrl` (non mostrato) è il percorso del collegamento nel **Aggiungi/Rimuovi programmi** finestra di dialogo per un'applicazione installata.  
  
  Le seguenti proprietà vengono impostate **gli aggiornamenti dell'applicazione** finestra di dialogo, accessibile dalle **Publish** pagina.  
  
- `UpdateEnabled` indica se l'applicazione deve verificare gli aggiornamenti.  
  
- `UpdateMode` Specifica gli aggiornamenti in primo piano o gli aggiornamenti in Background.  
  
- `UpdateInterval` Specifica la frequenza con cui l'applicazione deve cercare gli aggiornamenti.  
  
- `UpdateIntervalUnits` Specifica se il `UpdateInterval` valore è espresso in unità di ore, giorni o settimane.  
  
- `UpdateUrl` (non mostrato) è il percorso da cui l'applicazione riceverà gli aggiornamenti. Se specificato, questo valore viene inserito nel manifesto dell'applicazione.  
  
- Le seguenti proprietà vengono impostate **Publish Options** finestra di dialogo, accessibile dalle **Publish** pagina.  
  
- `PublisherName` Specifica il nome del server di pubblicazione visualizzato nel messaggio visualizzato durante l'installazione o esecuzione dell'applicazione. Nel caso di un'applicazione installata, viene anche utilizzata per specificare il nome della cartella il **avviare** menu.  
  
- `ProductName` Specifica il nome del prodotto visualizzato nel messaggio visualizzato durante l'installazione o esecuzione dell'applicazione. Nel caso di un'applicazione installata, viene anche utilizzata per specificare il nome del collegamento di **avviare** menu.  
  
- Le seguenti proprietà vengono impostate **prerequisiti** finestra di dialogo, accessibile dalle **Publish** pagina.  
  
- `BootstrapperEnabled` Determina se generare il programma di bootstrap setup.exe.  
  
- `IsWebBootstrapper` Determina se il programma di bootstrap setup.exe funziona tramite il Web o nella modalità basata su disco.  
  
## <a name="installurl-supporturl-publishurl-and-updateurl"></a>InstallURL SupportUrl, PublishURL e proprietà UpdateURL  
 Nella tabella seguente mostra le quattro opzioni di URL per la distribuzione ClickOnce.  
  
|Opzione URL|Descrizione|  
|----------------|-----------------|  
|`PublishURL`|Obbligatorio se si pubblica l'applicazione ClickOnce per un sito Web.|  
|`InstallURL`|Facoltativo. Impostare questa opzione di URL, se il sito dell'installazione è diverso da quella di `PublishURL`. Ad esempio, è possibile impostare il `PublishURL` a un percorso FTP e impostare il `InstallURL` a un URL Web.|  
|`SupportURL`|Facoltativo. Impostare questa opzione di URL, se il sito del supporto tecnico è diverso da quello di `PublishURL`. Ad esempio, è possibile impostare il `SupportURL` al sito Web del supporto clienti dell'azienda.|  
|`UpdateURL`|Facoltativo. Impostare questa opzione di URL, se il percorso di aggiornamento è diverso da quello di `InstallURL`. Ad esempio, è possibile impostare il `PublishURL` a un percorso FTP e impostare il `UpdateURL` a un URL Web.|  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.Build.Tasks.GenerateBootstrapper>   
 <xref:Microsoft.Build.Tasks.GenerateApplicationManifest>   
 <xref:Microsoft.Build.Tasks.GenerateDeploymentManifest>   
 [Sicurezza e distribuzione di ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Procedura dettagliata: distribuzione manuale di un'applicazione ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)



