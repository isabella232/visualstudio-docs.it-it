---
title: Panoramica del modello di programmazione delle estensioni SharePoint tools
titleSuffix: ''
description: Leggere una panoramica del modello di programmazione delle estensioni SharePoint tools. Implementare le interfacce di estendibilità. Comprendere i modelli a oggetti.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio, extending tools
- SharePoint development in Visual Studio, extensibility object models
- SharePoint development in Visual Studio, extending tools
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: f96c991315483ab4aa8c3764ba9415cf67077a1d
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126710141"
---
# <a name="overview-of-the-programming-model-of-sharepoint-tools-extensions"></a>Panoramica del modello di programmazione delle estensioni SharePoint tools
  Quando si crea un'estensione per gli strumenti di SharePoint in Visual Studio, si inizia implementando una o più interfacce di estendibilità che vengono esposte dagli strumenti di SharePoint. Nella maggior parte dei casi, si useranno anche altri tipi forniti dagli strumenti di SharePoint per implementare le funzionalità nell'estensione. In alcuni scenari è possibile usare anche tipi in altri modelli a oggetti forniti da Visual Studio e SharePoint. È necessario comprendere lo scopo di ciascuno dei modelli a oggetti e sapere come usarli per creare estensioni per gli strumenti di SharePoint.

## <a name="extend-the-sharepoint-tools-by-implementing-extensibility-interfaces"></a>Estendere gli strumenti SharePoint implementando le interfacce di estendibilità
 Visual Studio usa Managed Extensibility Framework (MEF) in .NET Framework 4 per fornire il modello di estendibilità per gli strumenti di SharePoint. MEF è un'API (implementata nell'assembly System.ComponentModel.Composition) che consente alle applicazioni di esporre i punti di estendibilità e individuare e caricare le estensioni in fase di esecuzione. Per altre informazioni su MEF, vedere Managed Extensibility Framework &#40;[MEF&#41;](/dotnet/framework/mef/index).

 Per estendere gli strumenti di SharePoint, è necessario implementare una o più interfacce di estendibilità che vengono esposte da Visual Studio. È inoltre necessario applicare l'attributo <xref:System.ComponentModel.Composition.ExportAttribute> e, se necessario, gli altri attributi specifici degli strumenti di SharePoint all'implementazione dell'interfaccia. Nella tabella seguente vengono elencate le interfacce che è possibile implementare per estendere gli strumenti di SharePoint.

