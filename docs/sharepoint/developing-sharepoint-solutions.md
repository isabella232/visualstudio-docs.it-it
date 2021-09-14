---
title: Sviluppo SharePoint soluzioni | Microsoft Docs
description: Sviluppare SharePoint soluzioni. Conoscere gli elementi di un SharePoint progetto. Informazioni SharePoint proprietà del progetto e dell'elemento di progetto.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: overview
f1_keywords:
- VS.SharePointTools.Project.ProjectProperties
- VS.SharePointTools.Project.ProjectItemProperties
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, overview
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 1998cad37c5fa5f8eecb6a1a7ea34154105662b3
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625313"
---
# <a name="develop-sharepoint-solutions"></a>Sviluppare soluzioni SharePoint

  In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] sono disponibili diversi modelli di tipi di progetto SharePoint per la creazione di siti ed elementi dei siti SharePoint. Per un elenco dei tipi di progetto disponibili, vedere SharePoint [di progetto e di elemento di progetto](../sharepoint/sharepoint-project-and-project-item-templates.md). Di seguito è riportata una descrizione degli elementi e delle proprietà di un progetto SharePoint.

 Per informazioni SharePoint componenti aggiuntivi, vedere Compilare SharePoint [componenti aggiuntivi](/sharepoint/dev/sp-add-ins/sharepoint-add-ins).

