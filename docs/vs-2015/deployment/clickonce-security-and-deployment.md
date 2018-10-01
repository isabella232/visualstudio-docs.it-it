---
title: ClickOnce Security and Deployment | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
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
- Windows applications, ClickOnce deployment
- deploying applications [ClickOnce]
- ClickOnce deployment
- publishing, ClickOnce
ms.assetid: abab6d34-c3c2-45c1-a8b6-43c7d3131e7a
caps.latest.revision: 34
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: be076232ee9214ad0039421c7c5610fad3f4c3b1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47527655"
---
# <a name="clickonce-security-and-deployment"></a>Sicurezza e distribuzione di ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [ClickOnce Security and Deployment](https://docs.microsoft.com/visualstudio/deployment/clickonce-security-and-deployment).  
  
[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] è una tecnologia di distribuzione che consente di creare applicazioni basate su Windows ad aggiornamento automatico che possono essere installate ed eseguite con l'interazione utente minima. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] fornisce supporto completo per la pubblicazione e aggiornamento delle applicazioni distribuite con la tecnologia ClickOnce, se è stata sviluppata i progetti con Visual Basic e Visual c#. Per informazioni sulla distribuzione di applicazioni Visual C++, vedere [distribuzione ClickOnce per applicazioni Visual C++](http://msdn.microsoft.com/library/9988c546-0936-452c-932f-9c76daa42157).  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] distribuzione risolve tre problemi nella distribuzione:  
  
-   **Difficoltà di aggiornamento delle applicazioni.** Con la distribuzione di Microsoft Windows Installer, ogni volta che viene aggiornata un'applicazione, l'utente può installare un aggiornamento, un file msp e applicarlo al prodotto installato. con [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] distribuzione, è possibile fornire gli aggiornamenti automaticamente. Vengono scaricate solo le parti dell'applicazione che sono stati modificati, e quindi l'intera applicazione aggiornata viene reinstallata da una nuova cartella side-by-side.  
  
-   **Impatto sul computer dell'utente.** Con la distribuzione di Windows Installer, le applicazioni si basano spesso su componenti condivisi, con potenziali conflitti di versioni. con [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] distribuzione, ogni applicazione è autonoma e non può interferire con altre applicazioni.  
  
-   **Autorizzazioni di sicurezza.** Distribuzione di Windows Installer richiede autorizzazioni amministrative e consente solo installazione utente con limitazioni. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] distribuzione consente agli utenti senza privilegi di amministratore installare e concede solo le autorizzazioni di sicurezza dall'accesso di codice necessarie per l'applicazione.  
  
 In passato, questi problemi causati in alcuni casi gli sviluppatori a creare applicazioni Web invece di applicazioni basate su Windows, compromettere un'interfaccia utente avanzata per agevolare l'installazione. Tramite le applicazioni distribuite utilizzando [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)], consente di ottenere il meglio di entrambe le tecnologie.  
  
## <a name="what-is-a-clickonce-application"></a>Che cos'è un'applicazione ClickOnce?  
 Oggetto [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] applicazione è qualsiasi (con estensione xbap) di Windows Presentation Foundation, Windows Form (.exe), applicazione console (.exe) o soluzione Office (con estensione dll) pubblicato tramite [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] tecnologia. È possibile pubblicare un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dell'applicazione in tre modi diversi: da una pagina Web, da una condivisione file di rete o da supporto, ad esempio un CD-ROM. Oggetto [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] applicazione può essere installata nel computer dell'utente finale ed eseguita in locale anche quando il computer è offline oppure può essere eseguita in modalità solo online senza alcuna operazione di installazione in modo permanente nel computer dell'utente finale. Per altre informazioni, vedere [Scelta di una strategia di distribuzione ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] le applicazioni possono essere di aggiornamento automatico; è possibile cercare le versioni più recenti non appena diventano disponibili e sostituire automaticamente eventuali file aggiornati. Lo sviluppatore può specificare il comportamento di aggiornamento. un amministratore di rete può anche controllare le strategie di aggiornamento, ad esempio, contrassegnare un aggiornamento come obbligatorio. Gli aggiornamenti possono anche essere rollback a una versione precedente dall'utente finale o da un amministratore. Per altre informazioni, vedere [scelta di una strategia di aggiornamento ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).  
  
 In quanto [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] applicazioni risultano isolate, installazione o esecuzione di un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] applicazione non può interferire con le applicazioni esistenti. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] le applicazioni sono indipendenti. ogni [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] applicazione viene installata ed eseguita da un sicura per ogni utente e della cache per ogni applicazione. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] le applicazioni eseguite nelle aree di protezione Internet o Intranet. Se necessario, l'applicazione può richiedere le autorizzazioni di sicurezza con privilegi elevati. Per altre informazioni, vedere [Protezione di applicazioni ClickOnce](../deployment/securing-clickonce-applications.md).  
  
