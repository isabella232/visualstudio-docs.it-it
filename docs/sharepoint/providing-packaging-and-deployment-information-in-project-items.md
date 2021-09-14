---
title: Creazione di & di distribuzione negli elementi di progetto
description: Aggiungere i dati di creazione di pacchetti e distribuzione SharePoint elementi del progetto usando le proprietà delle funzionalità, i ricevitori di funzionalità, i riferimenti all'output del progetto e le entità di controllo sicure.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 907bb1ed7131859dbf618c7b4b53e1d87b23e2ae
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126635603"
---
# <a name="provide-packaging-and-deployment-information-in-project-items"></a>Fornire informazioni sulla creazione di pacchetti e sulla distribuzione negli elementi del progetto
  Tutti SharePoint di progetto in hanno proprietà che è possibile usare per fornire dati aggiuntivi quando il progetto viene [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] distribuito in SharePoint. Di seguito sono riportate le proprietà:

- Proprietà di funzionalità

- Ricevitori di funzionalità

- Riferimenti all'output del progetto

- Voci di controllo sicure

  Queste proprietà vengono visualizzate nella **finestra** Proprietà.

## <a name="feature-properties"></a>Proprietà delle funzionalità
 Usare la **proprietà Proprietà** funzionalità per specificare i dati utilizzati dalla funzionalità. I dati delle proprietà delle funzionalità sono un set di valori (archiviati come coppie chiave/valore) inclusi in una funzionalità durante la distribuzione in SharePoint. Dopo la distribuzione della funzionalità, è possibile accedere ai valori della proprietà nel codice.

 Quando si aggiunge un valore di proprietà della funzionalità a un elemento di progetto, il valore viene aggiunto come elemento nel manifesto della funzionalità dell'elemento. In un progetto di modello BDC (Business Data Connectivity), ad esempio, la proprietà della funzionalità ModelFileName viene visualizzata come segue:

```xml
<Property Key="ModelFileName" Value="BdcModel1\BdcModel1.bdcm" />
```

 Dopo aver impostato un valore di Proprietà funzionalità, questo viene aggiunto come elemento FeatureProperty nel file *con estensione spdata del* progetto. Per informazioni sull'accesso alle proprietà in SharePoint, vedere [Classe SPFeaturePropertyCollection](/previous-versions/office/sharepoint-server/ms461895(v=office.15)).

 I valori identici delle proprietà delle funzionalità di tutti gli elementi di progetto vengono uniti nel manifesto della funzionalità. Tuttavia, se due elementi di progetto diversi specificano la stessa chiave di proprietà della funzionalità con valori non corrispondenti, si verifica un errore di convalida.

 Per aggiungere proprietà della funzionalità direttamente al file di funzionalità (*.feature*), chiamare il [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint metodo del modello a oggetti <xref:Microsoft.VisualStudio.SharePoint.Features.IPropertyCollection.Add%2A> . Se si usa questo metodo, tenere presente che la stessa regola sull'aggiunta di valori di proprietà di funzionalità identici in Proprietà funzionalità si applica anche alle proprietà aggiunte direttamente al file di funzionalità.

## <a name="feature-receiver"></a>Ricevitore di funzionalità
 I ricevitori di funzionalità sono codice che viene eseguito quando si verificano determinati eventi per la funzionalità contenitore di un elemento di progetto. Ad esempio, è possibile definire ricevitori di funzionalità che vengono eseguiti quando la funzionalità viene installata, attivata o aggiornata. Un modo per aggiungere un ricevitore di funzionalità è aggiungerlo direttamente a una funzionalità come descritto in [Procedura dettagliata: Aggiungere ricevitori di eventi di funzionalità](../sharepoint/walkthrough-add-feature-event-receivers.md). Un altro modo è fare riferimento al nome e all'assembly di una classe del ricevitore di funzionalità nella **proprietà Ricevitore di** funzionalità.

### <a name="direct-method"></a>Metodo diretto
 Quando si aggiunge direttamente un ricevitore di funzionalità a una funzionalità, un file di codice viene inserito sotto il **nodo Funzionalità** in Esplora soluzioni. Quando si compila la soluzione SharePoint, il codice viene compilato in un assembly e viene distribuito in SharePoint. Per impostazione predefinita, le proprietà della funzionalità **Assembly ricevitore** e **Classe ricevitore** fanno riferimento al nome della classe e all'assembly.

### <a name="reference-method"></a>Reference (metodo)
 Un altro modo per aggiungere un ricevitore di funzionalità è usare la proprietà **Ricevitore** di funzionalità di un elemento di progetto per fare riferimento a un assembly del ricevitore di funzionalità. Il valore della proprietà Ricevitore di funzionalità ha due **sottoproprietà: Assembly** e **Nome classe**. L'assembly deve usare il nome completo "sicuro" e il nome della classe deve essere il nome completo del tipo. Per altre informazioni, vedere [Assembly con nomi sicuri](/previous-versions/dotnet/netframework-4.0/wd40t7ad(v=vs.100)). Dopo aver distribuito la soluzione in SharePoint, la funzionalità usa il ricevitore di funzionalità a cui si fa riferimento per gestire gli eventi delle funzionalità.

 In fase di compilazione della soluzione, i valori delle proprietà del ricevitore di funzionalità nella funzionalità e nei relativi progetti vengono uniti per impostare gli attributi ReceiverAssembly e ReceiverClass dell'elemento Feature nel manifesto della funzionalità del file della soluzione SharePoint *(con estensione wsp).* Pertanto, se i valori delle proprietà Assembly e Nome classe di un elemento di progetto e di una funzionalità sono entrambi specificati, i valori delle proprietà dell'elemento di progetto e della funzionalità devono corrispondere. Se i valori non corrispondono, verrà visualizzato un errore di convalida. Se si vuole che un elemento di progetto fa riferimento a un assembly ricevitore di funzionalità diverso da quello utilizzato dalla funzionalità, spostarlo in un'altra funzionalità.

 Se si fa riferimento a un assembly del ricevitore di funzionalità che non è già presente nel server, è necessario includere anche il file di assembly stesso nel pacchetto. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] non lo aggiunge per l'utente. Quando si distribuisce la funzionalità, il file di assembly viene copiato nella cartella bin o del sistema nella directory SharePoint [!INCLUDE[TLA#tla_gac](../sharepoint/includes/tlasharptla-gac-md.md)] fisica. Per altre informazioni, vedere Procedura: [Procedura: Aggiungere e rimuovere assembly aggiuntivi.](../sharepoint/how-to-add-and-remove-additional-assemblies.md)

 Per altre informazioni sui ricevitori di funzionalità, vedere [Ricevitore di eventi di funzionalità](/previous-versions/office/developer/sharepoint-2007/bb862634(v=office.12)) ed Eventi di [funzionalità](/previous-versions/office/developer/sharepoint-2010/ms469501(v=office.14)).

