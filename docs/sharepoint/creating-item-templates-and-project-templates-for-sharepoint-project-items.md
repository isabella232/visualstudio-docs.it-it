---
title: Modelli di elemento/modelli di progetto per SharePoint di progetto
description: Creare modelli di elemento e modelli di progetto per SharePoint di progetto. Creare procedure guidate per modelli di elemento e modelli di progetto.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
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
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: edcc56e0b92d5a694793f54ede8056fbe81ce2b1
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126711447"
---
# <a name="create-item-templates-and-project-templates-for-sharepoint-project-items"></a>Creare modelli di elemento e modelli di progetto per SharePoint di progetto

Quando si definisce un tipo di SharePoint elemento di progetto personalizzato, è possibile associarlo a un modello di elemento o a un modello di progetto. Questa associazione consente ad altri sviluppatori di usare l'elemento di progetto in Visual Studio. È anche possibile creare una procedura guidata per il modello.

Ad esempio, Visual Studio non include un modello di progetto o un modello di elemento per l'aggiunta di un campo a un SharePoint sito. È possibile definire un tipo SharePoint elemento di progetto che rappresenta un campo e quindi costruire un modello di elemento che altri sviluppatori possono usare per aggiungere l'elemento campo a un SharePoint progetto. In caso contrario, è possibile creare un modello di progetto in modo che gli sviluppatori possano creare un nuovo SharePoint con l'elemento campo. In entrambi i casi, è anche possibile fornire una procedura guidata che viene visualizzata quando gli sviluppatori usano il modello. Questa procedura guidata consente di raccogliere informazioni dagli sviluppatori per configurare il nuovo elemento o progetto.

I modelli di elemento e *di progetto.zip* file che contengono file usati Visual Studio per creare un elemento o un progetto di progetto. Per altre informazioni sui concetti fondamentali dei modelli di elemento e dei modelli di progetto, vedere [Creare modelli di progetto e di elemento](../ide/creating-project-and-item-templates.md).

## <a name="create-item-templates"></a>Creare modelli di elementi
 Quando si crea un modello di elemento per un elemento di progetto SharePoint, sono sempre necessari alcuni file e file facoltativi che possono essere usati da determinati tipi di elementi di progetto. Per una procedura dettagliata che illustra come definire un tipo di elemento di progetto SharePoint e creare un modello di elemento per esso, vedere Procedura dettagliata: creare un elemento di progetto di azione personalizzata con un modello di [elemento, Parte 1.](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)

 Nella tabella seguente sono elencati i file necessari per creare un modello di elemento per un SharePoint di progetto.

|File obbligatorio|Descrizione|
|-------------------|-----------------|
|Un file *con estensione spdata*|Questo file XML specifica il contenuto e il comportamento predefinito dell'elemento di progetto. Questo file deve essere incluso nel modello di elemento. Per altre informazioni sul contenuto dei file *con estensione spdata,* vedere riferimento SharePoint [dello schema dell'elemento di progetto](../sharepoint/sharepoint-project-item-schema-reference.md).|
|Un file *con estensione vstemplate.*|Questo file fornisce Visual Studio le informazioni necessarie per visualizzare  il modello nella finestra di dialogo Aggiungi nuovo elemento e per creare un elemento di progetto dal modello. Questo file deve essere incluso nel modello di elemento. Per altre informazioni, vedere File [di metadati Visual Studio modello](/previous-versions/visualstudio/visual-studio-2010/xsxc3ete\(v\=vs.100\)).|
|Assembly Visual Studio di estensione che implementa <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> l'interfaccia .|Questo assembly definisce il comportamento in fase di esecuzione dell'elemento di progetto. Questo assembly deve essere incluso nel pacchetto VSIX con il modello di elemento. Per altre informazioni, vedere [Definire tipi di SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md) di progetto personalizzati e Distribuire estensioni per gli strumenti SharePoint in [Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).|

 Nella tabella seguente sono elencati alcuni dei file facoltativi più comuni che possono essere inclusi nel modello di elemento. Alcuni tipi di elementi di progetto potrebbero richiedere altri file non elencati qui.

