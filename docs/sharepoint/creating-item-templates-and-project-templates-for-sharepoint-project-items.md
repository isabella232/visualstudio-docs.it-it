---
title: Creazione elementi di modelli e i modelli di progetto per elementi di progetto SharePoint | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, creating custom templates
- .spdata files
- projects [SharePoint development in Visual Studio], creating custom templates
- SharePoint projects, creating custom templates
- SharePoint development in Visual Studio, creating custom project and item templates
- project items [SharePoint development in Visual Studio], creating custom templates
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d181891fb36645e4f246aa0c2238c12ea1dc4903
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2018
ms.locfileid: "51296008"
---
# <a name="create-item-templates-and-project-templates-for-sharepoint-project-items"></a>Creare modelli di elementi e modelli di progetto per elementi di progetto SharePoint
  Quando si definisce un tipo di elemento di progetto SharePoint personalizzato, è possibile associarlo a un modello di elemento o un modello di progetto. Questa associazione consente ad altri sviluppatori di usare l'elemento del progetto in Visual Studio. È anche possibile creare una procedura guidata per il modello.

 Ad esempio, Visual Studio non include un modello di progetto o un modello di elemento per aggiungere un campo a un sito di SharePoint. È possibile definire un tipo di elemento di progetto SharePoint che rappresenta un campo e quindi costruire un modello di elemento che altri sviluppatori possono usare per aggiungere l'elemento del campo a un progetto SharePoint. In alternativa, è possibile costruire un modello di progetto in modo che gli sviluppatori possono creare un nuovo progetto di SharePoint con l'elemento del campo. In entrambi i casi, è possibile fornire anche una procedura guidata che viene visualizzato quando gli sviluppatori utilizzano il modello. Questa procedura guidata può raccogliere informazioni da parte degli sviluppatori per configurare il nuovo elemento o progetto.

 Modelli di elementi e modelli di progetto vengono *zip* file che contengono i file che vengono utilizzati da Visual Studio per creare un progetto o elemento del progetto. Per altre informazioni sui concetti fondamentali di modelli di elementi e modelli di progetto, vedere [creare i modelli di progetto ed elemento](../ide/creating-project-and-item-templates.md).

