---
title: Creazione di pacchetti & informazioni sulla distribuzione negli elementi di progetto
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: db805c308fd245554824997b24236eb2e2d80e62
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/28/2019
ms.locfileid: "72984211"
---
# <a name="provide-packaging-and-deployment-information-in-project-items"></a>Fornire informazioni sulla creazione di pacchetti e sulla distribuzione negli elementi di progetto
  Tutti gli elementi del progetto SharePoint in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dispongono di proprietà che è possibile utilizzare per fornire dati aggiuntivi quando il progetto viene distribuito in SharePoint. Di seguito sono riportate le proprietà:

- Proprietà funzionalità

- Ricevitori di funzionalità

- Riferimenti all'output del progetto

- Voci di controllo sicure

  Queste proprietà vengono visualizzate nella finestra **Proprietà** .

## <a name="feature-properties"></a>Proprietà delle funzionalità
 Utilizzare la proprietà caratteristiche **Proprietà** per specificare i dati utilizzati dalla funzionalità. I dati delle proprietà delle funzionalità sono un set di valori (archiviati come coppie chiave/valore) incluso in una funzionalità quando viene distribuito in SharePoint. Dopo la distribuzione della funzionalità, è possibile accedere ai valori della proprietà nel codice.

 Quando si aggiunge un valore della proprietà feature a un elemento del progetto, il valore viene aggiunto come elemento nel manifesto della funzionalità dell'elemento. In un progetto di modello di connettività dei dati aziendali (BDC), ad esempio, la proprietà della funzionalità ModelFileName viene visualizzata come segue:

```xml
<Property Key="ModelFileName" Value="BdcModel1\BdcModel1.bdcm" />
```

 Dopo aver impostato un valore della proprietà Feature, questo viene aggiunto come elemento FeatureProperty nel file con *estensione spdata* del progetto. Per informazioni sull'accesso alle proprietà in SharePoint, vedere [classe SPFeaturePropertyCollection](/previous-versions/office/sharepoint-server/ms461895(v=office.15)).

 I valori delle proprietà di funzionalità identici di tutti gli elementi del progetto vengono uniti nel manifesto della funzionalità. Tuttavia, se due elementi del progetto specificano la stessa chiave di proprietà della funzionalità con valori non corrispondenti, si verificherà un errore di convalida.

 Per aggiungere direttamente le proprietà della funzionalità al file di funzionalità ( *. feature*), chiamare il metodo del modello a oggetti di SharePoint [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] <xref:Microsoft.VisualStudio.SharePoint.Features.IPropertyCollection.Add%2A>. Se si utilizza questo metodo, tenere presente che la stessa regola sull'aggiunta di valori di proprietà di funzionalità identiche nelle proprietà della funzionalità si applica anche alle proprietà aggiunte direttamente al file di funzionalità.

## <a name="feature-receiver"></a>Ricevitore di funzionalità
 I ricevitori di funzionalità sono codice eseguito quando si verificano determinati eventi nella funzionalità che contiene un elemento di progetto. Ad esempio, è possibile definire i ricevitori di funzionalità che vengono eseguiti quando la funzionalità viene installata, attivata o aggiornata. Un modo per aggiungere un ricevitore di funzionalità consiste nell'aggiungerlo direttamente a una funzionalità, come descritto in [procedura dettagliata: aggiungere ricevitori di eventi di funzionalità](../sharepoint/walkthrough-add-feature-event-receivers.md). Un altro modo consiste nel fare riferimento a un nome della classe del ricevitore di funzionalità e a un assembly nella proprietà **Receiver feature** .

### <a name="direct-method"></a>Metodo diretto
 Quando si aggiunge un ricevitore di funzionalità direttamente a una funzionalità, un file di codice viene inserito nel nodo **funzionalità** in Esplora soluzioni. Quando si compila la soluzione SharePoint, il codice viene compilato in un assembly e distribuito in SharePoint. Per impostazione predefinita, le proprietà della funzionalità **assembly ricevitore** e **classe ricevitore** fanno riferimento al nome e all'assembly della classe.