| File facoltativo | Descrizione |
|----------------------| - |
| *Elements.xml* | Un file *di elemento Feature.* Questo file definisce l'interfaccia utente e il comportamento della personalizzazione creata dall'elemento di progetto. Ogni tipo di personalizzazione, ad esempio istanze di elenco, tipi di contenuto o azioni personalizzate, ha uno schema diverso che definisce il contenuto di questo file. Per altre informazioni, vedere [Blocco predefinito: funzionalità](/previous-versions/office/developer/sharepoint-2010/ee537350(v=office.14)) e [schemi di funzionalità](/previous-versions/office/developer/sharepoint-2010/ms414322(v=office.14)). |
| *Schema.xml* | File di schema per le definizioni di elenco. Per altre informazioni, vedere [Blocco predefinito: elenchi e raccolte documenti](/previous-versions/office/developer/sharepoint-2010/ee534985(v=office.14)) e [Schema.xml](/previous-versions/office/developer/sharepoint-2010/ms459356(v=office.14)). |
| *Webpart* | Un *file di definizione della web* part. Questo file contiene le impostazioni delle proprietà per una web part. Per altre informazioni, vedere [Blocco predefinito: Web part](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14)). |
| *.ascx* | Un ASP.NET UserControl. Questo file definisce l'interfaccia utente di una web part visiva. |
| *Aspx* | Un ASP.NET di pagina. Questo file contiene il markup XML che definisce una pagina dell'applicazione. |
| *File con estensione cs* *o vb* | Questi file di codice definiscono il comportamento delle personalizzazioni SharePoint con un modello di programmazione accessibile da Visual C# o da codice Visual Basic, ad esempio pagine dell'applicazione, web part e flussi di lavoro. |

## <a name="create-project-templates"></a>Creare modelli di progetto
 Quando si crea un SharePoint di progetto, sono sempre necessari alcuni file e file facoltativi che possono essere usati da determinati tipi di progetti. In genere, SharePoint progetti includono almeno un SharePoint di progetto. ma ciò non è obbligatorio. È ad esempio possibile definire un modello SharePoint di progetto che deve essere usato solo per distribuire SharePoint soluzioni create in altri progetti.

 Per una procedura dettagliata che illustra come definire un tipo di elemento di progetto SharePoint e creare un modello di progetto per esso, vedere Procedura dettagliata: Creare un elemento di progetto di colonna del sito con un modello di [progetto, Parte 1.](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)

 Nella tabella seguente sono elencati i file che devono essere inclusi in un SharePoint di progetto.

|File obbligatorio|Descrizione|
|-------------------|-----------------|
|Un file *con estensione vstemplate*|Questo file fornisce Visual Studio le informazioni necessarie per visualizzare il modello nella finestra di dialogo Nuovo **Project** e per creare un progetto dal modello. Per altre informazioni, vedere File [di metadati Visual Studio modello](/previous-versions/visualstudio/visual-studio-2010/xsxc3ete\(v\=vs.100\)).|
|Un *file con estensione csproj* o *vbproj*|Questo è il file di progetto. Definisce il contenuto e le impostazioni di configurazione del progetto.|
|*Package.package*|Questo file definisce il pacchetto di distribuzione per il progetto. Quando si usa Progettazione pacchetti per personalizzare il pacchetto della soluzione per il progetto, Visual Studio i dati relativi al pacchetto della soluzione in questo file.<br /><br /> Quando si crea un modello di progetto SharePoint personalizzato, è consigliabile includere solo il contenuto minimo richiesto nel file *Package.package* e configurare il pacchetto della soluzione usando le API nello spazio dei nomi in un'estensione associata al modello di <xref:Microsoft.VisualStudio.SharePoint.Packages> progetto. In questo caso, il modello di progetto è protetto dalle modifiche future alla struttura del file *Package.package.* Per un esempio che illustra come creare un file *Package.package* con solo il contenuto minimo richiesto, vedere Procedura dettagliata: Creare un elemento di progetto di colonna del sito con un modello di [progetto, parte 1.](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)<br /><br /> Se si vuole modificare direttamente il file *Package.package,* è possibile verificare il contenuto usando lo schema in *%Programmi (x86)%\Microsoft Visual Studio 11.0\Xml\Schemas\PackageModelSchema.xsd*.|
|*Package.Template.xml*|Questo file fornisce la base per il file manifesto della soluzione (*manifest.xml*) per il pacchetto della soluzione SharePoint ( con estensione *wsp*) generato dal progetto. È possibile aggiungere contenuto a questo file se si vuole specificare un comportamento che non deve essere modificato dagli utenti del tipo di progetto. Per altre informazioni, vedere [Building Block: Solutions](/previous-versions/office/developer/sharepoint-2010/ee537008(v=office.14)) and [Solution Schema](/sharepoint/dev/schema/solution-schema).<br /><br /> Quando si compila un pacchetto della soluzione dal progetto, Visual Studio unisce il  contenuto del file *Package.package* ePackage.Template.xmlfile nel file manifesto della soluzione. Per altre informazioni sulla compilazione di pacchetti di soluzioni, vedere [Procedura: Creare un](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)pacchetto SharePoint soluzione usando le MSBuild attività .|

 Nella tabella seguente sono elencati i file facoltativi che possono essere inclusi nel modello di progetto.

