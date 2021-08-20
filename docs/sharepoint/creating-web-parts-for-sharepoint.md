---
title: Creazione Web part per SharePoint | Microsoft Docs
description: Creare web part per SharePoint. Usando le web part, è possibile modificare il contenuto, l'aspetto e il comportamento delle pagine di un SharePoint sito usando un browser.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: overview
f1_keywords:
- Microsoft.SharePoint.WebControls.DateTimeControl
- Microsoft.SharePoint.WebControls.CssLink
- Microsoft.SharePoint.WebControls.RssLink
- Microsoft.SharePoint.WebControls.Theme
- Microsoft.SharePoint.WebControls.AspMenu
- Microsoft.SharePoint.WebControls.ListProperty
- Microsoft.SharePoint.WebControls.ProjectProperty
- Microsoft.SharePoint.WebControls.FormsDigest
- Microsoft.SharePoint.WebControls.ScriptLink
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, Web Parts
- Web Parts [SharePoint development in Visual Studio], designing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: a21ec422677dfa0a2de03f8822046000b06a0293
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122149286"
---
# <a name="create-web-parts-for-sharepoint"></a>Creare web part per SharePoint
  Usando le web part, è possibile modificare il contenuto, l'aspetto e il comportamento delle pagine di un SharePoint sito usando un browser. Le web part sono controlli lato server che vengono eseguiti all'interno di una pagina web part: sono i blocchi predefiniti delle pagine visualizzate in un SharePoint sito. Vedere [Blocco predefinito: Web part](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14)).

 È possibile creare ed eseguire il debug di web part in SharePoint sito usando modelli di Visual Studio.

## <a name="create-a-web-part-in-visual-studio"></a>Creare una web part in Visual Studio
 Creare una web part aggiungendo un **elemento web part** a qualsiasi SharePoint progetto. È possibile usare un **elemento Web part** in una soluzione in modalità sandbox o in una soluzione farm.

 Se si vuole progettare una web part visivamente usando una finestra di progettazione, creare un progetto Web **part** visiva o aggiungere un elemento Web **part** visiva a qualsiasi SharePoint progetto. È possibile usare un **elemento Web part visivo** solo in una soluzione farm.

### <a name="web-part-item"></a>Elemento web part
 Un **elemento web part** fornisce file che è possibile usare per progettare una web part per un SharePoint sito. Quando si aggiunge un **elemento web part,** Visual Studio crea una cartella nel progetto e quindi aggiunge diversi file alla cartella. La tabella seguente descrive ogni file.

|File|Descrizione|
|----------|-----------------|
|*Elements.xml*|Contiene informazioni utilizzate dal file di definizione della funzionalità nel progetto per distribuire la web part.|
|File con estensione webpart|Fornisce informazioni necessarie SharePoint visualizzare la web part in una raccolta web part.|
|File di codice|Contiene metodi che aggiungono controlli alla web part e che generano contenuto personalizzato all'interno della web part.|

 Per altre informazioni, vedere [Procedura: Creare una SharePoint web part](../sharepoint/how-to-create-a-sharepoint-web-part.md).

### <a name="visual-web-part-item"></a>Elemento web part visivo
 Una web part visiva è una web part creata tramite la finestra di progettazione di Visual Web Developer in Visual Studio. Una web part visiva funziona come qualsiasi altra web part. Per aggiungere controlli, ad esempio pulsanti e caselle di testo, a una web part, si aggiunge codice a un file XML. È tuttavia possibile aggiungere controlli a una web part visiva trascinandoli o copiandoli nella web part dalla casella degli strumenti Visual Studio **.** La finestra di progettazione genera quindi il codice necessario nel file XML. Vedere [Procedura: Creare SharePoint web part usando una finestra di progettazione.](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)

