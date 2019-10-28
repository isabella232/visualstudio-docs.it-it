---
title: Modelli di elemento/modelli di progetto per gli elementi di progetto SharePoint
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 65bbd58bf9b3e0b399603a083615daccc382a98f
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/28/2019
ms.locfileid: "72981168"
---
# <a name="create-item-templates-and-project-templates-for-sharepoint-project-items"></a>Creare modelli di elementi e modelli di progetto per gli elementi di progetto SharePoint

Quando si definisce un tipo di elemento di progetto SharePoint personalizzato, è possibile associarlo a un modello di elemento o a un modello di progetto. Questa associazione consente ad altri sviluppatori di usare l'elemento del progetto in Visual Studio. È anche possibile creare una procedura guidata per il modello.

Ad esempio, Visual Studio non include un modello di progetto o un modello di elemento per l'aggiunta di un campo a un sito di SharePoint. È possibile definire un tipo di elemento di progetto SharePoint che rappresenta un campo e quindi creare un modello di elemento che altri sviluppatori possono utilizzare per aggiungere l'elemento campo a un progetto SharePoint. In alternativa, è possibile costruire un modello di progetto in modo che gli sviluppatori possano creare un nuovo progetto SharePoint con l'elemento campo. In entrambi i casi, è anche possibile fornire una procedura guidata che viene visualizzata quando gli sviluppatori usano il modello. Questa procedura guidata consente di raccogliere informazioni dagli sviluppatori per configurare il nuovo elemento o progetto.

I modelli di elemento e i modelli di progetto sono file con *estensione zip* che contengono file usati da Visual Studio per creare un progetto o un elemento di progetto. Per altre informazioni sulle nozioni di base dei modelli di elemento e dei modelli di progetto, vedere [creare modelli di progetto e di elemento](../ide/creating-project-and-item-templates.md).

## <a name="create-item-templates"></a>Creare modelli di elementi
 Quando si crea un modello di elemento per un elemento di progetto SharePoint, sono presenti alcuni file sempre necessari e file facoltativi che possono essere utilizzati da determinati tipi di elementi di progetto. Per una procedura dettagliata in cui viene illustrato come definire un tipo di elemento di progetto SharePoint e creare un modello di elemento, vedere [procedura dettagliata: creare un elemento di progetto azione personalizzata con un modello di elemento, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).

 Nella tabella seguente sono elencati i file necessari per creare un modello di elemento per un elemento del progetto SharePoint.

|File obbligatorio|Descrizione|
|-------------------|-----------------|
|Un file con *estensione spdata*|Questo file XML specifica il contenuto e il comportamento predefinito dell'elemento del progetto. Questo file deve essere incluso nel modello di elemento. Per ulteriori informazioni sul contenuto dei file con *estensione spdata* , vedere [riferimento allo schema degli elementi di progetto SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md).|
|Un file con *estensione vstemplate* .|Questo file fornisce Visual Studio con le informazioni necessarie per visualizzare il modello nella finestra di dialogo **Aggiungi nuovo elemento** e per creare un elemento di progetto dal modello. Questo file deve essere incluso nel modello di elemento. Per altre informazioni, vedere [file di metadati dei modelli di Visual Studio](/previous-versions/visualstudio/visual-studio-2010/xsxc3ete\(v\=vs.100\)).|
|Assembly di estensioni di Visual Studio che implementa l'interfaccia <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>.|Questo assembly definisce il comportamento in fase di esecuzione dell'elemento del progetto. Questo assembly deve essere incluso nel pacchetto VSIX con il modello di elemento. Per altre informazioni, vedere [definire tipi di elemento di progetto SharePoint personalizzati](../sharepoint/defining-custom-sharepoint-project-item-types.md) e [distribuire estensioni per gli strumenti di SharePoint in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).|

 Nella tabella seguente sono elencati alcuni dei file facoltativi più comuni che possono essere inclusi nel modello di elemento. Alcuni tipi di elementi di progetto potrebbero richiedere altri file non elencati qui.