## <a name="project-output-references"></a>Project riferimenti all'output
 La Project riferimenti di output specifica una dipendenza, ad esempio un assembly, che l'elemento di progetto deve eseguire. Si supponga, ad esempio, che la soluzione abbia un progetto BDC e un progetto di classe. Se il progetto BDC ha una dipendenza dall'assembly restituito dal progetto di classe, è possibile fare riferimento all'assembly nella proprietà riferimenti all'output Project del progetto BDC. Quando il progetto BDC viene incluso in un pacchetto, l'assembly dipendente viene incluso nel pacchetto.

 Project di output sono in genere assembly, ma in alcuni casi (ad esempio progetti Silverlight) possono essere altri tipi di file.

 Per altre informazioni, vedere [Procedura: Aggiungere un riferimento all'output del progetto](../sharepoint/how-to-add-a-project-output-reference.md).

## <a name="safe-control-entries"></a>Cassaforte voci di controllo
 SharePoint un meccanismo di sicurezza, denominato voci di controllo sicuro, per limitare l'accesso di utenti non attendibili a determinati controlli. Per impostazione predefinita, SharePoint utenti non attendibili di caricare e creare pagine ASPX SharePoint server. Per impedire a questi utenti di aggiungere codice unsafe alle pagine ASPX, SharePoint l'accesso a *controlli sicuri.* Cassaforte controlli sono controlli ASPX e web part designati come sicuri e che possono essere usati da qualsiasi utente del sito. Per altre informazioni, vedere [Passaggio 4: Aggiungere la web part all'elenco Cassaforte controlli](/previous-versions/office/developer/sharepoint-2007/ms581321(v=office.12)).

 Ogni SharePoint progetto in ha una proprietà denominata Cassaforte Control Entries con due sottoproprietà [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] booleane: **Cassaforte** e **Cassaforte Against Script**.  Con la proprietà Sicuro viene specificato se gli utenti non attendibili possono accedere a un controllo. La Cassaforte Against Script specifica se gli utenti non attendibili possono visualizzare e modificare le proprietà di un controllo.

 Cassaforte le voci di controllo vengono referenziati in base all'assembly. È possibile aggiungere voci di controllo sicure all'assembly di un progetto immettendole nella proprietà Cassaforte **Control Entries dell'elemento di** progetto. Tuttavia, è anche possibile aggiungere voci di controllo sicure  all'assembly  di un progetto tramite la scheda Avanzate in Progettazione pacchetti quando si aggiunge un assembly aggiuntivo al pacchetto. Per altre informazioni, vedere [Procedura: Contrassegnare](../sharepoint/how-to-mark-controls-as-safe-controls.md) i controlli come controlli sicuri o [Registrare](/previous-versions/office/developer/sharepoint2003/dd587360(v=office.11))un assembly di web part come Cassaforte controllo .

### <a name="xml-entries-for-safe-controls"></a>Voci XML per controlli sicuri
 Quando si aggiunge una voce di controllo sicuro a un elemento di progetto o all'assembly del progetto, nel manifesto del pacchetto viene scritto un riferimento nel formato seguente:

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

## <a name="see-also"></a>Vedi anche
- [Creare pacchetti e distribuire SharePoint soluzioni](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
- [Usare i moduli per includere i file nella soluzione](../sharepoint/using-modules-to-include-files-in-the-solution.md)
- [Estendere SharePoint creazione di pacchetti e distribuzione](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