|Interfaccia|Descrizione|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>|Implementare questa interfaccia per definire un nuovo tipo di elemento di progetto SharePoint. Per un esempio, vedere [Procedura: Definire un](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)tipo di elemento SharePoint progetto .|
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>|Implementare questa interfaccia per estendere un tipo di elemento di progetto SharePoint già installato in Visual Studio. Per un esempio, vedere [Procedura: Creare](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)un'estensione di SharePoint progetto .|
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>|Implementare questa interfaccia per estendere i progetti SharePoint. Per un esempio, vedere [Procedura: Creare un'estensione SharePoint progetto .](../sharepoint/how-to-create-a-sharepoint-project-extension.md)|
|<xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep>|Implementare questa interfaccia per definire un nuovo passaggio di distribuzione che può essere eseguito quando un elemento di progetto SharePoint viene distribuito o ritratto. Per un esempio, vedere [Procedura dettagliata: Creare un passaggio di distribuzione personalizzato per SharePoint progetti](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).|
|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>|Implementare questa interfaccia per estendere un nodo esistente nel nodo **SharePoint connessioni** nella finestra **Esplora server.** Per un esempio, vedere [Procedura: Estendere un](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)nodo SharePoint in Esplora server .|
|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>|Implementare questa interfaccia per definire un nuovo tipo di nodo nel nodo SharePoint **Connections** **nella** finestra Esplora server. Per un esempio, vedere [Procedura: Estendere un](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)nodo SharePoint in Esplora server .|
|<xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule>|Implementare questa interfaccia per definire una regola di convalida della funzionalità personalizzata. Per un esempio, vedere [Procedura: Creare funzionalità personalizzate](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md)e regole di convalida dei pacchetti per SharePoint soluzioni .|
|<xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule>|Implementare questa interfaccia per definire una regola di convalida del pacchetto personalizzata. Per un esempio, vedere [Procedura: Creare funzionalità personalizzate](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md)e regole di convalida dei pacchetti per SharePoint soluzioni .|

 Dopo aver implementato un'estensione degli strumenti di SharePoint, è necessario distribuire l'assembly dell'estensione in un pacchetto di Visual Studio Extension (VSIX) per consentire a Visual Studio di individuare e caricare l'estensione. Per altre informazioni, vedere [Deploy extensions for the SharePoint tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="understand-the-object-models-that-you-use-in-sharepoint-tools-extensions"></a>Comprendere i modelli a oggetti che si usano nelle estensioni SharePoint strumenti
 È possibile usare vari modelli a oggetti quando si creano estensioni per gli strumenti di SharePoint:

- *SharePoint strumenti a oggetti*. Questo modello a oggetti fornisce le interfacce di estendibilità implementate per creare le estensioni degli strumenti di SharePoint e altri tipi correlati.

- *Visual Studio modelli a oggetti di automazione e integrazione*. Usare questi modelli a oggetti per accedere alle funzionalità di Visual Studio che esulano dall'ambito del modello a oggetti degli strumenti di SharePoint.

    > [!NOTE]
    > È possibile convertire alcuni oggetti nel modello a oggetti degli strumenti di SharePoint in oggetti del modello a oggetti di automazione e integrazione di Visual Studio e viceversa, tramite il servizio di progetto SharePoint. Per altre informazioni, vedere [Convert between SharePoint project system types and other Visual Studio project types](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).

- *SharePoint server e i modelli a oggetti client*. Usare questi modelli a oggetti per modificare un sito di SharePoint o per recuperare dati da un sito di SharePoint dal contesto di un'estensione degli strumenti di SharePoint.

### <a name="sharepoint-tools-object-model"></a>SharePoint a oggetti degli strumenti di configurazione
 Ogni estensione degli strumenti di SharePoint usa dei tipi nel modello a oggetti degli strumenti di SharePoint per definire il comportamento e le funzionalità principali dell'estensione. Le tabelle seguenti descrivono gli spazi dei nomi inclusi in questo modello a oggetti dall'assembly che li contiene.

#### <a name="microsoftvisualstudiosharepointdll"></a>Microsoft.VisualStudio.SharePoint.dll

|Spazio dei nomi|Descrizione|
|-|-|
|<xref:Microsoft.VisualStudio.SharePoint>|Contiene i tipi che consentono di estendere e automatizzare il sistema di progetto SharePoint. Ad esempio, è possibile estendere i progetti e gli elementi del progetto SharePoint predefiniti oppure crearne di personalizzati. Per altre informazioni, vedere [Estendere il sistema SharePoint progetto](../sharepoint/extending-the-sharepoint-project-system.md).|
|<xref:Microsoft.VisualStudio.SharePoint.Deployment>|Contiene i tipi usati per estendere il processo di distribuzione per i progetti SharePoint, ad esempio la creazione di configurazioni di distribuzione e di fasi di distribuzione personalizzati. Per altre informazioni, vedere [Estendere SharePoint creazione di pacchetti e distribuzione](../sharepoint/extending-sharepoint-packaging-and-deployment.md).|
|<xref:Microsoft.VisualStudio.SharePoint.Explorer>|Contiene i tipi utilizzati per  estendere i nodi nel  nodo connessioni SharePoint nella finestra Esplora server oppure per definire nuovi tipi di nodi. Per altre informazioni, vedere [Estendere il nodo SharePoint connessioni in Esplora server](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).|
|<xref:Microsoft.VisualStudio.SharePoint.Features>|Contiene i tipi usati per accedere alle definizioni di funzionalità in un progetto SharePoint.|
|<xref:Microsoft.VisualStudio.SharePoint.Packages>|Contiene i tipi usati per accedere alla definizione di un pacchetto in una soluzione SharePoint.|
|<xref:Microsoft.VisualStudio.SharePoint.Validation>|Contiene i tipi usati per personalizzare il comportamento della convalida della funzionalità e del pacchetto per i progetti SharePoint. Per altre informazioni, vedere [Procedura: Creare regole di](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md)convalida dei pacchetti e funzionalità personalizzate per SharePoint soluzioni .|

#### <a name="microsoftvisualstudiosharepointcommandsdll"></a>Microsoft.VisualStudio.SharePoint.Commands.dll

|Spazio dei nomi|Descrizione|
|-|-|
|<xref:Microsoft.VisualStudio.SharePoint.Commands>|Contiene i tipi che è possibile usare per creare comandi *SharePoint personalizzati.* Un comando di SharePoint è un metodo che chiama il modello a oggetti server di SharePoint da un'estensione degli strumenti di SharePoint. Per altre informazioni, vedere [Chiamare nei modelli SharePoint a oggetti](../sharepoint/calling-into-the-sharepoint-object-models.md).|

#### <a name="microsoftvisualstudiosharepointexplorerextensionsdll"></a>Microsoft.VisualStudio.SharePoint.Explorer.Extensions.dll

|Spazio dei nomi|Descrizione|
|-|-|
|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions>|Contiene tipi che è possibile usare per  ottenere informazioni sui nodi Esplora server predefiniti che rappresentano singoli componenti in un sito SharePoint, ad esempio un nodo che rappresenta un elenco, un campo o un tipo di contenuto. Per altre informazioni, vedere [Estendere il nodo SharePoint connessioni in Esplora server](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).|

### <a name="visual-studio-automation-object-model"></a>Visual Studio a oggetti di automazione
 Il modello a oggetti di automazione di Visual Studio fornisce API che è possibile usare per automatizzare i progetti di Visual Studio e l'IDE. Usare il modello a oggetti Visual Studio per eseguire attività correlate al progetto che non sono specifiche dei progetti di SharePoint o per eseguire altre attività di automazione generali in Visual Studio. In genere, questo modello a oggetti viene spesso usato nelle macro e nei componenti aggiuntivi di Visual Studio, ma è possibile usarlo anche nelle estensioni degli strumenti di SharePoint.

 La parte principale del modello a Visual Studio di automazione è definita nell'assembly *EnvDTE.dll* di automazione. Gli *assembly \\ \<version>.dllEnvDTE* forniscono funzionalità aggiuntive introdotte in versioni specifiche Visual Studio. Questi assembly sono inclusi in Visual Studio.

 Per altre informazioni sul modello a oggetti di automazione, vedere informazioni [di Visual Studio SDK.](../extensibility/visual-studio-sdk-reference.md)

### <a name="visual-studio-integration-object-model"></a>Visual Studio a oggetti di integrazione
 Il modello a oggetti di integrazione fornisce API che è possibile usare per aggiungere funzionalità Visual Studio creando un *VSPackage.* Un VSPackage è un modulo che consente di estendere l'IDE di Visual Studio fornendo funzionalità personalizzate quali le finestre degli strumenti, gli editor, le finestre di progettazione, i servizi e i progetti.

 Se si desidera aggiungere una nuova funzionalità di Visual Studio che verrà usata con gli strumenti predefiniti di SharePoint, è possibile usare il modello a oggetti di integrazione. Ad esempio, se si crea un elemento di progetto SharePoint personalizzato che rappresenta un'azione personalizzata per un sito di SharePoint, è possibile creare un VSPackage che implementa una finestra di progettazione per l'azione personalizzata. È possibile associare la finestra di progettazione all'azione personalizzata aggiungendo una voce di menu di scelta rapida all'elemento del progetto che rappresenta **l'azione** personalizzata in Esplora soluzioni . È possibile aprire la finestra di progettazione aprendo il relativo menu di scelta rapida (facendo clic con il pulsante destro del mouse sull'elemento del progetto di azione personalizzata o scegliendolo e quindi premendo  + **MAIUSC F10)** e quindi scegliendo **Apri**.

 Questo modello a oggetti è definito in un set di assembly inclusi in Visual Studio SDK. Alcuni degli assembly principali in questo modello a oggetti *includonoMicrosoft.VisualStudio.Shell.11.0.dll*, *Microsoft.VisualStudio.Shell.Interop.dll* e *Microsoft.VisualStudio.OLE.Interop.dll*.

 Per altre informazioni sul modello a oggetti di integrazione, vedere Panoramica del modello [di](../extensibility/internals/automation-model-overview.md) automazione [e Visual Studio SDK.](../extensibility/visual-studio-sdk-reference.md)

### <a name="sharepoint-object-models"></a>SharePoint a oggetti
 Le estensioni degli strumenti di SharePoint possono usare le API di SharePoint per modificare un sito di SharePoint o per recuperare dati da un sito di SharePoint. [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] e [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] forniscono due modelli a oggetti diversi: un modello a oggetti del server e un modello a oggetti del client.

 È possibile usare le API in entrambi i modelli a oggetti in un'estensione degli strumenti di SharePoint, ma ogni modello a oggetti presenta alcuni vantaggi e svantaggi nel contesto delle estensioni degli strumenti di SharePoint. Per altre informazioni, vedere [Chiamare nei modelli SharePoint a oggetti](../sharepoint/calling-into-the-sharepoint-object-models.md).

|Modello a oggetti|Descrizione|
|------------------|-----------------|
|Modello a oggetti del server|Il modello a oggetti del server fornisce l'accesso a tutte le funzionalità esposte da [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] e [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] a livello di codice. Questo modello a oggetti è progettato per essere usato dalle soluzioni di SharePoint eseguibili nel server di SharePoint. La maggior parte di questo modello a oggetti è definita *nellMicrosoft.SharePoint.dll* assembly. Per altre informazioni sul modello a oggetti del server, vedere [Using the SharePoint Foundation Server-Side Object Model](/previous-versions/office/developer/sharepoint-2010/ee538251(v=office.14)).|
|Modello a oggetti del client|Il modello a oggetti del client è un subset del modello a oggetti del server che può essere usato per interagire con dati di SharePoint da un client remoto o dal server. È progettato per ridurre al minimo il numero di round trip che devono essere eseguiti per le attività comuni. La maggior parte del modello a oggetti client è definita negli *assembly* Microsoft.SharePoint.Client.dll *eMicrosoft.SharePoint.Client.Runtime.dll* client. Per altre informazioni sul modello a oggetti client, vedere [Managed Client Object Model](/previous-versions/office/developer/sharepoint-2010/ee537247(v=office.14)).|

## <a name="see-also"></a>Vedi anche
- [Estendere gli SharePoint in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)
- [Chiamare nei modelli SharePoint a oggetti](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [Usare il SharePoint servizio di progetto](../sharepoint/using-the-sharepoint-project-service.md)