## <a name="sharepoint-controls"></a>SharePoint controlli
 Visual Studio fornisce alcuni controlli per la creazione di SharePoint, ad esempio le pagine dell'applicazione. Questi controlli vengono visualizzati nella casella **degli strumenti** in **SharePoint controlli**. La funzionalità per questi controlli deriva da [Microsoft.SharePoint. Spazio dei nomi WebControls,](/previous-versions/office/sharepoint-server/ms413880(v=office.15)) che ASP.NET controlli server utilizzati nelle pagine SharePoint sito e elenco.

|Nome del controllo|Descrizione|
|------------------|-----------------|
|[Aspmenu](/previous-versions/office/sharepoint-server/ms454108(v=office.15))|Inserisce un menu ASP. Per altre informazioni, vedere [Cenni preliminari sul controllo Menu](/previous-versions/ecs0x9w5(v=vs.140)).|
|[CssLink](/previous-versions/office/sharepoint-server/ms439048(v=office.15))|Inserisce un **elemento LINK** nella pagina *aspx* e applica uno o più fogli di stile esterni definiti da **CssRegistration.**|
|[DateTimeControl](/previous-versions/office/sharepoint-server/ms414993(v=office.15))|Inserisce un controllo DateTime nella *pagina aspx.*|
|[FormDigest](/previous-versions/office/sharepoint-server/ms416616(v=office.15))|Inserisce una convalida di sicurezza nella *pagina aspx*|
|[Proprietà ListProperty](/previous-versions/office/sharepoint-server/ms455032(v=office.15))|Restituisce una proprietà di un elenco specificato.|
|[ProjectProperty](/previous-versions/office/sharepoint-server/ms478990(v=office.15))|Restituisce una proprietà globale del sito Web corrente.|
|[RssLink](/previous-versions/office/sharepoint-server/ms457574(v=office.15))|Inserisce un collegamento a un feed RSS nella *pagina aspx.*|
|[ScriptLink](/previous-versions/office/sharepoint-server/ms411959(v=office.15))|Fornisce proprietà e metodi per la registrazione di risorse, ad esempio script, in una pagina in modo che possano essere richieste quando viene eseguito il rendering della pagina.|
|[Tema](/previous-versions/office/sharepoint-server/ms460735(v=office.15))|Applica un tema alla *pagina aspx.*|

## <a name="debug-a-web-part"></a>Eseguire il debug di una web part
 È possibile eseguire il debug SharePoint progetto che contiene una web part esattamente come si farebbe per altri Visual Studio progetto. Quando si avvia il debugger Visual Studio, Visual Studio apre il SharePoint sito.

 Per iniziare a eseguire il debug del codice, aggiungere la web part a una pagina web part in SharePoint.

 Per altre informazioni su come eseguire il debug di SharePoint progetti, vedere [Risolvere i SharePoint soluzioni](../sharepoint/troubleshooting-sharepoint-solutions.md).

## <a name="visual-web-part-limitations"></a>Limitazioni della web part visiva
 A partire Visual Studio, è possibile aggiungere web part visive alle soluzioni SharePoint sandbox e alle soluzioni farm. Tuttavia, le web part visive presentano le limitazioni seguenti:

- Le web part visive non supportano parametri sostituibili. Per altre informazioni, vedere [Parametri sostituibili.](../sharepoint/replaceable-parameters.md)

- I controlli utente o le web part visive non possono essere trascinati e rilasciati o copiati nelle web part visive. Questa azione causa un errore di compilazione.

- Le web part visive non supportano direttamente SharePoint token del server, ad esempio $SPUrl. Per altre informazioni, vedere "Restrizioni dei token nell'oggetto visivo Web part sandbox" nell'argomento Risolvere i SharePoint [soluzioni](../sharepoint/troubleshooting-sharepoint-solutions.md).