## <a name="how-clickonce-security-works"></a>Funzionamento della sicurezza ClickOnce  
 Il nucleo [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] è basata su certificati, i criteri di sicurezza di accesso di codice e la richiesta di attendibilità di ClickOnce.  
  
### <a name="certificates"></a>Certificati  
 Per verificare l'autenticità dell'editore dell'applicazione vengono utilizzati i certificati Authenticode. Usando la tecnologia Authenticode per la distribuzione di applicazioni, ClickOnce consente di impedire che un programma dannoso figuri come programmi legittimi provenienti da una fonte definita e attendibile. Facoltativamente, certificati possono essere usati anche per firmare l'applicazione e manifesti della distribuzione per dimostrare che i file non sono stati alterati. Per altre informazioni, vedere [ClickOnce e Authenticode](../deployment/clickonce-and-authenticode.md). Certificati possono essere usati anche per configurare i computer client per un elenco di autori attendibili. Se un'applicazione proviene da un autore attendibile, può essere installato senza alcuna interazione dell'utente. Per altre informazioni, vedere [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md).  
  
### <a name="code-access-security"></a>Sicurezza per l'accesso al codice  
 Sicurezza dall'accesso di codice consente di limitare l'accesso di codice alle risorse protette. Nella maggior parte dei casi, è possibile scegliere le aree Internet o Intranet locale per limitare le autorizzazioni. Usare la **sicurezza** pagina il **ProjectDesigner** per richiedere l'area appropriata per l'applicazione. È anche possibile eseguire il debug di applicazioni con autorizzazioni limitate per emulare l'esperienza utente finale. Per altre informazioni, vedere [Sicurezza dall'accesso di codice per applicazioni ClickOnce](../deployment/code-access-security-for-clickonce-applications.md).  
  
### <a name="clickonce-trust-prompt"></a>Richiesta di attendibilità ClickOnce  
 Se l'applicazione richiede più autorizzazioni rispetto a quelle consentite la zona, all'utente finale può essere richiesto per prendere una decisione di attendibilità. L'utente finale può decidere se sono attendibili per l'esecuzione di applicazioni ClickOnce, ad esempio applicazioni Windows Forms, le applicazioni Windows Presentation Foundation, le applicazioni console, le applicazioni browser XAML e soluzioni Office. Per altre informazioni, vedere [procedura: configurare il comportamento della richiesta ClickOnce Trust](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md).  
  
## <a name="how-clickonce-deployment-works"></a>Funzionamento della distribuzione ClickOnce  
 Il nucleo [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] architettura delle distribuzioni si basa su due file manifesto XML: un manifesto dell'applicazione e un manifesto della distribuzione. I file vengono utilizzati per descrivere in cui le applicazioni ClickOnce sono installate dal modo in cui vengono aggiornate e quando vengono aggiornati.  
  
### <a name="publishing-clickonce-applications"></a>Pubblicazione di applicazioni ClickOnce  
 Il manifesto dell'applicazione descrive l'applicazione stessa. Ciò include gli assembly, le dipendenze e i file che costituiscono l'applicazione, le autorizzazioni necessarie e il percorso in cui gli aggiornamenti saranno disponibili. Lo sviluppatore dell'applicazione viene creato il manifesto dell'applicazione usando la procedura guidata di pubblicazione in Visual Studio o il Manifest Generation and Editing Tool (Mage.exe) nel [!INCLUDE[winsdklong](../includes/winsdklong-md.md)]. Per altre informazioni, vedere [procedura: pubblicare un'applicazione ClickOnce mediante la pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
 Il manifesto di distribuzione viene descritto come l'applicazione viene distribuita. Ciò include il percorso del manifesto dell'applicazione e la versione dell'applicazione in cui i client devono eseguire.  
  
