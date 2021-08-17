---
title: Localizzazione SharePoint soluzioni | Microsoft Docs
description: Localizzare SharePoint soluzioni rimuovendo le stringhe hard-coded dal codice e astraendole in file di risorse (resx) basati su XML contenenti stringhe tradotte.
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
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: b6017f54f7e32ddcccc6e9e765d9a850af9a416b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122047674"
---
# <a name="localize-sharepoint-solutions"></a>Localizzare SharePoint soluzioni

  Il processo di preparazione delle applicazioni in modo che possano essere usate in tutto il mondo è noto come localizzazione. La localizzazione traduce le risorse in impostazioni cultura specifiche. Per altre informazioni, vedere [Globalizzazione e localizzazione di applicazioni.](../ide/globalizing-and-localizing-applications.md) In questo argomento viene fornita una panoramica su come localizzare una SharePoint soluzione.

 Per localizzare una soluzione, rimuovere le stringhe hard coded dal codice e astrarle in file di risorse. Un file di risorse è [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] un file basato su con estensione *resx.* Il file di risorse contiene le versioni tradotte delle stringhe usate nella soluzione. Per altre informazioni, vedere [Risorse nelle applicazioni.](/previous-versions/dotnet/netframework-4.0/f45fce5x(v=vs.100))

> [!NOTE]
> Aggiungere solo risorse stringa ai SharePoint di risorse della soluzione. Sebbene l'Editor risorse consenta di aggiungere risorse non di tipo stringa, le risorse non di tipo stringa non vengono distribuite in SharePoint.

## <a name="resource-files"></a>File di risorse
 Esistono tre tipi di file di risorse: predefinito, indipendente dalla lingua e specifico della lingua.

|Tipo di file di risorse|Descrizione|
|------------------------|-----------------|
|Predefinito|Noti anche come risorsa di fallback, i file di risorse predefiniti contengono stringhe localizzate per le impostazioni cultura predefinite, ad esempio l'inglese. Vengono usati se non è possibile trovare file di risorse localizzati per la lingua specificata. Le risorse predefinite non hanno file separati, ma vengono archiviate nell'assembly principale dell'applicazione.|
|Indipendente dalla lingua|File di risorse che contiene stringhe localizzate per una lingua, ma non per impostazioni cultura specifiche. Ad esempio, "fr" per il francese.|
|Specifico della lingua|File di risorse che contiene stringhe localizzate per una lingua e impostazioni cultura. Ad esempio, "fr-CA" per il francese canadese.|

 Per altre informazioni, vedere [Organizzazione gerarchica delle risorse per la localizzazione.](../ide/globalizing-and-localizing-applications.md)

 Per specificare i file di risorse predefiniti nei progetti di SharePoint che si sviluppano in , scegliere [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] **Invariant Language (Invariant Country)** nell'elenco delle impostazioni cultura della finestra di dialogo Aggiungi risorsa quando si aggiunge un file di risorse. 