## <a name="elements-of-a-sharepoint-project"></a>Elementi di un SharePoint progetto

 I nodi di un progetto SharePoint sono noti come *elementi di SharePoint*. Gli elementi di SharePoint possono anche contenere uno o più file correlati, detti *file degli elementi di SharePoint*, ad esempio file di configurazione [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] , form ASPX e così via.

 Anziché creare progetti tramite modelli di progetto che sono già popolati con i file degli elementi del progetto, è possibile usare il modello **Progetto vuoto** per creare un progetto SharePoint vuoto e successivamente aggiungervi manualmente gli elementi. I progetti SharePoint possono inoltre contenere anche uno o più file di funzionalità (per l'attivazione in SharePoint) e un file di pacchetto in cui distribuire il progetto.

### <a name="special-nodes"></a>Nodi speciali

 Ogni progetto SharePoint contiene due nodi che non possono essere rinominati, eliminati, tagliati, copiati o trascinati dal progetto. Questi nodi sono:

- Funzionalità
- Pacchetto

  Entrambi i nodi vengono sempre visualizzati in tutti i progetti SharePoint anche se non sono stati definiti pacchetti o funzionalità per il progetto.

#### <a name="features-node"></a>Nodo Funzionalità

 Il nodo **Funzionalità** contiene una o più funzionalità del progetto SharePoint. Una funzionalità è un contenitore di estensioni per SharePoint. Una volta distribuita nel server SharePoint, una funzionalità può essere inclusa nelle definizioni dei siti o attivata individualmente dagli amministratori di SharePoint nei siti SharePoint. Per altre informazioni, vedere la pagina relativa all' [uso delle caratteristiche](/previous-versions/office/developer/sharepoint-2010/ms460318(v=office.14)).

 Quando un elemento, ad esempio un tipo di contenuto o un'istanza di elenco, viene aggiunto a un progetto SharePoint, viene anche aggiunto a una funzionalità del nodo **Funzionalità** . L'ambito dell'elemento determina se viene aggiunto a una funzionalità nuova o esistente. Se il nuovo elemento ha lo stesso ambito di una funzionalità esistente, viene aggiunto a tale funzionalità. In caso contrario, l'elemento viene aggiunto a una nuova funzionalità.

 Per aggiungere manualmente una funzionalità, eseguire il comando **Aggiungi funzionalità** dal menu di scelta rapida del nodo della funzionalità. Mediante la finestra di progettazione delle funzionalità, è possibile visualizzare o modificare il contenuto di una funzionalità. Per altre informazioni, vedere [Procedura: Personalizzare una SharePoint funzionalità](../sharepoint/how-to-customize-a-sharepoint-feature.md).

 Quando una funzionalità viene aggiunta a un progetto SharePoint, viene visualizzata in **Esplora soluzioni** come nodo con il nome predefinito Feature *x*.feature, dove *x* è un numero univoco. Dopo che una funzionalità viene distribuita nel server SharePoint, un amministratore di SharePoint può attivarla e renderla disponibile agli utenti del sito SharePoint.

#### <a name="package-node"></a>Nodo del pacchetto

 Il nodo **Pacchetto** contiene un singolo file che serve come meccanismo di distribuzione per il progetto SharePoint. Questo file, noto come pacchetto *della soluzione*, .CAB basato su con . Estensione WSP. Un pacchetto della soluzione è un file distribuibile e riutilizzabile che contiene un set di funzionalità, definizioni dei siti e assembly che è possibile applicare ai siti SharePoint, nonché abilitare o disabilitare individualmente. Il nodo **Pacchetto** contiene sempre anche un file denominato Package.wspdef, un file di definizione [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] per il pacchetto. Quando un pacchetto viene distribuito nel server che esegue SharePoint, l'amministratore di SharePoint può installarlo e attivare le relative funzionalità.

 È possibile visualizzare o modificare il contenuto del pacchetto in Progettazione pacchetti facendo doppio clic sul nodo del pacchetto o aprendo il relativo menu di scelta rapida e scegliendo **Apri**. Per altre informazioni, vedere [Creare SharePoint pacchetti della soluzione](../sharepoint/creating-sharepoint-solution-packages.md).

## <a name="sharepoint-project-and-project-item-properties"></a>SharePoint progetto e elemento di progetto

 Nei progetti SharePoint, come in qualsiasi altro progetto di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , le proprietà sono visualizzate nella finestra Proprietà e nella pagina delle proprietà. Le proprietà visualizzate dipendono dal nodo selezionato.

 Quando un progetto, un elemento di progetto o un nodo del file dell'elemento di progetto SharePoint viene selezionato in **Esplora soluzioni**, nella finestra Proprietà o nella pagina delle proprietà vengono visualizzate le proprietà seguenti:

### <a name="project-properties"></a>Proprietà progetto

|Nome proprietà|Descrizione|
|-------------------|-----------------|
|Configurazione distribuzione attiva|Specifica la serie di passaggi eseguiti durante la distribuzione. Per altre informazioni, vedere [Procedura: Modificare una configurazione di SharePoint distribuzione .](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md)|
|Destinazione distribuzione assembly|Determina dove si trovano gli *assembly di applicazione di SharePoint* . I valori validi per la posizione degli assembly sono *GlobalAssemblyCache* (valore predefinito) o *WebApplication*.<br /><br /> Se la proprietà *Sandboxed Solution* è impostata su **true**, questa proprietà è disabilitata.|
|Ritrazione automatica dopo il debug|Specifica se la soluzione distribuita viene ritratta automaticamente da SharePoint dopo l'esecuzione dell'applicazione in modalità di debug in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Quando la proprietà è selezionata, la soluzione viene ritratta quando l'IDE ritorna alla visualizzazione Progettazione dopo il debug. Quando non è selezionata, la soluzione non viene ritratta. Per altre informazioni, vedere [Ritrazione di una soluzione](/previous-versions/office/developer/sharepoint-2010/aa543958(v=office.14)).|
|Modifica configurazioni|Specifica la configurazione di distribuzione da usare per il progetto. Per altre informazioni, vedere [Procedura: Modificare una](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md) configurazione SharePoint distribuzione e [Distribuire,](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md)pubblicare e aggiornare SharePoint pacchetti della soluzione .|
|Abilita debug Silverlight (anziché il debug degli script)|Quando la proprietà è selezionata, il debugger di Silverlight si connette al processo di debug. Quando non è selezionata, il debugger di script si connette al processo di debug. Per altre informazioni, vedere [Cenni preliminari sul debug di Silverlight](/previous-versions/windows/).|
|Includi assembly in pacchetto|Specifica se l'assembly del progetto viene incluso o meno in un pacchetto in fase di compilazione.|
|Riga di comando post-distribuzione|Specifica i comandi da eseguire dopo avere distribuito la soluzione SharePoint. Questa riga supporta qualsiasi comando batch, nonché la risoluzione delle variabili MSBuild. Per altre informazioni, vedere [How to: Set SharePoint Deployment Commands](../sharepoint/how-to-set-sharepoint-deployment-commands.md).|
|Riga di comando pre-distribuzione|Specifica i comandi da eseguire prima della distribuzione della soluzione SharePoint. Questa riga supporta qualsiasi comando batch, nonché la risoluzione delle variabili MSBuild. Per altre informazioni, vedere [How to: Set SharePoint Deployment Commands](../sharepoint/how-to-set-sharepoint-deployment-commands.md).|
|File di progetto|Nome del file contenente le informazioni sulla build, la configurazione e altre informazioni sul progetto.|
|Cartella di progetto|Posizione del file di progetto nel sistema (sola lettura).|
|Sandboxed Solution|Specifica se il progetto deve essere distribuito come *soluzione in modalità sandbox*, nota anche come *soluzione creata dall'utente*. Le soluzioni in modalità sandbox non sono necessariamente attendibili. Un valore **true** indica che il progetto è distribuito come soluzione in modalità sandbox, mentre un valore **false** indica che il progetto è distribuito come soluzione farm. Per altre informazioni, vedere [Sandboxed Solution Considerations](../sharepoint/sandboxed-solution-considerations.md) e [Differences Between Sandboxed and Farm Solutions](../sharepoint/differences-between-sandboxed-and-farm-solutions.md).|
|Site URL|Specifica l' [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] del sito di destinazione per il progetto.|
|Elemento di avvio|Specifica il primo elemento del progetto da eseguire.|

 Quando si seleziona un file di elemento di SharePoint (ad esempio un flusso di lavoro o una funzionalità nel nodo Funzionalità), nella finestra Proprietà vengono visualizzate le proprietà seguenti:

### <a name="project-item-properties"></a>Project proprietà dell'elemento

|Nome proprietà|Descrizione|
|-------------------|-----------------|
|Risoluzione dei conflitti di distribuzione|Specifica l'azione da eseguire quando si distribuisce un elemento del progetto le cui proprietà sono identiche a quelle di un elemento già presente nel server. Per altre informazioni, vedere [Troubleshooting SharePoint Packaging and Deployment](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md).|
|Proprietà di funzionalità|Specifica un set di valori (archiviati come coppie chiave/valore) incluso in una funzionalità al momento della distribuzione in SharePoint. Dopo la distribuzione della funzionalità, è possibile accedere ai valori della proprietà nel codice. Per altre informazioni, vedere [Providing Packaging and Deployment Information in Project Items](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|
|Ricevitore di funzionalità|Fornisce il codice eseguito quando si verificano determinati eventi nella funzionalità che contiene un elemento di progetto. Per altre informazioni, vedere [Providing Packaging and Deployment Information in Project Items](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|
|Nome cartella|Nome della cartella dell'elemento di progetto SharePoint.|
|Riferimenti all'output del progetto|Specifica una dipendenza, ad esempio un assembly, che l'elemento di progetto deve eseguire. Per altre informazioni, vedere [Providing Packaging and Deployment Information in Project Items](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|
|Voci di controllo sicure|Specifica i controlli che gli utenti non attendibili possono modificare senza problemi per la sicurezza. Per altre informazioni, vedere [Providing Packaging and Deployment Information in Project Items](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|

### <a name="project-item-file-properties"></a>Project file dell'elemento

|Nome proprietà|Descrizione|
|-------------------|-----------------|
|Azione di compilazione|Specifica la relazione tra il file e i processi di compilazione e distribuzione. Per altre informazioni, vedere [Proprietà file](/previous-versions/visualstudio/visual-studio-2010/0c6xyb66\(v\=vs.100\)).|
|Copia nella directory di output|Specifica se i file di origine verranno copiati nella directory di output. I possibili valori sono i seguenti:<br /><br /> -   *Non copiare*<br />-   *Copia sempre*<br />-   *Copia se più recente*<br /><br /> Per altre informazioni, vedere [Proprietà file](/previous-versions/visualstudio/visual-studio-2010/0c6xyb66\(v\=vs.100\)).|
|Strumento personalizzato|Specifica il nome di uno strumento, se presente, che trasforma il file in fase di progettazione e inserisce l'output della trasformazione in un altro file. Ad esempio, un file di set di dati (.[!INCLUDE[TLA2#tla_xsd](../sharepoint/includes/tla2sharptla-xsd-md.md)]) ha uno strumento personalizzato predefinito. Per altre informazioni, vedere [Proprietà file](/previous-versions/visualstudio/visual-studio-2010/0c6xyb66\(v\=vs.100\)).|
|Spazio dei nomi dello strumento personalizzato|Spazio dei nomi in cui viene copiato l'output dello strumento personalizzato. Per altre informazioni, vedere [Proprietà file](/previous-versions/visualstudio/visual-studio-2010/0c6xyb66\(v\=vs.100\)).|
|Percorso di distribuzione|Percorso completo del file nel server SharePoint. Questo percorso è composto dalle sottoproprietà Radice distribuzione e Percorso distribuzione|
|Percorso distribuzione|Percorso relativo del file nel file SharePoint Server, ad esempio Workflow1 \\ . Il percorso completo per il file viene creato concatenando il valore *Deployment Path* alla fine del valore *Deployment Root* .<br /><br /> Se si seleziona il valore *RootFile*  per la proprietà *Tipo* di distribuzione , la proprietà Radice distribuzione viene modificata in , con un percorso completo \<SharePointRoot> \\ \<SharePointRoot> \Workflow1. \\ Per altre informazioni, vedere [Creazione di pacchetti e distribuzione SharePoint soluzioni](../sharepoint/packaging-and-deploying-sharepoint-solutions.md).|
|Deployment Root|Stringa. Cartella radice in cui viene distribuito il file nel server SharePoint. Ad esempio, \<SharePointRoot> \Template\Features \\ \<FeatureName> \\ .<br /><br /> Il valore della proprietà *Deployment Root* è determinato dall'impostazione di *Deployment Type* .|
|Tipo di distribuzione|Tipo di distribuzione del file, che determina il valore di *Deployment Root* . I possibili valori sono i seguenti:<br /><br /> NoDeployment: *\<no value>*<br /><br /> ElementManifest: *\<SharePointRoot> \Template\Features \\ \<FeatureName>*\\<br /><br /> ElementFile: *\<SharePointRoot> \Template\Features \\ \<FeatureName> \\*<br /><br /> TemplateFile: *\<SharePointRoot> \Template \\*<br /><br /> RootFile: *\<SharePointRoot>\\*<br /><br /> GlobalResource: *\<SharePointRoot> \Resources \\*<br /><br /> ClassResource: *\<ClassResourcePath>\\*<br /><br /> Per altre informazioni, vedere <xref:Microsoft.VisualStudio.SharePoint.DeploymentType>.|
|File Name|Nome del file o della cartella per il file dell'elemento.|
|Percorso completo|Percorso del file per l'elemento (sola lettura).|

## <a name="related-topics"></a>Argomenti correlati

|Titolo|Descrizione|
|-----------|-----------------|
|[Modelli di progetto e di elementi di progetto SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md)|Descrive i modelli di progetto e di elementi di progetto SharePoint disponibili in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].|
|[Procedura: Aggiungere elementi a un progetto SharePoint](../sharepoint/how-to-add-items-to-a-sharepoint-project.md)|Descrive come aggiungere elementi nuovi o esistenti a un progetto SharePoint in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .|
|[Procedura dettagliata: Creare una colonna del sito, un tipo di contenuto ed un elenco per SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)|Illustra la procedura dettagliata per creare un campo personalizzato, un tipo di contenuto, una definizione di elenco e un'istanza di elenco.|
|[Procedura: Creare un ricevitore di eventi](../sharepoint/how-to-create-an-event-receiver.md)|Viene descritto come aggiungere un ricevitore di eventi per il progetto creato in Procedura dettagliata: Creare una colonna [del sito,](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)un tipo di contenuto ed un elenco per SharePoint .|
|[Creare soluzioni SharePoint flusso di lavoro](../sharepoint/creating-sharepoint-workflow-solutions.md)|Descrive come creare progetti flusso di lavoro che includono form di associazione del flusso di lavoro e form di avvio del flusso di lavoro.|
|[Creare pagine per SharePoint](../sharepoint/creating-pages-for-sharepoint.md)|Descrive come creare pagine come pagine dell'applicazione, pagine del sito, pagine master e layout di pagina per SharePoint.|
|[Creare web part per SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)|Descrive come aggiungere controlli che consentono agli utenti di modificare direttamente il contenuto, l'aspetto e il comportamento delle pagine del sito SharePoint tramite un browser.|
|[Creare controlli riutilizzabili per web part o pagine dell'applicazione](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)|Descrive come creare controlli utente che possono essere utilizzati dalle pagine applicazione e dalle web part eseguite in SharePoint.|
|[Integrare i dati aziendali in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)|Descrive come integrare dati dei servizi Web e delle applicazioni server di back-end in un'applicazione di SharePoint.|
|[Creare definizioni di sito per SharePoint](../sharepoint/creating-site-definitions-for-sharepoint.md)|Descrive come creare definizioni di sito, ovvero modelli usati per creare i siti SharePoint.|
|[Importazione di elementi da un sito di SharePoint esistente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)|Descrive come importare elementi, come moduli e tipi di contenuto, da un sito SharePoint esistente in un progetto SharePoint in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .|
|[Utilizzo di moduli per includere file nella soluzione](../sharepoint/using-modules-to-include-files-in-the-solution.md)|Descrive come usare i moduli per la distribuzione di file dal progetto [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] al sito SharePoint.|
|[Esplorare SharePoint connessioni usando Esplora server](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)|Descrive come trovare siti SharePoint locali tramite Esplora Server.|
|[Fornire informazioni sulla creazione di pacchetti e sulla distribuzione negli elementi del progetto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)|Descrive come usare le proprietà dell'elemento di progetto per fornire informazioni sulla creazione di pacchetti e sulla distribuzione per i progetti, ad esempio voci di controllo sicure, riferimenti all'output del progetto e proprietà delle funzionalità.|
|[Procedura: Aggiungere e rimuovere cartelle mappate](../sharepoint/how-to-add-and-remove-mapped-folders.md)|Descrive in che modo le cartelle mappate possono essere aggiunte al progetto per semplificare l'accesso alle risorse di SharePoint.|
|[Considerazioni sulle soluzioni in modalità sandbox](../sharepoint/sandboxed-solution-considerations.md)|Descrive i problemi associati alle soluzioni in modalità sandbox.|
|[Sicurezza per le soluzioni SharePoint](../sharepoint/security-for-sharepoint-solutions.md)|Descrive le considerazioni sulla sicurezza relative allo sviluppo di soluzioni SharePoint in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].|
|[Finestra di dialogo selezione URL &#40;SharePoint sviluppo in Visual Studio&#41;](../sharepoint/url-picker-dialog-box-sharepoint-development-in-visual-studio.md)|Descrive una finestra di dialogo che è possibile usare per aggiungere riferimenti di percorso alle risorse nel progetto o nel server SharePoint locale.|

## <a name="see-also"></a>Vedi anche

- [Introduzione allo &#40;SharePoint sviluppo in Visual Studio&#41;](../sharepoint/getting-started-sharepoint-development-in-visual-studio.md)
- [Esplorare SharePoint connessioni usando Esplora server](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)
- [Build e debug delle soluzioni SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [Creare pacchetti e distribuire SharePoint soluzioni](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