| File facoltativo | Descrizione |
|----------------------| - |
| *Elements. XML* | File di *elemento della funzionalità* . Questo file definisce l'interfaccia utente e il comportamento della personalizzazione creata dall'elemento di progetto. Ogni tipo di personalizzazione, ad esempio le istanze di elenco, i tipi di contenuto o le azioni personalizzate, ha uno schema diverso che definisce il contenuto di questo file. Per altre informazioni, vedere [Building Block: features](/previous-versions/office/developer/sharepoint-2010/ee537350(v=office.14)) and [feature schemas](/previous-versions/office/developer/sharepoint-2010/ms414322(v=office.14)). |
| *Schema. XML* | Il file di schema per le definizioni di elenco. Per altre informazioni, vedere [blocco predefinito: elenchi e raccolte documenti](/previous-versions/office/developer/sharepoint-2010/ee534985(v=office.14)) e [schema. XML](/previous-versions/office/developer/sharepoint-2010/ms459356(v=office.14)). |
| *. WebPart* | Un file di *definizione della web part* . Questo file contiene le impostazioni delle proprietà per una Web part. Per altre informazioni, vedere [blocco predefinito: Web part](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14)). |
| *. ascx* | Un file UserControl ASP.NET. Questo file definisce l'interfaccia utente di una Web part visiva. |
| *. aspx* | Un file di paging ASP.NET. Questo file contiene il markup XML che definisce una pagina dell'applicazione. |
| file con *estensione cs* o *VB* | Questi file di codice definiscono il comportamento delle personalizzazioni di SharePoint che dispongono di un modello di programmazione a cui C# è possibile accedere dal codice Visual o Visual Basic, ad esempio pagine dell'applicazione, Web part e flussi di lavoro. |

## <a name="create-project-templates"></a>Creare modelli di progetto
 Quando si crea un modello di progetto SharePoint, sono presenti alcuni file sempre necessari e file facoltativi che possono essere utilizzati da determinati tipi di progetti. In genere, i progetti SharePoint includono almeno un elemento del progetto SharePoint. Tuttavia, questa operazione non è obbligatoria. Ad esempio, è possibile definire un modello di progetto SharePoint che deve essere utilizzato solo per distribuire soluzioni SharePoint create in altri progetti.

 Per una procedura dettagliata in cui viene illustrato come definire un tipo di elemento di progetto SharePoint e creare un modello di progetto per esso, vedere [procedura dettagliata: creare un elemento di progetto colonna del sito con un modello di progetto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).

 Nella tabella seguente sono elencati i file che devono essere inclusi in un modello di progetto SharePoint.

|File obbligatorio|Descrizione|
|-------------------|-----------------|
|Un file con *estensione vstemplate*|Questo file fornisce Visual Studio con le informazioni necessarie per visualizzare il modello nella finestra di dialogo **nuovo progetto** e per creare un progetto dal modello. Per altre informazioni, vedere [file di metadati dei modelli di Visual Studio](/previous-versions/visualstudio/visual-studio-2010/xsxc3ete\(v\=vs.100\)).|
|Un file con estensione *csproj* o *VBPROJ*|Questo è il file di progetto. Definisce il contenuto e le impostazioni di configurazione del progetto.|
|*Package. Package*|Questo file definisce il pacchetto di distribuzione per il progetto. Quando si usa progettazione pacchetti per personalizzare il pacchetto della soluzione per il progetto, Visual Studio archivia i dati relativi al pacchetto della soluzione in questo file.<br /><br /> Quando si crea un modello di progetto SharePoint personalizzato, è consigliabile includere solo il contenuto minimo richiesto nel file *Package. Package* e configurare il pacchetto della soluzione usando le API nello spazio dei nomi <xref:Microsoft.VisualStudio.SharePoint.Packages> in un'estensione che è associato al modello di progetto. In tal caso, il modello di progetto viene protetto da modifiche future alla struttura del file *Package. Package* . Per un esempio in cui viene illustrato come creare un file *Package. Package* con solo il contenuto minimo richiesto, vedere [procedura dettagliata: creare un elemento di progetto colonna del sito con un modello di progetto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).<br /><br /> Se si desidera modificare direttamente il file *Package. Package* , è possibile verificare il contenuto utilizzando lo schema in *% Program Files (x86)% \ Microsoft Visual Studio 11.0 \ Xml\Schemas\PackageModelSchema.xsd*.|
|*Package. template. XML*|Questo file costituisce la base per il file manifesto della soluzione (*manifest. XML*) per il pacchetto della soluzione SharePoint (con*estensione wsp*) generato dal progetto. È possibile aggiungere contenuto a questo file se si desidera specificare un comportamento che non deve essere modificato dagli utenti del tipo di progetto. Per altre informazioni, vedere [blocco predefinito: soluzioni](/previous-versions/office/developer/sharepoint-2010/ee537008(v=office.14)) e [schema della soluzione](/sharepoint/dev/schema/solution-schema).<br /><br /> Quando si compila un pacchetto della soluzione dal progetto, Visual Studio unisce il contenuto dei file Package. *Package* e *Package. template. XML* nel file manifesto della soluzione. Per altre informazioni sulla compilazione di pacchetti di soluzioni, vedere [procedura: creare un pacchetto di soluzione SharePoint usando le attività di MSBuild](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md).|

 Nella tabella seguente sono elencati i file facoltativi che possono essere inclusi nel modello di progetto.

