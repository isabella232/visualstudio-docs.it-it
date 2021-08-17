---
title: ClickOnce Sicurezza e distribuzione | Microsoft Docs
description: Informazioni sul Visual Studio per ClickOnce, una tecnologia di distribuzione che consente di creare applicazioni basate su Windows ad aggiornamento automatico.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 264dcfd427b70c452a86caee4fc20c3421a4e9aa
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122073903"
---
# <a name="clickonce-security-and-deployment"></a>Sicurezza e distribuzione di ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]è una tecnologia di distribuzione che consente di creare applicazioni basate su Windows ad aggiornamento automatico che possono essere installate ed eseguite con un'interazione utente minima. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]offre supporto completo per la pubblicazione e l'aggiornamento di applicazioni distribuite con ClickOnce se i progetti sono stati sviluppati con Visual Basic e Visual C#. Per informazioni sulla distribuzione di Visual C++, vedere [distribuzione ClickOnce per Visual C++ applicazioni](/cpp/windows/clickonce-deployment-for-visual-cpp-applications).

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] la distribuzione consente di risolvere tre problemi principali nella distribuzione:

- **Difficoltà di aggiornamento delle applicazioni.** Con la distribuzione di Microsoft Windows Installer, ogni volta che un'applicazione viene aggiornata, l'utente può installare un aggiornamento, un file msp e applicarlo al prodotto installato; con [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] la distribuzione, è possibile fornire automaticamente gli aggiornamenti. Vengono scaricate solo le parti dell'applicazione modificate e quindi l'applicazione aggiornata completa viene reinstallata da una nuova cartella side-by-side.

- **Impatto sul computer dell'utente.** Con Windows del programma di installazione, le applicazioni spesso si basano su componenti condivisi, con il rischio di conflitti di controllo delle versioni; con [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] la distribuzione, ogni applicazione è autonoma e non può interferire con altre applicazioni.

- **Autorizzazioni di sicurezza.** Windows La distribuzione del programma di installazione richiede autorizzazioni amministrative e consente solo un'installazione utente limitata. consente agli utenti non amministratori di installare e concede solo le autorizzazioni di sicurezza dall'accesso [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] di codice necessarie per l'applicazione.

  In passato, questi problemi talvolta causavano la decisione degli sviluppatori di creare applicazioni Web anziché applicazioni basate su Windows, con un'interfaccia utente completa per semplificare l'installazione. Usando le applicazioni distribuite con [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , è possibile ottenere il meglio di entrambe le tecnologie.

## <a name="what-is-a-clickonce-application"></a>Che cos'è un'applicazione ClickOnce?
 Un'applicazione è qualsiasi [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Windows Presentation Foundation (*.xbap),* Windows Forms (*.exe*), applicazione console (*.exe*) o soluzione Office (*.dll*) pubblicata usando la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] tecnologia . È possibile pubblicare un'applicazione in tre modi diversi: da una pagina Web, da una condivisione file di rete o da supporti, ad esempio [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] un CD-ROM. Un'applicazione può essere installata nel computer di un utente finale ed eseguita localmente anche quando il computer è offline oppure può essere eseguita in modalità solo online senza installare in modo permanente nulla nel [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] computer dell'utente finale. Per altre informazioni, vedere [Scegliere una strategia ClickOnce distribuzione.](../deployment/choosing-a-clickonce-deployment-strategy.md)

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] le applicazioni possono essere ad aggiornamento automatico. possono verificare la presenza di versioni più recenti non appena diventano disponibili e sostituire automaticamente eventuali file aggiornati. Lo sviluppatore può specificare il comportamento di aggiornamento; un amministratore di rete può controllare le strategie di aggiornamento, ad esempio, rendendo obbligatorio un aggiornamento. È anche possibile eseguire il rollback degli aggiornamenti a una versione precedente da parte dell'utente finale o di un amministratore. Per altre informazioni, vedere [Scegliere una strategia ClickOnce di aggiornamento.](../deployment/choosing-a-clickonce-update-strategy.md)

 Poiché [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] le applicazioni sono isolate, l'installazione o l'esecuzione di [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] un'applicazione non può interrompere le applicazioni esistenti. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] le applicazioni sono indipendenti; ogni [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione viene installata ed eseguita da una cache sicura per utente e per applicazione. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] le applicazioni vengono eseguite nelle aree di sicurezza Internet o Intranet. Se necessario, l'applicazione può richiedere autorizzazioni di protezione elevate. Per altre informazioni, vedere [Proteggere ClickOnce applicazioni](../deployment/securing-clickonce-applications.md).