### <a name="reference-method"></a>Reference (metodo)
 Un altro modo per aggiungere un ricevitore di funzionalità consiste nell'usare la proprietà **Receiver della funzionalità** di un elemento di progetto per fare riferimento a un assembly del ricevitore di funzionalità. Il valore della proprietà ricevitore funzionalità dispone di due sottoproprietà: **assembly** e **nome classe**. L'assembly deve usare il nome completo, "Strong" e il nome della classe deve essere il nome completo del tipo. Per altre informazioni, vedere [Assembly con nomi sicuri](/previous-versions/dotnet/netframework-4.0/wd40t7ad(v=vs.100)). Dopo aver distribuito la soluzione in SharePoint, la funzionalità Usa il ricevitore della funzionalità a cui si fa riferimento per gestire gli eventi di funzionalità.

 Al momento della compilazione della soluzione, i valori delle proprietà del ricevitore di funzionalità nella funzionalità e i relativi progetti si uniscono per impostare gli attributi ReceiverAssembly e ReceiverClass dell'elemento Feature nel manifesto della funzionalità del file della soluzione SharePoint (con*estensione wsp*). Pertanto, se i valori delle proprietà assembly e nome classe di un elemento di progetto e di una funzionalità sono entrambi specificati, i valori delle proprietà elemento progetto e funzionalità devono corrispondere. Se i valori non corrispondono, verrà visualizzato un errore di convalida. Se si vuole che un elemento del progetto faccia riferimento a un assembly del ricevitore di funzionalità diverso da quello usato dalla funzionalità, spostarlo in un'altra funzionalità.

 Se si fa riferimento a un assembly del ricevitore di funzionalità che non è già presente nel server, è necessario includere anche il file di assembly nel pacchetto. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] non lo aggiunge. Quando si distribuisce la funzionalità, il file di assembly viene copiato nel [!INCLUDE[TLA#tla_gac](../sharepoint/includes/tlasharptla-gac-md.md)] del sistema o nella cartella bin nella directory fisica di SharePoint. Per altre informazioni, vedere Procedura: [aggiungere e rimuovere assembly aggiuntivi](../sharepoint/how-to-add-and-remove-additional-assemblies.md).

 Per ulteriori informazioni sui ricevitori di funzionalità, vedere [funzionalità di ricevitore di eventi](/previous-versions/office/developer/sharepoint-2007/bb862634(v=office.12)) e eventi di [funzionalità](/previous-versions/office/developer/sharepoint-2010/ms469501(v=office.14)).

## <a name="project-output-references"></a>Riferimenti all'output del progetto
 La proprietà riferimenti all'output del progetto specifica una dipendenza, ad esempio un assembly, che deve essere eseguita dall'elemento del progetto. Si supponga, ad esempio, che la soluzione disponga di un progetto BDC e di un progetto di classe. Se il progetto BDC presenta una dipendenza dall'assembly restituito dal progetto di classe, è possibile fare riferimento all'assembly nella proprietà riferimenti output progetto del progetto BDC. Quando il progetto BDC viene incluso nel pacchetto, l'assembly dipendente viene incluso nel pacchetto.

 I riferimenti di output del progetto sono in genere assembly, ma in alcuni casi, ad esempio i progetti Silverlight, possono essere altri tipi di file.

 Per altre informazioni, vedere [procedura: aggiungere un riferimento all'output del progetto](../sharepoint/how-to-add-a-project-output-reference.md).

## <a name="safe-control-entries"></a>Voci di controllo sicure
 SharePoint fornisce un meccanismo di sicurezza, denominato voci di controllo sicure, per limitare l'accesso degli utenti non attendibili a determinati controlli. Per impostazione predefinita, SharePoint consente agli utenti non attendibili di caricare e creare pagine ASPX sul server SharePoint. Per impedire a questi utenti di aggiungere codice non sicuro alle pagine ASPX, SharePoint limita l'accesso ai *controlli sicuri*. I controlli sicuri sono i controlli ASPX e le web part designati come protetti e che possono essere utilizzati da qualsiasi utente nel sito. Per ulteriori informazioni, vedere [passaggio 4: aggiungere la Web part all'elenco dei controlli sicuri](/previous-versions/office/developer/sharepoint-2007/ms581321(v=office.12)).

 Ogni elemento del progetto SharePoint in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dispone di una proprietà denominata **voci di controllo sicure** con due sottoproprietà booleane: **Safe** e **Safe per script**. Con la proprietà Sicuro viene specificato se gli utenti non attendibili possono accedere a un controllo. La proprietà safe against script specifica se gli utenti non attendibili possono visualizzare e modificare le proprietà di un controllo.

 Si fa riferimento a voci di controllo sicure in base a un assembly. Per aggiungere voci di controllo sicure all'assembly di un progetto, immetterle nella proprietà **voci di controllo sicure** dell'elemento di progetto. Tuttavia, è anche possibile aggiungere voci di controllo sicure all'assembly di un progetto tramite la scheda **Avanzate** della **finestra di progettazione del pacchetto** quando si aggiunge un assembly aggiuntivo al pacchetto. Per altre informazioni, vedere [procedura: contrassegnare i controlli come controlli sicuri](../sharepoint/how-to-mark-controls-as-safe-controls.md) o [registrare un assembly Web part come controllo sicuro](/previous-versions/office/developer/sharepoint2003/dd587360(v=office.11)).

### <a name="xml-entries-for-safe-controls"></a>Voci XML per i controlli sicuri
 Quando si aggiunge una voce di controllo sicura a un elemento del progetto o all'assembly del progetto, un riferimento viene scritto nel manifesto del pacchetto nel formato seguente:

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
- [Pacchetto e distribuzione di soluzioni SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
- [Usare i moduli per includere i file nella soluzione](../sharepoint/using-modules-to-include-files-in-the-solution.md)
- [Estensione della creazione di pacchetti e della distribuzione di SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
