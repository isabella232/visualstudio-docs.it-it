---
title: Creazione di Web part per SharePoint | Microsoft Docs
description: Creazione di Web part per SharePoint. Utilizzando Web part è possibile modificare il contenuto, l'aspetto e il comportamento delle pagine di un sito di SharePoint tramite un browser.
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: bc9427d561817cb115473bddc71f2ba63475427e
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672795"
---
# <a name="create-web-parts-for-sharepoint"></a>Creazione di Web part per SharePoint
  Utilizzando Web part è possibile modificare il contenuto, l'aspetto e il comportamento delle pagine di un sito di SharePoint tramite un browser. Le web part sono controlli lato server che vengono eseguiti all'interno di una pagina Web part: si tratta dei blocchi predefiniti di pagine visualizzate in un sito di SharePoint. Vedere [blocco predefinito: Web part](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14)).

 È possibile creare ed eseguire il debug di Web part in un sito di SharePoint utilizzando i modelli di Visual Studio.

## <a name="create-a-web-part-in-visual-studio"></a>Creare una Web part in Visual Studio
 Creare una Web part aggiungendo un elemento **Web part** a qualsiasi progetto SharePoint. È possibile utilizzare un elemento **Web part** in una soluzione creata mediante sandbox o in una soluzione farm.

 Se si desidera progettare visivamente una Web part utilizzando una finestra di progettazione, creare un progetto **Web part visiva** o aggiungere un elemento **Web part visiva** a qualsiasi progetto SharePoint. È possibile utilizzare un elemento **Web part visiva** solo in una soluzione farm.

### <a name="web-part-item"></a>Elemento Web part
 Un elemento **Web part** fornisce i file che è possibile utilizzare per progettare una Web part per un sito di SharePoint. Quando si aggiunge un elemento **Web part** , Visual Studio crea una cartella nel progetto e quindi aggiunge diversi file alla cartella. Nella tabella seguente vengono descritti i singoli file.

|File|Descrizione|
|----------|-----------------|
|*Elements.xml*|Contiene informazioni che il file di definizione delle funzionalità nel progetto utilizza per distribuire la Web part.|
|file con estensione WebPart|Fornisce le informazioni necessarie a SharePoint per visualizzare la Web part in una raccolta web part.|
|File di codice|Contiene metodi che aggiungono controlli alla web part e che generano contenuto personalizzato all'interno della web part.|

 Per ulteriori informazioni, vedere [procedura: creare una Web part di SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md).

### <a name="visual-web-part-item"></a>Elemento Web part visiva
 Una Web part visiva è una Web part creata mediante la finestra di progettazione di Visual Web Developer in Visual Studio. Una Web part visiva funziona allo stesso modo di qualsiasi altra web part. Per aggiungere controlli, ad esempio pulsanti e caselle di testo, a una Web part, è necessario aggiungere codice a un file XML. Tuttavia, per aggiungere controlli a una Web part visiva, è possibile trascinarli o copiarli nella web part dalla **casella degli strumenti** di Visual Studio. La finestra di progettazione genera quindi il codice richiesto nel file XML. Vedere [procedura: creare una Web part di SharePoint tramite una finestra di progettazione](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md).

## <a name="sharepoint-controls"></a>Controlli di SharePoint
 Visual Studio fornisce alcuni controlli per la creazione di pagine di SharePoint, ad esempio le pagine dell'applicazione. Questi controlli vengono visualizzati nella **casella degli strumenti** in **controlli di SharePoint**. La funzionalità per questi controlli deriva dallo spazio dei nomi [Microsoft. SharePoint. WebControls](/previous-versions/office/sharepoint-server/ms413880(v=office.15)) , che contiene i controlli server ASP.NET che vengono utilizzati nelle pagine del sito e dell'elenco di SharePoint.

|Nome del controllo|Descrizione|
|------------------|-----------------|
|[AspMenu](/previous-versions/office/sharepoint-server/ms454108(v=office.15))|Inserisce un menu ASP. Per altre informazioni, vedere [Cenni preliminari sul controllo menu](/previous-versions/ecs0x9w5(v=vs.140)).|
|[CssLink](/previous-versions/office/sharepoint-server/ms439048(v=office.15))|Inserisce un elemento di **collegamento** nella pagina *aspx* e applica uno o più fogli di stile esterni definiti da **CssRegistration**.|
|[Attributo DateTimeControl](/previous-versions/office/sharepoint-server/ms414993(v=office.15))|Inserisce un controllo DateTime nella pagina *aspx* .|
|[FormDigest](/previous-versions/office/sharepoint-server/ms416616(v=office.15))|Inserisce una convalida della sicurezza nella pagina *aspx*|
|[ListProperty](/previous-versions/office/sharepoint-server/ms455032(v=office.15))|Restituisce una proprietà di un elenco specificato.|
|[ProjectProperty](/previous-versions/office/sharepoint-server/ms478990(v=office.15))|Restituisce una proprietà globale del sito Web corrente.|
|[RssLink](/previous-versions/office/sharepoint-server/ms457574(v=office.15))|Inserisce un collegamento a un feed RSS nella pagina *. aspx* .|
|[ScriptLink](/previous-versions/office/sharepoint-server/ms411959(v=office.15))|Fornisce proprietà e metodi per la registrazione di risorse, ad esempio script, in una pagina in modo che possano essere richieste quando viene eseguito il rendering della pagina.|
|[Tema](/previous-versions/office/sharepoint-server/ms460735(v=office.15))|Applica un tema alla pagina *aspx* .|

