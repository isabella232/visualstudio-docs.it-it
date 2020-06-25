---
title: Sicurezza e distribuzione di ClickOnce | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d33e99d11007ca4684f3d875620e2baeb7ddc1e7
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/23/2020
ms.locfileid: "85285494"
---
# <a name="clickonce-security-and-deployment"></a>Sicurezza e distribuzione di ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]è una tecnologia di distribuzione che consente di creare applicazioni basate su Windows con aggiornamento automatico che possono essere installate ed eseguite con interazioni utente minime. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]fornisce supporto completo per la pubblicazione e l'aggiornamento di applicazioni distribuite con la tecnologia ClickOnce se i progetti sono stati sviluppati con Visual Basic e Visual C#. Per informazioni sulla distribuzione di applicazioni Visual C++, vedere [la pagina relativa alla distribuzione ClickOnce per le applicazioni Visual C++](/cpp/windows/clickonce-deployment-for-visual-cpp-applications).

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]la distribuzione si verifica in tre problemi principali:

- **Difficoltà di aggiornamento delle applicazioni.** Con Microsoft Windows Installer distribuzione, ogni volta che un'applicazione viene aggiornata, l'utente può installare un aggiornamento, un file msp e applicarlo al prodotto installato; con la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] distribuzione, è possibile fornire aggiornamenti automaticamente. Vengono scaricate solo le parti dell'applicazione che sono state modificate, quindi l'applicazione aggiornata completa viene reinstallata da una nuova cartella affiancata.

- **Effetti sul computer dell'utente.** Con Windows Installer distribuzione, le applicazioni spesso si basano su componenti condivisi, con la possibilità di conflitti di controllo delle versioni. con la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] distribuzione, ogni applicazione è indipendente e non può interferire con altre applicazioni.

