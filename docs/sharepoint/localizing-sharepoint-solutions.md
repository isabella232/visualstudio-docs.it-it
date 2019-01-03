---
title: Localizzazione di soluzioni SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b653efc0cce8d8fb2b3e28b8e6c61e6371b4f6e9
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53837356"
---
# <a name="localize-sharepoint-solutions"></a>Localizzazione di soluzioni SharePoint

  Il processo di preparazione delle applicazioni in modo che possono essere usati in tutto il mondo è noto come localizzazione. Localizzazione consiste nella traduzione delle risorse per impostazioni cultura specifiche. Per altre informazioni, vedere [Globalizing and Localizing Applications](../ide/globalizing-and-localizing-applications.md). In questo argomento viene fornita una panoramica su come localizzare una soluzione di SharePoint.  
  
 Per localizzare una soluzione, rimuovere stringhe hardcoded dal codice ed estrarle in file di risorse. Un file di risorse è un [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]-basati su file con un *resx* estensione. Il file di risorse contiene le versioni tradotte delle stringhe utilizzate nella soluzione. Per altre informazioni, vedere [risorse nelle applicazioni](http://go.microsoft.com/fwlink/?LinkID=155844).  
  
> [!NOTE]  
>  Aggiungere solo le risorse di stringa ai file di risorse di soluzione SharePoint. Anche se l'Editor di risorse consente di aggiungere le risorse non di tipo stringa, non distribuire le risorse non di tipo stringa in SharePoint.  
  
## <a name="resource-files"></a>File di risorse
 Esistono tre tipi di file di risorse: predefinito, indipendente dalla lingua e specifico della lingua.  
  
|Tipo di File di risorse|Descrizione|  
|------------------------|-----------------|  
|Impostazione predefinita|Noto anche come risorse di fallback, file di risorse predefiniti contengono stringhe localizzate per le impostazioni cultura predefinite, ad esempio inglese. Vengono utilizzati se non viene trovati alcun file di risorse localizzati per la lingua specificata. Risorse predefinite non presentano file separati e vengono archiviate nell'assembly principale dell'applicazione.|  
|Indipendente dalla lingua|Un file di risorse contenente stringhe localizzate per una lingua, ma non una lingua specifica. Ad esempio, "fr" per il francese.|  
|Specifiche del linguaggio|Un file di risorse contenente stringhe localizzate per una lingua e le impostazioni cultura. Ad esempio, "fr-CA" per il francese canadese.|  
  
 Per altre informazioni, vedere [organizzazione gerarchica di risorse per la localizzazione](http://go.microsoft.com/fwlink/?LinkId=178360).  
  
 Per specificare i file di risorse predefiniti nei progetti SharePoint sviluppati in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], scegliere **lingua (paese invariabili)** nell'elenco delle impostazioni cultura del **Aggiungi risorsa** della finestra di dialogo quando si aggiungere un file di risorse.  
  
## <a name="localize-visual-studio-sharepoint-solutions"></a>Localizzazione di soluzioni di SharePoint di Visual Studio
 Quando si localizza una soluzione, è necessario considerare tutte le informazioni testuali che consente di visualizzare la soluzione agli utenti. I messaggi informativi, messaggi di errore e [!INCLUDE[TLA2#tla_ui](../sharepoint/includes/tla2sharptla-ui-md.md)] stringhe devono essere convertite e inserire le traduzioni nei file di risorse.  
  
 Ogni stringa in un file di risorse ha un identificatore univoco. Usare lo stesso identificatore per la stringa tradotta in ogni file di risorse. Ad esempio, se "String1" è l'identificatore per la prima stringa nel file di risorse predefinito, usare lo stesso identificatore per la prima stringa nei file di risorse specifici della lingua.  
  
 Esistono tre aree in genere si localizza in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] applicazioni SharePoint: funzionalità, markup delle pagine ASPX e codice. Ai fini dell'illustrazione, le sezioni seguenti si presuppongono una soluzione di SharePoint che si desidera localizzare in tedesco e giapponese. La lingua predefinita è l'inglese.  
  
### <a name="localize-features"></a>Localizzare le funzionalità
 Per localizzare una funzionalità, è necessario sostituire il titolo hardcoded e la descrizione della funzionalità con un'espressione che fa riferimento il titolo tradotta e la stringa nel file di risorse localizzate. Apportare questa modifica nel **Progettazione funzionalità** in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Per altre informazioni, vedere [Procedura: Localizzare una funzionalità](../sharepoint/how-to-localize-a-feature.md).  
  
 Per localizzare la funzionalità inglese in tedesco e giapponese, aggiungere tre elementi del progetto File di risorse al progetto: uno per l'inglese, uno per il tedesco e uno per il giapponese. Impossibile utilizzare i file di risorse di funzionalità per localizzare il markup ASPX o codice. sono necessari per i file di risorse separati.  
  
 Dopo aver creato la funzionalità file di risorse, aggiungervi le stringhe tradotte. Accedere alle stringhe localizzate con un'espressione nel formato seguente:  
  
```aspx-csharp  
$Resources:String ID  
```  
  
 Le risorse di funzionalità [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] vengono sempre denominate Resources. Se si seleziona una lingua diversa dall'inglese, quindi le impostazioni cultura [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] viene aggiunto al nome del file di risorse. Ad esempio, se si aggiunge un file di risorse di funzionalità di lingua inglese (impostazione predefinita), bensì *Resources*. Se si aggiunge una risorsa di funzionalità specifiche della lingua, selezionare una lingua giapponese (Giappone), il file è denominato *ja-JP. resx*. Nomi di file di risorse di funzionalità vengono assegnati automaticamente e non possono essere modificati.  
  
 L'ambito delle risorse di funzionalità è locale rispetto alla funzionalità a che vengono aggiunti. Per creare le risorse che possono essere usate da qualsiasi file di funzionalità o elemento nella soluzione, aggiungere un **File di risorse globali** elemento del progetto anziché un File di risorse di funzionalità. Il **File di risorse globali** elemento del progetto si trova nella **2010** cartella sotto **SharePoint** nel **Aggiungi nuovo elemento** nella finestra di dialogo. I file di risorse globali distribuire nella cartella \Resources della cartella radice di SharePoint.  
  
### <a name="localize-aspx-page-markup"></a>Localizzare il markup della pagina ASPX
 Per localizzare [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] pagine, aggiungere tre elementi del progetto File di risorse al progetto: uno per l'inglese, uno per il tedesco e uno per il giapponese. Se non hai localizzare codice oltre al markup, è invece possibile aggiungere file di risorse globali.  
  
 Specificare un nome per il file di risorse di lingua predefinita. Fornire i file di risorse localizzati lo stesso nome aggiunto con le impostazioni cultura specifiche della lingua [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]. Ad esempio, *MyAppResources.de-. resx* per il tedesco e *MyAppResources. ja-JP. resx* per il giapponese.  
  
 Impostare il **tipo di distribuzione** proprietà di ogni file di risorse da **AppGlobalResource**. In questo modo i file di risorse da distribuire nella cartella App_GlobalResources, dove sono disponibili per tutte le pagine ASPX e i controlli nella soluzione. La cartella App_GlobalResources si trova in C:\inetpub\wwwroot\wss\VirtualDirectories\\< numero porta\>\App_GlobalResources.  
  
> [!NOTE]  
>  Se si utilizzano file di risorse non globali, spostarli nella cartella di elementi del progetto per abilitare il tipo di distribuzione e altre proprietà specifiche di SharePoint.  
  
 Sono anche utilizzabile i file di risorse di markup ASPX per localizzare il codice. Se si utilizzano le risorse per localizzare codice oltre al markup ASPX, lasciare l'azione di compilazione impostazione della proprietà di ogni file come risorsa incorporata per la risorsa per la compilazione in un assembly satellite. Tuttavia, se si usa i file di risorse solo per localizzare il markup, è facoltativamente possibile modificare l'azione di compilazione al contenuto per impedire che il file venga compilato nell'assembly principale dell'applicazione.  
  
 Sostituire tutte le stringhe di proprietà impostati come hardcoded nel markup pagine e controlli ASPX con un'espressione nel formato seguente:  
  
```aspx-csharp  
<asp:<class> runat="server" Text="<%$Resources:<Resource File Name>, <String ID>%>" />  
```  
  
 Ad esempio:  
  
```aspx-csharp  
<asp:Button ID="btn1" runat="server" onclick="btn1_Click" Text="<%$Resources:Resource1,String7%>"></asp:Button>  
```  
  
 Per ASPX come testo, utilizzare un'espressione nel formato seguente:  
  
```aspx-csharp  
<asp:literal ID="<ID>" runat="server" Text="<%$Resources:<Resource File Name>, <String ID>%>" />  
```  
  
 Ad esempio:  
  
```aspx-csharp  
<asp:literal ID="Literal1" runat="server" Text="<%$Resources:Resource1, String9%>" />  
```  
  
 Per altre informazioni, vedere [Procedura: Localizzare il markup ASPX](../sharepoint/how-to-localize-aspx-markup.md).  
  
### <a name="localize-code"></a>Localizzare il codice
 Oltre a localizzare le stringhe di funzionalità e [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] markup, anche necessario localizzare le stringhe di messaggio e le stringhe di errore che vengono visualizzati nel codice della soluzione. Localizzato informativi e i messaggi di errore sono contenuti in assembly satellite. Gli assembly satellite contengono stringhe visibili agli utenti, ad esempio [!INCLUDE[TLA2#tla_ui](../sharepoint/includes/tla2sharptla-ui-md.md)] testo e messaggi di output, ad esempio le eccezioni.  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Usa il modello hub e spoke di .NET Framework standard. L'hub, o assembly del programma principale, contiene le risorse della lingua predefinita. Gli spoke, o gli assembly satellite, contengono le risorse specifiche della lingua. Per altre informazioni, vedere [Creazione del pacchetto e distribuzione delle risorse](http://go.microsoft.com/fwlink/?LinkId=179280). Gli assembly satellite vengono compilati dalla risorsa (*resx*) file. Quando si aggiungono file di risorse specifici della lingua per il progetto e il pacchetto della soluzione, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] compila i file di risorse in assembly satellite denominati *.resources.dll {nome progetto}*.  
  
 Come con markup ASPX, localizzare il codice dell'applicazione SharePoint tramite l'aggiunta di elementi di progetto di File di risorse separati al progetto. uno per la lingua predefinita e uno per ogni lingua localizzata. Tuttavia, come indicato in precedenza, se si dispone già di file di risorse per la localizzazione del markup ASPX, è possibile riutilizzarli per localizzare il codice. Se è necessario creare i file di risorse, che il file di risorse di lingua predefinita un nome di propria scelta con un *resx* estensione. Denominare i file di risorse localizzati lo stesso nome aggiunto con le impostazioni cultura specifiche della lingua [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]. Impostare la proprietà azione di compilazione di ogni file di risorse su risorsa incorporata per consentire la creazione di assembly di risorse satellite.  
  
 Per creare gli assembly satellite, compilare il progetto e quindi aggiungere i file come assembly aggiuntivi tramite il **avanzate** scheda della finestra di **Progettazione pacchetti**. Quando si aggiungono gli assembly, anteporre le impostazioni cultura [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] cartella al percorso, ad esempio *de-DE\\.resources.dll {nome elemento di progetto}*. In questo modo il pacchetto contenere i file con lo stesso nome.  
  
 Nel codice, sostituire le stringhe hardcoded con chiamate al <xref:System.Web.HttpContext.GetGlobalResourceObject%2A> metodo utilizzando la sintassi seguente:  
  
```aspx-csharp  
HttpContext.GetGlobalResourceObject("<Resource File Name>", "<String ID>")  
```  
  
 Per altre informazioni, vedere [Procedura: Localizzare il codice](../sharepoint/how-to-localize-code.md).  
  
#### <a name="web-part-code-localization"></a>Localizzazione del codice delle Web part
 Le Web part offrono una funzionalità dell'editor proprietà personalizzata che include gli attributi di codice che utilizzano stringhe hardcoded, quali WebDisplayName, Category e WebDescription. Per sostituire i valori di stringa per questi attributi, creare una classe separata che derivi dalla classe dell'attributo. In queste classi, impostare la proprietà dell'attributo. L'attributo della proprietà dipende dalla classe base. Ad esempio, la proprietà dell'attributo è DisplayNameValue e la proprietà dell'attributo WebDescription è DescriptionValue.  
  
 Nella classe derivata, fare riferimento all'ID stringa dal file di risorse e l'oggetto ResourceManager per ottenere il valore localizzato per l'ID di stringa. Restituisce questo valore di attributo dell'editor proprietà.  
  
## <a name="see-also"></a>Vedere anche
 [Procedura: Localizzare una funzionalità](../sharepoint/how-to-localize-a-feature.md)   
 [Procedura: Localizzare il markup ASPX](../sharepoint/how-to-localize-aspx-markup.md)   
 [Procedura: Localizzare il codice](../sharepoint/how-to-localize-code.md)   
 [Procedura: Aggiungere un file di risorse](../sharepoint/how-to-add-a-resource-file.md)   
 [Procedura: Usare un file di risorse per specificare nomi localizzati, proprietà e autorizzazioni](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)  