## <a name="debug-a-web-part"></a>Eseguire il debug di una Web part
 È possibile eseguire il debug di un progetto SharePoint che contiene una Web part così come si esegue il debug di altri progetti di Visual Studio. Quando si avvia il debugger di Visual Studio, Visual Studio apre il sito di SharePoint.

 Per iniziare a eseguire il debug del codice, aggiungere la Web part a una pagina Web part in SharePoint.

 Per ulteriori informazioni su come eseguire il debug di progetti SharePoint, vedere [risolvere i problemi di soluzioni SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md).

## <a name="visual-web-part-limitations"></a>Limitazioni della web part visiva
 A partire da Visual Studio, è possibile aggiungere web part visive alle soluzioni di SharePoint e alle soluzioni farm create mediante sandbox. Tuttavia, le web part visive presentano le limitazioni seguenti:

- Le web part visive non supportano parametri sostituibili. Per ulteriori informazioni, vedere [parametri sostituibili](../sharepoint/replaceable-parameters.md).

- I controlli utente o le web part visive non possono essere trascinati, eliminati o copiati in Web part visive. Questa azione causa un errore di compilazione.

- Le web part visive non supportano direttamente i token del server SharePoint, ad esempio $SPUrl. Per ulteriori informazioni, vedere "restrizioni dei token nell'oggetto visivo in sandbox Web part" nell'argomento [risolvere i problemi relativi alle soluzioni di SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md).

- Le web part visive in una soluzione in modalità sandbox ricevono occasionalmente l'errore "la richiesta di esecuzione del codice in modalità sandbox è stata rifiutata perché il servizio host del codice in modalità sandbox era troppo occupato per gestire la richiesta". Per ulteriori informazioni su questo errore, vedere questo post nel [Blog del team di sviluppo di SharePoint](/archive/blogs/sharepointdev/error-the-sandboxed-code-execution-request-was-refused-because-the-sandboxed-code-host-service-was-too-busy-to-handle-the-request-ricky-kirkham#10149157).

- Il debug JavaScript sul lato server non è supportato in Visual Studio, ma il debug JavaScript sul lato client è supportato.

   Sebbene sia possibile aggiungere codice JavaScript inline a un file di markup sul lato server, il debug non è supportato per i punti di interruzione aggiunti al markup. Per eseguire il debug di JavaScript, fare riferimento a un file JavaScript esterno nel file di markup, quindi impostare i punti di interruzione nel file JavaScript.

- Il debug del codice inline [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] deve essere eseguito nel file di codice generato anziché nel file di markup.

- Le web part visive non supportano l'utilizzo della `<@ Assembly Src=` direttiva.

- I controlli Web di SharePoint e alcuni [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] controlli non sono supportati nell'ambiente sandbox di SharePoint. Se i controlli non supportati vengono utilizzati in una Web part visiva in una soluzione creata mediante sandbox, viene visualizzato l'errore "il tipo o il nome dello spazio dei nomi ' Theme ' non esiste nello spazio dei nomi ' Microsoft. SharePoint. WebControls '".

  Per ulteriori informazioni sulle soluzioni create mediante sandbox, vedere [differenze tra soluzioni create mediante sandbox e soluzioni farm](../sharepoint/differences-between-sandboxed-and-farm-solutions.md).

## <a name="create-older-style-sharepoint-based-web-parts"></a>Creazione di Web part basate su SharePoint in stile obsoleto
 È possibile utilizzare i modelli in Visual Studio per creare [!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)] Web part personalizzate per SharePoint. [!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)] le web part sono basate sull'infrastruttura delle [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] Web part e sono il tipo consigliato per i nuovi progetti.

 In pochissimi casi, potrebbe essere necessario creare una Web part utilizzando la Web part basata su SharePoint di tipo obsoleto. È possibile utilizzare Visual Studio per creare questi tipi di Web part, ma Visual Studio non fornisce alcun modello progettato specificamente per facilitarne la creazione.

 Per ulteriori informazioni su quando si desidera creare una Web part basata su SharePoint di tipo obsoleto, vedere [infrastruttura di Web part in Windows SharePoint Services](/previous-versions/office/developer/sharepoint-2010/ms415560(v=office.14)). Per ulteriori informazioni su come creare una Web part utilizzando la Web part basata su SharePoint di stile precedente, vedere [procedura dettagliata per la creazione di una Web part di SharePoint di base](/previous-versions/office/ms452873(v=office.14)).

## <a name="related-topics"></a>Argomenti correlati

|Titolo|Descrizione|
|-----------|-----------------|
|[Procedura: creare una Web part di SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md)|Viene illustrato come creare Web part per le pagine di SharePoint.|
|[Procedura: creare una Web part di SharePoint tramite una finestra di progettazione](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)|Viene illustrato come creare Web part per SharePoint utilizzando un'area di progettazione visiva.|
|[Procedura: creare un controllo utente per una Web part o una pagina dell'applicazione di SharePoint](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|Viene illustrato come creare controlli personalizzati riutilizzabili che possono essere utilizzati dalle pagine dell'applicazione e dalle web part eseguite in SharePoint.|
|[Procedura dettagliata: creare una Web part per SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)|Viene descritto come progettare una Web part per SharePoint.|
|[Procedura dettagliata: creare una Web part per SharePoint tramite una finestra di progettazione](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)|Viene descritto come progettare una Web part per SharePoint trascinando i controlli in un'area di progettazione visiva.|
|[Procedura dettagliata: creare una Web part Silverlight che visualizza OData per SharePoint](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md)|Viene descritto come progettare una Web part per SharePoint che ospita un'applicazione Silverlight e Visualizza i dati dagli elenchi di SharePoint.|