## <a name="localize-visual-studio-sharepoint-solutions"></a>Localizzare Visual Studio SharePoint soluzioni
 Quando si localizza una soluzione, è consigliabile prendere in considerazione tutte le informazioni testuali visualizzate dagli utenti. I messaggi informativi, i messaggi di errore e [!INCLUDE[TLA2#tla_ui](../sharepoint/includes/tla2sharptla-ui-md.md)] le stringhe devono essere tradotti e le traduzioni devono essere inserite nei file di risorse.

 Ogni stringa in un file di risorse ha un identificatore univoco. Usare lo stesso identificatore per la stringa tradotta in ogni file di risorse. Ad esempio, se "String1" è l'identificatore per la prima stringa nel file di risorse predefinito, usare lo stesso identificatore per la prima stringa nei file di risorse specifici della lingua.

 Esistono tre aree in genere localizzate nelle [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] applicazioni SharePoint: funzionalità, markup della pagina ASPX e codice. A scopo illustrativo, le sezioni seguenti presuppongono che sia presente una soluzione SharePoint che si vuole localizzare in tedesco e giapponese. La lingua predefinita è l'italiano.

### <a name="localize-features"></a>Localizzare le funzionalità
 Per localizzare una funzionalità, è necessario sostituire il titolo e la descrizione hard coded della funzionalità con un'espressione che fa riferimento al titolo e alla stringa tradotti nel file di risorse localizzato. Questa modifica viene apportata in **Progettazione funzionalità** in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Per altre informazioni, [vedere Procedura: Localizzare una funzionalità.](../sharepoint/how-to-localize-a-feature.md)

 Per localizzare la funzionalità inglese in tedesco e giapponese, aggiungere tre elementi di progetto File di risorse al progetto: uno per l'inglese, uno per il tedesco e uno per il giapponese. I file di risorse delle funzionalità non possono essere usati per localizzare il codice o il markup ASPX. sono necessari file di risorse separati.

 Dopo aver creato i file di risorse delle funzionalità, aggiungervi stringhe tradotte. Accedere alle stringhe localizzate con un'espressione nel formato seguente:

```aspx-csharp
$Resources:String ID
```

 Le risorse delle funzionalità in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] sono sempre denominate Risorse. Se si seleziona una lingua diversa da Lingua invariante, le impostazioni cultura [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] vengono aggiunte al nome del file di risorse. Ad esempio, se si aggiunge un file di risorse di funzionalità della lingua invariante (predefinita), il file è *denominato Resources.resx.* Se si aggiunge una risorsa di funzionalità specifica della lingua selezionando le impostazioni cultura giapponese (Giappone), il file è denominato *Resources.ja-JP.resx.* I nomi dei file di risorse delle funzionalità vengono assegnati automaticamente e non possono essere modificati.

 L'ambito delle risorse delle funzionalità è locale per la funzionalità a cui vengono aggiunte. Per creare risorse che possono essere usate da qualsiasi funzionalità o file di elemento nella soluzione, aggiungere un elemento di progetto **File** di risorse globali anziché un file di risorse della funzionalità. **L'elemento di progetto File** di risorse globali si trova nella cartella **2010** in **SharePoint** nella finestra **di** dialogo Aggiungi nuovo elemento . I file di risorse globali vengono distribuiti nella cartella \Resources della SharePoint radice.

### <a name="localize-aspx-page-markup"></a>Localizzare il markup della pagina ASPX
 Per localizzare le pagine, aggiungere tre elementi di progetto File di risorse al progetto: uno per l'inglese, uno per il [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] tedesco e uno per il giapponese. Se non è necessario localizzare il codice oltre al markup, è invece possibile aggiungere file di risorse globali.

 Specificare un nome per il file di risorse della lingua predefinita. Assegnare ai file di risorse localizzati lo stesso nome aggiunto con le impostazioni cultura specifiche della [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] lingua. Ad esempio, *MyAppResources.de-DE.resx* per il tedesco e *MyAppResources.ja-JP.resx* per il giapponese.

 Impostare la **proprietà Tipo di** distribuzione di ogni file di risorse su **AppGlobalResource**. In questo modo i file di risorse vengono distribuiti nella cartella App_GlobalResources, in cui sono disponibili per tutte le pagine e i controlli ASPX nella soluzione. La App_GlobalResources si trova in C:\inetpub\wwwroot\wss\VirtualDirectories<numero di porta \\ \> \App_GlobalResources.

> [!NOTE]
> Se si usano file di risorse non globali, spostarli nella cartella dell'elemento di progetto per abilitare la proprietà Tipo di distribuzione e altre SharePoint specifiche del progetto.

 I file di risorse di markup ASPX possono essere usati anche per localizzare il codice. Se si usano le risorse per localizzare il codice oltre al markup ASPX, lasciare l'impostazione della proprietà Azione di compilazione di ogni file come Risorsa incorporata per fare in modo che la risorsa venga compilata in un assembly satellite. Tuttavia, se si usano i file di risorse solo per localizzare il markup, è possibile modificare facoltativamente Azione di compilazione in Contenuto per impedire che il file venga compilato nell'assembly principale dell'applicazione.

 Sostituire tutte le stringhe di proprietà hard-coded nelle pagine ASPX e nel markup dei controlli con un'espressione nel formato seguente:

```aspx-csharp
<asp:<class> runat="server" Text="<%$Resources:<Resource File Name>, <String ID>%>" />
```

 Esempio:

```aspx-csharp
<asp:Button ID="btn1" runat="server" onclick="btn1_Click" Text="<%$Resources:Resource1,String7%>"></asp:Button>
```

 Per ASPX come testo, usare un'espressione nel formato seguente:

```aspx-csharp
<asp:literal ID="<ID>" runat="server" Text="<%$Resources:<Resource File Name>, <String ID>%>" />
```

 Esempio:

```aspx-csharp
<asp:literal ID="Literal1" runat="server" Text="<%$Resources:Resource1, String9%>" />
```

 Per altre informazioni, vedere [Procedura: Localizzare il markup ASPX.](../sharepoint/how-to-localize-aspx-markup.md)

### <a name="localize-code"></a>Localizzare il codice
 Oltre a localizzare le stringhe di funzionalità e il markup, è necessario localizzare anche le stringhe di messaggio e le stringhe di errore visualizzate [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] nel codice della soluzione. I messaggi informativi e di errore localizzati sono contenuti negli assembly satellite. Gli assembly satellite contengono stringhe visibili agli utenti, ad esempio testo e [!INCLUDE[TLA2#tla_ui](../sharepoint/includes/tla2sharptla-ui-md.md)] messaggi di output come le eccezioni.

 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]usa il modello standard .NET Framework hub e spoke. L'hub, o assembly del programma principale, contiene le risorse della lingua predefinita. Gli spoke, o assembly satellite, contengono le risorse specifiche della lingua. Per altre informazioni, vedere [Creazione del pacchetto e distribuzione delle risorse](/previous-versions/dotnet/netframework-4.0/sb6a8618(v=vs.100)). Gli assembly satellite vengono compilati da file di risorse *(con estensione resx).* Quando si aggiungono file di risorse specifici della lingua al progetto e al pacchetto della soluzione, compila i file di risorse in assembly satellite denominati [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] *{Project Name}.resources.dll*.

 Come con il markup ASPX, localizzare SharePoint codice dell'applicazione aggiungendo elementi di progetto file di risorse separati al progetto; uno per la lingua predefinita e uno per ogni lingua localizzata. Tuttavia, come accennato in precedenza, se si dispone già di file di risorse per la localizzazione del markup ASPX, è possibile riutilizzarli per la localizzazione del codice. Se è necessario creare file di risorse, assegnare al file di risorse della lingua predefinito un nome di propria scelta, aggiungendo *l'estensione resx.* Assegnare ai file di risorse localizzati lo stesso nome aggiunto alle impostazioni cultura specifiche della [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] lingua. Impostare la proprietà Azione di compilazione di ogni file di risorse su Risorsa incorporata per abilitare la creazione di assembly di risorse satellite.

 Per creare gli assembly satellite, compilare il progetto e quindi aggiungere i file come assembly aggiuntivi tramite la **scheda** Avanzate di **Progettazione pacchetti**. Quando si aggiungono gli assembly, anteporre una cartella delle impostazioni cultura al percorso percorso, ad esempio [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] *de-DE \\ {Project Nome elemento}.resources.dll*. In questo modo il pacchetto può contenere file con lo stesso nome.

 Nel codice sostituire le stringhe hard-coded con chiamate al <xref:System.Web.HttpContext.GetGlobalResourceObject%2A> metodo usando la sintassi seguente:

```aspx-csharp
HttpContext.GetGlobalResourceObject("<Resource File Name>", "<String ID>")
```

 Per altre informazioni, vedere [Procedura: Localizzare il codice.](../sharepoint/how-to-localize-code.md)

#### <a name="web-part-code-localization"></a>Localizzazione del codice della web part
 Le web part includono una funzionalità dell'editor delle proprietà personalizzata che include attributi di codice che usano stringhe hard-coded, ad esempio WebDisplayName, Category e WebDescription. Per sostituire i valori stringa per questi attributi, creare una classe separata che deriva dalla classe dell'attributo. In tali classi impostare la proprietà dell'attributo. La proprietà dell'attributo dipende dalla classe di base. Ad esempio, la proprietà dell'attributo WebDisplayName è DisplayNameValue e la proprietà dell'attributo WebDescription è DescriptionValue.

 Nella classe derivata fare riferimento all'ID stringa dal file di risorse e all'oggetto ResourceManager per ottenere il valore localizzato per l'ID stringa. Restituire questo valore all'attributo dell'editor di proprietà.

## <a name="see-also"></a>Vedi anche
- [Procedura: Localizzare una funzionalità](../sharepoint/how-to-localize-a-feature.md)
- [Procedura: Localizzare il markup ASPX](../sharepoint/how-to-localize-aspx-markup.md)
- [Procedura: Localizzare il codice](../sharepoint/how-to-localize-code.md)
- [Procedura: Aggiungere un file di risorse](../sharepoint/how-to-add-a-resource-file.md)
- [Procedura: Usare un file di risorse per specificare nomi, proprietà e autorizzazioni localizzati](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)