|File facoltativo|Descrizione|
|-------------------|-----------------|
|SharePoint (elementi di progetto)|È possibile includere uno o più file con estensione spdata che definiscono i tipi di elementi del progetto SharePoint. Ogni file *. spdata* deve avere un'implementazione di <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> corrispondente in un assembly di estensione incluso nel pacchetto VSIX con il modello di progetto. Per altre informazioni, vedere [creare modelli di elementi](#create-item-templates).<br /><br /> In genere, i progetti SharePoint includono almeno un elemento del progetto SharePoint. Tuttavia, questa operazione non è obbligatoria.|
|*\<FeatureName >. feature*|Questo file definisce una funzionalità di SharePoint utilizzata per raggruppare diversi elementi di progetto per la distribuzione. Quando si usa progettazione funzionalità per personalizzare una funzionalità nel progetto, Visual Studio archivia i dati relativi alla funzionalità in questo file. Se si desidera raggruppare gli elementi del progetto in funzionalità diverse, è possibile includere più file con *estensione feature* .<br /><br /> Quando si crea un modello di progetto SharePoint personalizzato, è consigliabile includere solo il contenuto minimo richiesto in ogni file con estensione *feature* e configurare le funzionalità usando le API nello spazio dei nomi <xref:Microsoft.VisualStudio.SharePoint.Features> in un'estensione associata a modello di progetto. In tal caso, il modello di progetto viene protetto da modifiche future alla struttura del file con estensione *feature* . Per un esempio in cui viene illustrato come creare un file con *estensione feature* solo con il contenuto minimo richiesto, vedere [procedura dettagliata: creare un elemento di progetto colonna del sito con un modello di progetto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).<br /><br /> Se si desidera modificare direttamente un file con *estensione feature* , è possibile verificare il contenuto utilizzando lo schema in *% Program Files (x86)% \ Microsoft Visual Studio 11.0 \ Xml\Schemas\FeatureModelSchema.xsd*.|
|*\<> FeatureName. Template. XML*|Questo file costituisce la base per il file manifesto della funzionalità (*feature. XML*) per ogni funzionalità generata dal progetto. È possibile aggiungere contenuto a questo file se si desidera specificare un comportamento che non deve essere modificato dagli utenti del tipo di progetto. Per ulteriori informazioni, vedere la pagina relativa alla [creazione di blocchi: features](/previous-versions/office/developer/sharepoint-2010/ee537350(v=office.14)) e [feature. XML](/sharepoint/dev/schema/feature-xml-files) .<br /><br /> Quando si compila un pacchetto della soluzione dal progetto, Visual Studio unisce il contenuto di ogni coppia di *\<featurename >* file con estensione feature e *\<FeatureName >. File template. XML* in un file manifesto della funzionalità. Per altre informazioni sulla compilazione di pacchetti di soluzioni, vedere [procedura: creare un pacchetto di soluzione SharePoint usando le attività di MSBuild](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md).|

## <a name="create-wizards-for-item-templates-and-project-templates"></a>Creazione di procedure guidate per modelli di elementi e modelli di progetto
 Dopo aver definito un tipo di elemento di progetto SharePoint e averlo associato a un elemento o a un modello di progetto, è anche possibile creare una procedura guidata. La procedura guidata viene visualizzata quando uno sviluppatore utilizza il modello di elemento per aggiungere l'elemento di progetto SharePoint a un progetto o quando uno sviluppatore utilizza il modello di progetto per creare un nuovo progetto che contiene l'elemento del progetto SharePoint. È possibile utilizzare la procedura guidata per raccogliere informazioni dagli sviluppatori e per inizializzare il nuovo elemento del progetto SharePoint.

 Per le procedure dettagliate che illustrano come creare procedure guidate per i modelli di elemento e i modelli di progetto, vedere [procedura dettagliata: creare un elemento di progetto azione personalizzata con un modello di elemento, parte 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md) e [procedura dettagliata: creare un elemento di progetto colonna del sito con un progetto modello, parte 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).

## <a name="see-also"></a>Vedere anche

- [Definire i tipi di elementi di progetto SharePoint personalizzati](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Procedura dettagliata: creare un elemento di progetto azione personalizzata con un modello di elemento, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [Procedura dettagliata: creare un elemento di progetto azione personalizzata con un modello di elemento, parte 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)
- [Procedura dettagliata: creare un elemento di progetto colonna del sito con un modello di progetto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)
- [Procedura dettagliata: creare un elemento di progetto colonna del sito con un modello di progetto, parte 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)
- [Creare modelli di progetto e di elementi](../ide/creating-project-and-item-templates.md)