- **Autorizzazioni di sicurezza.** Windows Installer distribuzione richiede autorizzazioni amministrative e consente solo l'installazione limitata degli utenti. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]la distribuzione consente agli utenti non amministratori di installare e concedere solo le autorizzazioni di sicurezza per l'accesso al codice necessarie per l'applicazione.

  In passato, questi problemi causavano talvolta la creazione di applicazioni Web anziché di applicazioni basate su Windows, sacrificando un'interfaccia utente avanzata per semplificare l'installazione. Utilizzando le applicazioni distribuite mediante [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , è possibile sfruttare al meglio entrambe le tecnologie.

## <a name="what-is-a-clickonce-application"></a>Che cos'è un'applicazione ClickOnce?
 Un' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione è qualsiasi Windows Presentation Foundation (*. XBAP*), Windows Forms (*exe*), applicazione console (*exe*) o soluzione Office (con*estensione dll*) pubblicata usando la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] tecnologia. È possibile pubblicare un' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione in tre modi diversi: da una pagina Web, da una condivisione file di rete o da un supporto come un CD-ROM. Un' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione può essere installata nel computer di un utente finale ed eseguita localmente anche quando il computer è offline oppure può essere eseguito in modalità solo online senza installare in modo permanente alcun elemento nel computer dell'utente finale. Per ulteriori informazioni, vedere [scelta di una strategia di distribuzione ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]le applicazioni possono essere con aggiornamento automatico; possono verificare la disponibilità di versioni più recenti e sostituire automaticamente eventuali file aggiornati. Lo sviluppatore può specificare il comportamento di aggiornamento; un amministratore di rete può controllare le strategie di aggiornamento, ad esempio, rendendo obbligatorio un aggiornamento. È anche possibile eseguire il rollback degli aggiornamenti a una versione precedente dall'utente finale o da un amministratore. Per ulteriori informazioni, vedere [scelta di una strategia di aggiornamento ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).

 Poiché [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] le applicazioni sono isolate, l'installazione o l'esecuzione di un' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione non può interrompere le applicazioni esistenti. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]le applicazioni sono autosufficienti; ogni [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione viene installata ed eseguita da una cache protetta per singolo utente e per ogni applicazione. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]le applicazioni vengono eseguite nelle aree di sicurezza Internet o Intranet. Se necessario, l'applicazione può richiedere autorizzazioni di protezione elevate. Per altre informazioni, vedere [proteggere le applicazioni ClickOnce](../deployment/securing-clickonce-applications.md).

## <a name="how-clickonce-security-works"></a>Funzionamento della sicurezza ClickOnce
 La sicurezza di base [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] è basata sui certificati, i criteri di sicurezza dall'accesso di codice e la richiesta di attendibilità ClickOnce.

### <a name="certificates"></a>Certificati
 I certificati Authenticode vengono usati per verificare l'autenticità dell'editore dell'applicazione. Utilizzando Authenticode per la distribuzione di applicazioni, ClickOnce consente di evitare che un programma dannoso si tratti di un programma legittimo proveniente da un'origine attendibile stabilita. Facoltativamente, i certificati possono essere usati anche per firmare i manifesti dell'applicazione e della distribuzione per dimostrare che i file non sono stati manomessi. Per ulteriori informazioni, vedere [ClickOnce e Authenticode](../deployment/clickonce-and-authenticode.md). I certificati possono essere usati anche per configurare i computer client in modo che dispongano di un elenco di autori attendibili. Se un'applicazione deriva da un autore attendibile, può essere installata senza alcuna interazione dell'utente. Per altre informazioni, vedere [Cenni preliminari sulla distribuzione di applicazioni attendibili](../deployment/trusted-application-deployment-overview.md).

### <a name="code-access-security"></a>Sicurezza dall'accesso di codice
 La sicurezza dall'accesso di codice consente di limitare l'accesso del codice alle risorse protette. Nella maggior parte dei casi, è possibile scegliere le aree Internet o Intranet locale per limitare le autorizzazioni. Usare la pagina **sicurezza** in **ProjectDesigner** per richiedere l'area appropriata per l'applicazione. È anche possibile eseguire il debug di applicazioni con autorizzazioni limitate per emulare l'esperienza dell'utente finale. Per altre informazioni, vedere [Sicurezza dall'accesso di codice per applicazioni ClickOnce](../deployment/code-access-security-for-clickonce-applications.md).

### <a name="clickonce-trust-prompt"></a>Richiesta di attendibilità ClickOnce
 Se l'applicazione richiede più autorizzazioni rispetto a quelle consentite dalla zona, è possibile che all'utente finale venga richiesto di prendere una decisione di attendibilità. L'utente finale può decidere se le applicazioni ClickOnce come Windows Forms applicazioni, Windows Presentation Foundation applicazioni, applicazioni console, applicazioni browser XAML e soluzioni Office sono attendibili per l'esecuzione. Per ulteriori informazioni, vedere [procedura: configurare il comportamento della richiesta di attendibilità ClickOnce](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md).

## <a name="how-clickonce-deployment-works"></a>Come funziona la distribuzione ClickOnce
 L' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] architettura di distribuzione principale si basa su due file manifesto XML: un manifesto dell'applicazione e un manifesto di distribuzione. I file vengono utilizzati per descrivere la posizione di installazione delle applicazioni ClickOnce, il modo in cui vengono aggiornate e il momento in cui vengono aggiornate.

### <a name="publish-clickonce-applications"></a>Pubblicare applicazioni ClickOnce
 Il manifesto dell'applicazione descrive l'applicazione stessa. Sono inclusi gli assembly, le dipendenze e i file che costituiscono l'applicazione, le autorizzazioni necessarie e il percorso in cui saranno disponibili gli aggiornamenti. Lo sviluppatore dell'applicazione crea il manifesto dell'applicazione usando la pubblicazione guidata in Visual Studio o il Strumento per la generazione e la modifica di manifesti (*Mage.exe*) in [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)] . Per altre informazioni, vedere [procedura: pubblicare un'applicazione ClickOnce mediante la pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

 Il manifesto di distribuzione descrive il modo in cui viene distribuita l'applicazione. Inclusi il percorso del manifesto dell'applicazione e la versione dell'applicazione che i client devono eseguire.

### <a name="deploy-clickonce-applications"></a>Distribuire applicazioni ClickOnce
 Dopo la creazione, il manifesto di distribuzione viene copiato nella posizione della distribuzione, che può essere un server Web, un file condiviso in rete o un supporto come un CD. Il manifesto dell'applicazione e tutti i file dell'applicazione vengono copiati anche in un percorso di distribuzione specificato nel manifesto della distribuzione. Tale posizione può essere la stessa posizione della distribuzione o un'altra posizione. Quando si usa la **pubblicazione guidata** in Visual Studio, le operazioni di copia vengono eseguite automaticamente.

### <a name="install-clickonce-applications"></a>Installare applicazioni ClickOnce
 Dopo la distribuzione nella posizione specificata, gli utenti finali possono scaricare e installare l'applicazione con un clic su un'icona che rappresenta il file manifesto di distribuzione in una pagina Web o in una cartella. Nella maggior parte dei casi, l'utente finale viene visualizzata con una semplice finestra di dialogo in cui viene chiesto all'utente di confermare l'installazione, dopo la quale l'installazione continua e l'applicazione viene avviata senza ulteriori interventi. Nei casi in cui l'applicazione richiede autorizzazioni elevate o se l'applicazione non è firmata da un certificato attendibile, nella finestra di dialogo viene anche chiesto all'utente di concedere l'autorizzazione prima che l'installazione possa continuare. Sebbene le installazioni ClickOnce siano per utente, l'elevazione delle autorizzazioni potrebbe essere necessaria se sono presenti prerequisiti che richiedono privilegi di amministratore. Per ulteriori informazioni sulle autorizzazioni elevate, vedere [protezione di applicazioni ClickOnce](../deployment/securing-clickonce-applications.md).

 I certificati possono essere considerati attendibili a livello di computer o di organizzazione, in modo che le applicazioni ClickOnce firmate con un certificato attendibile possano essere installate automaticamente. Per ulteriori informazioni sui certificati attendibili, vedere [Cenni preliminari sulla distribuzione di applicazioni attendibili](../deployment/trusted-application-deployment-overview.md).

 È possibile aggiungere l'applicazione al menu **Start** dell'utente e al gruppo **Installazione applicazioni** nel **Pannello di controllo**. A differenza di altre tecnologie di distribuzione, non viene aggiunto nulla alla cartella **programmi** o al registro di sistema e non sono necessari diritti amministrativi per l'installazione

> [!NOTE]
> È anche possibile impedire che l'applicazione venga aggiunta al menu **Start** e al gruppo **installazione** applicazioni, in modo da comportarsi come un'applicazione Web. Per ulteriori informazioni, vedere [scelta di una strategia di distribuzione ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).

### <a name="update-clickonce-applications"></a>Aggiornare le applicazioni ClickOnce
 Quando gli sviluppatori di applicazioni creano una versione aggiornata dell'applicazione, generano un nuovo manifesto dell'applicazione e copiano i file in un percorso di distribuzione, in genere una cartella di pari livello nella cartella di distribuzione dell'applicazione originale. L'amministratore aggiorna il manifesto di distribuzione inserendo un riferimento alla posizione della nuova versione dell'applicazione.

> [!NOTE]
> Per eseguire questa procedura, è possibile usare la **pubblicazione guidata** in Visual Studio.

 Oltre alla posizione di distribuzione, il manifesto di distribuzione contiene anche una posizione di aggiornamento (una pagina Web o un file condiviso in rete) in cui l'applicazione verifica la disponibilità di versioni aggiornate. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Le proprietà di **pubblicazione** vengono utilizzate per specificare quando e con quale frequenza l'applicazione deve verificare la disponibilità di aggiornamenti. Il comportamento di aggiornamento può essere specificato nel manifesto di distribuzione oppure può essere presentato come scelta utente nell'interfaccia utente dell'applicazione per mezzo delle [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] API. Inoltre le proprietà di **pubblicazione** possono essere impiegate per rendere obbligatori o per annullare gli aggiornamenti a vantaggio di una versione precedente. Per ulteriori informazioni, vedere [scelta di una strategia di aggiornamento ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).

### <a name="third-party-installers"></a>Programmi di installazione di terze parti
 È possibile personalizzare il programma di installazione ClickOnce per installare componenti di terze parti insieme all'applicazione. È necessario disporre del pacchetto ridistribuibile (file con estensione exe o MSI) e descrivere il pacchetto con un manifesto del prodotto indipendente dalla lingua e un manifesto del pacchetto specifico della lingua. Per ulteriori informazioni, vedere [creazione di pacchetti del programma di avvio automatico](../deployment/creating-bootstrapper-packages.md).

## <a name="clickonce-tools"></a>Strumenti ClickOnce
 La tabella seguente illustra gli strumenti che è possibile usare per generare, modificare, firmare e firmare nuovamente i manifesti dell'applicazione e della distribuzione.

|Strumento|Description|
|----------|-----------------|
|[Pagina Sicurezza, Progettazione progetti](../ide/reference/security-page-project-designer.md)|Firma i manifesti dell'applicazione e della distribuzione.|
|[Pagina Pubblica, Progettazione progetti](../ide/reference/publish-page-project-designer.md)|Genera e modifica i manifesti dell'applicazione e della distribuzione per applicazioni Visual Basic e Visual C#.|
|[*Mage.exe* (strumento per la generazione e la modifica di manifesti)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)|Genera i manifesti dell'applicazione e della distribuzione per le applicazioni Visual Basic, Visual C# e Visual C++.<br /><br /> Firma e firma nuovamente i manifesti dell'applicazione e della distribuzione.<br /><br /> Può essere eseguito da script batch e dal prompt dei comandi.|
|[*MageUI.exe* (strumento per la generazione e la modifica di manifesti, client grafico)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)|Genera e modifica i manifesti dell'applicazione e della distribuzione.<br /><br /> Firma e firma nuovamente i manifesti dell'applicazione e della distribuzione.|
|[GenerateApplicationManifest (attività)](../msbuild/generateapplicationmanifest-task.md)|Genera il manifesto dell'applicazione.<br /><br /> Può essere eseguito da MSBuild. Per altre informazioni, vedere [riferimenti a MSBuild](../msbuild/msbuild-reference.md).|
|[GenerateDeploymentManifest (attività)](../msbuild/generatedeploymentmanifest-task.md)|Genera il manifesto della distribuzione.<br /><br /> Può essere eseguito da MSBuild. Per altre informazioni, vedere [riferimenti a MSBuild](../msbuild/msbuild-reference.md).|
|[SignFile (attività)](../msbuild/signfile-task.md)|Firma i manifesti dell'applicazione e della distribuzione.<br /><br /> Può essere eseguito da MSBuild. Per altre informazioni, vedere [riferimenti a MSBuild](../msbuild/msbuild-reference.md).|
|[Microsoft.Build.Tasks.Deployment.ManifestUtilities](/dotnet/api/microsoft.build.tasks.deployment.manifestutilities)|Sviluppare un'applicazione personalizzata per generare i manifesti dell'applicazione e della distribuzione.|

 Nella tabella seguente viene illustrata la versione .NET Framework necessaria per supportare le applicazioni ClickOnce in questi browser.

|Browser|Versione di .NET Framework|
|-------------|----------------------------|
|Internet Explorer|2.0, 3.0, 3.5, 3.5 SP1, 4|
|Firefox|2.0 SP1, 3.5 SP1, 4|
|Chrome|3,5|
|Microsoft Edge|3,5|

## <a name="see-also"></a>Vedi anche
- [Distribuzione ClickOnce in Windows Vista](../deployment/clickonce-deployment-on-windows-vista.md)
- [Pubblicare applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Proteggere le applicazioni ClickOnce](../deployment/securing-clickonce-applications.md)
- [Distribuire componenti COM con ClickOnce](../deployment/deploying-com-components-with-clickonce.md)
- [Compilare applicazioni ClickOnce dalla riga di comando](../deployment/building-clickonce-applications-from-the-command-line.md)
- [Eseguire il debug di applicazioni ClickOnce che usano System. Deployment. Application](../deployment/debugging-clickonce-applications-that-use-system-deployment-application.md)
