---
title: Che fornisce informazioni sui pacchetti e distribuzione negli elementi di progetto | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.SafeControlEntries
- VS.SharePointTools.Project.ProjectOutputReference
- VS.SharePointTools.Project.FeatureProperties
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, safe controls
- project output references [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, feature properties
- SharePoint development in Visual Studio, project output references
- SharePoint development in Visual Studio, advanced packaging tools
- feature properties [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, feature receiver
- feature receiver [SharePoint development in Visual Studio]
- safe controls [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5ec29871cc6e5062f2d44fb8938872b5f0531f2a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53843021"
---
# <a name="provide-packaging-and-deployment-information-in-project-items"></a>Fornire le informazioni di creazione di pacchetti e distribuzione negli elementi di progetto
  Tutti gli elementi di progetto SharePoint in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dispongono di proprietà che è possibile usare per fornire dati aggiuntivi quando il progetto viene distribuito in SharePoint. Di seguito sono riportate le proprietà:  
  
- Proprietà funzionalità  
  
- Ricevitori di funzionalità  
  
- Riferimenti all'output del progetto  
  
- Voci di controllo sicure  
  
  Queste proprietà vengono visualizzate nel **proprietà** finestra.  
  
## <a name="feature-properties"></a>Proprietà della funzionalità
 Usare la **le proprietà della funzionalità** proprietà per specificare i dati che usa la funzionalità. I dati delle proprietà di funzionalità sono un set di valori (archiviati come coppie chiave/valore) che è incluso in una funzione quando viene distribuita in SharePoint. Dopo la distribuzione della funzionalità, è possibile accedere ai valori della proprietà nel codice.  
  
 Quando si aggiunge un valore di proprietà di funzionalità a un elemento del progetto, il valore viene aggiunto come elemento nel manifesto della funzionalità dell'elemento. In un progetto di modello di integrazione applicativa dei dati (BDC), ad esempio, la proprietà della funzionalità ModelFileName viene visualizzato come:  
  
```xml  
<Property Key="ModelFileName" Value="BdcModel1\BdcModel1.bdcm" />   
```  
  
 Dopo aver impostato un valore di proprietà della funzionalità, viene aggiunto come elemento di progetto FeatureProperty *spdata* file. Per informazioni sull'accesso alle proprietà di SharePoint, vedere [classe SPFeaturePropertyCollection](http://go.microsoft.com/fwlink/?LinkId=177391).  
  
 I valori delle proprietà funzionalità identiche da tutti gli elementi di progetto vengono uniti nel manifesto della funzionalità. Tuttavia, se due diversi elementi del progetto specificano la stessa chiave di proprietà di funzionalità con valori non corrispondenti, si verifica un errore di convalida.  
  
 Aggiungere le proprietà della funzionalità direttamente il file di funzionalità (*feature*), chiamare il [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] metodo modello a oggetti SharePoint <xref:Microsoft.VisualStudio.SharePoint.Features.IPropertyCollection.Add%2A>. Se si usa questo metodo, tenere presente che la stessa regola sull'aggiunta di valori di proprietà di funzionalità identiche nelle proprietà della funzionalità si applica anche alle proprietà aggiunte direttamente al file di funzionalità.  
  
## <a name="feature-receiver"></a>Ricevitore di funzionalità
 Ricevitori di funzionalità sono codice eseguito quando si verificano determinati eventi a un elemento del progetto che contiene funzionalità. Ad esempio, è possibile definire i ricevitori di funzionalità che vengono eseguite quando la funzionalità è installata, attivata o aggiornata. Per aggiungere un ricevitore di funzionalità consiste nell'aggiungerlo direttamente a una funzionalità, come descritto in [procedura dettagliata: Aggiungere ricevitori di eventi di funzionalità](../sharepoint/walkthrough-add-feature-event-receivers.md). È inoltre possibile fare riferimento a un nome di classe ricevitore di funzionalità e un assembly nel **ricevitore di funzionalità** proprietà.  
  
### <a name="direct-method"></a>Metodo diretto
 Quando si aggiunge un ricevitore di funzionalità a una funzionalità direttamente, un file di codice viene inserito sotto il **funzionalità** nodo in Esplora soluzioni. Quando si compila la soluzione di SharePoint, il codice viene compilato in un assembly e della distribuzione in SharePoint. Per impostazione predefinita, le proprietà della funzionalità **Assembly del ricevitore** e **classe del ricevitore** facciano riferimento al nome della classe e assembly.  
  
### <a name="reference-method"></a>Reference (metodo)
 Un altro modo per aggiungere un ricevitore di funzionalità consiste nell'usare la **ricevitore di funzionalità** proprietà di un elemento di progetto per fare riferimento a un assembly del ricevitore di funzionalità. Il valore della proprietà ricevitore di funzionalità presenta due sottoproprietà: **Assembly** e **Class Name**. L'assembly deve usare il nome completo, nome "avanzato" e il nome della classe deve essere il nome completo del tipo. Per altre informazioni, vedere [Assembly con nomi sicuri](http://go.microsoft.com/fwlink/?LinkID=169573). Dopo aver distribuito la soluzione in SharePoint, la funzionalità utilizza il ricevitore di funzionalità di cui viene fatto riferimento per gestire gli eventi di funzionalità.  
  
 Soluzione a fase di compilazione, la funzionalità di valori di proprietà ricevitore nella funzionalità e i relativi progetti unire tra loro per impostare gli attributi vengono e ReceiverClass dell'elemento Feature nel manifesto della funzionalità della soluzione SharePoint (*wsp* ) file. Pertanto, se vengono specificati entrambi i valori delle proprietà Assembly e il nome di classe di un elemento di progetto e una funzionalità, devono corrispondere i valori delle proprietà progetto elemento e funzionalità. Se i valori non corrispondono, si riceverà un errore di convalida. Se si desidera che un elemento di progetto per fare riferimento a un assembly del ricevitore di funzionalità diverso da quello utilizzato dalla relativa funzionalità, spostarlo in un'altra funzionalità.  
  
 Se si fa riferimento a un assembly del ricevitore di funzionalità che non sia già nel server, è necessario includere anche il file di assembly nel pacchetto; [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] non verrà aggiunto automaticamente. Quando si distribuisce la funzionalità, viene copiato il file di assembly a che il sistema [!INCLUDE[TLA#tla_gac](../sharepoint/includes/tlasharptla-gac-md.md)] o la cartella Bin nella directory fisica SharePoint. Per altre informazioni, vedere Procedura: [Procedura: Aggiungere e rimuovere assembly aggiuntivi](../sharepoint/how-to-add-and-remove-additional-assemblies.md).  
  
 Per altre informazioni sui ricevitori di funzionalità, vedere [ricevitore di eventi](http://go.microsoft.com/fwlink/?LinkID=169574) e [eventi di funzionalità](http://go.microsoft.com/fwlink/?LinkID=169575).  
  
## <a name="project-output-references"></a>Riferimenti all'output del progetto
 La proprietà di riferimenti all'Output di progetto specifica una dipendenza, ad esempio un assembly, che l'elemento di progetto deve essere eseguita. Si supponga, ad esempio, che la soluzione contiene un progetto di integrazione applicativa dei dati e un progetto di classe. Se il progetto di integrazione applicativa dei dati ha una dipendenza dall'assembly che vengono restituite dal progetto di classe, è possibile fare riferimento all'assembly nella proprietà di riferimenti all'Output di progetto del progetto di integrazione applicativa dei dati. Quando il progetto viene compresso, l'assembly dipendente è incluso nel pacchetto.  
  
 Riferimenti all'output del progetto sono in genere gli assembly, ma in alcuni casi (ad esempio, i progetti Silverlight) possono essere altri tipi di file.  
  
 Per altre informazioni, vedere [Procedura: Aggiungere un riferimento all'output del progetto](../sharepoint/how-to-add-a-project-output-reference.md).  
  
## <a name="safe-control-entries"></a>Voci di controllo sicure
 SharePoint fornisce un meccanismo di sicurezza, denominato voci di controllo sicure, per limitare l'accesso degli utenti non attendibili di determinati controlli. Per impostazione predefinita, SharePoint consente agli utenti non attendibili caricare e creare le pagine ASPX nel server SharePoint. Per impedire questi utenti di aggiungere il codice unsafe per le pagine ASPX, SharePoint l'accesso al limitato *controlli sicuri*. Controlli sicuri sono controlli ASPX e Web part designata come protetto e che può essere utilizzato da altri utenti nel sito. Per altre informazioni, vedere [passaggio 4: Aggiungere la Web Part all'elenco di controlli sicuri](http://go.microsoft.com/fwlink/?LinkID=171014).  
  
 Ogni elemento del progetto SharePoint in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ha una proprietà denominata **voci di controllo sicure** che presenta due sottoproprietà booleane: **-Safe** e **sicurezza Script**. Con la proprietà Sicuro viene specificato se gli utenti non attendibili possono accedere a un controllo. La proprietà di sicurezza Script consente di specificare se gli utenti non attendibili possono visualizzare e modificare le proprietà di un controllo.  
  
 Le voci di controllo sicura vengono fatto riferimento in base all'assembly. Per aggiungere le voci di controllo sicuro all'assembly del progetto inserendole in dell'elemento del progetto **voci di controllo sicure** proprietà. Tuttavia, è possibile aggiungere le voci di controllo sicuro all'assembly di un progetto tramite il **avanzate** scheda le **Progettazione pacchetti** quando si aggiunge un assembly aggiuntivo per il pacchetto. Per altre informazioni, vedere [Procedura: Contrassegnare i controlli come controlli sicuri](../sharepoint/how-to-mark-controls-as-safe-controls.md) oppure [la registrazione di un Assembly della Web Part come SafeControl](http://go.microsoft.com/fwlink/?LinkID=171013).  
  
### <a name="xml-entries-for-safe-controls"></a>Voci XML per i controlli sicuri
 Quando si aggiunge una voce di controllo sicura a un elemento del progetto o assembly del progetto, viene scritto un riferimento al manifesto del pacchetto nel formato seguente:  
  
```xml  
<Assemblies>  
    <Assembly Location="<assembly name>.dll"     
      DeploymentTarget="<'GlobalAssemblyCache' or 'WebApplication'">>  
        <SafeControls>  
            <SafeControl Assembly="<assembly name>.dll" Namespace=  
              "<SharePoint project name>" Safe="<true/false>"     
                TypeName="<control name>"   
                SafeAgainstScript="<true/false>" />  
        </SafeControls>  
    </Assembly>  
</Assemblies>  
```  
  
## <a name="see-also"></a>Vedere anche
 [Pacchetto e distribuzione delle soluzioni SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)   
 [Usare i moduli per includere file nella soluzione](../sharepoint/using-modules-to-include-files-in-the-solution.md)   
 [Estendere la distribuzione e creazione di pacchetti di SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)  