### <a name="deploying-clickonce-applications"></a>Distribuzione di applicazioni ClickOnce  
 Dopo averlo creato, il manifesto di distribuzione viene copiato nel percorso di distribuzione. Può trattarsi di un server Web, condivisione file di rete o supporti, ad esempio un CD. Il manifesto dell'applicazione e tutti i file dell'applicazione vengono inoltre copiati in un percorso di distribuzione specificato nel manifesto di distribuzione. Ciò può essere identico al percorso di distribuzione oppure può essere un percorso diverso. Quando si usa la **pubblicazione guidata** in Visual Studio, le operazioni di copia vengono eseguite automaticamente.  
  
### <a name="installing-clickonce-applications"></a>Installazione di applicazioni ClickOnce  
 Dopo la distribuzione nel percorso di distribuzione, gli utenti finali possono scaricare e installare l'applicazione facendo clic su un'icona che rappresenta il file manifesto della distribuzione in una pagina Web o in una cartella. Nella maggior parte dei casi, all'utente finale viene visualizzata una finestra di dialogo che chiede all'utente di confermare l'installazione, dopo l'installazione procede e l'applicazione viene avviata senza l'intervento aggiuntivo. Nei casi in cui l'applicazione richiede autorizzazioni elevate o se l'applicazione non è firmata da un certificato attendibile, la finestra di dialogo chiede inoltre all'utente di concedere l'autorizzazione prima di poter continuare l'installazione. Anche se le installazioni ClickOnce sono per utente, l'elevazione delle autorizzazioni potrebbe essere necessario se esistono prerequisiti che richiedono privilegi di amministratore. Per altre informazioni sulle autorizzazioni con privilegi elevate, vedere [protezione di applicazioni ClickOnce](../deployment/securing-clickonce-applications.md).  
  
 Certificati possono essere attendibili a livello di computer o dell'organizzazione, in modo che le applicazioni ClickOnce firmate con un certificato attendibile possono installazione invisibile all'utente. Per altre informazioni sui certificati attendibili, vedere [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md).  
  
 L'applicazione può essere aggiunta a dell'utente **avviare** menu e il **Aggiungi / Rimuovi programmi** gruppo il **Pannello di controllo**. A differenza di altre tecnologie di distribuzione, viene aggiunto nulla per il **Program Files** cartella o il Registro di sistema e diritti amministrativi non sono necessari per l'installazione  
  
