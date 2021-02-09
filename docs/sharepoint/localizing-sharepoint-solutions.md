---
title: Localizzazione di soluzioni SharePoint | Microsoft Docs
description: Localizzare le soluzioni di SharePoint rimuovendo le stringhe hardcoded dal codice e astraendole in file di risorse basati su XML (con estensione resx) contenenti stringhe tradotte.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: overview
f1_keywords:
- VS.SharePointTools.Project.GlobalAndFeatureResource
- VS.SharePoint.Project.AddResourceDialog
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- globalizing [SharePoint development in Visual Studio]
- localizing [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a216e57bc9da15fca625e71c7e0430d4fbf4164b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99873554"
---
# <a name="localize-sharepoint-solutions"></a>Localizzare le soluzioni SharePoint

  Il processo di preparazione delle applicazioni in modo che possano essere utilizzati in tutto il mondo è noto come localizzazione. La localizzazione sta traducendo le risorse in impostazioni cultura specifiche. Per ulteriori informazioni, vedere [globalizzazione e localizzazione delle applicazioni](../ide/globalizing-and-localizing-applications.md). In questo argomento viene fornita una panoramica su come localizzare una soluzione SharePoint.

 Per localizzare una soluzione, è necessario rimuovere le stringhe hardcoded dal codice ed estrarle in file di risorse. Un file di risorse è un [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] file basato su con estensione *resx* . Il file di risorse contiene le versioni tradotte delle stringhe usate nella soluzione. Per ulteriori informazioni, vedere [risorse nelle applicazioni](/previous-versions/dotnet/netframework-4.0/f45fce5x(v=vs.100)).

> [!NOTE]
> Aggiungere solo risorse stringa a file di risorse della soluzione SharePoint. Sebbene l'editor di risorse consenta di aggiungere risorse non di stringa, le risorse non di stringa non vengono distribuite in SharePoint.

## <a name="resource-files"></a>File di risorse
 Sono disponibili tre tipi di file di risorse: predefinito, indipendente dalla lingua e specifico della lingua.

|Tipo di file di risorse|Descrizione|
|------------------------|-----------------|
|Predefinito|Nota anche come risorsa di fallback, i file di risorse predefiniti contengono stringhe localizzate per le impostazioni cultura predefinite, ad esempio l'inglese. Vengono utilizzati se non è possibile trovare file di risorse localizzati per la lingua specificata. Le risorse predefinite non hanno file separati, ma vengono archiviate nell'assembly principale dell'applicazione.|
|Indipendente dalla lingua|Un file di risorse contenente stringhe localizzate per una lingua, ma non per impostazioni cultura specifiche. Ad esempio, "fr" per il francese.|
|Specifico della lingua|Un file di risorse che contiene le stringhe localizzate per una lingua e le impostazioni cultura. Ad esempio, "fr-CA" per il francese canadese.|

 Per ulteriori informazioni, vedere [organizzazione gerarchica di risorse per la localizzazione](../ide/globalizing-and-localizing-applications.md).

 Per specificare i file di risorse predefiniti nei progetti SharePoint sviluppati in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , scegliere **lingua inglese (paese invariante)** nell'elenco impostazioni cultura della finestra di dialogo **Aggiungi risorsa** quando si aggiunge un file di risorse.

## <a name="localize-visual-studio-sharepoint-solutions"></a>Localizzare le soluzioni di Visual Studio SharePoint
 Quando si localizza una soluzione, è necessario prendere in considerazione tutte le informazioni testuali visualizzate dalla soluzione agli utenti. I messaggi informativi, i messaggi di errore e le [!INCLUDE[TLA2#tla_ui](../sharepoint/includes/tla2sharptla-ui-md.md)] stringhe devono essere tradotti e tali traduzioni vengono inserite nei file di risorse.

 Ogni stringa in un file di risorse dispone di un identificatore univoco. Usare lo stesso identificatore per la stringa tradotta in ogni file di risorse. Se, ad esempio, "string1" è l'identificatore della prima stringa nel file di risorse predefinito, utilizzare lo stesso identificatore per la prima stringa nei file di risorse specifici della lingua.

 Sono disponibili tre aree in genere localizzate nelle [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] applicazioni SharePoint: funzionalità, markup della pagina aspx e codice. Ai fini dell'illustrazione, nelle sezioni seguenti si presuppone che si disponga di una soluzione SharePoint che si desidera localizzare in tedesco e giapponese. La lingua predefinita è l'italiano.

### <a name="localize-features"></a>Localizzare le funzionalità
 Per localizzare una funzionalità, è necessario sostituire il titolo hardcoded e la descrizione della funzionalità con un'espressione che faccia riferimento al titolo tradotto e alla stringa nel file di risorse localizzato. Questa modifica viene apportata in **Progettazione funzionalità** di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Per altre informazioni, vedere [procedura: localizzare una funzionalità](../sharepoint/how-to-localize-a-feature.md).

 Per localizzare la funzionalità inglese in tedesco e giapponese, aggiungere tre elementi del progetto file di risorse al progetto: uno per l'inglese, uno per il tedesco e uno per il giapponese. Non è possibile usare i file di risorse della funzionalità per localizzare il markup o il codice ASPX; sono necessari file di risorse separati.

 Dopo aver creato i file di risorse di funzionalità, aggiungervi le stringhe tradotte. Accedere alle stringhe localizzate con un'espressione nel formato seguente:

```aspx-csharp
$Resources:String ID
```

 Le risorse di funzionalità in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] sono sempre risorse denominate. Se si seleziona una lingua diversa dalla lingua inglese, vengono aggiunte impostazioni cultura [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] al nome del file di risorse. Se ad esempio si aggiunge un file di risorse della funzionalità lingua inglese (impostazione predefinita), questo viene denominato *Resources. resx*. Se si aggiunge una risorsa della funzionalità specifica della lingua selezionando le impostazioni cultura giapponese (Giappone), il file viene denominato *Resources. ja-JP. resx*. I nomi dei file di risorse di funzionalità vengono assegnati automaticamente e non possono essere modificati.

 L'ambito delle risorse della funzionalità è locale per la funzionalità a cui vengono aggiunti. Per creare risorse che possono essere usate da qualsiasi file di funzionalità o elemento nella soluzione, aggiungere un elemento di progetto **file di risorse globali** anziché un file di risorse di funzionalità. L'elemento del progetto **file di risorse globali** si trova nella cartella **2010** in **SharePoint** nella finestra di dialogo **Aggiungi nuovo elemento** . I file di risorse globali vengono distribuiti nella cartella \Resources della cartella radice di SharePoint.

### <a name="localize-aspx-page-markup"></a>Localizza markup della pagina ASPX
 Per localizzare [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] le pagine, è necessario aggiungere tre elementi del progetto file di risorse al progetto: uno per l'inglese, uno per il tedesco e uno per il giapponese. Se non è necessario localizzare il codice oltre al markup, è invece possibile aggiungere file di risorse globali.

 Consente di specificare un nome per il file di risorse della lingua predefinita. Assegnare ai file di risorse localizzati lo stesso nome aggiunto con le impostazioni cultura specifiche della lingua [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] . Ad esempio, *MyAppResources.de-de. resx* per il tedesco e *MyAppResources. ja-JP. resx* per il giapponese.

 Impostare la proprietà **tipo distribuzione** di ogni file di risorse su **AppGlobalResource**. In questo modo i file di risorse vengono distribuiti nella cartella App_GlobalResources, dove sono disponibili per tutte le pagine e i controlli ASPX nella soluzione. La cartella App_GlobalResources si trova in C:\inetpub\wwwroot\wss\VirtualDirectories \\<numero di porta \> \ App_GlobalResources.

> [!NOTE]
> Se si usano file di risorse non globali, spostarli nella cartella degli elementi del progetto per abilitare la proprietà del tipo di distribuzione e altre proprietà specifiche di SharePoint.

 È inoltre possibile utilizzare i file di risorse di markup ASPX per localizzare il codice. Se si utilizzano le risorse per localizzare il codice oltre al markup ASPX, lasciare l'impostazione della proprietà azione di compilazione di ogni file come risorsa incorporata per fare in modo che la risorsa venga compilata in un assembly satellite. Tuttavia, se si usano i file di risorse solo per localizzare il markup, è possibile modificare facoltativamente l'azione di compilazione in contenuto per impedire che il file venga compilato nell'assembly principale dell'applicazione.

 Sostituire tutte le stringhe di proprietà hardcoded nelle pagine ASPX e controllare il markup con un'espressione nel formato seguente:

```aspx-csharp
<asp:<class> runat="server" Text="<%$Resources:<Resource File Name>, <String ID>%>" />
```

 Ad esempio:

```aspx-csharp
<asp:Button ID="btn1" runat="server" onclick="btn1_Click" Text="<%$Resources:Resource1,String7%>"></asp:Button>
```

 Per ASPX come testo, usare un'espressione nel formato seguente:

```aspx-csharp
<asp:literal ID="<ID>" runat="server" Text="<%$Resources:<Resource File Name>, <String ID>%>" />
```

 Ad esempio:

```aspx-csharp
<asp:literal ID="Literal1" runat="server" Text="<%$Resources:Resource1, String9%>" />
```

 Per altre informazioni, vedere [procedura: localizzare il markup ASPX](../sharepoint/how-to-localize-aspx-markup.md).

### <a name="localize-code"></a>Localizzare il codice
 Oltre a localizzare le stringhe di funzionalità e [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] il markup, è necessario localizzare anche le stringhe di messaggio e le stringhe di errore visualizzate nel codice della soluzione. Messaggi informativi e di errore localizzati sono contenuti in assembly satellite. Gli assembly satellite contengono stringhe visibili agli utenti, ad esempio [!INCLUDE[TLA2#tla_ui](../sharepoint/includes/tla2sharptla-ui-md.md)] i messaggi di testo e di output come le eccezioni.

 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Usa il modello di .NET Framework Hub e spoke standard. L'hub, o l'assembly del programma principale, contiene le risorse di lingua predefinite. I spoke, o gli assembly satellite, contengono le risorse specifiche della lingua. Per altre informazioni, vedere [Creazione del pacchetto e distribuzione delle risorse](/previous-versions/dotnet/netframework-4.0/sb6a8618(v=vs.100)). Gli assembly satellite vengono compilati da file di risorse (con *estensione resx*). Quando si aggiungono file di risorse specifici della lingua al progetto e al pacchetto della soluzione, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Compila i file di risorse in assembly satellite denominati *{nome progetto} .resources.dll*.

 Come per il markup ASPX, localizzare il codice dell'applicazione SharePoint aggiungendo elementi del progetto file di risorse separate al progetto; uno per la lingua predefinita e uno per ogni lingua localizzata. Tuttavia, come indicato in precedenza, se si dispone già di file di risorse per la localizzazione del markup ASPX, è possibile riutilizzarli per localizzare il codice. Se è necessario creare file di risorse, assegnare al file di risorse della lingua predefinita un nome a scelta aggiunto con l'estensione *resx* . Denominare i file di risorse localizzati con lo stesso nome aggiunto con le impostazioni cultura specifiche della lingua [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] . Impostare la proprietà operazione di compilazione di ogni file di risorse su risorsa incorporata per consentire la creazione di assembly di risorse satellite.

 Per creare gli assembly satellite, compilare il progetto e quindi aggiungere i file come assembly aggiuntivi tramite la scheda **Avanzate** della **finestra di progettazione del pacchetto**. Quando si aggiungono gli assembly, anteporre una [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] cartella delle impostazioni cultura al percorso, ad esempio *DE-de \\ {nome elemento progetto} .resources.dll*. Ciò consente al pacchetto di contenere file con lo stesso nome.

 Nel codice sostituire le stringhe hardcoded con le chiamate al <xref:System.Web.HttpContext.GetGlobalResourceObject%2A> Metodo usando la sintassi seguente:

```aspx-csharp
HttpContext.GetGlobalResourceObject("<Resource File Name>", "<String ID>")
```

 Per altre informazioni, vedere [procedura: localizzare il codice](../sharepoint/how-to-localize-code.md).

#### <a name="web-part-code-localization"></a>Localizzazione del codice della web part
 Le web part includono una funzionalità dell'editor proprietà personalizzata che include gli attributi del codice che usano stringhe hardcoded, ad esempio WebDisplayName, Category e WebDescription. Per sostituire i valori di stringa per questi attributi, creare una classe separata che deriva dalla classe dell'attributo. In queste classi, impostare la proprietà dell'attributo. La proprietà Attribute dipende dalla classe base. Ad esempio, la proprietà dell'attributo WebDisplayName è DisplayNameValue e la proprietà dell'attributo WebDescription è DescriptionValue.

 Nella classe derivata, fare riferimento all'ID stringa dal file di risorse e all'oggetto ResourceManager per ottenere il valore localizzato per l'ID stringa. Restituisce questo valore all'attributo dell'editor proprietà.

## <a name="see-also"></a>Vedi anche
- [Procedura: localizzare una funzionalità](../sharepoint/how-to-localize-a-feature.md)
- [Procedura: localizzare il markup ASPX](../sharepoint/how-to-localize-aspx-markup.md)
- [Procedura: localizzare il codice](../sharepoint/how-to-localize-code.md)
- [Procedura: aggiungere un file di risorse](../sharepoint/how-to-add-a-resource-file.md)
- [Procedura: usare un file di risorse per specificare nomi localizzati, proprietà e autorizzazioni](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)