## <a name="create-item-templates"></a>Creare modelli di elementi
 Quando si crea un modello di elemento per un elemento di progetto SharePoint, esistono alcuni file che sono sempre obbligatori e file facoltativi che potrebbero essere utilizzati da determinati tipi di elementi di progetto. Per una procedura dettagliata che illustra come definire un tipo di elemento di progetto SharePoint e creare un modello di elemento per tale, vedere [procedura dettagliata: creare l'elemento di progetto azione personalizzata con un modello di elemento, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).

 La tabella seguente elenca i file necessari per creare un modello di elemento per un elemento di progetto SharePoint.

|File obbligatorio|Descrizione|
|-------------------|-----------------|
|Un' *spdata* file|Questo file XML specifica il contenuto e il comportamento predefinito dell'elemento del progetto. Questo file deve essere incluso nel modello di elemento. Per altre informazioni sul contenuto di *spdata* i file, vedere [riferimento dello schema elementi di progetto SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md).|
|Oggetto *vstemplate* file.|Questo file fornisce le informazioni necessarie per visualizzare il modello in Visual Studio il **Aggiungi nuovo elemento** nella finestra di dialogo e creare un elemento del progetto dal modello. Questo file deve essere incluso nel modello di elemento. Per altre informazioni, vedere [metadati file modello di Visual Studio](/previous-versions/visualstudio/visual-studio-2010/xsxc3ete\(v\=vs.100\)).|
|Un assembly di estensioni di Visual Studio che implementa il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> interfaccia.|Questo assembly definisce il comportamento di runtime dell'elemento del progetto. Questo assembly deve essere incluso nel pacchetto VSIX con il modello di elemento. Per altre informazioni, vedere [definire tipi di elemento di progetto SharePoint personalizzati](../sharepoint/defining-custom-sharepoint-project-item-types.md) e [distribuire estensioni per gli strumenti di SharePoint in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).|

 Nella tabella seguente sono elencati alcuni dei più comuni file facoltativi che possono essere incluso nel modello di elemento. Alcuni tipi di elementi di progetto potrebbero richiedere altri file non elencati qui.


| File facoltativi | Descrizione |
|----------------------| - |
| *Elements. Xml* | Oggetto *elemento Feature* file. Questo file definisce l'interfaccia utente e il comportamento di personalizzazione creata dall'elemento del progetto. Ogni tipo di personalizzazione, ad esempio le istanze di elenco, i tipi di contenuto o azioni personalizzate, ha uno schema diverso che definisce il contenuto di questo file. Per altre informazioni, vedere [blocco predefinito: caratteristiche](http://go.microsoft.com/fwlink/?LinkId=169183) e [schemi per funzionalità](http://go.microsoft.com/fwlink/?LinkId=169192). |
| *File schema. Xml* | Il file di schema per le definizioni di elenco. Per altre informazioni, vedere [blocco predefinito: gli elenchi e raccolte documenti](http://go.microsoft.com/fwlink/?LinkId=177792) e [schema](http://go.microsoft.com/fwlink/?LinkId=177793). |
| *con estensione WebPart* | Oggetto *definizione di Web Part* file. Questo file contiene le impostazioni delle proprietà per una Web Part. Per altre informazioni, vedere [blocco predefinito: Web part](http://go.microsoft.com/fwlink/?LinkId=177791). |
| *. ascx* | Un file di UserControl di ASP.NET. Questo file definisce l'interfaccia utente di una Web Part visiva. |
| *. aspx* | Un file della pagina ASP.NET. Questo file contiene il markup XML che definisce una pagina dell'applicazione. |
| *. cs* oppure *vb* file | Questi file di codice definiscono il funzionamento delle personalizzazioni di SharePoint che dispone di un modello di programmazione che è possibile accedere da Visual c# o codice Visual Basic, ad esempio le pagine dell'applicazione, Web part e flussi di lavoro. |

## <a name="create-project-templates"></a>Creare modelli di progetto
 Quando si crea un modello di progetto SharePoint, esistono alcuni file che sono sempre file obbligatori e facoltativi che potrebbero essere utilizzati da determinati tipi di progetti. In genere, i progetti SharePoint includono almeno un elemento del progetto SharePoint. Tuttavia, ciò non necessario. Ad esempio, è possibile definire un modello di progetto SharePoint che dovrà essere utilizzato solo per distribuire soluzioni di SharePoint create in altri progetti.

 Per una procedura dettagliata che illustra come definire un tipo di elemento di progetto SharePoint e creare un modello di progetto per tale, vedere [procedura dettagliata: creare un elemento di progetto colonna del sito con un modello di progetto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).

 Nella tabella seguente sono elencati i file che devono essere inclusi in un modello di progetto SharePoint.

|File obbligatorio|Descrizione|
|-------------------|-----------------|
|Oggetto *vstemplate* file|Questo file fornisce le informazioni necessarie per visualizzare il modello in Visual Studio il **nuovo progetto** nella finestra di dialogo e creare un progetto dal modello. Per altre informazioni, vedere [metadati file modello di Visual Studio](/previous-versions/visualstudio/visual-studio-2010/xsxc3ete\(v\=vs.100\)).|
|Oggetto *file con estensione csproj* oppure *vbproj* file|Si tratta del file di progetto. Definisce il contenuto e le impostazioni di configurazione del progetto.|
|*Package. package*|Questo file definisce il pacchetto di distribuzione per il progetto. Quando si utilizza la finestra di progettazione di pacchetti per personalizzare il pacchetto della soluzione per il progetto, Visual Studio archivia i dati sul pacchetto della soluzione in questo file.<br /><br /> Quando si crea un modello di progetto SharePoint personalizzato, si consiglia di includere solo il contenuto minimo richiesto nel *package. package* file e che configuri il pacchetto della soluzione usando le API nel <xref:Microsoft.VisualStudio.SharePoint.Packages> spazio dei nomi in un'estensione che è associata il modello di progetto. In questo caso, il modello di progetto è protetto da future modifiche alla struttura del *package. package* file. Per un esempio che illustra come creare un *package. package* contenuto del file con solo il requisito minimo necessario, vedere [procedura dettagliata: creare un elemento di progetto colonna del sito con un modello di progetto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).<br /><br /> Se si desidera modificare il *package. package* direttamente il file, è possibile verificare il contenuto usando lo schema nel *% programmi (x86)%\Microsoft Visual Studio 11.0\Xml\Schemas\PackageModelSchema.xsd* .|
|*Package.Template.xml*|Questo file fornisce la base per il file manifesto della soluzione (*manifest*) per il pacchetto della soluzione SharePoint (*wsp*) che viene generato dal progetto. Se si desidera specificare un comportamento che non può essere modificata dagli utenti del tipo di progetto, è possibile aggiungere contenuto al file. Per altre informazioni, vedere [blocco predefinito: Solutions](http://go.microsoft.com/fwlink/?LinkId=169186) e [soluzione Schema](http://go.microsoft.com/fwlink/?LinkId=177794).<br /><br /> Quando si compila un pacchetto della soluzione dal progetto, Visual Studio consente di unire il contenuto del *package. package* e il *Package.Template.xml* nella soluzione di file manifesto. Per altre informazioni sulla creazione di pacchetti della soluzione, vedere [procedura: creare un pacchetto della soluzione SharePoint tramite le attività di MSBuild](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md).|

 Nella tabella seguente sono elencati i file facoltativi che possono essere incluso nel modello di progetto.

|File facoltativi|Descrizione|
|-------------------|-----------------|
|SharePoint (elementi di progetto)|È possibile includere uno o più file con estensione spdata che definiscono i tipi di elemento di progetto SharePoint. Ciascuna *spdata* file deve essere presente un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> implementazione in un assembly di estensione che è incluso nel pacchetto con il modello di progetto VSIX. Per altre informazioni, vedere [creazione di modelli di elemento](#creatingitemtemplates).<br /><br /> In genere, i progetti SharePoint includono almeno un elemento del progetto SharePoint. Tuttavia, ciò non necessario.|
|*\<featureName > feature*|Questo file definisce una funzionalità di SharePoint che viene usato per raggruppare diversi elementi di progetto per la distribuzione. Quando si utilizza la finestra di progettazione di funzionalità per personalizzare una funzionalità nel progetto, Visual Studio archivia i dati sulla funzionalità in questo file. Se si desidera raggruppare gli elementi del progetto in diverse funzionalità, è possibile includere più *feature* file.<br /><br /> Quando si crea un modello di progetto SharePoint personalizzato, si consiglia di includere solo il contenuto richiesto minimo in ognuno *feature* file e configurare le funzionalità usando le API nel <xref:Microsoft.VisualStudio.SharePoint.Features> dello spazio dei nomi in un estensione associata con il modello di progetto. In questo caso, il modello di progetto è protetto da future modifiche alla struttura del *feature* file. Per un esempio che illustra come creare un *feature* contenuto del file con solo il requisito minimo necessario, vedere [procedura dettagliata: creare un elemento di progetto colonna del sito con un modello di progetto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).<br /><br /> Se si desidera modificare una *feature* direttamente il file, è possibile verificare il contenuto usando lo schema nel *% programmi (x86)%\Microsoft Visual Studio 11.0\Xml\Schemas\FeatureModelSchema.xsd*.|
|*\<featureName >. Template. Xml*|Questo file fornisce la base per il file manifesto della funzionalità (*feature. XML*) per ogni funzione che viene generato dal progetto. Se si desidera specificare un comportamento che non può essere modificata dagli utenti del tipo di progetto, è possibile aggiungere contenuto al file. Per altre informazioni, vedere [blocco predefinito: caratteristiche](http://go.microsoft.com/fwlink/?LinkId=169183) e [feature. XML](http://go.microsoft.com/fwlink/?LinkId=177795) file.<br /><br /> Quando si compila un pacchetto della soluzione dal progetto, Visual Studio consente di unire il contenuto di ogni coppia di  *\<featureName > feature* file e  *\<featureName >. Template* i file in una funzionalità del file manifesto. Per altre informazioni sulla creazione di pacchetti della soluzione, vedere [procedura: creare un pacchetto della soluzione SharePoint tramite le attività di MSBuild](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md).|

## <a name="create-wizards-for-item-templates-and-project-templates"></a>Creazione di procedure guidate per i modelli di elemento e i modelli di progetto
 Dopo aver definito un tipo di elemento di progetto SharePoint e associarlo a un modello di elemento o un progetto, è possibile creare anche una procedura guidata. La procedura guidata viene visualizzato quando uno sviluppatore utilizza il modello di elemento per aggiungere l'elemento del progetto SharePoint a un progetto o quando uno sviluppatore utilizza il modello di progetto per creare un nuovo progetto che contiene l'elemento di progetto SharePoint. La procedura guidata può essere utilizzata per raccogliere informazioni da parte degli sviluppatori e inizializzare il nuovo elemento di progetto SharePoint.

 Per esercitazioni dettagliate che illustrano come creare le procedure guidate per i modelli di elemento e i modelli di progetto, vedere [procedura dettagliata: creare un elemento di progetto azione personalizzata con un modello di elemento, parte 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md) e [procedura dettagliata: creazione di un sito elemento di progetto colonna con un modello di progetto, parte 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).

## <a name="see-also"></a>Vedere anche

- [Definire tipi di elemento di progetto SharePoint personalizzati](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Procedura dettagliata: Creare un elemento di progetto azione personalizzata con un modello di elemento, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [Procedura dettagliata: Creare un elemento di progetto azione personalizzata con un modello di elemento, parte 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)
- [Procedura dettagliata: Creare un elemento di progetto colonna del sito con un modello di progetto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)
- [Procedura dettagliata: Creare un elemento di progetto colonna del sito con un modello di progetto, parte 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)
- [Creare modelli di progetto e di elementi](../ide/creating-project-and-item-templates.md)