## <a name="how-clickonce-security-works"></a>Funzionamento ClickOnce sicurezza
 La sicurezza di base è basata su certificati, criteri di sicurezza [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dall'accesso di codice e richiesta ClickOnce attendibilità.

### <a name="certificates"></a>Certificati
 I certificati Authenticode vengono usati per verificare l'autenticità dell'editore dell'applicazione. Usando Authenticode per la distribuzione di applicazioni, ClickOnce contribuisce a impedire a un programma dannoso di considerarsi un programma legittimo proveniente da un'origine consolidata e attendibile. Facoltativamente, i certificati possono essere usati anche per firmare i manifesti dell'applicazione e della distribuzione per dimostrare che i file non sono stati manomessi. Per altre informazioni, vedere [ClickOnce e Authenticode.](../deployment/clickonce-and-authenticode.md) I certificati possono essere usati anche per configurare i computer client in modo che dispongono di un elenco di autori attendibili. Se un'applicazione proviene da un autore attendibile, può essere installata senza alcuna interazione dell'utente. Per altre informazioni, vedere [Cenni preliminari sulla distribuzione di applicazioni attendibili](../deployment/trusted-application-deployment-overview.md).

### <a name="code-access-security"></a>Sicurezza dall'accesso di codice
 La sicurezza dall'accesso di codice consente di limitare l'accesso del codice alle risorse protette. Nella maggior parte dei casi, è possibile scegliere le aree Internet o Intranet locale per limitare le autorizzazioni. Usare la **pagina Sicurezza** in **ProjectDesigner per** richiedere l'area appropriata per l'applicazione. È anche possibile eseguire il debug di applicazioni con autorizzazioni limitate per emulare l'esperienza dell'utente finale. Per altre informazioni, vedere [Sicurezza dall'accesso di codice per applicazioni ClickOnce](../deployment/code-access-security-for-clickonce-applications.md).

### <a name="clickonce-trust-prompt"></a>Richiesta di attendibilità ClickOnce
 Se l'applicazione richiede più autorizzazioni di quelle concesse dall'area, all'utente finale può essere richiesto di prendere una decisione di attendibilità. L'utente finale può decidere se l'esecuzione di applicazioni ClickOnce quali applicazioni Windows Forms, applicazioni Windows Presentation Foundation, applicazioni console, applicazioni browser XAML e soluzioni Office è attendibile. Per altre informazioni, vedere [Procedura: Configurare il comportamento della richiesta ClickOnce attendibilità.](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)

## <a name="how-clickonce-deployment-works"></a>Come funziona la distribuzione ClickOnce
 L'architettura [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] di distribuzione di base si basa su due file manifesto XML: un manifesto dell'applicazione e un manifesto della distribuzione. I file vengono usati per descrivere la ClickOnce da cui vengono installate le applicazioni, come vengono aggiornate e quando vengono aggiornate.

### <a name="publish-clickonce-applications"></a>Pubblicare applicazioni ClickOnce
 Il manifesto dell'applicazione descrive l'applicazione stessa. Sono inclusi gli assembly, le dipendenze e i file che costituiscono l'applicazione, le autorizzazioni necessarie e il percorso in cui saranno disponibili gli aggiornamenti. Lo sviluppatore dell'applicazione crea il manifesto dell'applicazione usando la Pubblicazione guidata in Visual Studio o il Strumento per la generazione e la modifica di manifesti (*Mage.exe*) in [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)] . Per altre informazioni, vedere [Procedura: Pubblicare un'ClickOnce usando la Pubblicazione guidata.](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)

 Il manifesto di distribuzione descrive il modo in cui viene distribuita l'applicazione. Ciò include il percorso del manifesto dell'applicazione e la versione dell'applicazione che i client devono eseguire.

### <a name="deploy-clickonce-applications"></a>Distribuire ClickOnce applicazioni
 Dopo la creazione, il manifesto di distribuzione viene copiato nella posizione della distribuzione, che può essere un server Web, un file condiviso in rete o un supporto come un CD. Anche il manifesto dell'applicazione e tutti i file dell'applicazione vengono copiati in un percorso di distribuzione specificato nel manifesto della distribuzione. Tale posizione può essere la stessa posizione della distribuzione o un'altra posizione. Quando si usa **la Pubblicazione guidata** in Visual Studio, le operazioni di copia vengono eseguite automaticamente.

### <a name="install-clickonce-applications"></a>Installare ClickOnce applicazioni
 Dopo la distribuzione nella posizione specificata, gli utenti finali possono scaricare e installare l'applicazione con un clic su un'icona che rappresenta il file manifesto di distribuzione in una pagina Web o in una cartella. Nella maggior parte dei casi, all'utente finale viene visualizzata una semplice finestra di dialogo che richiede all'utente di confermare l'installazione, dopo di che l'installazione procede e l'applicazione viene avviata senza alcun intervento aggiuntivo. Nei casi in cui l'applicazione richiede autorizzazioni elevate o se l'applicazione non è firmata da un certificato attendibile, la finestra di dialogo chiede anche all'utente di concedere l'autorizzazione prima che l'installazione possa continuare. Anche ClickOnce installazioni sono per utente, l'elevazione delle autorizzazioni può essere necessaria se sono presenti prerequisiti che richiedono privilegi di amministratore. Per altre informazioni sulle autorizzazioni elevate, vedere [Protezione di ClickOnce applicazioni](../deployment/securing-clickonce-applications.md).

 I certificati possono essere considerati attendibili a livello di computer o aziendale, in modo che ClickOnce applicazioni firmate con un certificato attendibile possano essere installate automaticamente. Per altre informazioni sui certificati attendibili, vedere [Panoramica della distribuzione di applicazioni attendibili.](../deployment/trusted-application-deployment-overview.md)

 L'applicazione può essere aggiunta al menu **Start** dell'utente e **al** gruppo Installazione applicazioni nel **Pannello di controllo**. A differenza di altre tecnologie di distribuzione, non viene aggiunto nulla alla cartella **Programmi** o al Registro di sistema e non sono necessari diritti amministrativi per l'installazione

> [!NOTE]
> È anche possibile impedire l'aggiunta dell'applicazione  al menu **Start** e al gruppo Installazione applicazioni, in modo che si comporti come un'applicazione Web. Per altre informazioni, vedere [Scegliere una strategia ClickOnce distribuzione.](../deployment/choosing-a-clickonce-deployment-strategy.md)

### <a name="update-clickonce-applications"></a>Aggiornare ClickOnce applicazioni
 Quando gli sviluppatori di applicazioni creano una versione aggiornata dell'applicazione, generano un nuovo manifesto dell'applicazione e copiano i file in un percorso di distribuzione, in genere una cartella di pari livello nella cartella di distribuzione dell'applicazione originale. L'amministratore aggiorna il manifesto di distribuzione inserendo un riferimento alla posizione della nuova versione dell'applicazione.

> [!NOTE]
> La **Pubblicazione guidata** in Visual Studio può essere usata per eseguire questi passaggi.

 Oltre alla posizione di distribuzione, il manifesto di distribuzione contiene anche una posizione di aggiornamento (una pagina Web o un file condiviso in rete) in cui l'applicazione verifica la disponibilità di versioni aggiornate. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]**Le** proprietà di pubblicazione vengono usate per specificare quando e con quale frequenza l'applicazione deve verificare la disponibilità di aggiornamenti. Il comportamento di aggiornamento può essere specificato nel manifesto della distribuzione oppure può essere presentato come scelte dell'utente nell'interfaccia utente dell'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] tramite le API. Inoltre le proprietà di **pubblicazione** possono essere impiegate per rendere obbligatori o per annullare gli aggiornamenti a vantaggio di una versione precedente. Per altre informazioni, vedere [Scelta di una strategia ClickOnce di aggiornamento.](../deployment/choosing-a-clickonce-update-strategy.md)

### <a name="third-party-installers"></a>Programmi di installazione di terze parti
 È possibile personalizzare il programma ClickOnce per installare componenti di terze parti insieme all'applicazione. È necessario disporre del pacchetto ridistribuibile (file .exe o .msi) e descrivere il pacchetto con un manifesto del prodotto indipendente dalla lingua e un manifesto del pacchetto specifico della lingua. Per altre informazioni, vedere Creazione [di pacchetti del programma di avvio automatico.](../deployment/creating-bootstrapper-packages.md)

## <a name="clickonce-tools"></a>ClickOnce strumenti
 La tabella seguente illustra gli strumenti che è possibile usare per generare, modificare, firmare e firmare nuovamente i manifesti dell'applicazione e della distribuzione.

|Strumento|Descrizione|
|----------|-----------------|
|[Pagina Sicurezza, Progettazione progetti](../ide/reference/security-page-project-designer.md)|Firma i manifesti dell'applicazione e della distribuzione.|
|[Pagina Pubblica, Progettazione progetti](../ide/reference/publish-page-project-designer.md)|Genera e modifica i manifesti dell'applicazione e della distribuzione per Visual Basic applicazioni Visual C#.|
|[*Mage.exe* (Strumento per la generazione e la modifica di manifesti)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)|Genera i manifesti dell'applicazione e della distribuzione per Visual Basic, Visual C# e Visual C++ applicazioni.<br /><br /> Firma e firma nuovamente i manifesti dell'applicazione e della distribuzione.<br /><br /> Può essere eseguito da script batch e dal prompt dei comandi.|
|[*MageUI.exe* (Strumento per la generazione e la modifica di manifesti, client grafico)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)|Genera e modifica i manifesti dell'applicazione e della distribuzione.<br /><br /> Firma e firma nuovamente i manifesti dell'applicazione e della distribuzione.|
|[GenerateApplicationManifest (attività)](../msbuild/generateapplicationmanifest-task.md)|Genera il manifesto dell'applicazione.<br /><br /> Può essere eseguito da MSBuild. Per altre informazioni, vedere MSBuild [riferimento](../msbuild/msbuild-reference.md)a .|
|[GenerateDeploymentManifest (attività)](../msbuild/generatedeploymentmanifest-task.md)|Genera il manifesto della distribuzione.<br /><br /> Può essere eseguito da MSBuild. Per altre informazioni, vedere MSBuild [riferimento](../msbuild/msbuild-reference.md)a .|
|[SignFile (attività)](../msbuild/signfile-task.md)|Firma i manifesti dell'applicazione e della distribuzione.<br /><br /> Può essere eseguito da MSBuild. Per altre informazioni, vedere MSBuild [riferimento](../msbuild/msbuild-reference.md)a .|
|[Microsoft.Build.Tasks.Deployment.ManifestUtilities](/dotnet/api/microsoft.build.tasks.deployment.manifestutilities)|Sviluppare un'applicazione per generare i manifesti dell'applicazione e della distribuzione.|

 La tabella seguente illustra la .NET Framework necessaria per supportare ClickOnce applicazioni in questi browser.

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
- [Eseguire ClickOnce applicazioni che usano System.Deployment.Application](../deployment/debugging-clickonce-applications-that-use-system-deployment-application.md)