|File facoltativo|Descrizione|
|-------------------|-----------------|
|SharePoint (elementi di progetto)|È possibile includere uno o più file con estensione spdata che definiscono SharePoint tipi di elemento di progetto. Ogni file *con estensione spdata* deve avere un'implementazione corrispondente in un assembly di estensione incluso nel <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> pacchetto VSIX con il modello di progetto. Per altre informazioni, vedere Creare [modelli di elemento](#create-item-templates).<br /><br /> In genere, SharePoint progetti includono almeno un SharePoint di progetto. ma ciò non è obbligatorio.|
|*\<featureName>.feature*|Questo file definisce una funzionalità SharePoint usata per raggruppare diversi elementi di progetto per la distribuzione. Quando si usa Progettazione funzionalità per personalizzare una funzionalità nel progetto, Visual Studio i dati relativi alla funzionalità in questo file. Se si desidera raggruppare gli elementi del progetto in funzionalità diverse, è possibile includere più *file con estensione feature.*<br /><br /> Quando si crea un modello di progetto SharePoint personalizzato, è consigliabile includere solo il contenuto minimo richiesto in ogni file con estensione *feature* e configurare le funzionalità usando le API nello spazio dei nomi in un'estensione associata al modello di <xref:Microsoft.VisualStudio.SharePoint.Features> progetto. In questo caso, il modello di progetto è protetto dalle modifiche future alla struttura del file *con estensione feature.* Per un esempio che illustra come creare un file con estensione *feature* con solo il contenuto minimo richiesto, vedere Procedura dettagliata: Creare un elemento di progetto di colonna del sito con un modello di [progetto, parte 1.](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)<br /><br /> Se si vuole modificare direttamente un file con estensione *feature,* è possibile verificare il contenuto usando lo schema in *%Programmi (x86)%\Microsoft Visual Studio 11.0\Xml\Schemas\FeatureModelSchema.xsd.*|
|*\<featureName>File con estensione Template.xml*|Questo file fornisce la base per il file manifesto della funzionalità (*Feature.xml*) per ogni funzionalità generata dal progetto. È possibile aggiungere contenuto a questo file se si vuole specificare un comportamento che non deve essere modificato dagli utenti del tipo di progetto. Per altre informazioni, vedere [Blocco predefinito: funzionalità](/previous-versions/office/developer/sharepoint-2010/ee537350(v=office.14)) [ e ](/sharepoint/dev/schema/feature-xml-files)Feature.xmlfile.<br /><br /> Quando si compila un pacchetto della soluzione dal progetto, Visual Studio unisce il contenuto di ogni coppia di file con estensione *\<featureName> feature* e *\<featureName> Template.xml* file in un file manifesto della funzionalità. Per altre informazioni sulla compilazione di pacchetti di soluzioni, vedere [Procedura: Creare un](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)pacchetto SharePoint soluzione usando le MSBuild attività .|

## <a name="create-wizards-for-item-templates-and-project-templates"></a>Creare procedure guidate per modelli di elemento e modelli di progetto
 Dopo aver definito un SharePoint di elemento di progetto e associato a un elemento o a un modello di progetto, è anche possibile creare una procedura guidata. La procedura guidata viene visualizzata quando uno sviluppatore usa il modello di elemento per aggiungere l'elemento di progetto SharePoint a un progetto o quando uno sviluppatore usa il modello di progetto per creare un nuovo progetto che contiene l'elemento SharePoint progetto. La procedura guidata può essere usata per raccogliere informazioni dagli sviluppatori e inizializzare il nuovo SharePoint progetto.

 Per le procedure dettagliate che illustrano come creare procedure guidate per modelli di elemento e modelli di progetto, vedere Procedura dettagliata: Creare un elemento di progetto azione personalizzata con un modello di [elemento, Parte 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md) e Procedura dettagliata: Creare un elemento di progetto di colonna del sito con un modello di [progetto, Parte 2.](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)

## <a name="see-also"></a>Vedi anche

- [Definire tipi di SharePoint di progetto personalizzati](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Procedura dettagliata: Creare un elemento di progetto di azione personalizzata con un modello di elemento, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [Procedura dettagliata: Creare un elemento di progetto di azione personalizzata con un modello di elemento, parte 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)
- [Procedura dettagliata: Creare un elemento di progetto di colonna del sito con un modello di progetto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)
- [Procedura dettagliata: Creare un elemento di progetto di colonna del sito con un modello di progetto, parte 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)
- [Creare modelli di progetto e di elementi](../ide/creating-project-and-item-templates.md)