- Le web part visive in una soluzione sandbox occasionalmente ottengono l'errore "La richiesta di esecuzione del codice in modalità sandbox è stata rifiutata perché il servizio host del codice sandbox era troppo occupato per gestire la richiesta". Per altre informazioni su questo errore, vedere questo post nel blog del team [SharePoint developer.](/archive/blogs/sharepointdev/error-the-sandboxed-code-execution-request-was-refused-because-the-sandboxed-code-host-service-was-too-busy-to-handle-the-request-ricky-kirkham#10149157)

- Il debug JavaScript lato server non è supportato in Visual Studio, ma è supportato il debug JavaScript sul lato client.

   Anche se è possibile aggiungere JavaScript inline a un file di markup sul lato server, il debug non è supportato per i punti di interruzione aggiunti al markup. Per eseguire il debug di JavaScript, fare riferimento a un file JavaScript esterno nel file di markup e quindi impostare i punti di interruzione nel file JavaScript.

- Il debug del codice inline [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] deve essere eseguito nel file di codice generato anziché nel file di markup.

- Le web part visive non supportano l'uso della `<@ Assembly Src=` direttiva .

- SharePoint controlli Web e alcuni controlli non sono supportati [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] nell'ambiente SharePoint sandbox. Se in una web part visiva in una soluzione sandbox vengono usati controlli non supportati, viene visualizzato l'errore "Il nome del tipo o dello spazio dei nomi 'Theme' non esiste nello spazio dei nomi 'Microsoft'. SharePoint. Viene visualizzato WebControls'".

  Per altre informazioni sulle soluzioni sandbox, vedere [Differenze tra soluzioni sandbox e farm.](../sharepoint/differences-between-sandboxed-and-farm-solutions.md)

## <a name="create-older-style-sharepoint-based-web-parts"></a>Creare web part SharePoint basate su stili precedenti
 È possibile usare i modelli in Visual Studio per creare [!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)] web part personalizzate per SharePoint. [!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)] Le web part si basano sull'infrastruttura [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] web part e sono il tipo consigliato per i nuovi progetti.

 In pochissimi casi potrebbe essere necessario creare una web part usando lo stile precedente SharePoint web part basata su . È possibile usare Visual Studio per creare questi tipi di web part, ma Visual Studio non fornisce modelli progettati specificamente per facilitare la creazione.

 Per altre informazioni su quando creare una web part basata su SharePoint precedente, vedere Infrastruttura web [part in Windows SharePoint Services](/previous-versions/office/developer/sharepoint-2010/ms415560(v=office.14)). Per altre informazioni su come creare una web part usando lo stile precedente SharePoint web part basata su , vedere Procedura dettagliata Creazione di una web part di base [SharePoint web part](/previous-versions/office/ms452873(v=office.14)).

## <a name="related-topics"></a>Argomenti correlati

|Titolo|Descrizione|
|-----------|-----------------|
|[Procedura: Creare una SharePoint web part](../sharepoint/how-to-create-a-sharepoint-web-part.md)|Viene illustrato come creare web part per SharePoint pagine.|
|[Procedura: Creare una SharePoint web part usando una finestra di progettazione](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)|Viene illustrato come creare web part per SharePoint usando un'area di progettazione visiva.|
|[Procedura: Creare un controllo utente per una SharePoint o una web part dell'applicazione](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|Viene illustrato come creare controlli personalizzati e riutilizzabili che possono essere utilizzati dalle pagine dell'applicazione e dalle web part eseguite in SharePoint.|
|[Procedura dettagliata: Creare una web part per SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)|Viene descritto come progettare una web part per SharePoint.|
|[Procedura dettagliata: Creare una web part per SharePoint usando una finestra di progettazione](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)|Viene descritto come progettare una web part per SharePoint trascinando i controlli in un'area di progettazione visiva.|
|[Procedura dettagliata: Creare una web part Silverlight che visualizza OData per SharePoint](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md)|Viene descritto come progettare una web part per SharePoint che ospita un'applicazione Silverlight e visualizza i dati SharePoint elenchi.|