> [!NOTE]
>  È anche possibile impedire l'applicazione venga aggiunto al **avviare** dal menu e **Aggiungi / Rimuovi programmi** gruppo, in effetti esattamente come un'applicazione Web. Per altre informazioni, vedere [Scelta di una strategia di distribuzione ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
### <a name="updating-clickonce-applications"></a>Aggiornamento delle applicazioni ClickOnce  
 Quando gli sviluppatori di applicazioni creano una versione aggiornata dell'applicazione, che genera un nuovo manifesto dell'applicazione e copiare i file in un percorso di distribuzione, ovvero in genere una cartella di pari livello nella cartella di distribuzione dell'applicazione originale. L'amministratore aggiorna il manifesto di distribuzione in modo che punti al percorso della nuova versione dell'applicazione.  
  
> [!NOTE]
>  Il **pubblicazione guidata** in Visual Studio può essere utilizzato per eseguire questi passaggi.  
  
 Oltre al percorso di distribuzione, il manifesto di distribuzione contiene anche un percorso di aggiornamento (una condivisione file pagina Web o di rete) in cui l'applicazione verifica la presenza di versioni aggiornate. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] **Pubblicare** proprietà vengono usate per specificare quando e con quale frequenza controllare la disponibilità di aggiornamenti. Comportamento di aggiornamento può essere specificato nel manifesto di distribuzione o può essere presentata come scelte dell'utente nell'interfaccia utente dell'applicazione per mezzo del [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] API. È inoltre **pubblica** proprietà possono essere utilizzate per eseguire gli aggiornamenti obbligatori o eseguire il rollback a una versione precedente. Per altre informazioni, vedere [scelta di una strategia di aggiornamento ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).  
  
### <a name="third-party-installers"></a>Programmi di installazione di terze parti  
 È possibile personalizzare il programma di installazione ClickOnce per installare i componenti di terze parti insieme all'applicazione. È necessario disporre del package ridistribuibile (file con estensione msi o .exe) e descrivono il pacchetto con un manifesto del prodotto indipendente dalla lingua e un manifesto di pacchetto specifico del linguaggio. Per altre informazioni, vedere [creazione di pacchetti Bootstrapper](../deployment/creating-bootstrapper-packages.md).  
  
## <a name="clickonce-tools"></a>Strumenti ClickOnce  
 La tabella seguente illustra gli strumenti che è possibile usare per generare, modificare, accedere e firmare nuovamente i manifesti dell'applicazione e distribuzione.  
  
|Strumento|Descrizione|  
|----------|-----------------|  
|[Pagina Sicurezza, Creazione progetti](../ide/reference/security-page-project-designer.md)|Firma i manifesti dell'applicazione e distribuzione.|  
|[Pagina Pubblica, Creazione progetti](../ide/reference/publish-page-project-designer.md)|Genera e modificare i manifesti dell'applicazione e di distribuzione per le applicazioni Visual Basic e Visual c#.|  
|[Mage.exe (Strumento per la generazione e la modifica di manifesti)](http://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)|Genera i manifesti dell'applicazione e distribuzione per le applicazioni Visual Basic, Visual c# e Visual C++.<br /><br /> Firma e firma nuovamente i manifesti dell'applicazione e distribuzione.<br /><br /> Può essere eseguito dal prompt dei comandi e script di batch.|  
|[MageUI.exe (Strumento per la generazione e la modifica di manifesti, client grafico)](http://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14)|Genera e modificare i manifesti dell'applicazione e della distribuzione.<br /><br /> Firma e firma nuovamente i manifesti dell'applicazione e distribuzione.|  
|[Attività GenerateApplicationManifest](../msbuild/generateapplicationmanifest-task.md)|Genera il manifesto dell'applicazione.<br /><br /> Può essere eseguito da MSBuild. Per altre informazioni, vedere [riferimenti a MSBuild](../msbuild/msbuild-reference.md).|  
|[Attività GenerateDeploymentManifest](../msbuild/generatedeploymentmanifest-task.md)|Genera il manifesto di distribuzione.<br /><br /> Può essere eseguito da MSBuild. Per altre informazioni, vedere [riferimenti a MSBuild](../msbuild/msbuild-reference.md).|  
|[Attività SignFile](../msbuild/signfile-task.md)|Firma i manifesti dell'applicazione e distribuzione.<br /><br /> Può essere eseguito da MSBuild. Per altre informazioni, vedere [riferimenti a MSBuild](../msbuild/msbuild-reference.md).|  
|<xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities>|Sviluppare la propria applicazione per generare i manifesti dell'applicazione e distribuzione.|  
  
 La tabella seguente illustra la versione di .NET Framework necessaria per supportare le applicazioni ClickOnce in questi browser.  
  
|Browser|Versione di .NET Framework|  
|-------------|----------------------------|  
|Internet Explorer|2.0, 3.0, 3.5, 4 3.5 SP1|  
|Firefox|2.0 SP1, 3.5 SP1, 4|  
  
## <a name="see-also"></a>Vedere anche  
 [Distribuzione ClickOnce in Windows Vista](../deployment/clickonce-deployment-on-windows-vista.md)   
 [Pubblicazione di applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Protezione di applicazioni ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Distribuzione di componenti COM con ClickOnce](../deployment/deploying-com-components-with-clickonce.md)   
 [Compilazione di applicazioni ClickOnce dalla riga di comando](../deployment/building-clickonce-applications-from-the-command-line.md)   
 [Debug di applicazioni ClickOnce in cui si usa System.Deployment.Application](../deployment/debugging-clickonce-applications-that-use-system-deployment-application.md)



